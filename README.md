# Windows 11 Setup

This README contains instructions for the initial setup of Windows and software installation.
It only contains things that can be shared publicly, so it's easy to get to this repository and files via whatever browser is available.

Sensitive backup files to restore are placed in another (private) repository called [backup](https://github.com/joffrey-bion/backup).

## Windows upgrade and updates

Go to Windows Update and upgrade if not already on Windows 11.

## Install WSL2 (before Docker Desktop)

Run the following in an admin Powershell or CMD:

```
wsl --install
```

(More info in the [official installation doc](https://docs.microsoft.com/en-us/windows/wsl/install))

## Install WinGet

Winget might already be installed. Try to run `winget` from Powershell. If not installed:

1. Make sure you’re logged in to Windows
2. Open the Microsoft Store
3. Search for “winget” (you’ll find the App Installer application)
4. Get the `App Installer` application (it will install the `winget` CLI)

(More info in the [official installation doc](https://learn.microsoft.com/en-us/windows/package-manager/winget/))

## Install software

Download the relevant winget JSON files:

```powershell
curl -o winget-common.json https://raw.githubusercontent.com/joffrey-bion/setup/main/winget-common.json
curl -o winget-jetbrains.json https://raw.githubusercontent.com/joffrey-bion/setup/main/winget-jetbrains.json
```

Then import them using the following command:
```
winget import -i <filename>
```

## Restore backup files

For more sensitive things like SSH and GPG keys, env variables with tokens, etc., head over to the private repo:
https://github.com/joffrey-bion/backup/
