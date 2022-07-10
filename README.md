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


-------------------
#Winget Install 
https://aka.ms/getwinget


winget upgrade --all

---------------

winget install -e --id Microsoft.WindowsTerminal

winget install -e --id Greenshot.Greenshot;

winget install -e --id Google.Chrome;

winget install -e --id geeksoftwareGmbH.PDF24Creator

winget install -e --id DucFabulous.UltraViewer;

winget install -e --id RARLab.WinRAR;

winget install -e --id mcmilk.7zip-zstd;

winget install -e --id Zoom.Zoom;

winget install -e --id VideoLAN.VLC;


Intel.IntelDriverAndSupportAssistant

---------------
#Hidden Apps AutoRun
https://www.nirsoft.net/utils/whatinstartup-x64.zip



---------------
sfc /scannow

DISM /Online /Cleanup-Image /CheckHealth

DISM /Online /Cleanup-Image /ScanHealth

DISM /Online /Cleanup-Image /RestoreHealth

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
