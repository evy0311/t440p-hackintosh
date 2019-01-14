# T440p - Hackintosh Guide

### Overview

- This guide references a few other guides. Credit for those guides is given to their respective owners.
- It is assumed that you have a decent understanding of Hackintosh, the macOS environment, as well as how to do basic computer tasks
- Will guide you through some of the different information needed to get macOS Mojave 10.14.2 working on your Thinkpad T440p
- Special thanks to jloisel and his guide [Here](https://github.com/jloisel/t440p "Here") on how to configure the T440p for a hackintosh install. The `CLOVER` folder and the kexts for the ultrabay are his and credit goes to him. 
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
- Touchpad middle scroll button (works like a midle click button, but does not allow you to use it to scroll with the Trackpoint)

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
8. Download Clover bootloader from Here.
9. Still working on writing...



## Installing macOS Mojave
Currently writing.

## Post-Installation

##### FHD Screen

If you have done the full HD (1920x1080) screen mod (like myself), it is recommended that you install [One Key HiDPI](https://github.com/xzhih/one-key-hidpi "One Key HiDPI").  This will mimic the "retina" display feature that many of Apple's newer laptops come with.

##### UltraBay HDD

If you are using a HDD or SSD in place of the normal optical drive, you will need to install AHCIPortInjector.kext and AppleAHCIPort.kext into `Library/Extensions`.

`AHCIPortInjector.kext` fixes the `Disk not initialized` issue (disk cannot be read). `AppleAHCIPort.kext` fixes the disk being detected as an external drive (instead of internal).

##### Setting up Apple services (Facetime, iMessage, etc.)
I *highly* recommend following [This guide](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) to get these features working. It worked for me on the first try and was super straight forward compared to other guides that I have seen before in the past. 

##### Customizing About This Mac

In order to customize the About This Mac section, I recommend you follow the guide [Here](https://github.com/Haru-tan/Hackintosh-Things/blob/master/AboutThisMacMojave.md "Here").

For the section about changing the logo, you can use the T440p logo's I have designed in ` /SystemLogos/`.
