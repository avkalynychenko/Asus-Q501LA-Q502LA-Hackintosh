##Asus Q501/Q502LA Hackintosh## FORKED From https://github.com/RanbirAulakh/Asus-Q501LA-Hackintosh

Hello,

I have updated this repository for El Capitan. This laptop, Asus Q501LA/Q502LA, is near 100% stable. There are some issues, see the **issues** section. This is just for educational purposes and do it in your own risk! Once again, this only works with **Asus Q501LA and Q502LA**. 

How to install Maverick/Yosemite on Asus Q501LA:
* https://github.com/shamesung/Asus-Q501LA-Q502LA-Hackintosh/wiki/2.-Yosemite-Install

Additional reading:
* https://github.com/RanbirAulakh/Asus-Q501LA-Hackintosh/wiki
* https://github.com/gvkt/Asus-Q501LA-Hackintosh/wiki

How to install El Capitan on Asus Q501LA:
* https://github.com/shamesung/Asus-Q501LA-Q502LA-Hackintosh/wiki/3.-El-Capitan-Install and download the [zip 	  file](https://github.com/RanbirAulakh/Asus-Q501LA-Hackintosh/releases/tag/1.0)

PS: You are free to fork this and improve anything, if there is an improvement, I will accept changes!

##Table of Content##
* [Issues](#Issues)
* [Changelog](#Changelog)
* [Requirements](#Requirements)
* [DSDT Instructions](#Instructions)
* [Kexts](#Kexts)
* [Credit](#Credit)
* [FAQs](#FAQs)

# <a name="Issues"></a> Issues
- SD Card Reader (not tested!)
- Graphical glitches (1-2%)
- Doesn't fully shutdown (20% of the time)
- Trackpad is slow
- Intel Wi-Fi Card (Needs to be replaced) Recommended: BCM94352
- Touchscreen Partially Works - Able to move cursor around but tapping anying on the screen will have undesired results
- HDMI Audio does not work (may be fixable)
- HDMI unplugging causes graphics to garble plugging back fixes it (to unplug HDMI shutdown the laptop)

# <a name="Changelog"></a> Changelog
- Updated for El Capitan

# <a name="Requirements"></a> Requirements
- Asus Q501LA ( http://www.amazon.com/Asus-Q501LA-BBI5T03-15-6-Touch-Screen-Laptop/dp/B00FRSXJKI )
- Asus Q502LA **i5-4210U ONLY** (http://www.amazon.com/Asus-Q502LA-BBI5T12-Touch-Screen-Laptop-Convertible/dp/B00S8ISOW2)
- MaciASL ( http://sourceforge.net/projects/maciasl/files/ ) --> If you want to modify some .aml files
- MAC OSX distro, use AppStore. Please avoid 3rd-party distro(s)!

# <a name="Instructions"></a> DSDT Instructions
This DSDT and SSDT only works in **Asus Q501LA/Q502LA**. This will **not work** on other laptop.

**How to open EFI parition:**
 1. open your terminal and type in

    `mkdir /Volumes/efi`
    
    `sudo mount -t msdos /dev/disk0s1 /Volumes/efi`

 2. Then type in your password, there, you got EFI mounted on your laptop, and ready to use.

**Convert *.dsl to *.aml**
 1. Open MaciASL and open DSDT and SSDTs
 2. MaciASL -> File -> Save as -> `save as ACPI Machine Language Binary`
 3. Rename `
	- `dsdt.aml` to `DSDT.aml`
	- `ssdt.aml`, `ssdt1.aml`, `ssdt2.aml`,... to `SSDT.aml`, `SSDT-1.aml`, `SSDT-2.aml`, ...

**Place DSDT and SSDT to Clover**
 1. Place DSDT and SSDT in

    `cd /Volumes/efi/EFI/CLOVER/ACPI/patched/`
 
 2. After that, place config.plist in

    `cd /Volumes/efi/EFI/CLOVER/`
    
Before you reboot, you will need to install certain `kexts`, so your laptop can run close to 100%.

# <a name="Kexts"></a> Kexts
There are about 9 kexts that you will need to install. I do not recommend using Multibeast to install your kexts. I would install individual. 

In `kexts` folder, you find:
- IntelBacklight.kext
- ACPIBatteryManager.kext
- ApplePS2SmartTouchPad.kext
- AsusNBFNKeys.kext
- CodecCommander.kext
- FakeSMC.kext
- GenericUSBXHCI.kext
- RealtekRTL8111.kext
- AppleHDA.kext

I recommend you install `AppleHDA`, `CodecCommander`, `FakePCIID_Intel_HD_Graphics`(https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads), `FakePCIID`, and `ApplePS2SmartTouchPad` directly into `/System/Library/Extensions/`. And the rest goes to `/Volumes/efi/EFI/CLOVER/kexts/Other/`. Then fix permissions (using kext utility).

Then reboot, you should have close to 100% stable hackintosh.

# <a name="Credit"></a> Credit
- InsanelyMac, TonyOSx86, MaciASL
- Rehabman & his repo
- conradolpz - for sleep and changes in BIOs
- [gvkt](https://github.com/gvkt/) - updated my repository for Yosemite
- RanbirAulakh

# <a name="FAQs"></a> FAQs
**I got kernel panic. What should I do?**
- It is most likey has to do with bad kexts you have installed. If you have Voodoo or anything related to Voodoo, just remove that and fix permissions using kext utility, boot in **safe mode** to remove voodoo kexts.

**What each SSDTs represent?**
- SSDT 1, 2, 7, 8, 9 are CPU related.
- SSDT 3 is Unknown.
- SSDT 4 is Sata/Hard Drive releated.
- SSDT 5 is Graphics related.
- SSDT 6 is Sleep/_WAK related.

**What to do if you found an issue or bug?**
- Login your github account and go [here](https://github.com/RanbirAulakh/Asus-Q501LA-Hackintosh/issues) and report an issue. Then I will look over your issue.
