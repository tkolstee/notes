
```toc
```

## Links
- [Chocolatey package manager](https://chocolatey.org)
- Windows Subsystem for Android
	- [Installation](https://www.androidpolice.com/windows-11-apk-install-guide/)
	- [APKMirror](https://www.apkmirror.com/)



## Taskbar Size W11
[Source](https://www.tomshardware.com/how-to/change-taskbar-icon-size-windows-11)
Under `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`, create a new `DWORD` (32-bit) key called `TaskbarSi` with value of `0`, `1`, `2` for small, medium, or large respectively.

Close Regedit and reboot.