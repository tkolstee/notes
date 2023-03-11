
```toc
```

## Filesystems

### Mounting Network Shares


```bash
sudo mkdir /mnt/z
sudo mount -t drvfs '\\server\share' /mnt/z
```


### Mounting Linux Filesystems
[Source](https://pureinfotech.com/mount-drive-linux-file-system-wsl-windows-11/)

#### Enumerate Disks
Run command prompt or powershell as administrator

```dos
C:\Windows\system32>wmic diskdrive list brief
Caption                            DeviceID            Model                              Partitions  Size
CT2000MX500SSD1                    \\.\PHYSICALDRIVE1  CT2000MX500SSD1                    1           2000396321280
CT2000MX500SSD1                    \\.\PHYSICALDRIVE0  CT2000MX500SSD1                    2           2000396321280
Seagate Portable SCSI Disk Device  \\.\PHYSICALDRIVE2  Seagate Portable SCSI Disk Device  1           5000978465280
StoreJet Transcend USB Device      \\.\PHYSICALDRIVE3  StoreJet Transcend USB Device      1           2000396321280
```

#### Mount Entire Disk or Partition
```dos
wsl --mount \\.\PHYSICALDRIVE3
wsl --mount \\.\PHYSICALDRIVE3 --partition 1 -t vfat
```

Filesystem can now be accessed through WSL instances as `/mnt/wsl` or through system explorer

#### Unmount
```dos
wsl --unmount \\.\PHYSICALDRIVE3
```

## USB Passthrough
[Source](https://www.xda-developers.com/wsl-connect-usb-devices-windows-11/)

1. Install [usbipd-win](https://github.com/dorssel/usbipd-win/releases/latest) in Windows
2. Install usbip in Linux
3. Run `cmd.exe` as administrator and type the following, using the bus ID of the device from the first command to fill in the position in the second.
	```
	usbipd wsl list
	usbipd wsl attach --busid <busid>
	```

4. When complete, use the following to detach the device:
	```
	usbipd wsl detach --busid <busid>
	```


