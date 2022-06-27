#Windows Toolbox 

Set-ExecutionPolicy Unrestricted -Scope CurrentUser

iwr -useb https://raw.githubusercontent.com/WinTweakers/WindowsToolbox/main/run.ps1 | iex


iwr -outf C:\ET-AIO.bat https://github.com/semazurek/ET-All-in-One-Optimizer/releases/download/4.7/ET-AIO.bat

C:\ET-AIO.bat

clear


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
