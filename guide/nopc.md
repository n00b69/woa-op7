<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Installing Windows without a PC
> [!Warning]
> This page and its files are still in its early stages of development. Do not use unless you have been asked to test it.
> 
> Seriously, do not use it.

### Prerequisites
- Unlocked bootloader

- [OnePlus 7(T) Pro 4G WinInstaller](https://github.com/n00b69/woa-op7/releases/tag/WinInstaller)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [WOA Helper app](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

### Notes
> [!WARNING]  
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woahelperchat).

### Flash the modified TWRP
> While in fastboot mode, replace `path\to\moddedtwrp.img` with the actual path of the image.
>
> If you don't have a PC, you can boot the modified TWRP using Termux on another rooted phone.
```cmd
fastboot boot path\to\moddedtwrp.img reboot recovery
```

#### Opening TWRP terminal
- Once booted into TWRP press the **Advanced** button on the bottom right of the screen, then press **Terminal**.
- Run all future commands in this terminal

#### Unmount data
```cmd
umount /dev/block/by-name/userdata
```

#### Preparing for partitioning
```cmd
parted /dev/block/sda
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

<details>
<summary><a><strong>For 128GB devices</strong></a></summary>

#### Recreating userdata
> Replace **7971MB** with the former start value of **userdata** which we just deleted
>
> Replace **64GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 64GB-7971MB = 56GB
```cmd
mkpart userdata ext4 7971MB 64GB
```

#### Creating ESP partition
> Replace **64GB** with the end value of **userdata**
>
> Replace **64.4GB** with the value you used before, adding **0.4GB** to it
```cmd
mkpart esp fat32 64GB 64.4GB
```

#### Creating Windows partition
> Replace **64.4GB** with the end value of **esp**
```cmd
mkpart win ntfs 64.4GB 124GB
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
> Replace **128.4GB** with the value you used before, adding **0.4GB** to it
```cmd
mkpart esp fat32 128GB 128.4GB
```

#### Creating Windows partition
> Replace **128.4GB** with the end value of **esp**
```cmd
mkpart win ntfs 128.4GB 252GB
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

#### Rooting your phone
- If your phone isn't already rooted, you can flash Magisk at this point using the instructions in [the root guide](root.md), else continue to the next step.

### Formatting data and rebooting
- Format all data in TWRP, or Android will not boot.
- ( Go to Wipe > Format data > type `yes` ).
- Press the reboot button to reboot into Android.
> [!Note]
> If Android does not start after +- 10 minutes, reboot back into stock recovery and perform a factory reset there.

### Preparing necessary files
- Download the Windows image and make sure it remains in the `Download` folder **of your internal storage**.
- Download **WinInstaller.zip** and keep it in the `Download` folder as well.
- Download and install the [WOA Helper app](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA), then open it and grant it root access. Do not do anything else inside the app yet.
- Download TWRP installer for your device ([guacamole](https://dl.twrp.me/guacamole/) or [hotdog](https://dl.twrp.me/hotdog/)) and flash it in Magisk.

### Booting into TWRP
- Press the `Reboot to Recovery` button in the top right of Magisk.
- Once booted into TWRP, enter your password if it asks you to.

### Flashing WinInstaller
- In TWRP, select **Install** and then locate **WinInstaller.zip** and flash it.
> [!Note]
> If TWRP cannot read your internal storage, it means that you picked the wrong image and it is unable to decrypt your Android data. If this is the case, reboot back into Android and flash a different TWRP.
- Wait untill all processes complete and your device boots into Windows. This will take around 15-20 minutes.

> [!Tip]
> If you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
>
> If there is no such button, press the **SIM card** button at the top of the screen (the one that says **Connected**), and press **Disconnect**.

#### Booting to Android
- Run the **Android** shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access).

#### Booting to Windows
- Press **QUICKBOOT TO WINDOWS** inside the WOA Helper app, or use the newly created toggle in your quick settings panel.

## Finished!
