# Baselight Release 5.3.20255 (2024-04-25)



## Important Notes

Baselight 5.3 no longer supports the following legacy hardware and OS platforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
* Tape deck control within Baselight (the standalone VTRE application remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 11 Big Sur and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FilmLightOS 8 or later is required to use GPU JPEG 2000 acceleration with NVIDIA Ampere GPUs, and to use Blackmagic RAW media

Truelight Player (tl-player) is no longer available.

When running Baselight CONFORM or Daylight on macOS with AJA devices, AJA Software v16.x is required.

## New Features Since Baselight 5.3.19778

* Updated to R3D SDK 8.5.1. This fixes several bugs, and adds support for V-RAPTOR \[X] media. Note that Extended Highlights is beta functionality and is not yet available \[bug 67193]
* Added support for NVIDIA 550.76 driver \[bug 68044]
* Added support for new FilmLight CONNECT traffic routing scheme \[bug 68056]

## Bug Fixes Since Baselight 5.3.19778

* Fixed crash in flapid when adding an image item to a FormatBurnin via FLAPI \[bug 67724]
* Fixed extremely slow reading of some BLG files, in particular those using the "ACES RRT 1.1+" DRT \[bug 33064]
* Fixed issue with shot length for sequences inserted into 23.976fps scenes using FLAPI \[bug 67774]
* QuickTime metadata with reverse-DNS names, such as that in Apple ProRes RAW media, is now written to OpenEXR output files \[bug 67635]
* Removed the CPU speed test from fl-diag as it had become increasingly less useful \[bug 67227]
* Fixed error message when creating a new FilmLight CONNECT session via the Client Sessions view \[bug 66626]

## Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma \[bug 62237]
* Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  * click the padlock icon and use your password or Touch ID to allow changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  * select the file called "nfsd" and click "Open" After restarting your Mac, the volume(s) should now work correctly \[bug 62601]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Setting the Resampling Method in a strip to "Optical Flow" will force a transform to the scene's Working Format, similar to the "Process in Working Format" option. Please consider this when rendering to formats larger than the Working Format \[bug 54652]

***
