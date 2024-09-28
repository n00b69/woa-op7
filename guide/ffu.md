<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Installing Windows (FFU method) 

### Prerequisites
- A device running Windows 10 or higher

- [FFU image (Coming Soon)](guide/ffu.md) 

- [WOA Device Manager](https://github.com/n00b69/woa-vayu/releases/download/Files/WOA_Device_Manager.zip) 

### Notes:
> [!Warning]
> All your data will be erased! Use the [modified recovery image](https://github.com/n00b69/woa-vayu/releases/tag/Recovery) to back up any data now if needed. Make sure to copy it to your PC or an SD card before proceeding.
>
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woahelperchat) 

### Install WOA Device Manager
- Download **WOA Device Manager** and extract the file's contents somewhere. 

- Open the **Install.cmd** file and follow the on-screen instructions, then open WOA Device Manager. 

### Booting into FFU mode
- Plug your phone into your computer while booted in Android and press **Manual Mode** (the rotation icon on the left) in WOA Device Manager.

> If WOA Device Manager does not detect your device, reboot to **fastboot mode** instead and try again. To do this, hold the **volume down** + **power** button until the fastboot logo appears.

- In the newly opened menu, click **Switch to Windows-mode**, then hold the **volume down** button until the QR code and wrench icons appear on the screen.

### Flashing the FFU Image
- Click on **Flash** (the wrench icon on the left) in WOA Device Manager, then select your FFU file and click **Flash FFU Image**. 

- Wait until the FFU image has flashed and the green check mark appears, after which your phone should boot back into Android.

> [!Note]
> If it does not boot into Android, reboot into recovery by holding the **volume up** + **power** buttons, and do a factory reset there.

## [Next step: Setting up dualboot](dualboot-selection2.md)
