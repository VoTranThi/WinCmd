#Windows Toolbox 

Set-ExecutionPolicy Unrestricted -Scope CurrentUser

iwr -useb https://raw.githubusercontent.com/WinTweakers/WindowsToolbox/main/run.ps1 | iex

iwr -outf C:\ET-AIO.bat https://github.com/semazurek/ET-All-in-One-Optimizer/releases/download/4.7/ET-AIO.bat | cmd /c 'C:\ET-AIO.bat'


iwr -useb https://christitus.com/win | iex
-------------------
#Advance system Settings: sysdm.cpl

-------------------
#Install WindowsStore

Get-AppXPackage *WindowsStore* -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}


start ms-windows-store:full



https://github.com/kkkgo/LTSC-Add-MicrosoftStore/releases/tag/2019
-------------------
#Winget Install 
https://aka.ms/getwinget


PS> Install-Script -Name winget-install
PS> winget-install

```
Get-AppxPackage Microsoft.DesktopAppInstaller | Remove-AppxPackage
```

# install Chocolatey

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))



# install Scoop

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression


---------------

winget install -e --id geeksoftwareGmbH.PDF24Creator

winget install -e --id Microsoft.VCRedist.2010.x86

winget install -e --id Microsoft.VCRedist.2010.x64

winget install -e --id Microsoft.VCRedist.2012.x86

winget install -e --id Microsoft.VCRedist.2012.x64

winget install -e --id Microsoft.VCRedist.2013.x86

winget install -e --id Microsoft.VCRedist.2013.x64

winget install -e --id Microsoft.VCRedist.2015+.x86

winget install -e --id Microsoft.VCRedist.2015+.x64

winget install -e --id Microsoft.DotNet.DesktopRuntime.6

winget install -e --id Oracle.JavaRuntimeEnvironment


winget install -e --id OpenJS.NodeJS.LTS

winget install -e --id Evolus.Pencil

winget install -e --id 9PGCV4V3BK4W

winget install -e --id mcmilk.7zip-zstd

winget install -e --id AutoIt.AutoIt

winget install -e --id Dropbox.Dropbox

winget install -e --id ArtifexSoftware.GhostScript

winget install -e --id Git.Git

winget install -e --id Greenshot.Greenshot

winget install -e --id Microsoft.Azure.StorageEmulator

winget install -e --id Microsoft.Edge

winget install -e --id Microsoft.EdgeWebView2Runtime

winget install -e --id Microsoft.WindowsTerminal

winget install -e --id Notepad++.Notepad++

winget install -e --id OBSProject.OBSStudio

winget install -e --id Opera.Opera

winget install -e --id Postman.Postman

winget install -e --id Rufus.Rufus

winget install -e --id RARLab.WinRAR

winget install -e --id Zoom.Zoom

winget install -e --id ALCPU.CoreTemp

winget install -e --id SoftDeluxe.FreeDownloadManager

winget install -e --id voidtools.Everything

winget install -e --id Microsoft.PowerToys

winget install -e --id Google.Chrome

winget install -e --id Google.Drive

winget install -e --id VideoLAN.VLC

winget install -e --id TortoiseGit.TortoiseGit

winget install -e --id VMware.WorkstationPlayer

winget install -e --id DucFabulous.UltraViewer

winget install -e --id Microsoft.WebDeploy

winget install -e --id Microsoft.PowerBI

winget install -e --id Microsoft.SQLServerManagementStudio

winget install -e --id XP8CDJNZKFM06W


Intel.IntelDriverAndSupportAssistant

---------------
#Hidden Apps AutoRun
https://www.nirsoft.net/utils/whatinstartup-x64.zip



---------------
sfc /scannow

DISM /Online /Cleanup-Image /CheckHealth

DISM /Online /Cleanup-Image /ScanHealth

DISM /Online /Cleanup-Image /RestoreHealth


-------------

HDD Drive:

defrag c:

C:\windows\SYSTEM32\cleanmgr.exe /dC


---------------


1. hold left shift key and restart pc to get to advanced menu
 and click troubleshoot, then click command prompt.
Now you need to find the Windows directory, its normally c: or d: you can type: dir to see files and folders in that directory.

2. type, cd windows and then type cd system32

3. ren utilman.exe utilman1.exe

4. ren cmd.exe utilman.exe close command prompt and click continue

5. control userpasswords2 then close cmd and login

6. repeat to change back

7. type cd windows and then type cd system32

8. ren utilman.exe cmd.exe

9. ren utilman1.exe utilman.exe

------
Cài win không cần usb https://www.youtube.com/watch?v=EYa7iTgb6es


------

#wifi pwd


Check wifi password: for /f "skip=9 tokens=1,2 delims=:" %i in ('netsh wlan show profiles') do @echo %j | findstr -i -v echo | netsh wlan show profiles %j key=clear


--------
*Boot to Safe Mode Command Prompt*

bcdedit /set {default} safeboot network


------------

# Backup all Driver

dism /online /export-driver /destination:D:\Backup

# Telnet check open port

dism /online /Enable-Feature /FeatureName:TelnetClient

telnet <Server_IP_Address> port_number



------
Tạo file dung lượng lớn :
fsutil file createnew "D:\file100GB.dat" 107374182400
---------
Backup Setting windows Apps
https://github.com/builtbybel/CloneApp

-------
# lấy danh sách các tệp đã được chỉnh sửa sau ngày 14/08/2024, theo đúng cấu trúc thư mục con

Get-ChildItem -Path "C:\path\to\your\directory" -Recurse | Where-Object { $_.LastWriteTime -gt "2024-08-14" } | Select-Object FullName

--------
#Install Cloudflared

winget install --id Cloudflare.cloudflared

cloudflared tunnel --url http://localhost:3000


# ngrok tunnel 

winget install  Ngrok.Ngrok  --ignore-security-hash

ngrok config add-authtoken NGROK_AUTHTOKEN

ngrok http 7860

# extend trial windows server evaluation ( max = 6 times)




PS> slmgr -dlv

PS> slmgr -rearm

PS> shutdown -r -t 0

PS> 


# Task to sync Time server every Startup

$action = New-ScheduledTaskAction -Execute 'w32time.exe' -Argument '/resync'

$trigger = New-ScheduledTaskTrigger -AtStartup

Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "SyncTimeOnStartup" -User "SYSTEM" -RunLevel Highest




# Clean-up space 

dotnet nuget locals --clear all

npm cache verify


