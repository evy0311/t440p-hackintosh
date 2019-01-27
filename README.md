# T440p - Hackintosh Guide

### Overview

- This guide references a few other guides. Credit for those guides is given to their respective owners.
- It is assumed that you have a decent understanding of Hackintosh, the macOS environment, as well as how to do basic computer tasks
- Will guide you through some of the different information needed to get macOS Mojave 10.14.2 working on your Thinkpad T440p
- Special thanks to jloisel and his guide [Here](https://github.com/jloisel/t440p "Here") on how to configure the T440p for a hackintosh install. The `CLOVER` folder and the kexts for the ultrabay are his and credit goes to him. Also a special thanks to [midi1996](https://github.com/midi1996) on GitHub for his guide on how to create the macOS installer from Recovery.
- **Note:** I am NOT responsible for any harm you cause to your device. This guide is provided "as-is" and all steps taken are done at your own risk

# Guide

![](https://github.com/evy0311/t440p/raw/master/Guide%20Stuff/T440p_Day.png)

![](https://img.shields.io/github/issues/evy0311/t440p.svg) ![](https://img.shields.io/github/forks/evy0311/t440p.svg) ![](https://img.shields.io/github/stars/evy0311/t440p.svg) ![](https://img.shields.io/github/license/evy0311/t440p.svg) ![](https://img.shields.io/twitter/url/https/github.com/evy0311/t440p.svg?style=social)


## Information
##### What works:
- Power management/sleep
- Brightness Control
- Battery Information
- Audio (from internal speaker and headphone jack)
- USB Ports
- Graphics Acceleration
- Facetime/iMessage
- Trackpoint/Touchpad (see below)
- Pretty much everything except what is listed below

##### What Doesnt Work:
- As of right now, nothing! :)

**Note:** I am currently working on a fix for the items listed above. If you use this guide and information and find that something does not work, please submit an issue request so I can work on a fix.

## Creating the USB Installer
Since I don't have access to a legitimate Mac, I needed to be able to create a vanilla macOS installer. This guide (and many others) used to inform users to create a USB installer for a macOS Distro such as Niresh. While this may work just fine for then creating a vanilla macOS installer, distro's can be (and are) very shady. They come preloaded with a bunch of extra junk that is not needed, and just overall are *highly* advised against being used. Follow the steps below to figure out how to create a REAL macOS Mojave Vanilla installer without having access to a real Mac.

1. Follow the steps at this guide [Here](https://internet-install.gitbook.io/macos-internet-install/).
2. When you get to the part about installing clover bootloader, follow the steps below for configuring kexts, etc. 
3. **IMPORTANT (DO NOT MISS THIS):** Now, copy Clover bootloader and the kexts files that you have downloaded to another USB drive (not the one you're burning the installer too) or an external hard drive. You will need access to them later.
4. Copy the `CLOVER` folder you have downloaded from this repository onto your USB drive as well.
5. Copy the `CLOVER` folder you have downloaded from this repository into `EFI/`. You can simply copy over the whole folder as the config.plist and everything else is already configured for the T440p. 
6. The most important step that I missed twice in the guide above is to make sure you add the `HFSPlus.efi` driver into `/EFI/Clover/drivers64UEFI`. I missed this step twice and couldn't see any drivers at all inside of Clover.
7. For more help on configuring Clover and the USB installer, the original guide linked in step 1 will be of the most help to you. Make sure you install the kexts and `CLOVER` folder from this repo onto your Clover USB, as these will guarantee your T440p will work properly.
8. We are now ready to continue into the next topic: Installing macOS Mojave.



## Installing macOS Mojave
1. After you followed the guide above and have your USB drive ready to go, we can reboot the machine. When you reboot, enter into the BIOS to change some settings. On the T440p, you can do this by hitting `Enter` at the Lenovo boot screen.
2. Once in the BIOS, make sure you change the following settings. `Disable Security Chip`, `Disable Anti Theft Module`, and `Disable TPM`. Basically, disable all of the "security" features. Make sure Secure boot and other features like that are off. These features will affect how macOS sleeps.
3. Now, reboot into macOS and select the USB drive inside of Clover.
4. Boot into macOS and install onto your hard drive. I recommend using an SSD.
5. After this is done, reboot the computer and let it sit. Mine rebooted a few times on its own to go through some final installation procedures.
6. Once you see the "region selection" screen, you are good to proceed.
7. Create your user account and everything else, but do not sign in with your iCloud account. If it asks you to connect to a network, select the option that says do not connect and press continue. We will connect it later.
8. After you've booted, plug in the USB drive or external hard drive that you copied the Clover file to in step 9 of the previous section. 
9. Install Clover bootloader following the same steps as before and using the same settings, except this time install them onto your internal hard drive with your Mojave installation. I recommend checking the box that says `Install Clover Configurator` as well (it comes in handy later).
10. We now need to copy our Clover configuration from our USB to our hard drive with Mojave. Simply copy the `CLOVER` folder that you have on your other USB drive (the one you used in step 9 of the previous section) into the `EFI` partition that Clover should have mounted during install. 
11. 

## Post-Installation

##### FHD Screen

If you have done the full HD (1920x1080) screen mod (like myself), it is recommended that you install [One Key HiDPI](https://github.com/xzhih/one-key-hidpi "One Key HiDPI").  This will mimic the "retina" display feature that many of Apple's newer laptops come with.

##### UltraBay HDD

If you are using a HDD or SSD in place of the normal optical drive, you will need to install AHCIPortInjector.kext and AppleAHCIPort.kext into `Library/Extensions`.

`AHCIPortInjector.kext` fixes the `Disk not initialized` issue (disk cannot be read). `AppleAHCIPort.kext` fixes the disk being detected as an external drive (instead of internal).

##### Setting up Apple services (Facetime, iMessage, etc.)
I *highly* recommend following [This guide](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) to get these features working. It worked for me on the first try and was super straight forward compared to other guides that I have seen before in the past. 

##### Getting audio working

In order to get audio to work, there are a few simple steps we need to follow. This has been tested and working on High Sierra and Mojave. Special Thanks to this guide [Here](https://www.tonymacx86.com/threads/guide-lenovo-thinkpad-t440p.233282/) for help in getting this to work. By default, speaker audio should work, but audio via the headhpone jack does not. Follow the steps below to get it working.


1. First, copy the .zip file called `alc_fix.zip` inside the foldr `Audio Stuff` to the desktop.
2. Open terminal and type `cd desktop/alc_fix`, then hit enter.
3. Then, type `./install.sh` and press enter.
4. Then, mount your EFI partition using Clover Configurator.
5. Open the EFI partition and navigate to `/EFI/CLOVER/ACPI/patched`.
6. Delete the file inside that folder called `SSDT-T440P.aml`.
7. Copy the new `SSDT-T440P.aml` file you downloaded into the folder.
8. Copy the three .kext files from the `kexts` folder inside of `Audio Stuff` to `/EFI/CLOVER/kexts/Other`.
9. Open up Clover Configurator again and open your `config.plist` file.
10. Click `Devices`, then look for the section labeled `Audio`.
11. Where it says `Inject`, type `28` into the box. 
12. Save the `config.plist` file.
13. Restart and enjoy your audio from the headphone jack!

##### Customizing About This Mac

In order to customize the About This Mac section, I recommend you follow the guide [Here](https://github.com/Haru-tan/Hackintosh-Things/blob/master/AboutThisMacMojave.md "Here").

For the section about changing the logo, you can use the T440p logo's I have designed in ` /SystemLogos/`.

##### Fix Middle Button Scrolling with Non-Synaptics Trackpad

Since Apple only uses Synaptics trackpads in their Macbook's, a non-synaptics trackpad will have problems getting things like gestures to work, as well as the popular "middle button scrolling" used on Thinkpads (combination of pressing the middle button and using the Trackpoint to scroll). If you're like me, I ordered the Alps varient of the upgraded T450 trackpad, which the VoodooPS2Controller kext does not support gestures for. In order to "fake" the middle button scrolling, we need to download an app called [Smart Scroll](http://www.marcmoini.com/sx_en.html). Once this is done, go to the "vector scroll" section, and enable it. Then, if you clikc the middle button, you can now scroll down by using the trackpoint. This is unfortunetely only a temporary solution as it doesn't behave the same. Thanks to Redit user [daftguy](https://www.reddit.com/user/daftguy) for finding this solution. 

## More to come...
