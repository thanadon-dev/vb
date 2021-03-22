# VB.NET

```vb
Public Class Form1
    Dim sale As Double
    Dim table As New DataTable
    Dim Index As Integer

    Private Sub ComboBox1_SelectedIndexChanged(sender As Object, e As EventArgs) Handles ComboBox1.SelectedIndexChanged
        If ComboBox1.Text = "" Then
            MessageBox.Show("คุณยังไม่ได้เลือกรายการสินค้า", "ระวัง", MessageBoxButtons.OK, MessageBoxIcon.Exclamation)

        ElseIf ComboBox1.Text = "001" Then
            Label5.Text = "ดินสอ"
            Label6.Text = "10.75"
        ElseIf ComboBox1.Text = "002" Then
            Label5.Text = "ยางลบ"
            Label6.Text = "5.50"
        ElseIf ComboBox1.Text = "003" Then
            Label5.Text = "ปากกา"
            Label6.Text = "13.75"
        ElseIf ComboBox1.Text = "004" Then
            Label5.Text = "สมุด"
            Label6.Text = "15.00"
        ElseIf ComboBox1.Text = "002" Then
            Label5.Text = "ไม้บรรทัด"
            Label6.Text = "7.00"
        End If
    End Sub

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        If TextBox1.Text = "" Then
            MessageBox.Show("ยังไม่มีการเพิ่มข้อมูล", "ระวัง", MessageBoxButtons.OK, MessageBoxIcon.Exclamation)
            Exit Sub
        End If


        Dim aa As Double
        aa = (TextBox1.Text * Label6.Text)
        sale += aa


        table.Rows.Add(ComboBox1.Text, Label5.Text, TextBox1.Text.ToString, Label6.Text, TextBox1.Text * Label6.Text)
        DataGridView1.DataSource = table

        Label10.Text = sale.ToString("###,###.00")
        Label11.Text = (Label10.Text * 0.07).ToString("###,###.00")
        Label12.Text = Convert.ToDouble(Label10.Text) + Convert.ToDouble(Label11.Text)

    End Sub

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load

        table.Columns.Add("รหัสสินค้า")
        table.Columns.Add("ชื่อสินค้า")
        table.Columns.Add("ราคา")
        table.Columns.Add("จำนวน")
        table.Columns.Add("ราคารวม")
        DataGridView1.DataSource = table


        Label10.Text = sale.ToString("###,###.00")
        Label11.Text = (Label10.Text * 0.07).ToString("###,###.00")
        Label12.Text = Convert.ToDouble(Label10.Text) + Convert.ToDouble(Label11.Text)


    End Sub

    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click

        If DataGridView1.Rows.Count = 0 Then
            MessageBox.Show("ไม่มีข้อมูลในตาราง", "ระวัง", MessageBoxButtons.OK, MessageBoxIcon.Exclamation)
        ElseIf DataGridView1.CurrentRow.Selected = 0 Then
            MessageBox.Show("คุณยังไม่ได้เลือกข้อมูล", "ระวัง", MessageBoxButtons.OK, MessageBoxIcon.Exclamation)
        Else

            Dim del As String
            del = DataGridView1.CurrentRow.Cells(0).Value.ToString

            Dim res As DialogResult = MessageBox.Show("คุณต้องกาครลบ" & del & "หรือไม่", "ระวัง", MessageBoxButtons.YesNo, MessageBoxIcon.Information)


            If res = DialogResult.Yes Then
                sale -= (DataGridView1.Rows(Index.ToString).Cells(4).Value)
                DataGridView1.Rows.RemoveAt(Index.ToString)

                Label10.Text = sale.ToString("###,###.00")
                Label11.Text = (Label10.Text * 0.07).ToString("###,###.00")
                Label12.Text = Convert.ToDouble(Label10.Text) + Convert.ToDouble(Label11.Text)


            End If

        End If

    End Sub

    Private Sub Button3_Click(sender As Object, e As EventArgs) Handles Button3.Click
        Dim res As DialogResult = MessageBox.Show("คุณต้องการือไม่", "ระวัง", MessageBoxButtons.YesNo, MessageBoxIcon.Information)


        If res = DialogResult.Yes Then
            Me.Close()
        End If

    End Sub


End Class
```
