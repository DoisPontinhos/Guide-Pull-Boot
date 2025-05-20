# Extract Boot for Root

# Requirements
Download [ADB Tools](https://developer.android.com/tools/releases/platform-tools)
Extract the .zip file
Copy the platform-tools folder to C:\Windows\
WIN + R > "sysdm.cpl" > Enter > Advanced > Environment Variables... > System Variables > Path > Double Click it > Add "C:\Windows\platform-tools" > Ok > Ok > Ok

```mermaid
graph LR
A[Win+R] -- sysdm.cpl --> B[Enter] --> C[Advanced] --> D[Environment Variables...] --> E[System Variables] --> F[Path] -- Double Click it --> G[Add C:\Windows\platform-tools]

```

# Enabling Developer Options

To enable Developer Options on an Android device, you need to access a hidden menu within the settings. This involves  tapping the "Build number" in the "About phone" section seven times. Once enabled, Developer Options will appear in your settings, allowing you to access advanced features for development.

# Unlocking Bootloader

 Enable **OEM unlocking**
 Open a Terminal/Cmd Window
 Type > `Adb devices` in the Terminal/Cmd window  > Accept the window prompt on your phone
 `adb reboot bootloader`
 `fastboot flashing unlock`

# ADB Root
In the Terminal/CMD window type : 
> `adb root`

Restarting adb as root

> `adb shell`
> `whoami`

Root

> `getprop | grep slot`

Look for this line `[ro.boot.slot_suffix]: [_b]`
It should be [_a] or [_b] depending on the booted slot

>`dd if=/dev/block/bootdevice/by-name/init_boot_b of=/sdcard/init_boot.img`

Patch the image using Magisk/KernelSU

Rename the new patched image to for example "init_boot_patched.img"

>`exit`

>`adb pull /sdcard/Download/init_boot_patched.img desktop`
>`adb reboot bootloader`
>`fastboot flash init_boot init_boot_patched.img` or you can just drag the patched img to the terminal/cmd window
>`fastboot reboot`

## And your device is now rooted :D
