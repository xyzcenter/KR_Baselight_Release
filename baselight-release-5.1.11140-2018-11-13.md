# 베이스라이트 릴리즈 노트 5.1.11140 (2018-11-13)



## New Features Since Baselight 5.1.11047

### Miscellaneous

* New "Export SDL Data" option in EDL Export to write StereoGrade parameters as SDL metadata in CMX 3600 files \[bug 26152]
*   Added "LUTN.Filename", "LUTN.Path" and "LUTN.RelPath" variables to Shots view, where N is an index representing the Truelight operator found within the shot.

    The index N will be 0 for the Truelight operator in the Input layer. The index N will be 1 or above for each Truelight operator found in the grading stack below the Input layer.

    LUTN.Filename will give the base filename of the LUT.

    LUTN.RelPath will give the path to the LUT relative to the scene's current container directory.

    LUTN.Path will give the full path to the LUT \[bug 49344]
* Added support for Quadro P4000, P5000 and P6000 display GPUs \[bug 49495]

## Bug Fixes Since Baselight 5.1.11047

* Fixed bl-config-xorg tablet mapping for Blackboard ONE \[bug 48888]
* Fixed incorrect colours in Phantom Cine files which do not have a recorded colour temperature \[bug 49236]
* Fixed an issue where the coding equations tag could be omitted from MXF metadata when rendering XAVC codecs. This affected renders which produced the warning 'Unable to move index to header' \[bug 49297]
* Fixed connection failure when rendering with remote server with a user id that does not exist on the server \[bug 49309]
* Fixed rare crash on database access \[bug 49169]
* The application will now report an error rather than crash on certain corrupt scenes \[bug 49377]
* Full-sensor resolutions are no longer offered as Input Formats for Sony RAW media, because the Sony RAW SDK cannot decode at these resolutions \[bug 49241]
* Fixed issues when using a Baselight TRANSFER licence \[bug 49251]
* Scenes using a cube-based DRT or Dolby Vision Software CMU no longer invalidate the timeline cache on every new build \[bug 49187]
* Fixed memory leak when repeatedly opening/closing scenes \[bug 49367]
* Fixed issue where changing the timecode setting for Audio Metadata in the Render panel would not change the timecode embedded in rendered audio files \[bug 49393]
* Fixed issue where a separate audio file associated with a shot would repeat at the end of the shot if the audio file was shorter than the movie or image sequence \[bug 49404]
* Fixed crash reading HDE-compressed ARRIRAW media on multi-GPU systems \[bug 49405]
* Fixed issue conforming from R3D files that could cause the conform percentage to drop and alternative options to be offered for some events \[bug 49408]
* Fixed Render View "Prefer Source Codec" button becoming disabled after selecting it \[bug 49416]
* Fixed crash when an invalid Dolby Vision licence file is installed \[bug 49391]
* Fixed issue with the cut view displaying the wrong thumbnails when a reverse sort order was selected in the shot view \[bug 46383]
* Fixed file descriptor leak if a port scanner is run on a Baselight system \[bug 49432]
* Fixed incorrect colours in some FLUX Manage thumbnails \[bug 49236]
* Fixed Stereo Dual Output display option \[bug 49485]
* Fixed Shader operator failing in Baselight CONFORM. Unfortunately, Shader operators added in Baselight 5.1.11047 will remain broken and will need to be re-inserted in the newer build \[bug 49517]
