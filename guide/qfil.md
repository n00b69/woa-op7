<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Manually restoring your device in EDL mode
> Rather than flashing your device into a completely refreshed state using the regular [EDL guide](edl.md), you may want to try to restore it without losing data. If this is the case, the below guide is for you.

### Prerequisites
- [`Qfil, EDL Drivers & OP7series firehose`](https://github.com/n00b69/woa-op7/releases/tag/EDL)

- `OxygenOS firmware for [OnePlus 7 Pro`](https://onepluscommunityserver.com/list/Unbrick_Tools/OnePlus_7_Pro/Global_GM21AA/R/) or [OnePlus 7T Pro](https://onepluscommunityserver.com/list/Unbrick_Tools/OnePlus_7T_Pro/Global_HD01AA/R/) or any other files that you may want to flash

### Setting up Qfil
- Open **Qfil**.
- In "Select Build Type", select **flat build**.
- In "Select programmer", select the downloaded firehose.
- In "Configuration", make sure the "Device Type" is set to **UFS**.

#### Checking if EDL drivers are installed
- Open **Device Manager** on your PC and search for **Qualcomm HS-USB QDLoader 9008** in the **Ports (COM & LPT)** category of Device Manager.
- If the device is called **QUSB_BULK_CID** or has a ⚠️ yellow warning triangle / question mark, and is located in any other category (for example **Other devices**), you need to install EDL drivers first.
- To install EDL drivers, extract the contents of **QUD.zip** somewhere, right click on **QUSB_BULK_CID**, click on **Update driver** and **Browse my computer for drivers**, then find and select the **QUD** folder.

### Making sure Qfil works
- In **Qfil**, make sure the correct port is selected. If it says `No Port Available`, select the **Qualcomm HS-USB QDLoader 9008** port.
> Remember the `COM$` port number, as you will need it shortly.
- At the top, select "Tools" > "Partition manager", and click **Ok**.
> [!Note]
> If you see a **Download Fail:Sahara Fail** or **Download Fail:FireHose Fail:FHLoader Fail:Process Fail** error, make sure your cable stays connected and reboot to EDL again by holding **volume down** + **power**.
- Once you're back in EDL, try opening the Partition manager again.
- If it still fails, try to repeat the last step a few times. You can also try rebooting your phone and PC.

#### Minimize partition manager
> Once partition manager is open, leave it open in the background. Do not close it.

### Preparing necessary firmware files
> Prepare the firmware files that you want to flash, whether it be a single partition (e.g **system_a** or **modem_a**) or the entire firmware
- You may need to download the OxygenOS firmware linked in the prerequisites, then use [bkerler's Oppo Decrypt](https://github.com/bkerler/oppo_decrypt) to extract the **.ops** file that is inside.

### Flashing your partitions
> In Qfil's partition manager
- Right click on **name_of_partition** > **Manage Partition Data** and press **Load Image**.
- Select and flash the backup you made earlier.
- Do the same thing for any other partitions that you may want to flash.

### Reboot your device
> When you're done flashing the partitions, you can reboot your device
- Hold the **volume down** + **power** button for +- 30 seconds and your device should hopefully turn on.

## Finished!


















