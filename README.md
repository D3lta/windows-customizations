# Windows Customizations


# Windows 11
## User Interface

### Context menu
```
# Disable
reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

# Revert
reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f
```

## Services
### Bluetooth

BTAGService
Handsfree Bluetooth Service

```powershell
Get-Service -Name BTAGService
Stop-Service -Name BTAGService
Set-Service -Name BTAGService -StartupType Disabled
```

### Misc
```powershell
$Env:PSModulePath -split (';')
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
Get-ChildItem | Get-Member | ConvertTo-CSV -Delimiter `t | Set-Clipboard
Man get-process -showWindow
Get-process | Tee-object meow.csv

Get-Process |? ProcessName -EQ "chrome" |% Id
# ? short for Where-Object
# % short for ForEach-Object / Select-Object

(Get-Command kopia).Path
C:\bin\kopia.exe
```

```powershell
DISM /Online /Cleanup-Image /RestoreHealth
sfc /scannow
```
