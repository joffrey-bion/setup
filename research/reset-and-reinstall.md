# Research on Windows 11 reset

Here are some notes from what I gathered on the internet around Windows Setup, resetting, installing.

## Ways to reset a Windows machine

There are mainly 2 ways to reset an existing machine.

* The built-in [push-button reset](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/push-button-reset-overview?view=windows-11)
  feature, which is accessible in _Settings > Recovery > Reset this PC_. There are 2 "flavors" of this feature:
  * "Remove everything", a.k.a. Factory reset
  * "Keep my files", a.k.a. Basic reset
* Clean installation from an external media, a.k.a. 
  [Bare metal recovery](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/bare-metal-recovery?view=windows-11)

## Push-button reset

Push-button reset is a recovery tool that repairs the OS while preserving data and important customizations (or not, 
depending on the mode).

https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/add-a-script-to-push-button-reset-features?view=windows-11

## Clean installation – from external media

For a clean installation of Windows with a disk wipe and re-partition, we need to boot on an external media, usually a 
USB flash drive.

### Creating a bootable USB drive

Creating a bootable Windows installation USB drive doesn't strictly require special software.
You can also [manually copy files from the ISO](https://schneegans.de/windows/installation-media/) as suggested by 
Schneegans.

The Media Creation Tool is the standard way provided by Microsoft to create a bootable USB drive.
It is available on the [Windows 11 download page](https://www.microsoft.com/nl-nl/software-download/windows11)
([direct download here](https://go.microsoft.com/fwlink/?linkid=2156295)).

However, there is an interesting alternative called [Ventoy](https://www.ventoy.net/en/index.html).
Ventoy creates USB drives that can contain **multiple ISO files, and multiple answer files per ISO file**.
It will then ask to select the ISO file and the answer file to use (if there are more than one).
It is a complete solution to make great bootable USB drives. The website and UI is a bit old school, but the idea works
great.
Small downside:
* on machines with Secure Boot enabled, Ventoy requires enrolling its key in the Machine Owner Keys
* on Dell machines specifically, there is some extra hassle (we need to disable or change the mode of Secure Boot
  temporarily to allow enrolling the key). See [this issue](https://github.com/ventoy/Ventoy/issues/2902) for more 
  details.
Workarounds are described in [ventoy.md](ventoy.md).
