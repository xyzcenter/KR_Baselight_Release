# 베이스라이트 릴리즈 노트 5.0.10184 (2018-02-02)



## New Features Since Baselight 5.0.10074

* Added support for HP Z2 UI Host \[bug 45230]
*   The conversion of 4.4m1 jobs into 5.0 jobs requires the installation of Baselight 4.4m1.10068, available from the FilmLight website.

    This is a 'conversion' release, and should not be used for 4.4m1 jobs, it only needs to be installed for this and later 5.0 releases to convert 4.4m1 jobs fully.
* Added support for 8TB drives \[bug 46274]
* Added support for the Sony VENICE camera \[bug 43258]
* Updated to RED SDK v7.0.6. This includes a fix for failures on AMD GPUs on macOS 10.13.2 and up \[bug 46469]
* Generation VII Baselight TWO/X systems are now supported.

## Bug Fixes Since Baselight 5.0.10074

* Fixed an issue which could cause crashes when working with custom Blackboard 2 desk layouts \[bug 46239]
* Fixed port number on Quadro M620 GPU \[bug 46243]
* The Job Manager now shows the correct scene last modified date/time \[bug 46248]
* Fixed an issue that could cause the scratchpad scene to behave slowly over time \[bug 46228]
* Fixed Sequence "Legal to Full Scale" not being applied for "Input Only" renders \[bug 46258]
* Improved support for reading JPEG 2000 encoded MXF-files. Additional tags are now recognized, and files with 4 channels as well as files with subsampled YCC data can now be read \[bug 46263]
* NVIDIA driver version 367.44 is known to cause rendering artefacts and should be replaced by the 375.66 driver available from the FilmLight support website \[bug 45659]
* Fixed crash when using 8-bit Phantom Cine file \[bug 46288]
* Fixed Audio Sync crash when syncing with single-channel audio files \[bug 46300]
* Fixed incorrect file paths exported to DLEDL from sequences on cloud media \[bug 45950]
* Fixed an issue which caused the installation script to incorrectly identify old builds on machines low in disk space \[bug 46350]
* Fixed additional tabs remaining in FLUX Manage View, and eventual application crash, after using it for many sequence replacements \[bug 44381]
* Added pre-compiled aja driver for 2.6.32-696.6.3.el6.x86\_64 kernel \[bug 44623]
* Fixed "Copy Grades" option in EDL Import not working \[bug 45217]
* Fixed "Apply LUT", "Apply LUT2" and "Apply CCC/CDL XMLs" options in EDL Import not working \[bug 46406]
* Fixed an issue where AVC LongGOP essence stored in QuickTime movie files could occasionally be decoded with frames in the wrong order \[bug 46423]
* Fixed an issue where Y'CbCr formatted DPX files would turn green when copied with FLUX Manage or fl-cp \[bug 45995]
* Fixed support for reading Scanity DPX-Y 10-bit single channel DPX files \[bug 46475]
* Fixed rendering from flycc files with non-identity transforms \[bug 36926]
* To prevent decode failures, when IPP2 colour science is selected for R3D files, decoding is not attempted on RED Rocket cards \[bug 46497]
* Fixed drawing of RGB parade in overlay mode \[bug 45974]
* Fixed "On-disk image cache size" preference being incorrectly reset to its lowest possible value after being increased beyond its highest possible value \[bug 46516]
* Fixed bl-install not correctly offering the latest installed builds from other machines \[bug 46518]
* Fixed occasional application startup failures on macOS \[bug 46520]
* Fixed ALE export for stereo scenes \[bug 46528]
