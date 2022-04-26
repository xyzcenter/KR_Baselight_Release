# Baselight Release 5.3.16616 (2022-04-22)

## Important Notes

Baselight 5.3 no longer supports the following legacy hardware and OS platforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
* Tape deck control within Baselight (the standalone VTRE application remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 10.14 and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FilmLightOS 8 is now released and supported by Baselight. The minimum software requirement is that your system must be running Baselight 5.3.15167 or later \[bug 60310]

FilmLightOS 8 or later is required to use GPU JPEG 2000 acceleration with NVIDIA Ampere GPUs

Truelight Player (tl-player) is no longer available.

When running Baselight CONFORM or Daylight on macOS 11.x Big Sur with AJA devices, AJA Software v16.x is required.





## New Features Since Baselight 5.3.16381

### Miscellaneous

* Improved speed of raidadaptec diagnostic \[bug 60171]

## Bug Fixes Since Baselight 5.3.16381

* Added support for the NVIDIA driver version 510.54 on FilmLightOS 8 systems \[bug 59873]
* Audio meters now work when using an SDI card as an audio output device while using DP, HDMI or DVI output from a GPU \[bug 60189]
* Fixed desk service failing to exit \[Bug 60218]
* Fixed a hang when using Blackmagic devices in macOS Monterey \[bug 60126]
* Fixed an issue with macOS floating licences \[bug 57978]
* Added support for NVIDIA Quadro T1000 GPU \[bug 60264]
* Fixed incorrect channels being read from multi-part OpenEXR media when channel names being read exist in more than one of the parts which are being read \[bug 60326]
* Fixed bl-config-xorg and fl-service xorg on Rocky Linux 8.5 \[bug 60041]
* A Truelight install is no longer recommended to use Baselight; it will only be needed for older scenes which make use of resources installed with Truelight \[bug 57602]





## Known Issues

* When running Baselight CONFORM or Daylight on macOS 10.15 Catalina, local volumes which are defined in volume.cfg within /Volumes can result in "Stale NFS file handle" errors. This is due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  * click the padlock icon and use your password or Touch ID to allow changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  * select the file called "nfsd" and click "Open" After restarting your Mac, the volume(s) should now work correctly \[bug 53073]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Baselight 5 enables GPU acceleration in OFX plugins. This improves performance but may introduce new issues depending on the 3rd-party plugin implementation \[bug 47224]
* Canon RAW media added to scenes in Baselight 5.1.10836 or earlier using the tone curve setting "Canon Log" may now fail to decode with an error message stating "Invalid function parameter". Changing the tone curve will allow images to decode, but will change their look \[bug 50371]
* ProRes RAW decodes have been seen to fail on macOS 10.14.5 with Apple Pro Video Formats 2.2 installed; downgrading to Apple Pro Video Formats 2.1.1 fixes this issue \[bug 56591]
