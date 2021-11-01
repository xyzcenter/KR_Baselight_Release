# 베이스라이트 릴리즈 노트 5.2.14242 (2021-01-26)



Baselight Release 5.2.14242 (2021-01-26)

## Important Notes

### Compatibility With 5.1

Due to changes listed below, notably the new Image Transform Settings, scenes saved in 5.2 will no longer open in 5.1.

So as to ensure consistent image decoding access to remote Baselight, Daylight or FLUX Store systems also require a 5.2 release installed.

BLG files exported from 5.2 cannot be used by 5.1 products, including Baselight Editions.

### Baselight FOUR and EIGHT

Baselight 5.2 is the last version that is supported on Baselight FOUR and Baselight EIGHT systems. Baselight 5.3 and later will not install or run on such systems.

### DVI-to-SDI Convertors

Baselight 5.2 is also the last version for which DVI-to-SDI Convertors or Combiners performing that function are supported. At Baselight 5.3 Generation V systems will have to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems will be constrained to a GPU DVI output only.

### Baselight CONFORM

Installing and running on macOS 10.15 Catalina is now supported. Due to Apple's enhanced security, you will be asked to permit Baselight to access files on your local and/or remote disks \[bug 51560]

## New Features Since Baselight 5.2.14009

*   FLUX Store systems now run internal diagnostics periodically, and those diagnostic results are available to every Baselight system that shares the same cloud. The 'Network' group has a set of results for 'FLUX Store diagnostics', where the diagnostics are summarised for each FLUX Store.

    Any failures or warnings in any FLUX Store's own diagnostics will result in a warning for the Baselight. Selecting any of the specific warnings or failures will launch a new fl-diag to view the FLUX Store diagnostics in full detail \[bug 23035]

## Bug Fixes Since Baselight 5.2.14009

* Fixed Baselight HOME causing licensing errors on a Baselight TWO \[bug 56348]
* Fixed audio sync with Blackmagic Design UltraStudio and DeckLink SDI devices \[bug 56346]
* Added support for Adaptec SmartRAID 2.30 firmware for improved compatibility with HGST Data60 drive arrays. This firmware is applicable to Adaptec SmartRAID 3154-4i, 3154-24i and 3154-8i16e controllers \[bug 56477]
* Prevent the fl-diag dpm test from causing a WARN status when a disks maximum-ever temperature has been above 70 degrees \[bug 56560]
* Fix an issue that could cause some fl-diag modules not to run when fl-diag is invoked using the '-run module' option \[bug 56564]
* Fix an issue that could cause the dpm diagnostic tool to fail on systems that have SSDs \[bug 55984]
* Fix an issue that affected the running of selected modules in the fl-diag tool \[bug 56598]
* Fixed an issue that caused crash reports for the 'vol' service to be incorrectly sent to FilmLight on macOS \[bug 53938]
* Fixed fl-diag cubixconfig test slowness \[bug 56619]
* Fixed slow Cuts View behaviour when using Optical Flow Sequence Resampling \[bug 56713]
* Fixed corrupted 2048x1080 image output on AJA T-Tap \[bug 56722]
* Fixed local rendering not being available on Baselight CONFORM systems running Baselight HOME \[bug 56764]
* Fixed invalid green HDMI output on AJA T-Tap \[bug 56419]
* Fixed several bugs in Multi-Paste when:
  * Matching by "Record Timecode" and some shots had speed changes
  *   Source and destination scenes had different working frame

      rates
  *   Source and destination shots had different timecode frame

      rates \[bug 44994]
* Fixed issue with missing thumbnails on Blackboard 2 \[bug 56669]
* Fixed a bug that affected the list of diagnostic tests that are run during fl-diag operation \[bug 56802]

## Known Issues

* When running Baselight CONFORM or Daylight on macOS 10.15 Catalina, local volumes which are defined in volume.cfg within /Volumes can result in "Stale NFS file handle" errors. This is due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  *   click the padlock icon and use your password or Touch ID to allow

      changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  *   select the file called "nfsd" and click "Open"

      After restarting your Mac, the volume(s) should now work correctly

      \[bug 53073]
* When running on a Baselight TWO/FOUR/EIGHT system whose UI host has a NVS 450 graphics card, many of the new operators in Baselight 5 currently cause thumbnail errors in Cuts View and elsewhere. This issue will be addressed in a future Baselight 5 release. Please contact FilmLight Support if you wish to discuss upgrading the graphics card in your UI host \[bug 40279]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Baselight and Daylight are known to hang on macOS 10.13 High Sierra when run on older (2012 and mid-2014) MacBook Pro machines with nvidia graphics \[bug 44949, bug 48343]
* Sony RAW media added to scenes in Baselight 4.4m1.9217 or earlier may now fail to decode at half resolution. A workaround is to enable Max Quality decoding on the cursor and/or Sequence \[bug 46625]
* Canon RAW media added to scenes in Baselight 5.1.10836 or earlier using the tone curve setting "Canon Log" may now fail to decode with an error message stating "Invalid function parameter". Changing the tone curve will allow images to decode, but will change their look \[bug 50371]
* On first installation on macOS Mojave (10.14) setup of the vol service will fail due to macOS security enhancements. In order to work around this issue it is necessary to manually run the command 'sudo fl-service setup vol' and authorise Terminal to administer the computer \[bug 50732]
* AAC-encoded audio may not sync correctly when reading MP4-files created by Adobe Premiere. Typically the offset is around a frame in either direction \[bug 51199]
* Disk Performance Monitoring (DPM) occasionally indicates above threshold latency figures for MSCC 31XX RAID controllers when system performance is not effected \[bug 53435]
