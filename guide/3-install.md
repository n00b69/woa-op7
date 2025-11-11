<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Installing Windows

### Prerequisites

- [`Modified TWRP`](https://github.com/n00b69/woa-op7/releases/tag/Recovery)

- [`Windows on ARM image`](https://arkt-7.github.io/woawin/)
  
- [`Drivers`](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [`Modemprov.zip`](https://github.com/n00b69/woa-op7/releases/download/Files/modemprov.zip)

- [`UEFI image`](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp.img
```

### Entering mass storage mode
- In TWRP press **Advanced** > **Enable Mass Storage Mode**

### Diskpart
> [!WARNING]
> **DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!** THIS CAN ERASE ALL OF YOUR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for flashing it with [EDL](edl.md))
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace `$` with the actual number of **WINONEPLUS**
>
> If you do not see **WINONEPLUS**, please use [these instructions](troubleshooting-ru.md#mass-storage-mode-does-not-work) for an alternative method of entering mass storage mode
```diskpart
select volume $
``` 

#### Assign the letter X
```diskpart
assign letter x
``` 

#### Select the ESP volume of the phone
> Use `list volume` to find it, replace `$` with the actual number of **ESPONEPLUS**
```diskpart
select volume $
``` 

#### Assign the letter Y
```diskpart
assign letter y
```

#### Exit diskpart
```cmd
exit
```

### Installing Windows
> [!Important]
> For performance reasons, it is recommended to use Windows 11 25H2 (builds that start with 262XX, such as 26200.6713)

> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim or 26200.6713.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of **Windows 11 Pro** in your image

### Copying your boot.img into Windows
- Drag and drop the **rooted_boot.img** from the **platform-tools** folder into the **WINONEPLUS** disk in Windows Explorer, then rename it to **boot.img**.

### Installing Drivers
- Download and unpack the driver archive for your device, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINONEPLUS** (which should be **X**), then press enter
  
#### Create Windows bootloader files
> If any error shows up, such as "Failure when attempting to copy boot files", open `diskpart` again and assign any new letter to **ESPONEPLUS**, then replace the letter `Y` in the next command with the letter that you just added.
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Remove the drive letter for ESP
> If this does not work, ignore it and skip to the next command. This phantom drive will disappear the next time you reboot your PC.
```cmd
mountvol y: /d
```

### Flashing modemprov.zip
> Or LTE will not work
- In twrp recovery on your phone go to **`Advanced`** tab - **`ADB Sideload`** - **`Swipe to Start Sideload`**

> Replace `path\to\modemprov.zip` with the actual path of the .zip file
```cmd
adb sideload path\to\modemprov.zip
```

### Reboot to fastboot
```cmd
adb reboot bootloader
```

#### Boot into the UEFI
> Download the UEFI image **for your device**, then replace `path\to\devicename-uefi.img` with the actual path of the UEFI image.
```cmd
fastboot boot path\to\devicename-uefi.img
```

### Reboot to Android
Your device should reboot by itself after +- 10 minutes of waiting, after which you will be booted into Android, for the last step.

## [Last step: Setting up dualboot](dualboot-selection.md)

















