# Windows 11 Setup

This README contains instructions for the initial setup of Windows and software installation.
It only contains things that can be shared publicly, so it's easy to get to this repository and files via whatever browser is available.

Sensitive backup files to restore are placed in another (private) repository called [backup](https://github.com/joffrey-bion/backup).

## Windows upgrade and updates

Go to Windows Update and upgrade if not already on Windows 11.

## Install WSL2 (before Docker Desktop)

In an admin powershell (or CMD), run `wsl --install`.
If already installed, run `wsl --update` to make sure the kernel is the latest.

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

Then import them using the following command (in an admin shell if :
```
winget import -i <filename>
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

Log in to Toolbox with the JetBrains account.

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
