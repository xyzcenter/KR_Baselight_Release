# Baselight Release 5.3.18465 (2023-08-22)



## New Features Since Baselight 5.3.18123

* Updated AJA SDK to v16.2. This adds support for AJA IO X3 devices \[bug 60491]
* BRAW movie files can now be trimmed in Consolidate \[bug 58461]
* Added support for decoding XF-AVC Long GOP 4:2:2 10-bit (xfga) in QuickTime and MP4 files \[bug 64793]
* Dolby Metafier can now be used to validate Dolby Vision XML during export. Metafier is a command line utility bundled with Dolby Vision Professional Tools. The location of Metafier must be set in Preferences->Advanced->Dolby Vision Validation for Metafier Validation to work \[bug 64364]
* Added NVIDIA RTX 6000 Ada Lovelace as a supported GPU \[bug 65355]
* Added support for HP Z2 Mini G9 UI host \[bug 62887]
* Added support for Generation VIII Baselight TWO and Baselight X systems \[bug 65268]

## Bug Fixes Since Baselight 5.3.18123

* Fixed "Could not find OFX plugin" error during pre-render \[bug 64697]
* Fixed handling of rotated ProRes RAW media (e.g. media recorded by Atomos Ninja V) \[bug 64795]
* Fixed Tape and Clip metadata in ARRI media \[bug 64839]
* Fixed Dolby Vision HDMI Tunneling in UHD on Kona 4 \[bug 64797]
* Fixed "Unknown colour space in doAffine" failure \[bug 64698]
* Fixed crash when rapidly adjusting an OFX parameter \[bug 64908]
* Fixed an accuracy issue that occurred when rapidly rotating the Blackboard Classic jog wheel \[bug 65009]
* Blackboard Classic Wacom tablets will now reconnect without restarting the desk service \[bug 65122]
* Fixed very slow behaviour with CLF LUTs \[bug 65096]
* "Averaged Frames" metadata is now shown for ARRI media \[bug 65198]
* Fixed slow performance of multi-part OpenEXR media on some filesystems (e.g. CVFS SAN on a macOS client) \[bug 65093]
* Fixed crash in Frame.io package when downloading comments made by anonymous users \[bug 65351]
* Fixed hang when rendering or playing and caching large format images \[bug 65041]
* Fixed crash when pressing Apply, with a Tracker strip and protect paste categories \[bug 64724]

***
