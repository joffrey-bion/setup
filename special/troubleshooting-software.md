# Tips and software for troubleshooting

## Find HotKey / shortcut owner

Sometimes a shortcut doesn't work in your application because something else registered it globally.

The best way to find out who owns that shortcut is [HotKey screener](https://www.ntwind.com/freeware/hotkey-screener.html).
It can list all global shortcuts and detect which app is responding to it (requires admin priviledge).

### Common example: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Space</kbd>

If IntelliJ's extract funtion/method refactoring doesn't respond, it might be that 
<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>M</kbd> is taken by `nvsphelper64.exe` (NVidia's).

1. Open NVidia App
2. Open the overlay with <kbd>Alt</kbd> + <kbd>Z</kbd>
3. Open the overlay settings (the cog icon at the top)
4. Edit the "Toogle microphone" shortcut (press <kbd>Del</kbd> to remove it)
