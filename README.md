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
- Pretty much everything accept what is listed below

##### What Doesnt Work:
- Audio Jack (as a microphone and as a headphone jack)
- Trackpad middle scroll button

**Note:** I am currently working on a fix for the items listed above. If you use this guide and information and find that something does not work, please submit an issue request so I can work on a fix.

## Creating the USB Installer
Currently writing.

## Installing macOS Mojave
Currently writing.

## Post-Installation
Currently Writing.

##### FHD Screen

If you have done the full HD (1920x1080) screen mod (like myself), it is recommended that you install [One Key HiDPI](https://github.com/xzhih/one-key-hidpi "One Key HiDPI").  This will mimic the "retina" display feature that many of Apple's newer laptops come with. 

##### UltraBay HDD

If you are using a HDD or SSD in place of the normal optical drive, you will need to install AHCIPortInjector.kext and AppleAHCIPort.kext into `Library/Extensions`.

`AHCIPortInjector.kext` fixes the `Disk not initialized` issue (disk cannot be read). `AppleAHCIPort.kext` fixes the disk being detected as an external drive (instead of internal).

##### Customizing About This Mac

In order to customize the About This Mac section, I recommend you follow the guide [Here](https://github.com/Haru-tan/Hackintosh-Things/blob/master/AboutThisMacMojave.md "Here").

For the section about changing the logo, you can use the T440p logo's I have designed in ` /SystemLogos/`.




