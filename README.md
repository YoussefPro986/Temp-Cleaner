# Temp-Cleaner

Simple program that deletes temp recycle files Using Visual Basic

![TempCleaner32](https://user-images.githubusercontent.com/72635460/132961975-d0db3c22-0801-4adc-ae1f-86179c9c967a.PNG)

Screenshot from the application (Temp Cleaner V1.6)

The code used in programming the application is

Imports System.Threading
Imports System.IO
Public Class Form1
    Dim tempclean As Thread
    Dim tempFolderPath As String = System.IO.Path.GetTempPath()
    Private Sub Button2_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button2.Click
        Me.Hide()
    End Sub
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
        tempclean = New System.Threading.Thread(AddressOf clean)
        tempclean.Start()
        MsgBox("Temp Files Cleaned", MsgBoxStyle.Information)
 
    End Sub
    Sub clean()
        For Each filePath In Directory.GetFiles(tempFolderPath)
            Try
                File.Delete(filePath)
            Catch
            End Try
        Next
    End Sub
End Class
