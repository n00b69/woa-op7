<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Dualboot guide (DualbootKernelPatcher)

### Prerequisites
- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Magiskboot](LINKNOW)

- [Dualboot Kernel Patcher](LINKNOW)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp
img
```

#### Back up your boot image
> This will back up your boot image in the current directory (for example `C:\platform-tools`)
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Unpacking your boot image
- Open **magiskboot.exe** and IDFK

### Patching your boot image
- Open **dbkp.exe** and IDFK

### Repacking your boot image
- Open **magiskboot.exe** and IDFK

### Reboot to fastboot
```cmd
adb reboot bootloader
```

### Flashing the patched boot image
> Replace `path\to\patched_boot.img` with the actual path of the image
```cmd
fastboot flash boot_a path\to\patched_boot.img
```
```cmd
fastboot flash boot_b path\to\patched_boot.img
```

#### Reboot your device
```cmd
fastboot reboot
```

#### Booting into Windows
- Move the **alert slider** into IDFK position and reboot (or turn on) your device.

#### Booting into Android
- Move the **alert slider** into IDFK position and reboot (or turn on) your device.

## Finished!

















