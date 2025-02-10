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
regedit /s <path>\Explorer.reg
```

Now you can make Explorer open .rar, .bz2, .7z, etc. If you had set 7-Zip or WinRAR as the default opener, you can undo the changes.

<img src="https://i.imgur.com/8kTE9r1.png" />
