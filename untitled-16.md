# Baselight Release 4.3.5314 (2012-04-13)



## New Features Since Baselight 4.3.5245

* Added support for reading and writing MXF files encoded using DNx444 (4:4:4 DNxHD).
* Added gain control to right-click context menu on scope views.
* The Sony F65 Decode "Exposure Index" control is now a slider rather than a popup menu with fixed values.
* Cursor View can now be floated.
* SMPTE timecode stored in Phantom cine files is now read by Baselight.
* Fixed DNxHD on Mac OS X 10.5.
* Added fl-diag test to verify permissions on /dev/shm.

## Bug Fixes Since Baselight 4.3.5245

* Video grade now saves the currently selected page as the default for new grades when the (customize) menu option 'Save Config To User Preferences' is selected \[bug 20329]
* Fixed potential crash when adjusting shape feathering with very small values while grouped grading & switching scenes \[bug 20356]
* The list of Truelight profiles and LUTs in the Render View is now updated when 'Reload' is selected in Cursor View and when a scene using a file from a non-standard directory is selected \[bug 20357]
* Reinstated option to render to 64bit RIFF64 WAV files (required for long multi-channel audio files) \[bug 20367]
* Fix for AAF conform timing with speed events \[bug 18187]
* Fixed bug which could cause crash when tracking with 290 series nvidia drivers \[bug 20280]
* Reinstated option to render to 64bit RIFF64 WAV files (required for long multi-channel audio files) \[bug 20367]
* Fixed bug which could cause a scene containing a sequence with 'OFX' in the filename to crash Baselight (only on systems with a Blackboard connected) \[bug 20363]
* Fixed reading large MXF files on Mac \[bug 20432]
* Fixed incorrect cache resize warnings when background caching a scene containing explicitly cached strips \[bug 20450]
* Fixed issue with AAF reading crashing \[bug 19953]
* Removed StereoGrade from the inside/outside layer0 list \[bug 20494]
* Fixed double speed playback \[bug 20251]
* Fixed performance drop after extended periods of grading \[bug 20461]
* Fixed rendering of video luts & intermediate caching \[bug 20502]
* Fixed crashes reading JPEG2000-encoded DPX files \[bug 20254]
* Fixed thumbnail caching of RAW files \[bug 20511]
* Fixed slow conform, by making it optional to scan for movie files with missing or no extension (i.e. filenames not ending in .mov, .mxf etc). To enable scanning for these files, turn on the preference (under Timeline->Conform) \[bug 20462]
