# Windows 11 Setup

This README contains instructions for the initial setup of Windows and software installation.
It only contains things that can be shared publicly, so it's easy to get to this repository and files via whatever browser is available.

Sensitive backup files to restore are placed in another (private) repository called [backup](https://github.com/joffrey-bion/backup).

## Windows upgrade and updates

Go to Windows Update and upgrade if not already on Windows 11.

## Install WSL2 (before Docker Desktop)

Run `wsl --install` (or `wsl --update` if already there) in an admin Powershell or CMD.
It doesn't look like installing a new distro is necessary for Docker Desktop.

(More info in the [official installation doc](https://docs.microsoft.com/en-us/windows/wsl/install))

## Install software

The Windows Terminal and `winget` are now available by default on Windows 11 (at least when logged in with my account).
If it's not the case, follow the [official installation doc](https://learn.microsoft.com/en-us/windows/package-manager/winget/).

To install the required software, download the relevant winget JSON files:

```powershell
curl -o winget-common.json https://raw.githubusercontent.com/joffrey-bion/setup/main/winget-common.json
curl -o winget-jetbrains.json https://raw.githubusercontent.com/joffrey-bion/setup/main/winget-jetbrains.json
```

Then import them using the following command:
```
winget import -i <filename>
```

## IntelliJ IDEA

Install IntelliJ IDEA from JetBrains Toolbox.
Open it and activate settings sync, which should retrieve the color theme and coding style preferences.

## Restore backup files

For more sensitive things like SSH and GPG keys, env variables with tokens, etc., head over to the private repo:
https://github.com/joffrey-bion/backup/
