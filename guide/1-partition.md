<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Partitioning your device

### Prerequisites
- Unlocked bootloader

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

### Notes
> [!WARNING]  
> 
> DO NOT REBOOT YOUR PHONE! If you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woahelperchat).
> 
> Do not run all commands at once, execute them in order!
>
> YOU CAN BREAK YOUR DEVICE WITH THE COMMANDS BELOW IF YOU DO THEM WRONG!!!

> [!Important]
> OOS12 and ROMs that use OOS12 firmware have extremely experimental Windows support and may not work at all.
>
> It is highly recommended to downgrade to OOS11 if you want to use Windows.

### Opening CMD as an admin
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
> 
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

> [!Note]
> If your device is not detected in fastboot or recovery mode, you'll have to install USB drivers [using this guide](troubleshooting.md#device-is-not-recognized-in-fastboot-or-recovery)

#### Boot modified TWRP recovery
> While your phone is in fastboot mode, replace `path\to\moddedtwrp.img` with the actual path of the image
>
> If the image does not boot on OnePlus 7 Pro (guacamole), use [this image](https://github.com/n00b69/woa-op7/releases/download/Files/guacamolefunny.img) instead
```cmd
fastboot boot path\to\moddedtwrp.img
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
> This will back up your boot image in the current directory (which should be the **platform-tools** folder)
>
> Replug the cable if it says "no devices/emulators found"
```cmd
adb pull /dev/block/by-name/boot_a boot.img
```

### Fixing the GPT
> If you do not do this, Windows may break your device
```cmd
adb shell fixgpt
```

#### Opening a shell
```cmd
adb shell
```

### Preparing for partitioning
> [!Note]
> If at any moment in parted you see an error prompting you to type "Yes/No" or "Ignore/Cancel", type `Yes` or `Ignore` depending on the situation to ignore the errors and continue.
>
> If you see any **udevadm** errors, you can ignore these as well.
```cmd
parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, **userdata** should be the last partition in the list.
```cmd
print
```

#### Removing userdata
> Replace **$** with the number of the **userdata** partition, which should be **19** or **22**
```cmd
rm $
```

#### Recreating userdata
> Replace **7971MB** with the former start value of **userdata** which we just deleted
>
> Replace **64GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 64GB-7971MB = **56GB**
```cmd
mkpart userdata ext4 7971MB 64GB
```

#### Creating ESP partition
> Replace **64GB** with the end value of **userdata**
>
> Replace **64.3GB** with the value you used before, adding **0.3GB** to it
```cmd
mkpart esp fat32 64GB 64.3GB
```

#### Creating Windows partition
> Replace **64.3GB** with the end value of **esp**
```cmd
mkpart win ntfs 64.3GB -0MB
```

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be **20** or **23**
```cmd
set $ esp on
```

#### Exit parted
```cmd
quit
```

### Formatting data
- Format all data in TWRP, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

#### Check if Android still starts
- Just restart the phone, and see if Android still works
- If it doesn't, boot into stock recovery and perform a factory reset there
- Select **Wipe data and cache** > **Erase everything** > **yes**

### Formatting Windows and ESP drives
> Reboot into the modded TWRP, then run the below command
```cmd
adb shell format
```

## [Next step: Rooting your phone](/guide/2-root.md)





















