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

### Opening CMD as an admin
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
> 
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Boot modified TWRP recovery
> [!Note]
> This image may not boot on OOS12, if this is the case, downgrade to OOS11 first, install Windows, then update back to OOS12.

> While your phone is in fastboot mode
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
> This will back up your boot image in the current directory
```cmd
adb pull /dev/block/by-name/boot_a boot.img
```

#### Unmount data
```cmd
adb shell umount /dev/block/by-name/userdata
```

### Partitioning guide
> Pick the one that applies to you

<details>
<summary><a><strong>For 128GB devices</strong></a></summary>

#### Preparing for partitioning
```cmd
adb shell parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, userdata should be the last partition in the list.
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
> Replace **32GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 32GB-7971MB = 24GB
```cmd
mkpart userdata ext4 7971MB 32GB
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
```cmd
mkpart win ntfs 32.3GB 124GB
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

  </summary>
</details>

<details>
<summary><a><strong>For 256GB devices</strong></a></summary>

#### Preparing for partitioning
```cmd
adb shell parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, userdata should be the last partition in the list.
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
> Replace **128GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 128GB-7971MB = 120GB
```cmd
mkpart userdata ext4 7971MB 128GB
```

#### Creating ESP partition
> Replace **128GB** with the end value of **userdata**
>
> Replace **128.3GB** with the value you used before, adding **0.3GB** to it
```cmd
mkpart esp fat32 128GB 128.3GB
```

#### Creating Windows partition
> Replace **128.3GB** with the end value of **esp**
```cmd
mkpart win ntfs 128.3GB 252GB
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

  </summary>
</details>

### Formatting data
- Format all data in TWRP, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

#### Check if Android still starts
- Just restart the phone, and see if Android still works

### Formatting Windows and ESP drives
> Reboot into the modded TWRP, then run the below two commands
```cmd
adb shell mkfs.ntfs -f /dev/block/by-name/win -L WINONEPLUS
``` 

```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPONEPLUS
```


## [Next step: Rooting your phone](/guide/2-root.md)





















