## Add custom programs to defaults apps settings page in Windows

To add Windows Explorer, you need trustedinstaller privilege, open Powershell as admin:
```ps1
Set-ExecutionPolicy Unrestricted CurrentUser;Set-ExecutionPolicy Unrestricted LocalMachine;install-module ntobjectmanager -Force;sc.exe start trustedinstaller;$p = Get-NtProcess TrustedInstaller.exe;
```
Create Command Prompt with trustedinstaller privilege
```ps1
import-module ntobjectmanager;sc.exe start trustedinstaller;$p = Get-NtProcess TrustedInstaller.exe;$proc = New-Win32Process commend.exe -CreationFlags NewConsole -ParentProcess $p
```
In the Command Prompt window, type
```cmd
regsvr32 /s <path>\Windows_Explorer.reg
```
