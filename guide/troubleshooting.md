<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Troubleshooting Issues
> Below you will find a list of common problems and their solutions

## Mass storage mode does not work
> This can rarely happen, depending on the OOS version that is installed.
- Download the [guacamole](https://github.com/n00b69/woa-op7/releases/download/Files/renegade-guacamole.img) or [hotdog](https://github.com/n00b69/woa-op7/releases/download/Files/renegade-hotdog.img) Renegade UEFI.
- Reboot into fastboot mode by running `adb reboot bootloader`.
> Replace `path\to\renegade-DEVICENAME.img` with the actual path of the UEFI image.
```cmd
fastboot boot path\to\renegade-DEVICENAME.img
```
> Once booted into the UEFI, use the volume buttons to navigate the menu and the power button to confirm
- Select **UEFI Boot Menu**.
- Select **USB Attached SCSI (UAS) Storage**.
- Press the **power** button twice to confirm.

Now return to the [diskpart section](3-install.md#diskpart) of the installation guide.

> [!Important]
> Do not use this **Renegade UEFI** image to try and boot Windows later!
>
> Use the updated UEFI image provided in the link in the guide instead.

##### Finished!

## LTE and other network services in Android no longer work
> Sometimes Windows may wipe your modem partitions, resulting in the loss of LTE in Android. To fix this, you'll need to restore your modem using the backups that you hopefully made [while partitioning your device](1-partition.md#backing-up-important-files). If you did not do this step, there is likely no way to recover.
- Boot into any recovery other than the stock recovery (ADB commands do not work there)
- Open CMD in the **platform-tools** folder.
- Restore the four partitions that you backed up using the below commands. Replace `path\to` with the actual path of the images.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Reboot your device and check if LTE works.
> [!Note]
> If it still does not work, you will have to do some additional steps;
- Download the stock rom for your device
- Open it, look for a file called **modem.img** and extract it.
- Boot into fastboot mode (`adb reboot bootloader`).
- Flash this **modem.img** with the below command, replacing `path\to\modem.img` with the actual path of the image
```cmd
fastboot flash modem path\to\modem.img
```

##### Finished!

## LTE in Windows does not work
- Flash [modemprov.zip](https://github.com/n00b69/woa-op7/releases/download/Files/modemprov.zip) in any recovery and then boot into Windows.

> [!Note]
> You may have to follow the steps above in "LTE and other network services in Android no longer work" to restore your modem first
- In Android, find your APN settings. It should be located in `Connections` > `Mobile Networks` > `Access Point Names`.
- Write the information of your current APN settings down, then boot into Windows.
- In `Cellular Settings`, click on `Mobile operator settings` > `APN settings` and add the APN settings you wrote down earlier.
- Enable **Cellular**. It may say `No Internet Access`, but it should still work. 

##### Finished!

## Cannot mount Windows in Android
If mounting Windows produces an empty folder, you either don't have Windows installed, or your rom does not have mount support.

##### Finished!

## Cannot write to Windows in Android
> This is caused by shutting down Windows instead of restarting it.
- To solve this, boot to Windows and then press "restart", then as the screen shuts off boot to TWRP and from there load up Android.
- Or, disable hibernation in Windows. 
> Alternatively, if you have already set up the Switch to Android app, simply use this to switch to Android.

##### Finished!

## USB does not work
Enable USB host mode using the optional [post install guide](materials.md#toggling-usb-host-mode).

##### Finished!

## I want to use Windows while using OOS12
> You will need to follow some additional steps, or the system may not boot and / or it will be broken.

#### If you are using WOA Helper
- If this is your first time booting Windows, run **DEVCFG FLASHER** in the **WOA TOOLBOX** section in WOA Helper. This will flash OOS11 devcfg & copy the files into Windows that are necessary to return to Android.
- If mounting fails, you will have to manually copy **sdd.exe** and **sdd.conf** into Windows.
- Enable the **Flash OOS11 devcfg when quickbooting** option in the **PREFERENCES** menu in WOA Helper, now you can use the **QUICKBOOT TO WINDOWS** option.
- Run **sdd.exe** before running the **Switch to Android** shortcut each time when switching to Android, or modify the **sdd.conf** file accordingly so that it also flashes the boot.img. The instructions to do so can be found in the **sdd.conf** file itself.

#### If you are using Dualboot Kernel Patcher
- Run **DEVCFG FLASHER** in the **WOA TOOLBOX** section in WOA Helper. This will flash OOS11 devcfg & copy the files into Windows that are necessary to return to Android.
- If mounting fails, you will have to manually copy **sdd.exe** and **sdd.conf** into Windows (this is only needed once, and can be ignored afterwards).
- Run **sdd.exe** every time before rebooting to Android.

##### Finished!


## Error: 3 The system cannot find the path specified.
This error usually means that you are trying to install Windows on a disk that already has Windows installed. To solve this issue, format the disk in Windows Explorer and try again.

##### Finished!

## 0xc000021a BSOD
This usually means that winlogon.exe has failed, and you may need to reapply the Windows image.

##### Finished!

## The computer restarted unexpectedly or encountered an unexpected error
If you stumble upon this error, you will need to [reinstall Windows](reinstall.md).

##### Finished!

## INACCESSIBLE_BOOT_DEVICE BSOD
This Blue Screen of Death likely means some broken driver installation. To fix this, [reinstall Windows](reinstall.md).

##### Finished!



















