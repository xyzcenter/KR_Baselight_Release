# 베이스라이트 릴리즈 노트 5.2.11644 (2019-04-02)

## 최신기능 Baselight 5.2.11581이후&#x20;

*   Added the capability to cycle through groups that contain the&#x20;

    current shot. With a keyboard, Alt + '+' and Alt + '-' will cycle

    forwards and backwards (resp.) through the groups that contain the

    shot. The same can be achieved on a Blackboard with the 'Cycle Fwd'

    and 'Cycle Back' buttons in the Group menu \[bug 50611]

### Multi Directory Conform

*   The EDL Import view has been updated to support up to 7 different

    media directories. The media conform settings (source directories,

    sub directories, filenames, and included file types) have moved

    above the conform setting list into a specific media section. For

    each media directory, a filtering dialog can be used (by pressing

    the filter button) to test location and filename patterns or file

    types and visualize the scanning result in a thumbnail view. Once

    the result is satisfactory, it can be applied to the selected media

    directory \[bug 29103]

## Bug Fixes Since Baselight 5.2.11581

* Boost Contrast missing controls mapped to Blackboard 2 \[bug 48067]
* Boost Colour works with LUT export \[bug 50523]
* Fixed error in Denoise pick that could scramble the picked region for small non-square picks with speedfx. Does not affect existing Denoise, just new picks \[bug 50511]
* Updated the Sony XAVC Encoder to version 1.1.10. This fixes a crash when multiple encoders are intialised with different format types. It also improves picture quality for XAVC Long HDR HLG \[bug 49996]
* In FCP7 XML import, reversed clips with a different framerate to the timeline and a speed change have the correct offset \[bug 49578]
* In AAF import, the ordering of Avid FrameFlex and a flip or flop on a clip has been corrected \[bug 49653]
* Fixed update of Comments field in Shots View in response to "Toggle Strip Category" \[bug 49242]
* Added the Input DRT options to the DBS apply with "Layer 0 Ops" \[bug 50134]
* Fixed issue with copy and pasting Grid Warps of different dimensions \[bug 50482]
* Fixed floating licence issues in Baselight CONFORM \[bug 48160]
* Slate diagnostic now reports firmware version \[bug 39596]
* Fix potential division by zero bug in Relight3D UI \[bug 50498]
* OFX and Shader strips are now grouped under "Plugins" on the Insert menu \[bug 50549]
* Changed the default tone curve used for decoding Canon CRM files from 'Canon Log' to 'Canon Log 3'. This avoids a decode problem when not using the automatic input colour space \[bug 50371]
* Fixed behaviour of Link Files option in Consolidate when using multi-part movie files \[bug 50565]
* Fixed crash in colour space parser when the current directory has been deleted \[bug 50520]
* Added support for OFX "OfxParamPropGroupOpen" \[bug 50574]
* Fixed vertical spacing of empty text lines \[bug 50483]
* NVMe storage diagnostics now accepts 1 controller for Generation VI Baselight ONE systems \[bug 50440]
* Fixed bug which could cause a crash when pressing the Gridwarp button "Hide Overlays on Edit" during playback \[bug 50459]
* Fixed issue with Paste where the tracker strip was being removed in replace mode even when Paste Protect Mattes was on \[bug 50570]
* Fixed an issue that could cause slow performance of temporally compressed MXFs around frame 400. This affected e.g. XAVC Long encoded files \[bug 50606]
* In CDL grade, bump amount for contrast, saturation and power can now be set \[bug 33384]
* Added fix message for users when Adaptec RAID test in fl-diag warns, "Adaptec RAID manager is running..." \[bug 46136]
* Audio stem searches now also find files without a digit at the end of the filename base stem \[bug 50653]
* Rendering with with "Analyse MaxCLL/MaxFALL" will now fail when an inappropriate Render Colour Space is chosen \[bug 50491]
* Fixed crash when exporting an ALE, caused by missing sound timecode \[bug 50581]
* Fixed failure to copy to/from cloud media volumes that are exported by systems not in cloud.cfg and/or local DNS \[bug 50622]
* OFX plugins are now correctly "unloaded" when the application is quit \[bug 50547]
* Fixed "internal error" message when accessing movie files using an account with an extremely long list of numeric supplemental group ids \[bug 47494]
* Improved speed of presenting initial file scans in FLUX Manage View \[bug 38500]
* Fixed loss of Dolby Vision Target Display information from Dolby Vision Trim strips when loading a Baselight 5.1 scene \[bug 50644]
* A scene can now be changed between "Software CMU (v2.9)" and "Hardware CMU (v2.9)" without its Dolby Vision strips being deleted \[bug 50638]
* Fixed an issue where inverting projection in Panorama could while playing could cause a crash \[bug 50458]
* Enable scene detect to run on multiple selected shots or on the currently selected shot \[bug 35112]
* Ensure "Group Grade All Keyframes" is temporarily disabled while adjusting Stereo Grade parameters \[bug 50641]
* Improved stability when using OFX plugins on macOS \[bug 50726]
* Fixed crash in the Text operator when renaming a colour space upon scene load \[bug 50752]
* Fixed crash loading galleries \[bug 50859]
* Fixed wrong source and destination selection during a copy and paste operation (with DBS and the blackboard/Slate) \[bug 50616]
* Fixed a crash that could occur when copying files by drag and drop actions on indexed volumes \[bug 50637]
* Fixed an issue that could cause both audio and video decode of temporally compressed MXFs to fail, typically with a message stating 'Bad index at position' \[bug 50920]
