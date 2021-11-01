# Baselight Release 4.4.7204 (2015-02-05)



## New Features Since Baselight 4.4.7170

* Updated to RED SDK v5.3. This addresses some issues in earlier SDK releases, and adds REDcolor 4 and DRAGONcolor 2 color spaces.
*   Added support for reading and writing MXF and QuickTime movies in the new Avid DNxHR codecs:

    DNxHR 444 - 12/10-bit 4:4:4 RGB DNxHR HQX - 12/10-bit 4:2:2 high quality extended DNxHR HQ - 8-bit 4:2:2 high quality DNxHR SQ - 8-bit 4:2:2 standard quality DNxHR LB - 8-bit 4:2:2 low bandwidth

    These codecs extend the existing DHxHD codecs by supporting unlimited resolution images.

    PLEASE NOTE: Avid's code requires CPUs supporting SSE 4.1. This means that DNxHR support is not available on Generation III and earlier Baselight systems.

## Bug Fixes Since Baselight 4.4.7170

* Changes to ISIS mounts now correctly update cloud media \[bug 30665]
* Fixed an issue where long QuickTime and MP4 files could take a long time to open. Particularly affected highly compressed H264 files \[bug 30654]
* Fixed reading some DNxHD MXF files which reported "Unsupported flavour of DNxHD" \[bug 30678]
* Fixed potential crash in Stereo Grade picking when stereo colour match was active in layer 0 \[bug 30712]
* The scopes "Resolution when Playing" setting is no longer reset to Medium if you have previously set it to Low or Off \[bug 26845]
* Fixed bug in conform which prevented multi-part R3D files (and sidecar RMD files) from being consolidated correctly \[bug 30737]
* Fixed bug which allowed background services to create very large log files \[bug 30613]
* fl-diag and fl-config-validate now detect and report duplicated volume names in volume.cfg \[bug 30707]
* Fixed a shape issue where the "Find Stereo Correspondence" tool was failing with an active stereo colour match in layer 0 \[bug 30713]
* Fixed problem with stereograde zero convergence point picks accumulating results from previous picks \[bug 30767]
* Fixed a crash that could occur when rendering ProRes to Quicktime files on Linux \[bug 30542]
* Fixed endless logging loop in flfsd (tcp: max = ...) \[bug 30780]
* Fix problem with communications with FilmLight Framestore display hardware \[bug 29947]
* Fixed issue in bl-config-video sending commands to FilmLight DVI2SDI & framestore hardware \[bug 29947]
* Fixed crash when resetting Button Action Slots in Chalk \[bug 30719]
* Baselight's scene load time has been improved considerably, for very large scenes \[bug 30446]
* Fixed error in rendering stereo scenes when they contained both multiple track stacks and stereo strip stacks \[bug 30787]
* Fixed Balance Exposure button moving cursor onto image when turning off \[bug 30874]
* Fixed the default DCP title to be the scene name excluding job folders \[bug 30201]
* XDCAM 422 encoded movies now write the same values to the MPEG2 aspect ratio field that Sony XDCAM devices do \[bug 30337]
* Fixed an flfsd assertion error (bad fileid) triggered by bad data \[bug 30553]
* Errors caused by writing images to an unsupported resolution now correctly fail a render \[bug 30920]
* Consolidate no longer reduces the number of frames it copies in situations where the Handles information in Shots View indicates that there are not enough frames on disk \[bug 30794]
* Fixed incorrect automatic colour space assignment for Sony MXF files \[bug 30938]
* Creation of invalid DCPs with uneven numbers of audio channels is now prevented \[bug 29033]
* The default GOP size for H264 encoded QuickTime files rendered on Linux has been reduced from 250 to 64. This improves playback of these files in QuickTime Player on Windows \[bug 29315]
* Fixed error introduced with SSD support causing dpm diagnostics to fail on early Gen I & Gen II machine equipped with 3ware 9500 or 9550 RAID controllers \[bug 30959]
* Fixed bug which caused the Baselight installer to fail due to AJA kernel module being in use \[bug 30418]
* Added support for NVIDIA 346.35 driver.
* Fixed bl-genedl tool \[bug 31013]
