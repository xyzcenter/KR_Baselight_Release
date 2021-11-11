# Baselight Release 5.3.15701 (2021-11-08)



Baselight Release 5.3.15701 (2021-11-08)

## Important Notes

Baselight 5.3 no longer supports the following legacy hardware and OS platforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
* Tape deck control within Baselight (the standalone VTRE application remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 10.13 and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FilmLightOS 8 or later is required to use GPU JPEG 2000 acceleration with Nvidia Ampere GPUs

Truelight Player (tl-player) is no longer available.

When running Baselight CONFORM or Daylight on macOS 11.x Big Sur with AJA devices, AJA Software v16.x is required.

## New Features Since Baselight 5.3.15583

* Updated to ARRIRAW SDK 7. This adds support for media from Alexa Mini LF cameras. The ARRIRAW Params operator shows which SDK is being used (the older v5 SDK or the current v7 SDK), and allows the SDK to be switched if the media is supported by both SDKs. Note that a reduced set of parameters is available for the v7 SDK \[bug 57557]
* CentOS/FilmLightOS 8 systems now use the "nconnect=8" option when mounting NFS filesystems under /vol. This option causes the client to use multiple TCP connections to the NFS server, significantly improving performance \[bug 58972]

## Bug Fixes Since Baselight 5.3.15583

* The "desk" fl-service now works correctly on Baselight TWO/X systems \[bug 58890]
* Fixed Unknown error when relinking AAF \[bug 58958]
* Fixed occasional failure to read an embedded LUT (e.g. from .ari files) \[bug 59134]
* Fixed crash caused when cancelling a conform that had not started \[bug 59131]
* Fixed Mac to Mac communication for the Remote Slate \[bug 59067]
* Fixed crash when switching between Chalk profiles \[bug 59135]

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
