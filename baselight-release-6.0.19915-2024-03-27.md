# Baselight Release 6.0.19915 (2024-03-27)

##

### Important Notes

Baselight 6.0 no longer supports **FilmLightOS 6**. Please contact [FilmLight Support](mailto:baselight-support@filmlight.ltd.uk) to discuss upgrading to FilmLightOS 8. Bug 60176

**RED Rocket** hardware is no longer supported. Bug 65725

Using a **Grade Result Colour Space** is deprecated and this functionality may be removed in a future release. [Please watch this video](https://filmlight.ltd.uk/graderesult) for information about recommended workflows for telecine-style grading. Bug 64729

**Dolby Vision external CMU devices** are no longer supported. Bug 62581

The **vtre** application is no longer included. Bug 66448

### New Features Since Baselight 6.0.19881

* Updated to R3D SDK 8.5.1. This fixes several bugs, and adds support for V-RAPTOR \[X] media. Note that Extended Highlights is beta functionality and is not yet available. Bug 67193

### Bug Fixes Since Baselight 6.0.19881

* Fixed memory leak in Timeline drawing, which could occur if a shot overlapped other shots' horizontal extents (a common example would be an offline located above the grading strips). Bug 67522
* Fixed extremely slow reading of some BLG files, in particular those using the "ACES RRT 1.1+" DRT. Bug 33064
* Fixed editing of mark note text via clicking on the note text bubble in the timeline. Bug 67684

### Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237
*   Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

    * Open System Preferences from the Dock or the Apple menu
    * Choose "Security & Privacy"
    * Click the padlock icon and use your password or Touch ID to allow changes to be made
    * Select "Full Disk Access" in the list on the left
    * Click the `+` button on the right to open a file browser
    * On your keyboard, press `/` to open the "Go to the folder" dialog
    * Enter `/sbin` and click `Go`
    * Select the file called `nfsd` and click `Open`

    After restarting your Mac, the volume(s) should now work correctly. Bug 62601
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights. Bug 44769
* The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798
* Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406
* On some Intel Macs, adding or removing Luma Waveform, RGB Parade, or YCbCr Parade views can result in image corruption and missing scopes. However, if one restarts Baselight with these views present, the scopes will behave properly. Bug 65932
* Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016
