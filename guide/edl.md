<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Restoring your device using EDL

### Prerequisites
- [Qualcomm EDL Drivers](https://github.com/n00b69/woa-op7/releases/tag/EDL)

- [MSM Download Tool](https://onepluscommunityserver.com/list/Unbrick_Tools/OnePlus_7_Pro/Global_GM21AA/R/) (OnePlus 7 Pro)

- [MSM Download Tool](https://onepluscommunityserver.com/list/Unbrick_Tools/OnePlus_7T_Pro/Global_HD01AA/R/) (OnePlus 7T Pro)

### Extracting the MSM Download Tool
- Download the **MSM Download Tool** rom for your device (which should be in .zip format), then extract the contents of the .zip file somewhere.

### Booting into EDL Mode
> If you're already in EDL, you can skip this step
- Open **Device Manager** on your PC.
- Connect your phone to your PC and hold down the **volume up** and **power** buttons for 10 seconds.
- When your phone starts rebooting, hold down the **volume up**, **volume down**, and **power** buttons simultaneously for 10 seconds.
- Locate **Qualcomm HS-USB QDLoader 9008** in the **Ports (COM & LPT)** category of Device Manager.
- If the device is missing entirely, is called **QUSB_BULK_CID**, or has a ⚠️ yellow warning triangle / question mark, (or is located in any other category such aa**Other devices**), you need to install EDL drivers first.
- To install EDL drivers, extract the contents of **QUD.zip** somewhere, right click on **QUSB_BULK_CID**, click on **Update driver** and **Browse my computer for drivers**, then find and select the **QUD** folder.

### Flashing the stock rom
- Open **MsmDownloadTool V4.0.exe** located in the MSM DownloadTool archive you downloaded earlier.
- In the login menu user type, select **Others**.
- Press the `flash` button, then **guacamole/hotdog_....ops** file located in the same folder

#### Rebooting to Android
> After the flashing is completed (it will usually take around 10 minutes), your device should automatically reboot into Android.
- If it doesn't, hold the **volume down** + **power** buttons until it reboots.

## Finished!
















