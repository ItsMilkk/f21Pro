Welcome!
============
Welcome to my notes on installing dumbdroid on the f21 Pro. There is a real lack of resource surrounding this topic and so I thought I would create a more user friendly guide on how to install Dumbdroid on the f21 pro including links to all the resources needed.


Installing Dumbdroid ~ _Milk's Notes_ ~
============

Download Dumbdroid
------------------
Remember where you save this as you will need this in the final step.

Qin F21 pro with Google Apps: https://dumbdroid.eu/downloads/dumbdroid_f21_gapps_20250627.img

Doov R77 pro with Google Apps: https://dumbdroid.eu/downloads/dumbdroid_r77_gapps_20250627.img

F21 pro: https://dumbdroid.eu/downloads/dumbdroid_f21_vanilla_20250627.img

R77 pro: https://dumbdroid.eu/downloads/dumbdroid_r77_vanilla_20250627.img

Necessary tools
---------------

* mtkclient: https://github.com/bkerler/mtkclient
* Fastboot and ADB: https://dl.google.com/android/repository/platform-tools-latest-windows.zip

Recommended!!!!
---------------
This ISO contains a version of Linux Mint with mtkclient, Fastboot and ADB preinstalled.
* https://www.swisstransfer.com/d/79c5592a-c85c-4ad4-86f7-dd00f1e3ead7

* Flash this to a USB using Rufus or Balena Etcher (https://inv.nadeko.net/watch?v=eM2C3FXD-qw)
* Plug into your laptop/PC and boot to the USB. 
* Password is 'user'
* Once installed and logged in, open terminal and run the commands from there.


Unlock the bootloader
---------------------

This will factory reset your phone!

Open Settings->About phone. Tap on "Build Number" until you unlock the Developer mode. Go into Settings->System->Developer options, and enable "USB debugging" and "OEM Unlocking". Turn off the phone.

Plug your phone into your laptop/PC.

Use the following commands to unlock the bootloader: 

* mtk e metadata,userdata,md_udc
* mtk da seccfg unlock

Make a backup
-------------

Back up the original software on your phone. 
This way if anything goes wrong, you can easily go back and start from scratch. You'll need about 5 GB of free space on your hard drive.

* mkdir f21_stock_rom
* mtk rl --skip userdata f21_stock_rom

Flash the new system
--------------------

Turn on your phone and enable "USB debugging" in the settings again. With the phone plugged in and turned on;

Reboot into fastboot mode:

* adb reboot fastboot

Erase user data if you are upgrading from the stock ROM. Updating Dumbdroid doesn't require this step, unless you are downgrading from GApps to Vanilla.

* fastboot -w


Flash Dumbdroid
--------------------

  * fastboot flash system /path/to/dumbdroid/image.img
  * fastboot reboot

Booting the system for the first time might take 5-10 minutes.

Recover from backup
-------------------
* mtk wl f21_stock_rom
