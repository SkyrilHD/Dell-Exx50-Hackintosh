# Dell Exx50 Hackintosh

[![OpenCore Version](https://img.shields.io/badge/OpenCore-0.6.9-green.svg)](https://github.com/SkyrilHD/Dell-Exx50-Hackintosh/)
[![GitHub release](https://img.shields.io/github/release/SkyrilHD/Dell-Exx50-Hackintosh.svg)](https://github.com/SkyrilHD/Dell-Exx50-Hackintosh/releases/)
[![GitHub issues](https://img.shields.io/github/issues/SkyrilHD/Dell-Exx50-Hackintosh.svg)](https://github.com/SkyrilHD/Dell-Exx50-Hackintosh/issues/)

### This repo contains all the fixes for Exx50 on macOS Big Sur.

### I need a [confirmation](https://github.com/SkyrilHD/Dell-Exx50-Hackintosh/discussions/2) if the EFI is working on other models, so I can complete my list. Thanks!

I noticed that my E7250 has nearly the same specs as other Exx50 models, so this repo was created. This will NOT replace the E7250 repo.

Tested on:

Model | Latitude E7250
------------- | ---------------
CPU | Intel Core i5-5300U
GPU | Intel HD Graphics 5500
RAM | 16GB DDR3 1600Mhz
Storage | SK hynix SC210 mSATA 128GB
WiFi | Intel Dual Band Wireless-AC 7265
GSM/LTE | Sierra Wireless AirPrime EM7305 (DW5809e)
Software | macOS 11.2.3 Big Sur

## EFI Compatibility list

Exx50 model | Supported? | Additional notes
:----------: | :----------: | :----------:
13 7350 | _Yes_ | 2
E7450 | **Yes** | -/-
E7250 | **Yes** | -/-
E5550 | **Yes** | 1
E5450 | **Yes** | -/-
E5250 | _Yes_ | -/-
E3550 | _Yes_ | 1
E3450 | _Yes_ | -/-

Bold: confirmed working

Italic: not confirmed

1: disable your dGPU (if you have one) with a SSDT

2: make sure to change your SMBIOS to MacBook8,1

Disclaimer: The list was created based on the specs. Please correct my mistakes

## What works?

Everything...

## Download and Install

Go to the [Releases](https://github.com/SkyrilHD/Dell-Exx50-Hackintosh/releases/) page of this repo and download the latest release. Then, copy the EFI folder to your EFI partition... That's it.

## What to expect

- Works really good
- no Verbose (Apple Logo)
- little glitches at boot (Graphics Driver loads)
- brightness control now works via F11/F12
- Apple's audio driver as main
- sleep works
- Bluetooth is working too and can also be disabled

## Graphical glitches in macOS

There are two ways to fix the horizontal glitches (as seen [here](https://github.com/newyb/Something-useful-of-E7250/blob/main/BUG2%20at%20sign.jpg)) in macOS.

1. (Recommended) Enable 'Enable Legacy Option ROMs' in the BIOS by clicking General>Advanced Boot Options. [Here](https://supportkb.dell.com/img/ka02R000000oLv9QAE/ka02R000000oLv9QAE_en_US_2.jpeg) is a picture of that option.

2. If you want to use pure UEFI as a workaround, you can use [one-key-hidpi](https://github.com/xzhih/one-key-hidpi). Download and run the code and select 'Enable HIDPI (with EDID)'. Then restart your computer and the glitches should be resolved.

## Intel WiFi

Starting with v2.3, AirportItlwm is included in the EFI but disabled to ensure stability. To enable Intel WiFi, enable it in the config. The EFI will only have stable versions of AirportItlwm. So if you want to experiment with Intel WiFi, you can do so by visiting the [itlwm repo](https://github.com/OpenIntelWireless/itlwm) and downloading the latest alpha build. Stability can be much worse, so use with caution! Also, do not forget to enable IntelBluetooth to make Bluetooth more stable!

If you experience no internet with AirportItlwm, I suggest switching to itlwm and see if it works there.

## Recommended BIOS settings
<details>
  <summary>Expand BIOS settings</summary>
  
**General:**

* Boot sequence -> Boot List Option: UEFI
        
**System configuration:**
        
* Parallel Port: Disabled
* Serial Port: Disabled
* SATA Operation: AHCI
        
**Security:**

* TPM Security: Off
 
**Secure Boot:**

* Secure Boot: Disabled
  
**Power Management:**

* Wake on LAN/WLAN: Disabled
* USB Wake Support: Off

</details>

## How to Install macOS Big Sur

There are two ways you can install Big Sur:

1. If you have an already working macOS, download the Installer from the App Store and make a bootable Installer with `createinstallmedia` by using this command in Terminal: `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. If you are using Windows, use [macrecovery.py](https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery) from the offical [OpenCore release package](https://github.com/acidanthera/OpenCorePkg/releases/). Follow this [guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) to understand how it works.

After you have created a bootable Installer, copy the EFI folder to the EFI partition and install as usual. After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

If you want an OOTB-WiFi: You need to change your WiFi card in order for your internet to work. Buy it on eBay or your trusted website and find a suitable card with the kexts.

## Screenshot

![About this Mac](https://user-images.githubusercontent.com/28839925/95805006-9d98d000-0d04-11eb-80f5-4d8c385f0cee.png)


## Credits

Thanks to:

- me (for wasting my time writing this and providing fixes)
- acidanthera (for making an awesome bootloader)
- dortania (with their troubleshooting guide, I was able to fix sleep)
- DrHurt (for supporting our ALPS Trackpad)
- emrah7celik (for providing a guide on how to fix the glitches in macOS with pure UEFI)
- Harvé (for suggesting to inject property in Clover)
- hickorysb (for confirming the fix for glitches with Legacy Option ROMs)
- zxystd (for fixing the Bluetooth issue and Intel WiFi card)


All this was written on an E7250 with Big Sur installed :D
