# Baselight Release 4.4m1.7567 (2015-07-29)



## New Features Since Baselight 4.4m1.7448

* A new "Manage Colour Spaces" dialog can be opened from the Baselight menu or from the Formats editor (in Baselight or in bl-formats). This allows colour spaces to be set as hidden, which will hide them from all colour space menus unless Shift is pressed. The list of hidden colour spaces is stored in the global preference database \[bug 32641]
* Pixel aspect ratio values are now written into DPX files correctly \[bug 32841]
* Pixel aspect ratio values stored in many media types now shown in the Sequence Browser and are used to help select formats \[bug 32841]
* Added support for multiple monitors on Baselight ONE systems \[bug 32185]
*   bl-config-xorg has been changed to support systems without Blackboard control surfaces. bl-config-xorg will now ask whether you have a Blackbaord ONE or TWO attached to your system.

    This frees the second DVI/DisplayPort connector on Baselight ONE systems for use with UI monitors.

    On Gen 5 and Gen 6 Baselight ONE systems, bl-config-xorg will also ask which connector on the UI GPU that the Blackboard is attached to, allowing you to attach UI monitor(s) via the DisplayPort connector rather than the DVI connector \[bug 30627]
* Increased maximum zoom range of retime operator's time vs time graph \[bug 32815]
* Added Export ccc file option to the CDL operator \[bug 29757]
* Improvements to BLG Export of BLGs compatible with v4.4:
  *   In the BLG Export panel, changed "Version Compatibility Warning"

      to "Version Compatibility" with explicit choices of "v4.4" and

      "v4.4m1"
  *   Exporting a BLG with "Version Compatibility" set to "v4.4" will

      replace all the CDL grade operators with VideoGrade operators

      with the same CDL compatible values set \[bug 31861]
  *   ColourSpace operators can now be included in BLGs exported with

      a "Version Compatibility" setting of "v4.4" \[bug 33014]
* In preparation for the upcoming beta tests of Baselight for Avid v4.4m1 and Baselight for Nuke v4.4m1, added a "Version Compatibility" option to the "Update Avid AAF with Baselight Grades" EDL Export panel. By default, this is set to "v4.4", to produce AAF files compatibile with the released versions of the plugins. When beta- testing v4.4m1 versions of the plugins, use the "v4.4m1" option. \[bug 33014]
* Added new preference "Prevent Transitions from being grabbed to gallery". This will prevent any incoming or outgoing transition from being picked up when shots are batch copied to a gallery. The default is set to off \[bug 32296]
* Added option to create hard links to unchanged input files when rendering \[bug 32947]
* Added support for extended sensitivity (ISOBase) metadata in Panasonic VRAW files \[bug 33163]

## Bug Fixes Since Baselight 4.4m1.7448

* Fixed potential dropped frames if a mark was added during playback \[bug 32586]
* Fixed order of Gain and Gamma in Dolby Vision XML export \[bug 32793]
* Fixed problems with using bl-conform and and --ApplyASCCDL option \[bug 32446]
* Fixed recognition of XDCAM HD MXF files written by MOG \[bug 32757]
* CDL grade now adds Metadata values to the shot \[bug 32795]
* Sony XDCAM HD MXF output now permits 24p output \[bug 32798]
* Fixed timecode read from R3D media when the first frame is the second frame of a doubled timecode pair \[bug 32806]
* Fixed Replace with protect mattes paste mode moving paste protected layers \[bug 32615]
* Denoise gives message when pick sets values and error messages when pick cannot set values \[bug 32750]
* Fixed delta being left open when cutting up a strip \[bug 32834]
* The Sequence Browser no longer offers formats for movies where a proxy resolution of the format matches the movie's dimensions (e.g. a 4K format will not be offered for a 2K movie) \[bug 32836]
* Fixed crash pasting non-ASCII characters into a text field on Mac \[bug 32889]
* Added diagnostic preference to disable Adaptec RAID configuration check \[bug 32860]
* The nightly crash report flushing process no longer generates mail to root each night when there is no error \[bug 29501]
* Handle degraded-rbld status in 3ware raid diagnostic \[bug 32931]
* Fix 'Source Relative' conform issues for sequences with timecode \[bug 32631]
* Fixed failed to multipaste BLGs exported from FLIP \[bug 32951]
* fl-cp no longer copies movies into resolution directories; its behaviour now matches flux \[bug 32985]
* bl-power will now accept short-form node names when performing actions on the nodes of a Baselight FOUR/EIGHT \[bug 31358]
* "Update Avid AAF with Baselight Grades" now warns if one of the grades generated will not load into a v4.4 version of Baselight for Avid.
* Multi-paste no longer offers to change the container of every scene it opens \[bug 32817]
* Fixed crash caused by a Truelight strip with an incomplete Truelight command \[bug 32903]
* Fixed LUT export to match grades when the scene's Grade Result Colour Space is not set to 'From Stack' \[bug 32999]
* Added an option to LUT export to allow the Input Colour Space conversion for a sequence to be replaced with the LUT \[bug 33149]
* Fixed LUT export failure caused by the input strip having Orientation set to Flip or Flop \[bug 33277]
* Allow 1.5G SDI to be selected for SDI output at UltraHD and 4K resolutions \[bug 30200]
* Fixed behaviour of Colour Space operator when it is used in a layer \[bug 33067]
* Fixed initialisation of Sequence Interlacing Treatment when inserting interlaced media \[bug 33071]
* Fixed incorrect brightness of UI elements when using an HDR display device \[bug 33105]
* Fixed Sequence Browser colour management when selected colour space is "Default" \[bug 32902]
* Fixed problem with fl-cp caused by using the wrong effective identity which could cause failures on NFS drives \[bug 33131]
* Fixed "View" appling the sRGB option to the main display if it was turned on in the cut view. Removed sRGB being disabled when the viewing and working colour space matched. Fixed gallery notes not being added correctly \[bug 25416, 33073, 26786]
* Fixed Conforming a CDL not naming CDL layer correctly \[bug 33126]
* EDL conform now warning if a film grade can't be created when conforming a EDL with CDL values \[bug 32455]
* Fixed bug which prevented 12 bit DPX files produced by the Codex Vault from being recognised \[bug 33186]
* Fixed playback of UHD material on Gen VI machines. Playback could enter a slow state caused by the Nvidia driver incorrectly deciding that buffers used to transfer from CPU -> GPU were used for GPU -> CPU transfers. This issue affected cached and non-cached playback \[bug 33257]
* Fixed a decode failure affecting the last frames of MXF files with start offsets \[bug 32863]
* Improved accuracy of fl-diag disk controller performance test for faster RAID HBAs \[bug 18612]
* Fixed an issue which prevented some OpAtom MXF files from being read, giving an 'Unsupported MXF' message \[bug 33289]
* Fixed command line conform with a CDL grade \[bug 32446]
* Audio Timecode written to Avid OP-Atom MXF movies now correctly uses the Audio TC from Shots View \[bug 33319]
* Fixed tl-utils TcsToCtf to handle gammas beneath 1.0 correctly for Autodesk .ctf files \[bug 33297]
* Fixed failure to conform material whose resolution matches the proxy resolution of a known format, but not the high resolution of any known format \[bug 33301]
* Improved error handling when rendering SStP codec to a Sony MXF container fails with an exception \[bug 33326]
