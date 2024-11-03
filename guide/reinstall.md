<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Reinstalling Windows

### Prerequisites
- [Modified TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

### Boot modified TWRP recovery
> Replace `path\to\moddedtwrp.img` with the actual path of the image
```cmd
fastboot boot path\to\moddedtwrp.img
```

### Formatting Windows and ESP partitions
```cmd
adb shell mkfs.ntfs -f /dev/block/by-name/win -L WINONEPLUS
```

```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPONEPLUS
```

## [Next step: Reinstalling Windows](3-install.md)

















