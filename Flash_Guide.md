📥 *How to Flash Lunaris AOSP / AviumUI on OnePlus Nord 4 (avalon)*

⚠️ Read fully before starting. Flashing wrong images can hard brick your device. There is no support for skipped steps.

**Requirements**
- Unlocked bootloader
- Latest `platform-tools` (adb/fastboot) from Google
- Device on the required base firmware. see [Firmware](https://github.com/SathiyaSenpai/android_device_oneplus_avalon/blob/luna/proprietary-files.txt#L2)
- ROM zip + boot.img, init_boot.img, vendor_boot.img and recovery.img. Use `/downloads`
- GApps zip only if you want Google apps on vanilla

***Step 1:** Unlock Bootloader* (skip if already unlocked)
1. Enable OEM unlocking in Developer Options
2. `adb reboot bootloader`
3. `fastboot flashing unlock`. Confirm on screen
4. Device factory resets. Enable USB debugging again after setup **( Wipes everything. Backup you data )**

***Step 2:** Flash Partitions + Recovery*
1. `adb reboot bootloader`
2. Flash each image:
>`fastboot flash boot boot.img`
>`fastboot flash init_boot init_boot.img`
>`fastboot flash vendor_boot vendor_boot.img`
>`fastboot flash recovery recovery.img`
3. Use Volume keys + Power key to boot into *Recovery*

***Step 3:** Flash the ROM*
1. First time install only: *Factory Reset > Format Data*
2. Back to main menu of recovery then *Apply Update > Apply from ADB*
3. On PC: `adb sideload rom-file-name.zip`

> For Example:
>  adb sideload Lunaris-AOSP-avalon-Community-3.12-GMS-2026071623.zip

4. Flashing GApps too? When recovery asks to reboot again, reboot then choose Apply from ADB again 
5. On PC: `adb sideload gapps-file-name.zip`
>For Example
>adb sideload NikGapps-core-arm64-16-20250716-signed.zip
6. Reboot to system, first boot can take Some time

*Updating later*
- OTA: Settings > System > Updates
- Manual: repeat Step 3 without formatting data

***Sideload stuck / error 21?***
Boot to fastbootd from recovery → `fastboot wipe-super super_empty.img` (from the initial-install package) → back to recovery and retry sideload.
