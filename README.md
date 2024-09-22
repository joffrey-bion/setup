# Windows 11 Setup

This README contains instructions for the initial setup of Windows and software installation.

It only contains things that can be shared publicly, and is thus accessible without authentication, so we can use 
whatever browser is available on a fresh machine.
Sensitive backup files to restore are placed in another (private) repository called
[backup](https://github.com/joffrey-bion/backup).

## Wait before you reset!

You have probably forgotten something. Go check the [before-reset checklist](./before-reset.md) first.

## Windows upgrade and updates

[Open Windows Update](ms-settings:windowsupdate) and check and install updates.

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

1. Download the `winget-packages.json` file:
   ```powershell
   curl -o winget-packages.json https://raw.githubusercontent.com/joffrey-bion/setup/main/winget-packages.json
   ```
2. Remove undesired software
3. Import them using the following command (in an admin shell):
   ```powershell
   winget import -i winget-packages.json
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
