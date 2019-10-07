# C系停止履歴FIND

**見つかったデータの一個前のデータをコピーする**

```
Sub C系停止履歴FIND()
Dim n As Long
Dim i As Long
Dim z As Long
Dim c As Range
Dim firstAddress As String
Dim sh1 As Worksheet
Dim sh2 As Worksheet
Dim sh3 As Worksheet
Dim r As Range
Dim Rng As Range

'sheet選択

Set sh1 = Sheets("データ入力")
Set sh2 = Sheets("データ抽出")
Set sh3 = Sheets("停止原因一覧")


Worksheets("データ抽出").Select

'各行の最終行数を数える

n = Range("A10").End(xlDown).Row

Set r = Range(Cells(11, 4), Cells(n, 5))

'指定セルを文字型に変換する

    
 For Each Rng In r
 Rng.NumberFormatLocal = "@"
 Rng.Value = Format(Rng.Value, "h:mm:ss")
 Next
   
'指定セルの時刻をfilterする



    With sh1.UsedRange.Columns(2)
    
        Set c = .Find(What:=sh2.Range("B11").Value, _
                       LookIn:=xlValues, LookAt:=xlPart)


'条件に当てはまるセルがあるかどうかを判定
        If Not c Is Nothing Then
           '最初のセルのアドレスを覚える
           firstAddress = c.Address

           '繰返し検索し、条件を満たすすべてのセルを検索する
           Do
               z = sh3.Range("A" & sh3.Rows.Count).End(xlUp).Row
               sh1.Range("B10:F10").Copy _
               Destination:=sh3.Range("A" & z).Offset(1)
               
               z = sh3.Range("A" & sh3.Rows.Count).End(xlUp).Row
               c.Resize(1, 5).Offset(-1, 0).Copy _
               Destination:=sh3.Range("A" & z).Offset(1)
                    
               Set c = .FindNext(c)
               If c Is Nothing Then Exit Do
           Loop Until c.Address = firstAddress
         End If
    End With
    
End Sub

```
