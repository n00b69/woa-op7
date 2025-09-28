<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Updating drivers

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/tag/Recovery)

- [Drivers](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [UEFI image](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp.img
```

### Entering mass storage mode
- In TWRP press **Advanced** > **Enable Mass Storage Mode**

### Diskpart
```cmd
diskpart
```

#### Select Windows volume
> Use `list volume` to find it, replace `$` with the actual number of **WINONEPLUS**
```cmd
select volume $
```

#### Assign the letter X
```cmd
assign letter x
```

#### Exit diskpart
```cmd
exit
```

### Installing Drivers
> [!Note]
> This process will take +- 20 minutes. Do not worry, this is normal.

- Unpack the driver archive, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINONEPLUS** (which should be **X**), then press enter

#### Reboot your device
> Make sure to also change the UEFI image in Android, otherwise you may face a "blue screen of death" (BSoD) when booting Windows later.

## Finished!











