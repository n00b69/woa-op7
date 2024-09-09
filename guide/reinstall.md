<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Reinstalling Windows

### Prerequisites
- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)
  
- [Drivers](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [UEFI image](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp
img
```

### Entering mass storage mode
- In TWRP press **Advanced** > **Enable Mass Storage Mode**

### Diskpart
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace `$` with the actual number of **WINOP7**
```diskpart
select volume $
``` 

#### Assign the letter X
```diskpart
assign letter x
``` 

#### Exit diskpart
```cmd
exit
```

#### Formatting Windows
> Go to Windows Explorer > This PC and select **WINOP7**. Right click and format as NTFS.

### Installing Windows
> [!Warning]
> DO NOT USE 24H2!!!

> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim or 22631.2861.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of **Windows 11 Pro** in your image

### Copying your boot.img into Windows
> Skip this step if you do not have a copy of your rooted boot.img
- Drag and drop the **rooted_boot.img** from the **platform-tools** folder into the **WINOP7** disk in Windows Explorer, then rename it to **boot.img**.

### Installing Drivers
- Download and unpack the driver archive for your device, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINOP7** (which should be **X**), then press enter
  
### Boot into Windows
- Reboot your phone. If you end up in Android instead of Windows, flash the UEFI again using WOA Helper.

#### Setting up Windows
> Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.

> [!Tip]
> If you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.

## Finished!

















