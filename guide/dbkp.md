<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Dualboot guide (DualbootKernelPatcher)
> There are two methods listed below, the first one requires root, the second one does not. Use whichever method suits you the most, as they both do the same.

Currently not working

### ~~Prerequisites (method 1: root required)~~
~~- [WOA Helper app](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)~~

### ~~Setup - Android~~
~~- Download and install the **WOA Helper** app, then open it and grant it root access.~~
~~- Open **WOA Toolbox**, then press the **DUALBOOT KERNEL PATCHER** button.~~
~~- Wait for it to finish, then reboot your phone.~~

#### ~~Booting into Windows~~
~~- Move the **alert slider** into the top position and reboot (or turn on) your device.~~

#### ~~Booting into Android~~
~~- Move the **alert slider** into the middle or bottom position and reboot (or turn on) your device.~~

## ~~Finished!~~


### Prerequisites (method 2: no root required)
- [WOA Helper app](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Magiskboot](https://github.com/n00b69/woa-op7/releases/download/DBKP/magiskboot.exe)

- [DualBoot Kernel Patcher](https://github.com/n00b69/woa-op7/releases/download/DBKP/DualBootKernelPatcher.zip)

- [.fd file](https://github.com/n00b69/woa-op7/releases/DBKP) (download the one for your device, either `guacamole` or `hotdog`)

### Opening CMD as an admin
> Open CMD as an **administrator**, then run the below command, replacing `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
>
> Do not close this window. You will need to use it throughout this entire guide.
```cmd
cd path\to\platform-tools
```

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp.img
```

#### Back up your boot image
> This will back up your boot image in the current directory (for example `C:\platform-tools`).
```cmd
adb pull /dev/block/by-name/boot_a boot.img
```

#### Setting up required files
- Download **magiskboot.exe** and move it into the `platform-tools` folder.
- Download **DualBootKernelPatcher.zip** and extract the **DualBootKernelPatcher** folder into the `platform-tools` folder.
- Download **DEVICENAME.fd** for your device and move it into the `platform-tools` folder.

### Unpacking your boot image
> Make sure **boot.img** is in the `platform-tools` folder.
```cmd
./magiskboot unpack boot.img
```

### Patching your boot image
> Replace `DEVICENAME.fd` in the below command with your actual devicename (`guacamole.fd` or `hotdog.fd`)
```cmd
./DualBootKernelPatcher\bin\Windows\DualBootKernelPatcher-x86_64.exe ./kernel ./DEVICENAME.fd ./output ./DualBootKernelPatcher\Config\DualBoot.Sm8150.cfg ./DualBootKernelPatcher\ShellCode\ShellCode.Hotdog.bin
```

### Renaming the kernel file
- Delete or rename the **kernel** file in the `platform-tools` folder, then rename the **output** file to `kernel`

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

















