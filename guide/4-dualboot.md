<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Dualboot guide

### Prerequisites
- [`UEFI image`](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

- [`WOA Helper app`](https://github.com/n00b69/woa-helper/releases/tag/APK)

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, please follow [this guide](root.md) first.

### Setup - Android
- Download and install the **WOA Helper** app, then open it and grant it root access.
- Download the **UEFI image** and place it inside the folder named `UEFI` in your internal storage.
- Open the WOA Helper app and press the **QUICKBOOT TO WINDOWS** button.

> [!Important]
> If you are using OOS12 or a ROM that uses OOS12 firmware, you will need to follow some additional & alternative steps found [here](troubleshooting.md#i-want-to-use-windows-while-using-oos12)

### Setup - Windows
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press **QUICKBOOT TO WINDOWS** inside the app, or use the newly created toggle in your quick settings panel

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside the **C:\ folder** in Windows, overwriting the old file.
>
> You can also use the **BACK UP BOOT IMAGE** feature in the WOA Helper app to do so.

## Finished!















