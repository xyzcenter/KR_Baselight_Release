# Baselight Release 6.0.19881 (2024-03-20)

##

### New Features Since Baselight 6.0.19514

#### Sapphire for Baselight

*   FilmLight has partnered with Boris FX to create **Sapphire for Baselight**. This is the long-established Sapphire suite of OFX plug-ins, optimised for use in Baselight and now sold and supported by FilmLight.

    On Linux systems, Boris FX Sapphire is no longer supported in Baselight 6.0 or Daylight 6.0, instead you can purchase a subscription for Sapphire for Baselight directly from FilmLight.

    Sapphire for Baselight is not yet available for macOS systems; Baselight CONFORM and Daylight on macOS will continue to support Boris FX Sapphire until Sapphire for Baselight is released on macOS.

    If you have an existing Boris FX Sapphire licence, please contact your FilmLight sales representative. Bug 61703

#### SDK Updates

* Updated the Sony SMDK Toolkit to version 4.24 and Sony RAW SDK to version 5.0.0. This adds support for media from the Sony BURANO camera. Bug 64882

#### Miscellaneous

* Added an option to the parade Scope Views to hide the scope title drawn in the lower-left corner of the scope. Bug 54786
* Added simple filtering to the Presets View. Bug 65559
* Added diagnostic support for Broadcom MR9580-8i8e RAID controller. Bug 65173
* Added support for Generation VIII Baselight ONE systems. Bug 67225
* Added support for reading XAVC H encoded MXF files. Bug 67210
* Added "Ctrl" modifier support to Shape opacity desk encoder press to reset its value to 0. Bug 26767

### Bug Fixes Since Baselight 6.0.19514

* Fixed large size of cache files for BLG media. Bug 66724
* Fixed gallery thumbnail related crash on scene close. Bug 66499
* Fixed crash in Flare when using `Ctrl` and the middle track ball to pan the image. Bug 66816
* Fixed a bug that could result in slight image differences in stacks that use "Texture Blend" layer blending mode in scenes upgraded from v5.3. Bug 66796
* Stopped the Composite Paint Strokes Separately button updating the timeline during the operation. Bug 66752
* Fixed crash on first run after installation on some Mac systems. Bug 50126
* Fixed issue in Shape overlays with Face Warp where the shape outline wouldn't represent the matte accurately. Bug 66832
* Fixed colour shifts seen when using 10-bit Integer 4:2:2 Y'CbCr caching. If you are using this caching option please run `bl-reset-cache` to remove older cached frames. Bug 32705
* Fixed crash exporting Dolby Vision XML from a scene without Dolby Vision Trim strips. Bug 66949
* Fixed issues with Dolby Vision Analysis of pure-black frames. Bug 66953
* Fixed issues with Dolby Vision 2.9 Tone Detail Weight control for 100-nit target displays. Bug 66807
* Fixed issue where matte generated using face warp would end up with holes when the face is bigger than the image. Bug 66959
* Fixed issue in the Tracker strip where clicking "Return to XXX" after copy and pasting an operator containing faces would select a wrong layer. Bug 66890
* Fixed crash using Presets in stereo strips. Bug 66531
* Improved help text in Flare operator. Bug 66851
* Fixed issue where the Presets View would list all presets saved from OFX effects in the same page, and a similar issue for presets saved from Shader effects.\
  **Important: This change will remove access to previously saved OFX and Shader presets**. Bug 65999
* Fixed issue where Tracker strips would lose their categories when copy and pasting and operator containing faces. Bug 66955
* Fixed crash when bypassing an inside outside operator. Bug 67001
* QuickTime/MP4 media rendered with Legacy colour space tagging no longer includes mastering display (`mdcv`) metadata. Bug 54320
* Fixed crash using Dolby Vision Analysis of Current Frame. Bug 67015
* Fixed errors on console when reading interlaced PNG media. Bug 67018
* Fixed issue where the Area Tracker couldn't be rotated on keyframes. Bug 67007
* Fixed invalid 'scene already exists' issue when opening a gallery scene and making a copy with the `_v6` suffix. Gallery scene names now require the full `_v6` suffix, before only `v6` was required. Also changed the dialog that shows when opening an old gallery to remove any mention of 'beta'. Bug 65463
* Fixed crash removing a cursor. Bug 17548
* Fixed crash when clicking between the thumbnail and filename columns of the sequence list within FLUX Manage. Bug 66631
* Fixed crash when ctrl-dragging on a control point in Matte Curve. Bug 67058
* Fixed crash when pressing "Composite Paint Strokes Separately" and the paint operator was on the outside of a layer. Bug 67059
* Fixed behaviour of the Discard option when quitting the application with multiple unsaved scenes. Bug 67055
* Updated behaviour to respect the convention that colour channels in OpenEXR media are premultiplied by alpha. This is now respected when inserting and rendering OpenEXR media. Bug 67048
* Fixed issue where upgrading Paint operators from 5.3 scenes would lose their trackers. Bug 67021
* Fixed issue where the face tracker would stop too often with motion blur, when the tracking quality is still good. Bug 67089
* Fixed issue where the left edges of text would sometimes not correctly align in some table columns. Bug 67067
* Fixed issue where the dialog prompting to make a copy of an old gallery would continue showing after choosing not to open the scene. Bug 67065
* Fixed 'missing global blur radius' error reported when Flip / Flop is used with Sander, Median or Erode / Dilate operator. Bug 49971
* Fixed behaviour when conforming AAFs so shot marks are not missing and are applied to the correct track. Bug 66633
* Fixed issue rendering DCI Audio using the 'Sequences + Audio File' option in Render View. Bug 67154
* Fixed an issue in Chromogen where changing layer on a default Chromogen would bring up the Presets View. Bug 66822
* Fixed an issue in the Gallery when showing the Current Cursor where the Gallery would scroll to the current cursor when the cursor moves to another shot. Bug 67209
* Fixed an issue with the XFS filesystem driver which could cause the system to reboot without notice. Bug 60706
* Improved Blackboard Classic detection in bl-config-xorg. Bug 58687
* Changed the design of colour wells to be more visible. Bug 67284
* Fixed failure to insert a Matchbox Shader that specifies a custom colour space file. Bug 67161
* Fixed issue only seen on macOS Sonoma, where the edges of images incorrectly had rectangular areas of black or white pixels. Bug 67341
* Removed the CPU speed test from fl-diag as it had become increasingly less useful. Bug 67227
* Fixed issue in FLUX Manage where dragging in the sequence list or non-media file list would scroll instead of performing a drag. Bug 67350
* Fixed a crash when conforming ALEs with possibly undefined keycode gearing values. Bug 61029
* Fixed crash in Flare occurring in Timeline Sort, moving or splitting strips. Bug 67102
* Fixed a render failure that would occur when rendering out shots from a v6.0 gallery scene. Bug 67420
* Fixed crash after deleting a Stereo Colour Matching strip. Bug 67082
* A new Flexi package filmlight-flexi-effects installer is available in the support section of the FilmLight website. It fixes a VRAM allocation issue on NVIDIA Ada GPUs. Bug 67033
* Fixed depth scaling issue with faces that would negatively affect Face Perspective. Bug 67490
* Fixed defunct fl-clean-shm processes on Linux. Bug 67516
* Fixed errors setting up the vol service on macOS 14 Sonoma. Bug 67498
* Fixed hang when generating a report preview or exporting a report containing a large number of shots. Bug 67598
* Fixed hang when using some OFX operator features (e.g. Sapphire Preset Browser) when the OFX operator is beneath another OFX operator. Bug 67661
* Updated the DPM diagnostic to include temperature range checks for NVMe devices. Bug 67429
