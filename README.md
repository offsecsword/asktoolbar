
%SYSTEMROOT%\System32\taskkill.exe /f /im iexplore.exe /im firefox.exe /im chrome.exe /im apnmcp.exe /im toolbar.exe /im TBNotifier.exe
start /wait msiexec.exe /X{13F537F0-AF09-11D6-9029-0002B31F9E59} /qn /norestart
start /wait msiexec.exe /X{2318C2B1-4965-11D4-9B18-009027A5CD4F} /qn /norestart
start /wait msiexec.exe /X{2E5E800E-6AC0-411E-940A-369530A35E43} /qn /norestart
start /wait msiexec.exe /X{4E7BD74F-2B8D-469E-C0FB-F778B590AD7D} /qn /norestart
start /wait msiexec.exe /X{5A263CF7-56A6-4D68-A8CF-345BE45BC911} /qn /norestart
start /wait msiexec.exe /X{86D4B82A-ABED-442A-BE86-96357B70F4FE} /qn /norestart
start /wait msiexec.exe /X{AA58ED58-01DD-4D91-8333-CF10577473F7} /qn /norestart
start /wait msiexec.exe /X{AF69DE43-7D58-4638-B6FA-CE66B5AD205D} /qn /norestart
start /wait msiexec.exe /X{D4027C7F-154A-4066-A1AD-4243D8127440} /qn /norestart
start /wait msiexec.exe /X{EF99BD32-C1FB-11D2-892F-0090271D4F88} /qn /norestart
start /wait MsiExec.exe /X{4152532D-4D45-4400-76A7-A758B70C0A06} /qn /norestart
start /wait MsiExec.exe /X{41525333-2D56-3700-76A7-A758B70C0300} /qn /norestart
start /wait MsiExec.exe /X{41525333-0076-A76A-76A7-A758B70C0A02} /qn /norestart
start /wait MsiExec.exe /X{4F524A2D-5637-4300-76A7-A758B70C0A03} /qn /norestart
start /wait msiexec.exe /X{42435041-2d53-4154-00a7-a758b70b0a00} /qn /norestart
start /wait MsiExec.exe /X{4F524A2D-5350-4500-76A7-A758B70C0F01} /qn /norestart
start /wait MsiExec.exe /X{54425F44-454D-4F5F-5637-A758B70C0A02} /qn /norestart
start /wait MsiExec.exe /X{41525333-0076-A76A-76A7-A758B70B0601} /qn /norestart 
start /wait MsiExec.exe /X{4F524A2D-5637-006A-76A7-A758B70C0202} /qn /norestart
start /wait MsiExec.exe /X{41525353-502D-4D45-4400-A758B70C0F00} /qn /norestart 
start /wait MsiExec.exe /X{54425F44-454D-4F5F-5637-A758B70C0A02} /qn /norestart 

IF EXIST "%PROGRAMFILES(X86)%" (GOTO 64BIT) ELSE (GOTO 32BIT)
:32BIT
IF EXIST "%PROGRAMFILES%\Ask.com\Updater\Updater.exe" "%PROGRAMFILES%\Ask.com\Updater\Updater.exe" -uninstall
IF EXIST "%PROGRAMFILES%\AskBar\unins000.exe" "%PROGRAMFILES%\AskBar\unins000.exe" /SILENT
GOTO MORECLEANUP
:64BIT
IF EXIST "%ProgramFiles(x86)%\Ask.com\Updater\Updater.exe" "%ProgramFiles(x86)%\Ask.com\Updater\Updater.exe" -uninstall
IF EXIST "%ProgramFiles(x86)%\AskBar\unins000.exe" "%ProgramFiles(x86)%\AskBar\unins000.exe" /SILENT
GOTO MORECLEANUP

:MORECLEANUP
IF EXIST "%ProgramData%\APN" RD /S /Q "%PROGRAMDATA%\APN"
IF EXIST "%SYSTEMDRIVE%\Users\All Users\APN" RD /S /Q "%SYSTEMDRIVE%\Users\All Users\APN"
DEL %WINDIR%\PreFetch\APN*EXE*.pf /Q /F
DEL %WINDIR%\PreFetch\ASKBAR*.pf /Q /F

:END
