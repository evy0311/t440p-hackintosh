# T440p - Hackintosh Guide

### Overview

- Not a full in depth guide
- It is assumed that you have a decent understanding of Hackintosh, the macOS environment, as well as how to do basic computer tasks
- Will guide you through some of the different information needed to get macOS Mojave 10.14.2 working on your Thinkpad T440p
- Special thanks to jloisel and his guide [Here](https://github.com/jloisel/t440p "Here") on how to configure the T440p for a hackintosh install. All credit for information on stuff like the Ultrabay kexts goes to him.
- **Note:** I am NOT responsible for any harm you cause to your device. This guide is provided "as-is" and all steps taken are done at your own risk

# Guide

![](https://github.com/evy0311/t440p/raw/master/Guide%20Stuff/T440p_Day.png)

![](https://img.shields.io/github/issues/evy0311/t440p.svg) ![](https://img.shields.io/github/forks/evy0311/t440p.svg) ![](https://img.shields.io/github/stars/evy0311/t440p.svg) ![](https://img.shields.io/github/license/evy0311/t440p.svg) ![](https://img.shields.io/twitter/url/https/github.com/evy0311/t440p.svg?style=social)


## Information
##### What works:
- Power management/sleep
- Brightness Control
- Battery Information
- Speaker Audio
- USB Ports
- Graphics Acceleration
- Facetime/iMessage
- Trackpoint/Touchpad (see below)
- Pretty much everything except what is listed below

##### What Doesnt Work:
- Audio Jack (as a microphone and as a headphone jack)
- Trackpad middle scroll button

**Note:** I am currently working on a fix for the items listed above. If you use this guide and information and find that something does not work, please submit an issue request so I can work on a fix.

## Creating the USB Installer
Since I don't have access to a legitimate Mac, I needed to be able to create a vanilla macOS installer. I highly advise against using "distro" style installer's like the one's from Niresh. Although they may claim to be "vanilla," they never truly will be. However, it is really nice to be able to use them to create a vanilla installer of macOS. It is possible to create the installer from a real Mac, but the steps that follow will be for those that do not have access to an actual Mac.

1. Download Niresh's distro for macOS High Sierra Here.
2. Download a copy of TransMac. It has a free, 15-day free trial. You can obtain it Here.
3. Open TransMac as an administrator. Then, right click on the USB drive you're using, and clean "format disk for Mac". I recommend a USB 2.0 flash drive with a capacity of 32gb or larger.
4. Then, burn the .dmg file you downloaded from Niresh to a flash drive. You can do this by right clicking on the drive and clicking "Burn disk image for Mac."  
5. After the .dmg is finished burning to the USB, you can go ahead and eject it from your computer.
6. Boot to the USB drive and install macOS High Sierra. 
7. Then, boot into High Sierra. Once you're in, make sure you can connect to the internet. After that, open the App Store and download the upgrade file for "macOS Mojave."
8. Download Clover bootloader from [Here](https://bitbucket.org/RehabMan/clover/downloads/). 
9. **IMPORTANT (DO NOT MISS THIS):** Now, copy Clover bootloader and the kexts files that you have downloaded to another USB drive (not the one you're burning the installer too) or an external hard drive. You will need access to them later.
10. Copy the `CLOVER` folder you have downloaded from this repository onto your USB drive as well.
11. I recommend following this guide [Here](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/) for properly formatting your USB drive and getting it ready for installing the macOS Mojave installer onto it. This guide also walks you through how to download the Mojave installer and writing it to the USB drive as well.
12. Copy the `CLOVER` folder you have downloaded from this repository into `EFI/`. You can simply copy over the whole folder as the config.plist and everything else is already configured for the T440p. 
13. The most important step that I missed twice in the guide above is to make sure you add the `HFSPlus.efi` driver into `/EFI/Clover/drivers64UEFI`. I missed this step twice and couldn't see any drivers at all inside of Clover.
14. We are now ready to continue into the next topic: Installing macOS Mojave.



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

##### Customizing About This Mac

In order to customize the About This Mac section, I recommend you follow the guide [Here](https://github.com/Haru-tan/Hackintosh-Things/blob/master/AboutThisMacMojave.md "Here").

For the section about changing the logo, you can use the T440p logo's I have designed in ` /SystemLogos/`.
