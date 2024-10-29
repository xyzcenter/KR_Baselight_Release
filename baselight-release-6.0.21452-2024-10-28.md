# Baselight Release 6.0.21452 (2024-10-28)

## Important Notes&#x20;

Baselight 6.0 no longer supports FilmLightOS 6. Please contact FilmLight Support to discuss upgrading to FilmLightOS 8. Bug 60176\
\
Baselight now supports macOS 15 Sequoia; the minimum supported version is now macOS 13 Ventura. Bug 69501\
\
RED Rocket hardware is no longer supported. Bug 65725

Using a Grade Result Colour Space is deprecated and this functionality may be removed in a future release. Please watch this video for information about recommended workflows for telecine-style grading. Bug 64729

Dolby Vision external CMU devices are no longer supported. Bug 62581

The vtre application is no longer included. Bug 66448

Many colour spaces have been updated with higher precision matrices. Scenes upgraded from Baselight 5.3 will use the older colour spaces and warn about that in the console. Visual output is consistent between original and new colour spaces. Bug 67302

## 중요 참고 사항&#x20;

Baselight 6.0은 더 이상 FilmLightOS 6을 지원하지 않습니다. FilmLight 지원 팀에 연락하여 FilmLightOS 8로 업그레이드에 대해 논의하시기 바랍니다. 버그 60176

Baselight는 이제 macOS 15 <mark style="color:red;">Sequoia</mark>를 지원하며, 최소 지원 버전은 macOS 13 <mark style="color:red;">Ventura</mark>입니다. 버그 69501\
\
RED Rocket 하드웨어는 더 이상 지원되지 않습니다. 버그 65725

Grade Result Colour Space 사용은 더 이상 권장되지 않으며, 이 기능은 향후 릴리스에서 제거될 수 있습니다. 텔레시네 스타일 그레이딩에 대한 권장 워크플로에 대한 정보는 이 비디오를 참조하십시오. 버그 64729

Dolby Vision 외부 CMU 장치는 더 이상 지원되지 않습니다. 버그 62581

vtre 애플리케이션이 더 이상 포함되지 않습니다. 버그 66448

많은 컬러 스페이스가 더 높은 정밀도의 매트릭스로 업데이트되었습니다. Baselight 5.3에서 업그레이드된 장면은 이전 컬러 스페이스를 사용하며 콘솔에 경고 메시지가 표시됩니다. 시각적 출력은 원본과 새로운 컬러 스페이스 간에 일관성을 유지합니다. 버그 67302



## New Features Since Baselight 6.0.21211&#x20;



### Automated Issue Reporting&#x20;

A new 'Issue Report' feature has been added to Baselight and Daylight. It allows users to report software or system issues in an easy-to-use web interface.

Using the feature will ensure that the support team automatically receives important system and application information that could help with the resolution of the issue.

Creating a report will automatically collate system diagnostics, preferences, console logs, licenses, and information about the operating system and hardware. (Users have the option to check and remove files at any time.)

Users can also attach multiple scenes, screenshots, and other supporting files and list download locations for material on file sharing sites.

The package needs to be installed before use:

In the menu bar, select 'Views', then select 'Scripts View'.

Navigate to the Packages tab and select the 'fl-automated-issue-reporting' package and click on 'Install package'.

After installation, the 'Report Issue' menu item will be visible in the Baselight/Daylight menu.

Select 'Report Issue' to launch the web-based reporting application. Baselight/Daylight must remain open while reporting any issues.

If the system is online, once you submit the report, all information and attached data will be uploaded to our servers, and a support ticket will be created.

If the reporting system is offline, complete the web form, and create the report. The application will create a metadata file that can be emailed to FilmLight support. This will contain the basic information to create a support ticket. Upon receipt, the support system will create a ticket and will provide the location of the supporting files so they can be retrieved by the support team.

Please note, no personal or private data is collected at any time.

### Layer Matte Improvements&#x20;

Up to 4 matte inputs/channels can now be accessed/configured directly from the "Matte Operators" grid and desk's Stack Manager section.

On the grid, there are now left and right arrow buttons on either side of the "Matte Operators" heading. Each grid column (except for the last, which is reserved for adding new matte inputs) is labelled with the matte input/channel number it represents. When there are more than 2 matte inputs, the arrow buttons can be used to "scroll" the 2 columns through the layer's matte channels.

On a desk, holding the Stack Manager's matte merge key will cause the layer up/down keys to flash. They can then be used to "scroll" the desk's 2 rows (1 on a Slate) of matte keys through the layer's matte channels. Bug 67417

Unused matte operators can now be removed from the "Matte Operators" grid by right clicking on an operator in the grid and selecting the "Remove XXX Operator From Grid" menu option. Operators can be added back to the grid from its Customise menu.

Specific OFX Filter and Flexi Effect matte operators can now be saved as default options in the grid. This allows them to be inserted directly into a layer's matte without first invoking the effect picker dialog. To do this, first select the generic (OFX Filter or Flexi Effect) operator and use the picker to insert the specific operator required. That operator will then appear in the grid above the generic type. It can then be saved to the grid as a default option from the Customise menu's "Add Matte Operator To Grid" submenu.

Which matte (filter) operators are available from the desk keys can now be customised. This is done using the "Configure Desk Matte Operators" dialog, available from the Matte Operator grid's Customise menu.

This dialog has dropdowns representing the first 2 matte (filter operator) desk keys, which can be used to select the operator assigned to those keys.

If the operator selected is one of the 2 generic types (OFX Filter or Flexi Effect), the key can be further configured to recall a specific operator type (avoiding having to first invoke the effect picker dialog). To do this, first insert the desired, specific operator type via the picker dialog. Then, press and hold the desk key (which should now show the type of the operator inserted). Alternatively, return to the "Configure Desk Matte Operators" dialog and use the "Default OFX Filter" or "Default Flexi Effect" dropdown.

The default for the key can be returned to the generic type by pressing and holding the desk key again (or from the dialog).

Once a specific Flexi/OFX operator type has been assigned to a desk key, the picker can still be used to select a different type by holding the "Ctrl" modifier while pressing the key.

### Scope Enhancements&#x20;

Zoned Vectorscope/Chromaticity is a new scope view which shows three plots split based on luminance zones.

Clicking on the image shows a yellow cross only on the appropriate plot.

The zone thresholds can be set for each plot type from the right-click menu. For the CbCr vectorscope the default zone thresholds are at Y'=0.25 and Y'=0.75; for the chromaticity scopes the default zone thresholds are at -2 and +2 stops relative to 18% grey. Bug 65176

Chromaticity plots can now be rotated in the same way as the CbCr vectorscope. Bug 68050

The adjustment sliders in the Scope View right-click menus now have reset buttons. Bug 68846

### Miscellaneous&#x20;

DNxHR codecs in MXF and QuickTime deliverables now support RGBA/YCCA channels, for including opacity (alpha) data in renders. Bug 68400

IMF and Broadcast Contribution Profile JPEG 2000 can now be rendered using custom bitrates, as well as constant bitrate (CBR). Bug 68286

Invalid settings for IMF and Broadcast Contribution Profile JPEG 2000 deliverables now show a warning in Render View and during render verification. Bug 55911

Added a new (icon) button that simplifies configuring a layer to grade the raw image on top of the layer(s) above. This is typically combined with a matte to specify the area of the raw image to reveal/grade. A layer configured this way provides similar functionality to "layer mixer" mode in other systems.

If the Ctrl (Cmd on a Mac) modifier is held when the mode is activated, an explicit "Blend Source" reference (to the raw image) is added above the layer. This allows more complex grades to be applied to the raw image by inserting additional grade layers directly below the Blend Source.

The button is located in a layer's "Result Blending" section, to the right of the blend type dropdown. Bug 68771

Added 65x65x65 option for LUT generation. Bug 63113

MXF and QuickTime raw metadata now includes additional information about DNx codecs. Bug 68764

Added support for reading "User Comment" metadata in JPEG files. Bug 69156

Added "With Filename If No Tape Name" to Overwrite Tape Name conform option, to support updating the tape name only when it is empty. Bug 63867

Additional metadata is now read from PNG media. PNG files whose metadata identifies them as sRGB are now assigned an sRGB colour space by default. Bug 69254

Colour spaces in opened scenes that are different from any colour spaces known to the application are no longer written out to .flspace files in /vol/.support/etc/colourspaces because that is rarely useful and causes clutter in colour space menus. Instead these spaces are indicated with a scene icon in menus, and are available for use in other open scenes until you quit the application. Bug 68763

The R3D Params operator now supports Extended Highlights for RED media from cameras which support Extended Highlights (e.g. V-RAPTOR \[X]). Decoding with Extended Highlights requires a lot of GPU memory so may fail on systems with smaller GPUs. Bug 69169

Added support for reading HDE-compressed ARRIRAW MXF files from older (pre-ALEXA 35) cameras. Bug 69213

Updated the conform behaviour of transforms in an AAF so that it sets the interpolation mode read from the AAF. Bug 61149

When running in REMOTE mode, the IP address of the machine hosting the Blackboard Classic, Slate or Tangent control panels can now be determined automatically for systems using NICE DCV or HP Anyware/PCoIP.

REMOTE mode can be enabled by setting "Auto-detect REMOTE Mode" in the "REMOTE" section of the "System" page in Baselight Preferences.

Tangent Element and Wave panels are also supported when running Baselight via remote desktop.

The IP address of the machine hosting the Tangent control panels can either be specified via the "Remote USB server IP Address" setting in Preferences, or determined automatically when using NICE DCV or HP Anyware/PCoIP if REMOTE mode is enabled. Bug 69648

Added support to copy and paste AAF/XML Shot ID Metadata. When replacing media in a scene conformed from an AAF or XML, the metadata allowing Baselight to associate a shot with its equivalent event in the AAF/XML file could be lost. The Edit menu items "Copy AAF/XML Shot ID Metadata" and "Paste AAF/XML Shot ID Metadata" allows the metadata to be copied from the selected strip to the replacement strip, this allows media to be replaced in the scene and still maintain the Modify AAF/XML workflow.

The new 'Has AAF/XML Shot ID Metadata' column in Shots View can be used to check if a shot contains metadata. Bug 63830

Added 'get\_channels' to the FLAPI 'SequenceDescriptor' class. When called on OpenEXR media, it will return an array of all channel names. Bug 69723

Added 'update\_matte\_references' to the FLAPI 'Shot' class. This method updates matte channel names in any Reference operators within the Shot. Bug 69735

## Bug Fixes Since Baselight 6.0.21211&#x20;

Boost Contrast with large Scale is faster. Bug 62973

Improved GPU JPEG 2000 accelerated compression speed for high resolution deliverables. This also fixes an issue where acceleration was not used when rendering image sequences to remote volumes. Bug 67783

Fixed channel naming when rendering to single-channel OpenEXR deliverables. Bug 68364

The fl-diag hostname test is now compatible with the zoneless-hostnames option in cloud.cfg. Bug 68657

The fl-diag cloud test now accepts the 'nara' flag for ws hosts in cloud.cfg. Bug 68862

fl-fsr no longer ignores sequences which have extended attributes. Bug 68698

Fixed crash in Presets View when the current strip is shorter than other strips in the stack. Bug 68659

Jobs can no longer be created with, or renamed to, an empty name. Bug 68776

Fixed crash rendering XAVC or XDCAM codecs in Sony MXF. Bug 23576

Fixed issues with metadata in Cuts View, for example the Text operator. Bug 68966

Fixed crash exporting LUTs in some situations. Bug 68723

Improved the performance of Gallery and Shots View when nothing relevant has changed. Bug 68498

Fixed various Image Viewer/Clean Output related bugs in Stereo and Dual Output display layouts. Bug 67929

Fixed various Image Viewer/Clean Output related bugs in Dual Colour Space display layouts. Bug 67877

In bl-config-xorg with the -v option it now prints out the command line used to determine which control surface is connected. Bug 69091

Fixed Image Viewer updating of custom mouse pointer and showing/hiding of previous strokes when setting a clone brush offset in Paint. Bug 67932

Fixed behaviour of %{SceneNameOnly} token in Render View and Reports View with scenes nested in more than one folder. Bug 69130

Fixed issue where if overlays were disabled in the Transform operator UI, they would still appear/flash on the image when the operator was deselected. Bug 69131

Fixed crash if a Matchbox/ShaderToy GLSL file cannot be opened. Bug 69100

Fixed crash when a ProRes RAW Params operator is selected when quitting the application. Bug 66276

Edge Crop now shows more precision for "Current Aspect Ratio". Bug 69188

The icon used for Client Sessions has been updated. Bug 69284

Added 8k formats to bl-benchmark. Bug 59634

Improved error messages when a licence cannot be obtained. Bug 69334

Suppressed warnings about storage fragmentation when accessing solid-state media. Bug 69322

Fixed unnecessary re-caching of cached strips caused by changes below them in the grading stack. Bug 69381

Fixed crash on starting Matte Tool if the default config was damaged. Bug 69455

Fixed layer matte viewing modes when used in conjunction with explicit strip caching (the cache wasn't being used). Bug 69416

Fixed Kona 5 firmware switching on macOS. Bug 69485

Fixed issue where GPU JPEG 2000 acceleration could incorrectly be shown as unlicensed in the About dialog. Bug 69422

Fixed issue with renders using GPU JPEG 2000 acceleration at resolutions higher than UHD. Bug 68914

Fixed issue reading QuickTime movies containing unused fragments. Bug 69570

Console warnings about "Fma" from the ARRI Image SDK are no longer seen. Bug 69019

Fixed issue where drawing the face overlays on very long shots would take a long time. Bug 69523

Fixed issues with BLGs exported from Dolby Vision scenes. Bug 59952

Fixed "Too many connection values" error when loading some scenes saved in older versions. Bug 68517

Fixed crash on macOS when Display View has a very large zoom-in. Bug 67806

Prevented the cache state of input strips from being copied to the destination. Bug 69488

Fixed issue where the render service (on FLUX Store and Baselight RENDER system) would not relaunch itself after an error. Bug 60823

Fixed Pane Description getting stuck in the 'Scratchpad Original Version'. Bug 69266

Fixed incorrect behaviour in Shader operators when using the "Output Alpha: From Shader" option. Bug 69662

Fixed crash when a corrupt TIFF file is encountered. Bug 57949

Fixed error crosses in the Image Viewer having a random colour unless the Setup's Error Cross Colour was changed. Bug 69797

Fixed slight green shift on some thumbnails, notably Apple ProRes 4444. Bug 68589

Fixed Colour Crosstalk operator not being included in LUT Export. Bug 69214

Fixed an issue where shots before or after the DBS in the Gallery could no longer be selected by holding the 'Select' button and a directional arrow on a Blackboard or Slate. Bug 69415

## Known Issues&#x20;

Internal Image Viewer on MacOS is now tagged as sRGB Display. To get accurate colour reproduction on MacOS, the cursor colour space must be set to sRGB Display: 2.2 Gamma / Rec.709 in all cases. Previously, the viewing colour space needed to match the physical calibration of the attached monitor. Bug 69661

Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237

Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

Open System Preferences from the Dock or the Apple menu Choose "Security & Privacy" Click the padlock icon and use your password or Touch ID to allow changes to be made Select "Full Disk Access" in the list on the left Click the + button on the right to open a file browser On your keyboard, press / to open the "Go to the folder" dialog Enter /sbin and click Go Select the file called nfsd and click Open After restarting your Mac, the volume(s) should now work correctly. Bug 62601

The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798

Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406

Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016

Using "Network Stream" as the Primary Video Output on Intel Mac Pro systems with AMD GPUs is currently unsupported. This will be addressed in a future release of Baselight 6.0. Bug 68727
