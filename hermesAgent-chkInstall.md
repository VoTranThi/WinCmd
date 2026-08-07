# Kiem tra nhanh loi cai dat Hermes va Playwright

Dung checklist nay khi cai Hermes hoac Playwright that bai tren Windows.

## 1. Kiem tra Node.js va npm

```powershell
node --version
npm --version
```

Hermes yeu cau Node `>=22.22.0`. Kiem tra them gioi han npm trong `package.json` neu can.

## 2. Chay npm install khong an thong bao loi

```powershell
cd "$env:LOCALAPPDATA\hermes\hermes-agent"
& "C:\Program Files\nodejs\npm.cmd" install
```

Khong dung `--silent` khi chan doan, vi no co the che gan het thong bao loi cua npm.

## 3. Kiem tra chinh sach tuoi phat hanh cua dependency

```powershell
npm config get min-release-age
Get-Content .npmrc
```

Neu co `min-release-age=14`, npm co the bao `ETARGET` khi dependency can dung qua moi.
Thu chan doan bang cach bo qua gioi han nay mot lan:

```powershell
& "C:\Program Files\nodejs\npm.cmd" install --min-release-age=0
```

Neu sau do bao `ERESOLVE`, day la xung dot peer dependency, khong phai loi Playwright.

## 4. Kiem tra tien trinh Playwright bi treo

```powershell
Get-CimInstance Win32_Process |
  Where-Object { $_.CommandLine -match "playwright.*install|oopDownloadBrowserMain" } |
  Select-Object ProcessId, CommandLine
```

Neu con tien trinh tai Playwright bi treo tu lan truoc, dung dung PID tuong ung:

```powershell
Stop-Process -Id <PID> -Force
```

## 5. Kiem tra lock trong cache Playwright

```powershell
Get-ChildItem "$env:LOCALAPPDATA\ms-playwright" -Force
```

Neu co `__dirlock` nhung khong con tien trinh tai Playwright, xoa rieng tep lock do:

```powershell
Remove-Item "$env:LOCALAPPDATA\ms-playwright\__dirlock" -Force
```

## 6. Cai Chromium truc tiep

```powershell
cd "$env:LOCALAPPDATA\hermes\hermes-agent"
npx --yes playwright install chromium
```

## 7. Xac minh Chromium da duoc tai

```powershell
Get-ChildItem "$env:LOCALAPPDATA\ms-playwright"
```

Can thay cac thu muc nhu `chromium-*` va `chromium_headless_shell-*`.

## 8. Xac nhan Hermes nhan dien Chromium

```powershell
& "$env:LOCALAPPDATA\hermes\hermes-agent\venv\Scripts\python.exe" -c "from tools.browser_tool import _chromium_installed; print(_chromium_installed())"
```

Ket qua `True` nghia la Playwright va Chromium da san sang cho Hermes.
