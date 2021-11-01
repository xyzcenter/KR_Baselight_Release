# Baselight Release 4.4m1.8174 (2016-04-07)



## New Features Since Baselight 4.4m1.8085

### Baselight CONFORM

*   Added the new Baselight CONFORM product on Mac OS X. This runs on any Mac system with OS X 10.9 or later.

    It supports all Baselight functionality except

    *   Rendering (though it can submit renders to the Operations Queue on

        a full Baselight system)
    * SDI output via an AJA device
    * Control surfaces (Slate, Tangent, etc)

    The Baselight PORTABLE product is no longer available.

### GPU Acceleration

*   Improved utilisation of multiple render GPUs in Generation VI

    Baselight TWO and Baselight X systems, which can significantly

    accelerate caching, playback and rendering operations \[bug 35237]

### File Formats

* DNG files with post-demosaic operations (e.g. warp corrections) are now read, but the corrections are not rendered \[bug 34369]
* Added new cube formats for Amira and BMD with extended range. The IRIDAS cube worked for Amira, once they fixed their reader but this makes the Amira user's choice easier \[bug 31767]
* Added support for reading split-file Canon EOS C300 media, and improved metadata reading from these files \[bug 34933]
* Added support for 12-bit encoding in the DNxHR HQX codec \[bug 34868]
* Added support for reading multi-part OpenEXR files (except where the display window is not the same for all parts) \[bug 34972]
* Added support for reading multi-view OpenEXR files. This includes automatically selecting left/right views in stereo scenes for both the image and any referenced matte channels \[bug 35059]

### Miscellaneous

* The Rotation parameter of Transform operators is now adjustable in hundredths of a degree \[bug 34384]
* When a scene is opened and a format which it used has been edited or deleted, a Scene Format is created to maintain the previous behaviour of the scene. A dialog box is now presented when a scene is opened to explain this \[bug 34467]
* Updated LUT export with Extended Ranges support for HDR input. Truelight cubes and the newly added Autodesk CTF format support an extra input LUT for mapping high dynamic range inputs. There is now an option to include this in the LUT export dialog \[bug 33499]
* LUT export also now includes an option to override the input colour space, replacing the one used for a sequence with one specified for the LUT export. This allows LUTs to be generated for use in other applications using images that have been converted to a different colour space \[bug 33157]
* Added option to sort jobs by size (note that this feature is not available when browsing jobs on FLOS 2.1 systems) \[bug 5208]
* LUT export has been extended to include options for the Input Display Rendering Transform when the Input Colour Space is set to anything other than the Sequence Input Colour Space. Previously the Input DRT was not handled in the LUT export \[bug 35118]

## Bug Fixes Since Baselight 4.4m1.8085

* Fixed LUT export which was failing for Shots with Hue Angle and Matte Tool Blur \[bug 34225]
* Improved accuracy of warning counter on EDL Import View \[bug 34284]
* Sequences on cloud media are no longer reported as missing when using Verify on a render \[bug 32311]
* Fixed alpha channels in thumbnails of ProRes 4444 media \[bug 34334]
* Fixed keyboard accelerator for changing Edit Type on Mac \[bug 34336]
* Fixed error with zero handling in "Dolby: ST 2084 PQ / P3 D65" colour space \[bug 34382]
* Fixed intermittent crash related to periodic events in the user interface \[bug 34305]
* MJPEG encoded material in MXF files is no longer stretched from legal to full on read \[bug 34402]
* Fixed screen switching by double tapping the UI/Image button on systems with both multiple monitors and a Blackboard 1 \[bug 32511]
* Updated the ACES Scene Template to use ACES Cineon Log / AP0 as a working colour space, due to issues with ACEScc \[bug 34051]
* Fixed bug setting up floating-point cubes that take negative values. This gave visible pixels in regions that should be fully dark. Such cubes are not used outside development work, so we do not expect current Baselight jobs to be affected \[bug 34465]
* Fixed Group Grading of several operator parameters \[bug 34407]
* Fixed issues with Cloud Media connected to the node of a Baselight TWO system \[bug 34297]
* A missing source file will no longer case a Consolidate operation to abort \[bug 34240]
* Adaptec web interface no longer requires an SSL connection because many browsers refuse its self-signed certificate \[bug 31422]
* BLG export using unavailable filename templates (e.g. %P when the shot has no clip name) now correctly report the error \[bug 30551]
* Fixed an issue that prevented interop DCPs being rendered via command line \[bug 31693]
* Rendering a DCP now finishes with 'Wrote DCP package', to better indicate the completed status of the render job \[bug 31967]
* Fixed an issue that could cause frames to be repeated in MP4 movies with frame rates of 100 fps or higher \[bug 34594]
* Fixed excessive file searching when opening some R3D movie files \[bug 34690]
* Adjusted calculation of max frame size in JPEG 2000 compressed MXF files to avoid introducing minor bitrate overshoots when creating DCPs in e.g. Clipster \[bug 31622]
* Fixed LUT export for a LUT transforming from a Log Colour Space to a Linear Colour Space, which previously clamped output values to 1.0 \[bug 34423]
* Fixed LUT export for shots with pixel aspect ratio other than 1.0 \[bug 34611]
* Fixed some console warnings about undefined parameters when rendering H264 to MP4 or Quicktime containers \[bug 34825]
* Deleting a format which overrides another format no longer removes some mappings to the remaining format \[bug 34920]
* Fixed crash when activating a licence from a downloaded file \[bug 33708]
* Improve licensing dialog and activation process \[bug 33418]
* Improvements to Licence window layout \[bug 34464]
* Updated to latest version of fl-setup-vol, which removes support for Avid Unity filesystems (superceded by Avid ISIS) \[bug 34599]
* Improved error message when trying to open an encrypted DCP or MXF \[bug 34979]
* Fixed 100% quality JPEG output \[bug 35034]
* Fixed deselect on paste still clearing the selection when it was turned off \[bug 25917]
* Reduced risk of GPU memory errors when working with large RED media (e.g. 8K WEAPON) \[bug 35041]
* Updated preview features licence support \[bug 34539]
* Fixed a memory allocation issue which could cause subtitles not to appear in DCP output \[bug 35012]
* Avoid running overnight disk defragmentation process twice on Baselight TWO systems \[bug 34925]
* Fixed temperature query tool 'sdi-info -temp' bug \[34978]
* Fixed an issue where the Blackboard 'Undo' functionality was no longer available after a Tracker modification using any Blackboard trackball or ring \[bug 35192]
* Fixed a problem with Optical Flow retime, where Baselight FOUR and EIGHT systems would render incorrectly \[bug 35091]
* Fix application hang caused by Audio Waveform view \[bug 35512]
* Improved serial number and licence file validation support \[bug 35363]
* Fix behaviour of "Reset All To Camera Metadata" on R3D Params operator \[bug 35516]
* Update licensing to allow appropriate licenses to be installed \[bug 35896]
* Fixed an issue that caused blocky artefacts and green frames when decoding XDCAM \[bug 36016]
