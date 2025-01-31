<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Additional materials
> Below you will find a list of tweaks and materials for Windows on your ARM device


### List of supported apps/games
> These are by no means comprehensive lists, they do however list apps/games that have been tested by the community

- [Renegade Google Sheets list](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

- [ARM Repo (native ARM software)](https://armrepo.ver.lt/)

- [News & supported applications](https://windowsonarm.org/)

#### Finished!


### Toggling USB host mode
> [!Warning]
> Disable USB host mode if you use a powered USB hub, as this can irreversibly damage your device. If you don't use a powered USB hub, enable USB host mode or you will not be able to use any USB devices.

- Run [USB Host Mode Control](https://github.com/Misha803/My-Scripts/releases/tag/USB-Host-Mode-Control) to enable/disable USB host mode, then confirm that you want to disable/enable USB host mode.
- If USB host mode is currently enabled and USB does not work, turn it off, then back on.

#### Finished!


### Set up Android boot.img auto-flashing

>[!NOTE]
> Set up Android boot.img auto-flashing on Windows boot or when the battery is low (<15%) to prevent battery dies with uefi.img flashed. 

- Download the **boot.img auto-flasher** [here](https://github.com/Misha803/My-Scripts/releases/tag/boot.img-Auto-Flasher).
- Run it, click **INSTALL** button, select when should Android boot.img be auto-flashed (on Windows boot/Low battery) and wait for installation to complete.

#### Finished! 


### Install Microsoft Office
- Go to [Gravesoft's Office installer page](https://gravesoft.dev/office_c2r_links).
- Download the installer that fits your purposes. Make sure you select `Online x64`.
- Open the `setup.exe` and follow any instructions provided within.

#### Finished!


### Activate Windows / Office
- Follow the instructions by Massgravel [here](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Finished!


### Making the keyboard float
> [!WARNING]  
> Make sure these steps are done on the device running Windows, not your computer!

- Open CMD as an administrator and run ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Press `y` then enter.
- Reboot your device.

##### Finished!



















