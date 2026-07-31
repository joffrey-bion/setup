# Ventoy

## Using the Ventoy bootable USB

On machines with Secure Boot enabled, Ventoy might fail to boot with a message like:

```
Verification Failed: (0x1A) Security Violation
```

You'll need to enroll Ventoy's key as a trusted key in the Machine Owner Key (MOK) database.

1. Press enter on the error screen
2. Two things might happen here
   * You get the UEFI key management screen: go to the next step
   * You get a BitLocker-related error asking you to perform BitLocker recovery. See the BitLocker section below.
3. Press any key on the Shim UEFI key management screen
4. Select `Enroll key from disk` and press Enter
5. Select `VTOYEFI` and press Enter
6. Select `ENROLL_THIS_KEY_IN_MOKMANAGER.cer` and press Enter
7. Accept the enrollment on one or more screens
8. When back to the MOK mangement screen, select `Reboot`

### BitLocker recovery

When trying to enroll the Ventoy key, sometimes BitLocker gets in the way and asks you to perform a recovery.

1. Go to https://account.microsoft.com/devices/recoverykey in your MS account
2. Find the recovery key for your device (the Recovery Key ID mentioned in the error screen helps identify the key)
3. Enter the recovery key in the BitLocker recovery screen

### Working around Dell's Secure Boot issues

On some Dell laptops, Secure Boot might be trickier and prevent Ventoy not only from booting, but also from enrolling 
the key. Normally the MOK Manager is started to allow enrolling the key, but even this fails sometimes. To work around 
this:

1. Find the `MokManager.efi` in the VTOYEFI partition of the Ventoy USB drive (under `<drive>:\EFI\BOOT`)
2. Copy it to the regular Ventoy drive partition as if it were any other ISO (Ventoy can boot from it)
3. Disable Secure Boot temporarily in the BIOS of the target machine
4. Now that you can boot with Ventoy, boot on the MokManager.efi file instead of an ISO, and use it to enroll the key
5. Re-enable Secure Boot in the BIOS
6. Reboot the machine and verify that Ventoy is now bootable
