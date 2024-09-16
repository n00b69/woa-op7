<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Dualboot guide (DualbootKernelPatcher)

### Prerequisites
- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Magiskboot](https://github.com/n00b69/woa-op7/releases/download/Files/magiskboot.exe)

- [DualBoot Kernel Patcher](https://github.com/n00b69/woa-op7/releases/download/Files/DualBootKernelPatcher.zip)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp
img
```

#### Back up your boot image
> This will back up your boot image in the current directory (for example `C:\platform-tools`).
> 
> If your current directory is not your **platform-tools** folder, run ```cd path\to\platform-tools```, replacing `path\to` with the actual path of the folder.
```cmd
adb pull /dev/block/by-name/boot boot.img
```

#### Setting up magiskboot
- Download **magiskboot.exe** and move it into your `platform-tools` folder.

### Unpacking your boot image
> Make sure both **boot.img** and **magiskboot.exe** are in your current directory.
```cmd
./magiskboot unpack boot.img
```

### Patching your boot image
- Download and extract **DualBootKernelPatcher.zip**.
- Navigate to `bin` > `Windows`, then run **DualBootKernelPatcher-x86_64.exe**
- Then idk what else, I guess "Select the unpacked boot image and press patch"?

### Repacking your boot image
> This will repack your patched boot image into a new file called **new_boot.img**
```cmd
./magiskboot repack boot.img
```

### Reboot to fastboot
```cmd
adb reboot bootloader
```

### Flashing the patched boot image
> Replace `path\to\new_boot.img` with the actual path of the image
```cmd
fastboot flash boot_a path\to\new_boot.img
```
```cmd
fastboot flash boot_b path\to\new_boot.img
```

#### Reboot your device
```cmd
fastboot reboot
```

#### Booting into Windows
- Move the **alert slider** into the top position and reboot (or turn on) your device.

#### Booting into Android
- Move the **alert slider** into the middle or bottom position and reboot (or turn on) your device.

## Finished!

















