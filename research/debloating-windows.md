# Debloating Windows

## Win11Debloat

[Win11Debloat](https://github.com/Raphire/Win11Debloat) is, at its core, a PowerShell script that removes a lot of
Windows 11 bloatware and can deactivate unwanted features.
It offers plently of customization through command line options.

It can also be called via a UI to make things easier when used manually. This downloads the script and runs the UI:
```
& ([scriptblock]::Create((irm "https://debloat.raphi.re/")))
```

Here is an example config that could be suitable (without apps removal):

```powershell
& ([scriptblock]::Create((irm "https://debloat.raphi.re/"))) `
-LogPath %userprofile%\debloat.log `
-ClearStartAllUsers `
-CombineMMTaskbarAlways `
-CombineTaskbarAlways `
-CreateRestorePoint `
-DisableBing `
-DisableBitlockerAutoEncryption `
-DisableClickToDo `
-DisableCopilot `
-DisableDVR `
-DisableDeliveryOptimization `
-DisableDesktopSpotlight `
-DisableDragTray `
-DisableEdgeAI `
-DisableEdgeAds `
-DisableGameBarIntegration `
-DisableLockscreenTips `
-DisableNotepadAI `
-DisablePaintAI `
-DisableRecall `
-DisableSearchHistory `
-DisableSettings365Ads `
-DisableStartPhoneLink `
-DisableStartRecommended `
-DisableStickyKeys `
-DisableSuggestions `
-DisableTelemetry `
-EnableDarkMode `
-EnableEndTask `
-ExplorerToDownloads `
-HideDupliDrive `
-HideGallery `
-HideHome `
-HideSearchTb `
-MMTaskbarModeAll `
-ShowHiddenFolders `
-ShowKnownFileExt
```

# Winhance

[Winhance](https://winhance.net) is the "Windows Enhancement Utility".

It offers both a UI and a CLI to inspect and debloat Windows and deactivate unwanted features.
