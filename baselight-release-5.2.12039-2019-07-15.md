# 베이스라이트 릴리즈 노트 5.2.12039 (2019-07-15)

## 최신 기능 Baselight 5.2.11913이후&#x20;

### Layer View 레이어

*   Along with a new look, Layer View can now follow both the current cursor and the DBS cursor.

    Layers can be easily drag and dropped between the current cursor and DBS cursor.

    Added the ability to change between viewing the current cursor, DBS cursor, or both cursors.

    Renamed 'Show Matte' to 'Large Matte' to better reflect its function.

    Resizing the view has been made consistent to keep text readable.

    Multiple layers can now be selected within a layer stack using Control and/ or Shift keys; allowing for multiple layers to be drag and dropped.

    A temporary floating Layer View from Cuts View now moves correctly when moving the DBS and layers can be properly selected using a Blackboard or Slate.

    Layer View titles for cursor stacks now better reflect what is selected.

    When dragging layers, the provided information for what is being dragged and what will occur when you drop the layers at the current destination has been made more accurate.

    Layers can now be selected in Gallery shots via the layer View, allowing multiple layer drag and drop from the Gallery \[bug 49421]
* Added a button in Layer View when showing both Current and DBS cursor stacks to swap their positions \[bug 50891]
* Layer names are now shown for easier location of layers and there is an option within Layer View to hide layer names \[bug 50906]

### Dolby Vision 돌비비

* Added option to perform Dolby Vision analysis at the poster frames of all selected strips, to enable a draft preview render to be produced quickly \[bug 49863]
* Target displays that are as bright or brighter than the mastering display do not use Software CMU, so their colour spaces are no longer offered in Cursor View or Render View \[bug 51515]

### Miscellaneous 기타기

* Changed Master, Red, Green, Blue, Luma (Y) Curve Grade axis labeling from 10 bit values to normalised 0->1 values \[bug 50696]
* Added a toggle button to the selection menu for obeying playback filtering; enabling strip and stack selection to obey the current playback filter \[bug 50579]
* Added a diagnostic test for the SDI card temperature to the Video submenu \[bug 50205]
* Avid MXF "Disk Label" metadata is now shown \[bug 51538]
* The installer on Linux now uses more efficient 'xz' compression \[bug 51540]
* Mastering Colour Space information is now stored in QuickTime movies (in the new mdcv atom), and this metadata is also read from such movies \[bug 51652]
* MaxCLL/MaxFALL analysis is now stored in QuickTime movies (in the new clli atom), and this metadata is also read from such movies. A new option on Render View allows this data to only be stored in the movies without also writing a sidecar XML file \[bug 51652]
* When rendering to OpenEXR using a display-referred colour space, the colourimetry of the space is now stored in the file \[bug 51659]
* The "Colour Space Tagging" menu on Render View, which is shown when rendering to QuickTime movies, now shows the tags that will be written to the output files \[bug 51671]
* Added FLUX Manage filter tiles "Has image channel", "Has image track", "Image channels" and "Image tracks" to assist filtering of multi-channel OpenEXR files \[bug 51447]
* Mastering Colour Space information is now read from metadata in MXF movies \[bug 51566]
* Added Histogram waveform to Base Grade. Right-click on the waveform to switch between the two waveforms. Base Grade will retain the last used waveform settings on restart \[bug 37225]
* Updated to RED SDK 7.0.8. This contains fixes as follows: **레드 SDK 7.0.8이 업데이트되었습니다. 다음과 같이 개선이 포함됩니다.**
  *   REDWideGamutRGB output incorrectly had gamut mapping applied

      in IPP2; this fix may cause very saturated colours to change
  * HLG rendering artifacts
  * memory leak
  * missing audio for incomplete DSMC clips \[bug 51660]
* Improved the ability for an OFX plugin to request a large amount of GPU memory \[bug 50245]
* Added support for reading audio from OpAtom MXF-files. This adds support for audio MXF-files written by Avid \[bug 51380]
*   Added support for rendering Dolby Vision Mezzanine MXF files. This file type contains JPEG 2000 compressed image data and frame wrapped Dolby Vision XML. The available JPEG 2000 profiles are "IMF Profile", "IMF Profile YCC 422", "Broadcast Contribution Profile" and "Broadcast Contribution Profile YCC 422" with the same encoding options as for the IMF MXF filetype, except for bit depth which is locked to 12-bit.

    The "Dolby Vision Mezzanine MXF" filetype only appears if a Dolby Vision mastering display has been set into the scene settings. The available colour spaces are restricted to the relevant Dolby mastering spaces.

    The ASDCP library has been updated from version 2.7.19 to version 2.10.32. This fixes partition version and index rate metadata issues in AS-02 MXF-files, as used with the "IMF MXF" filetype.

    Mastering Colour Space information is now stored in Dolby Vision Mezzanine and IMF MXF movies using SMPTE mastering display labels \[bug 48053]
*   Added support for creating Dolby Vision ISXD MXF files. This file type is an IMF compliant metadata only track based on SMPTE RDD 47. The "Dolby Vision ISXD MXF" filetype only appears if a Dolby Vision mastering display has been set into the scene settings.

    Dolby Vision ISXD MXF does not contain image data, but images are still rendered to perform MaxCLL/MaxFALL analysis. Available colour spaces are restricted to the relevant Dolby mastering spaces \[bug 51417]
* fl-diag will now suggest an upgrade of the nvidia driver on compatible systems; doing this will enable Blackmagic RAW and ProRes RAW support \[bug 51336]
* Added support for 3x1 tiled output for DVI/HDMI/DisplayPort video output configurations \[bug 51480]
* Improved Zoom/Pan behaviour. It is now possible to zoom in close to a particular subject in the image in bird's eye mode. This frees the need to pan the image to readjust its centre \[bug 51108]

## Bug Fixes Since Baselight 5.2.11913

* Fixed bug in Curve Grade's Saturation vs Lightness curve which prevented setting saturation values greater than 1 \[bug 45428]
* Changed Curve Grade axis labeling from 10 bit values to normalised 0->1 values \[bug 50696]
* Ensured that clips with variable retimes from AAFs have appropriate static retimes in the case that variable retimes are not applied \[bug 51275]
* Fixed an issue reading MXF-files with index partitions written before the corresponding essence partitions \[bug 51084]
* Fixed an issue where double-frame timecode in MXF-files was incorrectly calculated if the timecode edit rate was different to the frame rate \[bug 51374]
* Reduced amount of RAM required when opening very large scenes \[bug 51353]
* Improved scene load times when using extremely large job databases \[bug 51576]
* Improved job export times when using extremely large job databases \[bug 51590]
* Relaxed out of memory threshold to prevent out of memory killer thread from killing Baselight prematurely \[bug 51278]
* Fixed a rare remote grading notification has mismatch error \[bug 51094]
* Removed some legacy settings from the Decode Parameters Tab within Media Import Rules View \[bug 51239]
* Fixed incorrect labels being shown for the R3D Params "Highlight Roll Off" control. The image is not affected by this change, just the on-screen labels \[bug 51445]
* Fixed an issue that caused renders to 8-bit IMF MXF to produce broken images \[bug 51456]
* Fixed Transform Alarm Overlay to work with transform strips that have "Flip" or "Flop" enabled \[bug 48397]
* Network card config diagnostic now warns if no link speed has been found \[bug 50985]
* Fixed crash closing application when licence has expired \[bug 51212]
* Fixed crash when using Playback Filtering when the cursor is beyond the end of the timeline \[bug 51612]
* Fixed crash in Text operator when editing text field during playback \[bug 51224]
* Improved speed of updating Shots View highlights \[bug 51550]
* Increased RAM requirements in diagnostics when running on Gen VII hardware \[bug 51343]
* Fixed colour space identification of ARRI QuickTime files as LogC \[bug 51575]
* Fixed crash when applying Media Import Rules \[bug 51643]
* Fixed crash when inserting many Text operators \[bug 51308]
* Improved speed of Media Import Rules View response to selection changes \[bug 51648]
* Fixed crash when inserting a Text operator into a scene with certain working colour spaces \[bug 51635]
* Fixed crash upon importing certain AAFs \[bug 51627]
* Fixed issue where drag & drop was possible into Gallery \[bug 51613]
* Fixed issue where temporary Layer Views could be open during playback with Lock Scroll to Cursor Position enabled \[bug 51065]
* Fixed issue where thumbnails within Layer View were being rebuilt unnecessarily \[bug 50888]
* Fixed crash when replacing layers through Layer View that are below the render line. It is now impossible to paste below the render line through Layer View drag and drop \[bug 50817]
* Fixed crash when opening a temporary Layer View for a shot and navigating using the Blackboard or Slate \[bug 28126]
* The Cursor View clip alarm now uses more accurate thresholds for alarms based on the viewing colour space \[bug 51357]
* Improved test for running applications when starting Baselight or Daylight on Linux \[bug 51440]
* Fixed rare crash when changing workspaces \[bug 50188]
* Characters '&', '<' and '>' now display correctly when used in a Text operator \[bug 51592]
* Fixed reporting of disk activity information shown in fl-systemmonitor and System Monitor View \[bug 51636]
* Fixed issue where Graticule would round a manually entered entry to a wrong value \[bug 51561]
* Fixed "OfxImageClipPropConnected" property when an OFX plugin has optional inputs \[bug 51410]
* Fixed failures and crashes when working with old scenes that use the legacy "Log", "Linear", "Video" and/or "Video (Full Range)" colour spaces \[bug 51599]
* Fixed crash in Reference when using tracks/channels, e.g. from an EXR Sequence added in an older build \[bug 51615]
* Fixed crash when opening Layer View with no available width \[bug 51688]
* Fixed various issues in Dolby Vision XML output, including animated trim under a Dissolve \[bug 51476]
* Fixed incorrect Dolby Vision analysis when the analysed stack is not at the bottom of the timeline \[bug 51582]
* Fixed incorrect timecode rate reported for some media (e.g. 50fps timecode reported as 50@25fps) \[bug 51370]
* 1x1 Stereo Difference Layout now uses a grey level equivalent to 0.5 linear in the viewing colour space, to improve usage on PQ displays \[bug 51654]
* Fixed Shots View columns incorrectly becoming read only \[bug 51666]
* Fixed crash when clicking "Current" conform tab after cancel conform \[bug 51307]
* Fixed an issue where rendering very short QuickTime movies with AAC-encoded audio could crash \[bug 51649]
* Fixed identification of OpenEXR channels in sequences that have handles without the full set of channels \[bug 51031]
* Fixed bug when moving keyframes of shapes with custom inner/outer curves enabled \[bug 51697]
* Fixed crash when switching between scenes with different containers, prior to FLUX Manage View being opened \[bug 51333]
* Fixed problem when applying a filter for a Media Import Rule that caused Shots View to display incorrectly \[bug 51715]
* Fixed inability to stop playback using mouse or keyboard when Big Metadata View is in use \[bug 42433]
* Timecode is now set correctly when rendering IMF MXF movies. The timecode rate must match the frame rate of the file or the timecode will be ignored \[bug 48053]
* Added support for Wacom Intuos Pro M tablet \[bug 44170] **와콤 인튜어스 프로 M 타블렛 지원 추가**
* Fixed the QuickTime colour space tag written when rendering to sRGB \[bug 51682]
* Fixed hang when interacting with some OFX plugins \[bug 51589]
* Images in PDF Reports are now JPEG compressed, resulting in far smaller file sizes for reports containing images and thumbnails \[bug 51653] **PDF리포트의 이미지가 압축된 JPEG가 가능하게 되어 리포트에 포함되는 썸네일이미지가 작게되었습니다.**
* Fixed crash when doing a multipaste from an edl \[bug51482]
* Fixed an issue in the index service that caused it to consume memory \[bug 51692] **인덱스 서비스에서 소모되는 메모리관련 이슈 해결**
* Fixed misreporting of 8GB DIMMs in fl-diag "Installed RAM" test \[bug 51925]
* Fixed an issue that could cause some sequences to appear missing in FLUX Manage \[bug 51932]
