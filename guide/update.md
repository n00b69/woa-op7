<img align="right" src="https://github.com/n00b69/woa-dipper/blob/main/dipper.png" width="350" alt="Windows 11 running on dipper">

# Running Windows on the Xiaomi Mi 8

## Updating drivers

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [UEFI image](https://github.com/n00b69/woa-dipper/releases/tag/UEFI)

- [Drivers](https://github.com/n00b69/woa-dipper/releases/tag/Drivers)

### Boot into the UEFI
> Replace `path\to\dipper-uefi.img` with the actual path of the UEFI image
```cmd
fastboot boot path\to\dipper-uefi.img
```

#### Enabling mass storage mode
> Once booted into the UEFI, use the volume buttons to navigate the menu and the power button to confirm
- Select **UEFI Boot Menu**.
- Select **USB Attached SCSI (UAS) Storage**.
- Press the **power** button twice to confirm.

### Diskpart
```cmd
diskpart
```

#### Select Windows volume
> Use `list volume` to find it, replace `$` with the actual number of **WINDIPPER**
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

> If it asks you to enter a letter, enter the drive letter of **WINDIPPER** (which should be **X**), then press enter

#### Reboot your device
> Make sure to also change the UEFI image in Android, otherwise you may face a "blue screen of death" (BSoD) when booting Windows later.

## Finished!











