# Baselight Release 4.4.7079 (2014-11-11)



## New Features Since Baselight 4.4.6964

### Consolidate

*   Consolidate View allows the images and movies used by one or more

    scenes to be copied to a new location, optionally adding handles to

    image sequences, and optionally updating the scene(s) to use the new

    location. For example, consolidation can be used after conform to

    copy the necessary material onto local Baselight storage \[bug 27407]

### Conform

* The conform process has been redesigned to be more efficient.
* Command line conform is supported via the bl-conform tool. The tool has a lot of help text built in, but its full use is documented in a separate FilmLight manual

### Cloud Media

* Baselight can now access files stored on removable drives ("cloud media") connected to any Baselight system on the network, without having to configure shared volumes.
* Baselight can directly conform from EDLs and material on cloud media. Once the conform is complete, the Consolidate function can be used to copy only the used material \[bug 27638]

### Apple ProRes

* Baselight now uses Apple's ProRes library for encoding and decoding Apple ProRes movies.
* QuickTime movies can now be written using the Apple ProRes XQ codec.
* Apple ProRes movies can now be decoded at half-resolution for speed (except where the movie has alpha channel data).
* Apple ProRes 4444 and Apple ProRes 4444 XQ QuickTime movies containing valid (non-opaque) alpha channel data are now indicated as such in the Sequence Browser.

### AJA Display Output

*   Baselight can now use AJA Kona 4 hardware for image display.

    The following video modes are supported via AJA hardware:

    * NTSC 720x486  at 29.97, 30 Hz
    * PAL  720x576  at 25 Hz
    * HD  1920x1080 at 23.976, 24, 25, 29.97, 30, 50, 50.94, 60 Hz
    * UHD 3840x2160 at 23.976, 24, 25, 29.97, 30, 50, 50.94, 60 Hz
    * DCI 2048x1080 at 23.976, 24, 25, 29.97, 30, 47.95, 48, 50, 59.94, 60 Hz
    * DCI 4096x2160 at 23.976, 24, 25, 29.97, 30, 47.95, 48, 50, 59.94, 60 Hz

    The SDI output can be configured as 1.5G SDI, 3G-SDI Level A or 3G-SDI Level B.

    NOTE: 50, 59.94 and 60 Hz modes are only available using the Y'CbCr 4:2:2 signal format, and are only available as progressive formats.
* Stereoscopic display via AJA display hardware is supported for HD 1920x1080p/sF and DCI 2048x1080p display modes.
* Simultaneous HDMI and SDI output is available from the AJA Kona 4. The HDMI output can match the resolution of the SDI format, or can be configured as an HD downscale from the UltraHD or 4K signal being displayed via SDI.
* Audio output via SDI is supported on systems using AJA SDI display hardware. The following audio output options are available when routing audio via the AJA hardware:
  * 16 channels of audio are embedded in the SDI output
  *   16 channels of audio are available on the AES stereo outputs

      (as 8 stereo AES outputs)
  * 8 channels of audio are embedded in the HDMI output
  *   2 channels of analog audio available on phono connectors on the

      AJA SDI breakout box.
* The Baselight Setups editor has been modified to support editing settings for the AJA SDI output device. When running on a system with AJA SDI hardware, the Display tab will show a set of settings:
  *   Resolution

      &#x20; Allows you to choose the resolution of the display format.
  *   Rate

      &#x20; Allows you to choose the frame rate of the display format.
  *   Signal Type

      &#x20; Allows you to choose Progressive, PsF or Interlaced.
  *   Speed

      &#x20; For HD/UltraHD/DCI formats, this option allows you to specify

      &#x20; the base SDI signal speed, choosing between 1.5G, 3G Level A and

      &#x20; 3G Level B.
  *   Video Format

      &#x20; Allows you to choose between RGB 4:4:4 or Y'CbCr 4:2:2.
  *   Sync Source

      &#x20; Allows you to choose internal or external sync.
  *   HDMI Mode

      &#x20; When the main SDI output format is 3840x2160 or 4096x2160, you

      &#x20; can choose whether the HDMI output is the same resolution, or

      &#x20; downscaled to HD/2K. The HDMI output will have the same frame

      &#x20; rate as the SDI output however (it does not perform 2:3

      &#x20; pulldown).
  *   SDI Audio

      &#x20; Allows you to choose to output audio via the SDI hardware (which

      &#x20; also provides AES, HDMI and analog stereo output), or via the

      &#x20; existing audio hardware (for example, via the USB optical audio

      &#x20; interface or Hammerfall audio interface).
* Known issues with AJA Kona 4 SDI/HDMI output:
  *   When using an UltraHD or DCI 4K display mode, and using the HDMI

      HD mode (which performs a downscale from UltraHD/4k to HD/DCI 2K),

      this currently only works when using a 4:2:2 SDI output. This will

      be fixed in a future release of Baselight.
  * SDI timecode output is not implemented yet.
* Please contact FilmLight support for details on upgrading your system to AJA Kona 4 display hardware.
* Please note that AJA Kona 4 SDI output requires an update to your Baselight licence.

### DVI/HDMI/DisplayPort Output

*   It is now possible to configure Baselight to use the DVI, HDMI or DisplayPort output on the main processing GPU to drive monitors or projectors.

    Baselight allows the resolution and refresh rate for the display to be selected in the Baselight Setups editor. These options are read dynamically from the attached display device.

    Note this option is not available on systems using FilmLight DVI2SDI or Framestore display hardware.

    This option requires NVIDIA driver 340.32 or later.
*   "Primary Output Device":

    In the Baselight Setups editor, you can choose which display device to use on a per-setup basis. Most setups will use the "Default" device, which is governed by the "Default Display Device" preference.

    Available devices include:

    * AJA SDI display cards
    * FilmLight DVI2SDI or Framestore hardware
    * GPU DVI/HDMI/DisplayPort outputs

    This allows you to use SDI output for the majority of setups, but to switch to DVI/HDMI/DisplayPort on certain setups if required to drive a specific display device.

    On systems with AJA SDI hardware, AJA SDI is the default display device.

    On systems with FilmLight DVI2SDI or Framestore hardware, DVI2SDI or Framestore is the default display device.
*   "Default Display Device" preference has been added to bl-prefs, in the Display->Output section. This allows you to choose the preferred image output mechanism.

    When a setup in the Baselight Setups editor is set to use the Default display device, Baselight

    There are the following options

    *   Choose Automatically

        &#x20; Allow Baselight to automatically determine the best display

        &#x20; device to use for the image output. Baselight chooses in the

        &#x20; following order:

        1. SDI hardware, if present
        2. FilmLight combiner/framestore, if present
        3. DVI/HDMI/DisplayPort from GPU
    *   SDI (PCI Express/Thunderbolt)

        &#x20; Default to using AJA SDI hardware via PCI Express if it is

        &#x20; present.
    *   FilmLight DVI2SDI/Framestore:

        &#x20; Default to using FilmLight DVI2SDI/Framestore hardware, if it

        &#x20; is present.
    *   DVI/HDMI/DisplayPort from GPU:

        &#x20;  Default to use the DVI/HDMI/DisplayPort outputs from the main

        &#x20;  processing GPU.

    The default option is "Choose Automatically", which is the appropriate setting for the majority of systems.

### R3D GPU Acceleration

*   R3D movies can now be decoded using the Baselight GPU. This is generally faster than using the CPU, and does not require RED Rocket hardware.

    GPU decoding of R3D movies requires 1. An NVIDIA GPU which a. supports CUDA Compute capability 2.0 or higher (see [http://developer.nvidia.com/cuda-gpus](http://developer.nvidia.com/cuda-gpus)) b. has at least 3GB of RAM 2. FilmLight OS 6.4 or later

    The GPU requirement means that this functionality is available on Generation V Baselight systems, or Generation IV systems with upgraded graphics cards. (Mac systems do not support GPU R3D decoding in Baselight at this time.)

    The "Decode" option on the R3D Params operator allows GPU decoding to be disabled, or to be chosen in preference to a RED Rocket.

    GPU decoding is not supported for scenes which use R3D Colour Science v2 "New Colour Science".

    When GPU decoding is available, the speed of CPU R3D decoding is impacted (just as it is when a RED Rocket card and driver are installed). A preference (under System/Render) allows GPU decoding to be disabled should you wish to continue using CPU decoding without a speed penalty.

### Miscellaneous

*   Support for 10-bit Y'CbCr 4:2:2 timeline cache.

    When dealing with the increased data rate and storage requirements of UltraHD at 59.94 or 60 Hz frame rates, it may be desirable to change the "Display and Timeline Cache" format in scene settings to use "10-bit Integer 4:2:2 Y'CbCr". This reduces the disk space, disk bandwidth and network bandwidth requirements for playing back UltraHD/60p material by 33%.

    UltraHD 50, 59.94 and 60Hz display modes use Y'CbCr 4:2:2 encoding, so there is no visual loss in quality when using this format.

    Selecting this format does not affect the chroma resolution when rendering to RGB or Y'CbCr 4:4:4 deliverable formats, as the image data will not be compressed to Y'CbCr 4:2:2 format when rendering to image/movie formats with higher chroma resolution.
* Updated to RED SDK v5.1. This addresses some issues in earlier SDK releases, and adds:
  *   Support for Dragon Enhanced Blacks (D.E.B.) processing (not

      available on RED Rocket or RED Rocket X)
  * Low-pass filter metadata
* Added fl-vers and fl-service commands to Mac OS X
* Added ability to save the log for an operation \[bug 28907]
* Automatic adjustment of the floating window option in stereograde now acts globally \[bug 28990]
* Scrollable text items, for example on the right side of the Sequence Browser, can now be copied to the clipboard using a right-click menu \[bug 29205]
* Added support for reading metadata for ARRIRAW files from Codex Vault XML files \[bug 27374]
* When a render operation has multiple deliverables, Setup For Tape Playout now offers the choice of deliverable \[bug 28824]
* When a scene has multiple deliverables, Setup For Rendered Scene now offers the choice of deliverable \[bug 29284]
* Added bl-aja-upgrade tool for upgrading AJA Kona card firmware \[bug 29293]
* Added firmware version check for SDI diagnostic test \[bug 29293]
* Add suport for 12-bit SDI output via Kona 4 for HD, UltraHD, DCI 2K and DCI 4K resolutions \[bug 29369]
* In BLG Export, added additional 1/16, 1/32 and 1/64 proxy resolution options, to allow the creation of BLGs with much small file sizes.
* Baselight now requires 290.10 or later drivers for GPU rendering. If upgrading from 177.70, please use the latest Nvidia driver release from FilmLight \[bug 29793]

## Bug Fixes Since Baselight 4.4.6964

* Fixed bl-setups and bl-config-video on systems with FilmLight combiner, DVI2SDI or Framestore hardware \[bug 28302]
* Fixed stereo display modes on FilmLight combiner, DVI2SDI and Framestore hardware \[bug 28303]
* Fixed tearing on SDI output when using FilmLight combiner, DVI2SDI or framestore hardware \[bug 28352]
* Fixed support for 3840x2160/50p video mode \[bug 28774]
* Fixed crash in GPU renderer \[bug 28019]
* Fixed bug that prevented using Truelight profiles on the cursor \[bug 28621]
* Fixed support for DVI/HDMI/DisplayPort output on Baselight TWO/FOUR/EIGHT.
* Fixed dual-link 1.5G SDI support.
* Added support for 48p display modes at DCI 2K and DCI 4K resolutions on Linux.
* Added support for Dual 1920x1080 and Dual 2048x1080 stereo display modes, up to 4:4:4 30p and 4:2:2 60p \[bug 27868]
* Fixed incorrect buffer capacity assertion in flfsd \[bug 28891]
* Fixed bug in 59.94 conform from CMX3600 EDLs \[bug 28806]
* Added support for NVIDIA driver 340.32 on systems with GTX 680 or GTX 780 GPUs \[bug 28979]
* Fixed failure to recognise/read some DNxHD MXF movies \[bug 28372]
* Changed Job Browser to indicate what product a scene was created with \[bug 28837]
* Fixed issue where some error messages were truncated \[bug 26889]
* Fixed scene detection failures when image/movie filenames contain unusual characters \[bug 28986]
* Fixed behaviour of Colour Space Journey View when docked into a workspace \[bug 29015]
* Fixed typo in Technical Manual pg\_dumpall section \[bug 27284]
* Fixed bl-conform to sanity check that the requested format exists \[bug 28172]
* Fixed bug that showed a percentage on the 'Raw EDL' tab of the EDL Import panel \[bug 28128]
* Fixed a bl-conform but that would not accept '.' characters in host names \[bug 28179]
* Fixed the retrieval and display of scan statistics in the Baselight conform panel \[bug 28129]
* Fixed error display for bl-conform when the required broker service is not available \[bug 28198]
* Fixed default minimum conform percentage, raised from zero to 10 percent. Can be overridden from the command line \[bug 28159]
* Fixed problem with colour coding of access rights in the filesystem browser \[bug 28407]
* Fixed problem causing sequences to be missing in browse results \[bug 28393]
* Fixed problem using copy with sync option on raw frames for which there is no internal writer available \[bug 28953]
* Fixed license warning on FLUX Store systems \[bug 29084]
* Select Missing Media now has a Cancel button \[bug 28827]
* Fixed crash using AST file in Audio Sync \[bug 29028]
* Fixed an issue preventing MXF files written by ASDCP from being read. Affects JPEG2000 and audio files used for e.g. DCPs \[bug 29152]
* Reduced the number of partitions created when writing XDCAM MXFs. The large number of partitions previously created caused the file to open and read very slowly in Baselight \[bug 29183]
* Fixed BLGs exported from stacks containing both layer blending and Truelight operators not containing the required cubes \[bug 29216]
* Sony RAW Parameters are now initialised to use the Colour Primaries and Tone Curve which match the monitoring metadata in the MXF file \[bug 28650]
* Fixed crash on Baselight Kompressor when /etc/hosts doesn't have configuration comments that are normally added by fl-config-master \[bug 25949]
* Using a full-sensor-size format for Sony RAW media no longer fails with "Sequence Input Format is too large" \[bug 29250]
* Support Quadro 600 card as a replacement for a GeForce 6200 to drive the Blackboard display on gen3 Baselight ONE systems running FilmlightOS 6.4 due to the GeForce 6200 driver crashing in this configuration \[bug 29134]
* Fixed pfs-verify false positive warning "\[file] has redundant sparse files" for zero-length round-robin file \[bug 29252]
* Fixed incorrect black levels in the letterboxing area when rendering to ProRes \[bug 29264]
* Fixed problem with Video grade lifting black when no parameters have been changed \[bug 29196]
* When an AAF references the start of an image sequence in the FileName column, this is turned into a descriptor for a likely sequence, and will be searched for when conforming \[bug 29170]
* Fixed renderer crash on clusters ("Invalid internal buffer format") \[bug 29008]
* Fixed upward shift when decoding some XDCAM MXF files, resulting in black lines at the bottom \[bug 29325]
* Fixed flfsd tight retry loop (transmit failed: bad address) when an internally generated request was deleted prematurely \[bug 29068]
* Fixed audio sync when playing 59.94fps scenes on a 29.97fps display devices \[bug 29384]
* Fixed bug with Nvidia GPU Configuration diagnostic on systems with NVIDIA 340.32 driver \[bug 29389]
* Fixed bug that could cause more than the correct number of conforms to be attempted when using 'Timecode location = Header' \[bug 29374]
* Fixed crash on startup when running on a machine with NVIDIA 340.32 drivers and FilmLight DVI2SDI or Framestore hardware \[bug 29417]
* Fixed queued render failures with "Cannot fetch unparsed string" errors \[bug 28693]
* Fix playback errors on systems with DVI2SDI or Framestore combiners \[bug 29430]
* Fixed the export resolution dropdown doing nothing in the BLG Export dialog \[bug 29372]
* Fixed problem with configuring "Sony 4K" and related video modes when using FilmLight DVI2SDI or Framestore hardware \[bug 29623]
* Fixed flfsd assertion '((\_length + 3) & \~3) <= capacity' \[bug 29636]
* Fixed flfsd dropping reply packet when tcp connection is temporarily unavailable \[bug 29643]
* Fixed problem with conforming rendered media \[bug 29615]
* Fixed bad colours of "ph7" Phantom cine files. Existing scenes are unchanged; to update the behaviour of an existing scene, use the Update Sequence Behaviour button \[bug 29697]
* Fixed an issue where some very old Baselight scenes could not be opened \[bug 29765]
* Fixed problem with corrupt output via FilmLight Framestore hardware when using "Sony 4K" or "DCI 4096x2160 24p" video modes \[bug 29782]
* Fixed artefacts in highlights in some Phantom cine files \[bug 29839]
* Fixed problems with trackball sensitivity on newer Blackboard 2 hardware which was causing text boxes to occasionally undo typing \[bug 29410]
* Fixed issue with Blackboard 2 jog shuttle sensitivity on newer hardware which could occasionally cause playback to stop \[bug 29746]
* Fixed problem with genlock at 23.976 and 29.97 frame rates on older GPUs (8800/9800GT) when using newer NVIDIA drivers (290.10, 304.117 and newer) \[bug 26598]
* Fixed a problem that could cause the movie reader to crash when reading DCPs \[bug 28999]
* Added check to installer to valid GPU hardware configuration before allowing Baselight to install \[bug 26598]
* Fix problem with communications with FilmLight Framestore display hardware \[bug 29947]
* Disable PAT/MTRR Nvidia config patch for Baselight ONE systems using PCI Express UI GPUs \[bug 26598]
* Fixed installer test on Gen 3 Baselight ONE with Quadro K600 \[bug 26598]
