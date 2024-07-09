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
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```
  2. Edit pwsh profile
  ```powershell
  notepad $PROFILE
  ```
  3. Reload pwsh profile
  ```powershell
  . $PROFILE
  ```

## Install `scoop`

- [scoop github](https://github.com/ScoopInstaller/Install#advanced-installation)

## Configs for certain Apps

- Steps in [here](url)
