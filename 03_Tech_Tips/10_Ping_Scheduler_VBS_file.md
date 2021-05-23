# Excel Ping automation script

1. Copy below code to a text file.
2. Change the excel file path according to where the excel file is saved.
3. Rename the text file extension to *.vbs
4. Setup a task in the windows task scheduler (follow the instructions along from the video: https://www.youtube.com/watch?v=R2RXYCONe00)

```vb
'Input Excel File's Full Path
ExcelFilePath = "C:\Users\basdemo\Desktop\09_Ping_Tester_with_scheduler_monitor.xlsm"

'Input Module/Macro name within the Excel File
MacroPath = "Module1.Ping"

'Create an instance of Excel
Set ExcelApp = CreateObject("Excel.Application")

'Do you want this Excel instance to be visible?
ExcelApp.Visible = False

'Prevent any App Launch Alerts
ExcelApp.DisplayAlerts = False

'Open Excel File
Set wb = ExcelApp.Workbooks.Open(ExcelFilePath)

'Execute Macro Code
ExcelApp.Run MacroPath

'Save Excel File (if applicable)
wb.Save

'Reset Display Alerts Before Closing
ExcelApp.DisplayAlerts = True

'Close Excel File
wb.Close

'End instance of Excel
ExcelApp.Quit

'Leaves an onscreen message!
'MsgBox "Your Automated Task successfully ran at " & TimeValue(Now), vbInformation
```