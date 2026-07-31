# Windows Setup automation

Here is some research on how to automate parts of the Windows installation process.

## Answer file – `autounattend.xml` (external media only)

An [answer file](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs?view=windows-11)
is a way to automate the Windows installation and configuration.

At its core, it pre-records the answers Windows needs during the very first boot (the Out-of-Box Experience, or OOBE),
hence the name. Here are some of the things that answer files can automate:

* language and region settings
* disk partitioning
* user account creation
* recursive copy of some files from the `$OEM$` directory of the external media
  ([more info](https://schneegans.de/windows/unattend-generator/usage/#oemfolder)).
  Normally useful for OEMs, but we could use it to copy files
* post-installation tasks via scripts, which can be used to debloat Windows, automatically configure Windows, install
  software, etc.

You can generate an answer file using the [autounattend generator](https://schneegans.de/windows/unattend-generator/)
provided by Christoph Schneegans.

> [!WARNING]
> The **push-button reset** feature doesn't support answer files.
> They are only available during a clean installation (from external media).

### Provisioning packages

TODO

### Post-setup script – `SetupComplete.cmd`

TODO

### Extensibility scripts (push-button reset)

TODO
https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/add-a-script-to-push-button-reset-features?view=windows-11
