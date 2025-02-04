# Windows 11 Setup

This README contains instructions for the initial setup of Windows and software installation.

It only contains things that can be shared publicly, and is thus accessible without authentication, so we can use 
whatever browser is available on a fresh machine.
Sensitive backup files to restore are placed in another (private) repository called
[backup](https://github.com/joffrey-bion/backup).

## Wait before you reset!

You have probably forgotten something. Go check the [before-reset checklist](./before-reset.md) first.

## Windows clean slate

* Follow the initial boot, and log in to your Microsoft Account
* [Open Windows Update](https://intradeus.github.io/http-protocol-redirector/?r=ms-settings:windowsupdate) and check and install updates.
* Unpin / uninstall all unnecessary pre-installed apps (OneDrive, weather, news, to-do, ...)
  ```powershell
  winget uninstall OneDrive
  winget uninstall "Microsoft Clipchamp"
  winget uninstall "Microsoft People"
  winget uninstall "Phone Link"
  winget uninstall "Power Automate"
  winget uninstall "Windows Notepad"
  ```

## Setup a dev drive D:\

Follow the instructions on the [official Windows page](https://learn.microsoft.com/en-us/windows/dev-drive/).

In short, go to [Settings > Storage > Disks & volumes](https://intradeus.github.io/http-protocol-redirector/?r=ms-settings:disksandvolumes) and create it from there (you can shrink the current `C:\` partition to create unallocated space for the future `D:\`).

Then, create the file structure by running this in PowerShell:

```powershell
mkdir D:\projects
mkdir D:\packages
mkdir D:\packages\cargo
mkdir D:\packages\gradle
mkdir D:\packages\konan
mkdir D:\packages\maven
mkdir D:\packages\npm
mkdir D:\packages\yarn

setx /M CARGO_HOME "D:\packages\cargo"
setx /M GRADLE_USER_HOME "D:\packages\gradle"
setx /M KONAN_DATA_DIR "D:\packages\konan"
setx /M MAVEN_OPTS "-Dmaven.repo.local=D:\packages\maven"
setx /M npm_config_cache "D:\packages\npm"
setx /M YARN_CACHE_FOLDER "D:\packages\yarn"

mkdir "$env:USERPROFILE\.m2"
@"
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 
                              http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <localRepository>D:\packages\maven</localRepository>
</settings>
"@ | Set-Content -Path "$env:USERPROFILE\.m2\settings.xml" -Encoding UTF8
```

## Install WSL2 (before Docker Desktop)

1. Open an admin PowerShell
2. Run `wsl --install` to install WSL itself (and the default Ubuntu distro)
3. Run `wsl --update` to make sure the kernel is the latest (especially if WSL was already installed)
4. Once Ubuntu started, setup a username and password (independent of the Windows ones, e.g. `jbion`)
5. Then update the software and distribution:
   
   ```bash
   sudo apt update && sudo apt upgrade
   ```

(More info in the [official installation doc](https://docs.microsoft.com/en-us/windows/wsl/install))

## Install software

The Windows Terminal and `winget` are now available by default on Windows 11 (at least when logged in with my account).
If it's not the case, follow the [official installation doc](https://learn.microsoft.com/en-us/windows/package-manager/winget/).

1. Download the `winget-packages.json` file (the short URL is a link to the raw file in this repo):
   ```powershell
   curl -o pkgs.json https://git.new/joff-pkgs
   ```
2. Remove undesired software fron the JSON file
3. Import them using the following command (in an admin shell):
   ```powershell
   winget import -i pkgs.json
   ```

## Chrome

**Do not pin to taskbar** initially, wait until multiple accounts are setup.

1. Open Chrome and log in with personal Google account to get access to passwords and whatnot.
2. Open Chrome (again) and log in with the JetBrains Google account.
3. Maybe pin both to the taskbar now

## Restore backup files

For more sensitive things like SSH and GPG keys, env variables with tokens, etc., head over to the private repo:
https://github.com/joffrey-bion/backup/

## JetBrains Toolbox

Open Toolbox and log in as the JetBrains organization through the [Toolbox Enterprise JetBrains portal](https://tbe.labs.jb.gg/).
If presented the option, also log in with the JetBrains account.
![image](https://github.com/user-attachments/assets/84d21b75-70bd-45b3-a992-879f40f48289)

Also log in to Space in Toolbox services.

## IntelliJ IDEA

Install IntelliJ IDEA from JetBrains Toolbox.

1. On first start on the initial IDEA Welcome window (no projects open), go to `Customize` and `All settings...` at the bottom
2. In `Settings Sync`
   1. Click `Enable Settings Sync...`
   2. Check `UI settings`, `Code settings`, `Plugins` (bundled only), and `Tools`
   3. Click `Get Settings from Account`. This should retrieve the color theme and coding style preferences too.
3. In `Version Control > Git`
   1. Clear the protected branches text field
   2. Uncheck `load protection rules from GitHub` (it doesn't know about exceptions and forbids force-push for me too)
4. In `Version Control > GitHub`
   1. Log-in via GitHub
   2. Make sure `Clone git repositories using SSH` is checked
5. In `Tools > Space`
   1. Log in to `jetbrains.team`
   2. Select `SSH` mode for cloning repositories
