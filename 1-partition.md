<img align="right" src="https://github.com/n00b69/woa-dipper/blob/main/dipper.png" width="350" alt="Windows 11 running on dipper">

# Running Windows on the Xiaomi Mi 8

## Partitioning your device

### Prerequisites
- Unlocked bootloader

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [TWRP](https://github.com/n00b69/woa-dipper/releases/download/Files/twrp.img)

- [Parted](https://github.com/n00b69/woa-dipper/releases/download/Files/parted)

### Notes
> [!WARNING]  
> 
> DO NOT REBOOT YOUR PHONE! If you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woadipper).
> 
> Do not run all commands at once, execute them in order!
>
> YOU CAN BREAK YOUR DEVICE WITH THE COMMANDS BELOW IF YOU DO THEM WRONG!!!

### Opening CMD as an admin
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
> 
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Flash TWRP recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in fastboot mode) run
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

### Backing up important files
> This will back up **fsc**, **fsg**, **modemst1** and **modemst2** to the current path your CMD is opened in (for example **C:\platform-tools**). Confirm these files are actually there before proceeding.
> 
> Keep these backups in a safe place. If your device's software ever gets destroyed, you might need these backups or your phone could lose cellular capabilities.
>
> If you've got anything else you want to back up, do this now. Your Android data will be erased in the next steps.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

#### Backing up your boot image
> This will back up your boot image in the current directory
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Partitioning guide
> Your Xiaomi Mi 8 may have different storage sizes. This guide uses the values of the 128GB model as an example. When relevant, the guide will mention if other values can or should be used.

#### Unmount data
```cmd
adb shell umount /dev/block/by-name/userdata
```

#### Preparing for partitioning
> Download the parted file and move it in the platform-tools folder, then run
```cmd
adb push parted /cache/ && adb shell "chmod 755 /cache/parted" && adb shell /cache/parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, userdata should be the last partition in the list.
```cmd
print
```

#### Removing userdata
> Replace **$** with the number of the **userdata** partition, which should be **21**
```cmd
rm $
```

#### Recreating userdata
> Replace **1611MB** with the former start value of **userdata** which we just deleted
>
> Replace **32GB** with the end value you want **userdata** to have
```cmd
mkpart userdata ext4 1611MB 32GB
```

#### Creating ESP partition
> Replace **32GB** with the end value of **userdata**
>
> Replace **32.3GB** with the value you used before, adding **0.3GB** to it
```cmd
mkpart esp fat32 32GB 32.3GB
```

#### Creating Windows partition
> Replace **32.3GB** with the end value of **esp**
>
> Replace **123GB** with the end value of your disk, use `p free` to find it
```cmd
mkpart win ntfs 32.3GB 123GB
```

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be 22
```cmd
set $ esp on
```

#### Exit parted
```cmd
quit
```

### Formatting Windows drive
> [!note]
> If this command and the next one fails (for example: "Failed to access `/dev/block/by-name/win`: No such file or directory"), reboot your phone, then boot back into the recovery provided in the guide and try again
```cmd
adb shell mkfs.ntfs -f /dev/block/by-name/win -L WINDIPPER
``` 

### Formatting ESP drive
```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPDIPPER
```

### Formatting data
- Format all data in TWRP, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

#### Check if Android still starts
- Just restart the phone, and see if Android still works

## [Next step: Rooting your phone](/guide/2-root.md)





















