# WindowsNT suckless settings

## Install Apps from WinGet

- Steps in [here](url)

## Install Apps using `Window Repair Toolbox`

- [WRT Link](https://windows-repair-toolbox.com/files/Windows_Repair_Toolbox.zip)
- Replace `custom.xml` in "Custom Tool" tab, and press "Refresh list".

## Check `Startup` settings

- In `Registry`:
  - `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
  - `Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
- In Folder:
  - `C:\Users\{USERNAME}\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`
  - `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`
- Also in "Settings -> Apps -> Startup", and "Task Manager -> Startup".

## Setup shells

- Install `zsh`:
  - [msys2 zsh Link](https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64)
  - Extract the zip file and place the contents into `C:/Program Files/Git`.
  - place `.zshenv` in `C:/Users/{USERNAME}/`.
- Config `pwsh`:
  1. Open pwsh as "Admin", change excution policy via:
  - ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```
  2. Edit pwsh profile:
  - ```powershell
    notepad $PROFILE
    ```
  3. Reload pwsh profile:
  - ```powershell
    . $PROFILE
    ```

## Install `scoop`

- [scoop github](https://github.com/ScoopInstaller/Install#advanced-installation)

## Configs for certain Apps

- Steps in [here](./app-config/readme.md)

## `CHKDSK` vs `SFC` vs `DISM`

- CHKDSK(Check Disk):
  - `chkdsk c: /f`: find and fix any errors on the hard disk.
  - `chkdsk c: /r`: detect and locate the bad sectors on the target hard disk, and try to recover the readable information from the bad sectors.
  - `chkdsk c: /r /f`: detect errors and fix it.
- SFC(System File Checker):
  - `sfc /scannow`: the System File Checker tool helps you scan and repair corruptions in Windows system files.
  - `sfc /verifyonly`: only scan but not repair the corrupted system files.
- DISM(Deployment Image Servicing and Management):
  - `DISM /Online /Cleanup-Image /CheckHealth`: checks if there are any corruptions inside the local image, but not repair them.
  - `DISM /Online /Cleanup-Image /ScanHealth`: performs a more advanced scan to check if the Windows image has corruptions.
  - `DISM /Online /Cleanup-Image /RestoreHealth`: run an advanced scan and automatically repair any detected problems with the image.

## DoH (DNS over HTTPS)

- IPV4:
  - 1.1.1.1: https://cloudflare-dns.com/dns-query
  - 8.8.8.8: https://dns.google/dns-query
- IPV6:
  - 2606:4700:4700::64: https://cloudflare-dns.com/dns-query
  - 2001:4860:4860::64: https://dns.google/dns-query
