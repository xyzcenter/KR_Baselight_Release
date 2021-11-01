# Baselight Release 4.4m1.8720 (2016-10-06)



## New Features Since Baselight 4.4m1.8607

### File Formats

* Added support for reading HEVC (h.265) encoded QuickTime and MP4 files \[bug 36531]
* Added support for reading Sony X-OCN format from MXF files \[bug 37061]
* Added V-RAW Params for controlling the exposure and colour temperature of Panasonic Varicam RAW files \[bug 36975]
* Added support for reading the "clean aperture" rectangle stored in QuickTime files. This is used, for example, in ProRes files written by ARRI cameras \[bug 36665]
*   Support for reading and writing encrypted DCPs has been added, as well as a new dedicated DCP render tab allowing improved control over DCP structure and metadata.

    Certificates and self-encrypted DCPs When the software is installed, it will create a self-signed root certificate, an intermediate certificate and a leaf certificate. The default certificate preference point to this generated leaf certificate.

    To select a different certificate, open the Preferences dialog, go to the 'System' tab and scroll down to the 'DCP' section. There you need to select three files: 1. A file containing the private key, stored in PEM format. The contents of the file should start with =-----BEGIN RSA PRIVATE KEY-----=. The private key must be usable without a password. 2. A file containing the public certificate, also in PEM format. The contents of the file should start with =-----BEGIN CERTIFICATE-----=. 3. A certificate trust chain for the certificate. Instructions for creating such a file can be found e.g. here: [https://www.digicert.com/ssl-support/pem-ssl-creation.htm](https://www.digicert.com/ssl-support/pem-ssl-creation.htm)

    A DCP is considered self-encrypted when the default certificate, as specified in the preferences, can be used to read an encrypted DCP, using a KeyDeliveryMessage (KDM) stored in a file named kdm\_fl\_self.xml located in the root of the DCP. The default configuration of the render dialog is to create such a KDM when creating an encrypted DCP.

    Self-signed certificates for the purposes of DCP creation can be created with the command-line tool fl-certgen. It takes a destination directory as an argument. A self-signed root certificate, an intermediate certificate, a leaf certificate and a certificate trust chain will be created in the destination directory. This tool is included for testing and support purposes. It is not expected to be necessary for normal operation.

    Decoding / Playing a DCP To read a DCP, open the Sequence Browser and select the desired CompositionPlayList (CPL) from the DCP. Due to legacy reasons, it is also possible to select the ASSETMAP file, which will have the same effect as selecting the CPL listed first in the PackingList (PKL). A DCP Params strip will be available, where you can specify the correct private key and KDM if required.

    Creating DCPs To create a DCP, open the Render dialog and click the DCP output button. The first step is then to select the DCP type. The choices are SMPTE + Audio (the default), SMPTE (no audio), Interop + Audio and Interop. Both video and audio contents will be encrypted by default. Which components to encrypt, and what certificate to use can be selected in the 'Encryption' section. The subsequent controls provide control over the file names and different metadata fields of all XML and MXF files created as part of the rendered DCP. It is currently only possible to create packages with a single CPL.

    It is possible to create a DCP consisting of multiple reels by clicking the 'Add Reel' button. When creating a DCP consisting of a single reel, the number of frames in the reel is determined by the number of frames to render. To be able to alter the number of frames in the first reel, you must first add a second reel. You can then select any reel in the list, including the first one, and change the number of frames it contains.

    By default, a single KDM will be created for the default certificate. KDMs for additional certificates can be created by clicking on the 'Add KDM' button. NB: If no KDM is created for any certificate for which you have the private key, you will not be able to view the result of the render!

    To create additional KDMs for an existing DCP there is a command line tool called dcptool. It takes as arguments a current KDM, the private key, a certificate chain for that private key, a recipient certificate and the file name of the new KDM. The plan is to provide an interface for additional KDM generation in a future release \[bug 36976]

### Dolby Vision

* Updated Dolby Vision XML output to include details of the render colour space. This is selected on the file browser when using "Export Dolby EDR Metadata" \[bug 36702]
* Added additional controls to Dolby Vision View to allow the CMU state to be seen and changed, and to launch the web control interface \[bug 36718]
* Analysing a Dolby Vision strip under a Dissolve now sets the Trim and Advanced parameters so they animate between the values in the two Dolby Vision strips either side of the dissolve \[bug 36698]

### Miscellaneous

* The flos-tools package has been updated to version 6.4.8119. This includes the following fixes & enhancements:
  * netboot-chkconfig: Improve parsing of service script levels
  *   fl-create-network-template: Avoid spurious error disabling

      firstboot.
  * mknetbootrd: Make image world-readable after running dracut.
  * fl-config-master: Avoid crash when no avahi-daemon.conf
  * fl-setup-database: Add support for PostgreSQL 9.5
* Updated the H.264 encoder. Rendering speed when creating H.264 QuickTime files on Linux has improved significantly \[bug 33923]
* The formats editor now allows the opacity of burnin text and borders to be set \[bug 17432]
* Histogram View may now be floated in a window \[bug 36616]
* When viewing in Stereo Anaglyph Layout, you can choose between five anaglyph modes using a submenu on the Display menu \[bug 34383]
* When rendering in Muxed Anaglyphic, you can choose between five anaglyph modes \[bug 34383]
* Added in Play Controls View a new speed : 1.25x \[bug 28710]
* In Preferences/Display, the pencil screen switching can be turned off now \[bug 28830]
* Added a new kind of view, BigMetadata (available of course in the view menu), which allows to display metadatas in a large scale about the current cursor output image as timecode or keycode \[Bug 19640]
* Added "Force Expand By" option to Timeline Sort View's "Handles" parameter. When used, this option will ensure that shots are _always_ expanded by the amount specified, regardless of whether or not there is sufficient image data for those handles. This can be useful in pipelines where the user wishes the Baselight timeline to refer to image data which has yet to be generated \[bug 37211]
* EDL Import is now able to load and apply CDL values from AAF files \[bug 27763]
* Updated to RED SDK v6.2.1. This includes bug fixes and the following changes:
  * 8K sensor support.
  * New colour primaries option "RED Wide Gamut RGB".
  * New tone curve option "Log 3G10".
  * Minimum Rocket-X driver version is now 2.1.34.0
  * Minimum Rocket-X firmware version is now 1.4.22.18 \[bug 37708]
* "Full Sensor" resolutions are now available for several ARRIRAW resolutions, including for ALEXA Mini. PLEASE NOTE: using the 3424x2202 full sensor area from a 3414x2198 image may reveal artefacts at the sensor edges \[bug 38714]
* Added support for NVIDIA Quadro K1200 UI GPU \[bug 38815]

## Bug Fixes Since Baselight 4.4m1.8607

* Fixed an issue reading QuickTime and MP4 movies where subsampling is less than 4:2:2 and bitdepth larger than 8 \[bug 36531]
* When changing the Frame Rate of a Sequence, you are now offered the choice to maintain the Offset in seconds or in frames, as was the case in Baselight 4.4 \[bug 36557]
* Fixed reading ActionCam files with certain colour temperature settings \[bug 36549]
* Fixed crash when adding an image to a Burnin using the right-click menu \[bug 36600]
* Fixed bl-reset-cache -hardssd error 'umount2: No such file or directory' \[bug 35318]
* Fixed failures making chequer/black frames on errors, when rendering scenes using cached strips to some image/movie formats \[bug 35306]
* Addressed a number of issues with dpm which is used in fl-diag to test disk performance:
  *   Fixed directory generation error when run on Gen VI machines

      outside of fl-diag \[bug 36128]
  *   Hardened the application against scrambled output from command

      line RAID management utilities \[bug 35847]
  *   Provide a fail indicator ‘!’ for diagnostics with clear limits

      that can in the future be incorporated into fl-diag \[bug 18448]
* Fixed scenes incorrectly remaining locked after using "bl-render -queue" \[bug 36666]
* Stereo Colour Match is now automatically excluded from LUT export as its operations cannot be matched by a LUT \[bug 35916]
* Fixed bug in switch diagnostic for non-contiguously numbered interfaces that could cause divide by zero error \[bug 35534]
* Fixed error in PQ colour spaces (Dolby: ST 2084 PQ / P3 D65 and Rec.2084: ST 2084 PQ / Rec.2020) which could cause errors when resizing \[bug 36773]
* Fixed crash reading some corrupt OpenEXR files \[bug 36806]
* Reduced time taken to open the first scene using a Truelight directory with a large number of cube files \[bug 36555]
* bl-render commandline now reports when it is waiting for the GPU to become available \[bug 31808]
* Fixed crash using edit mode on single strips \[bug 35581]
* Fixed performance degradation which could occur for some minutes after launch when connected to a Dolby Vision CM Box \[bug 36823]
* Anamorphic R3D media now selects an anamorphic format where possible \[bug 36862]
* Fixed an issue where reading ProRes media in QuickTime files with varying frame durations could produce incorrect results on Linux \[bug 36851]
* Fixed bug in Timeline Sort which, when used in a single stack stereo scene with different frame offsets for each eye, would result in the non-current eye's frame offsets to be incorrectly overwritten \[bug 36914]
* Fixed an issue that prevented certain types of RAW images from decoding correctly \[bug 36921]
* Fixed zones diagnostic which would fail on systems with OS X CONFORM nodes that are version 10.11.1 (El Capitan) \[bug 36880]
* Fixed reset operator not working on the Slate \[bug 36978]
* Fixed unwanted switching of a colour space to a different space with the same tone curve, when opening a scene which uses a colour space different from any already known on your system \[bug 37020]
* Changed the behaviour when navigating up/down through the layers of a (complex) stack (using 'Page Up' & 'Page Down'). Previously, if a layer had more than one input (a composite layer, for example), navigating to the layer above would select the first layer of the first (foreground) input. Now the first input is ignored and the first layer of the last (background) input will be selected. Similarly, navigating down though a stack will skip foreground (and matte) strip inputs to a layer \[bug 24500]
* Fixed failures and crashes when using OpenEXR files with a very large number of channels \[bug 36999]
* Audio is now correctly written to QuickTime movies when using Modify XML workflow \[bug 37139]
* Generate a warning when attempting to render a Sony MXF with an invalid timecode, and prevent render failure due to the drop-frame flag being incorrectly set \[bug 37091]
* Fixed issue where the CDL grade always took control of the numeric keygrade \[bug 37168]
* Fixed problem with zone discovery when cloud.cfg contains a null mac address \[bug 37165]
* Improved keyframing behaviour in OFX plugins to behave more like other keyframes \[bug 37210]
* Fixed incorrect Canon MXF metadata when there are multiple clips in one directory sharing the same INDEX.MIF file \[bug 37170]
* Added a diagnostic to check that SMART functionality is disabled on drives behind Adaptec RAID controllers because when it's enabled we see regular transfer latency spikes which can affect playback. Added a utility to disable SMART on drives behind Adaptec RAID controllers \[bug 37254]
* Errors which occur while making movies fast-start no longer cause renders to fail \[bug 37245]
* Fix crash when exporting a BLG containing several large Truelight cubes \[bug 36622]
* Fixed list scrolling behaviour in the application on macOS when using mouse scroll-wheel or trackpad \[bug 37301]
* Fixed an issue where rendering to RLE or v408 codecs in QuickTime containers would incorrectly stretch colours \[bug 36984]
* Fixed failures with Truelight operators when submitting a render from Baselight CONFORM to the operations queue on a Linux system \[bug 37330]
* Fixed bug in Despot on first/last frames when 'Use Source Handles' mode set to 'None' \[bug 29222]
* Added option to display Scene & Take metadata in Gallery and Cut views \[bug 37331]
* Fixed hangs when reading some badly-formed QuickTime files on macOS \[bug 37366]
* Fixed errors when using R3D movies comprised of very many separate files \[bug 35330]
* Fixed crash in CDL grade when switching between to 2 scenes and editing values \[bug 37053]
* Fixed render out issue with mismatched sizes \[bug 37663]
* Fixed "Source data did not contain required samples" error when rendering or playing back audio that requires resampling \[bug 36407]
* Fixed failure to decode 2560x2145 ARRIRAW MXF media \[bug 37660]
* Fixed render operation hang when grading while rendering to ProRes \[bug 37831]
* Fixed crash using Truelight with 1x1 interleaved stereo layout \[bug 37531]
* Fixed bug with audio output stopping intermittently during playback \[bug 37105]
* Fixed incorrect pixel aspect ratio read from some QuickTime movies \[bug 38501]
* Fixed issues with "Sony: Linear / S-Gamut3" colour space when installed using the Linear Colour Spaces pack from www.filmlight.ltd.uk \[bug 37706]
* Fixed ordering on the Manage Colour Spaces panel \[bug 37706]
* Fixed issues where rendering XAVC to MXF did not close partitions, and 1280x720 XAVC Intra and interlaced XAVC Intra formats did not properly write CBE indexes \[bug 38174]
* Changed the location of the VBE index in XAVC LongGOP and XAVC Intra VBR encoded MXF files. It is now in the header instead of the footer of the file \[bug 38524]
* Fixed crash when area tracker is applied to a zero-area shape \[bug 38508] \[bug 37495]
* Fixed bl-render on multi-GPU systems \[bug 38604]
* Fixed bug which could slow performance when working with very complex stacks \[bug 38340]
* Fixed playback stall when using multiple cursors on multi-gpu machines \[bug 38658]
* Fixed bug with AJA Kona 4 SDI output when switching between RGB 1.5G dual-link and 3G-A output configurations \[bug 38519]
* Fixed crash when sorting by 'Circle Take' column in Shots view with a scene imported from Daylight \[bug 37574]
* Fixed failure to read some malformed ARRIRAW files which presented as 2578x2160 resolution instead of 2880x2160 \[bug 38128]
* Fixed incorrect decode of RED and ARRIRAW media on Baselight FOUR/EIGHT when rendering from queue \[bug 38792]
* Reduced delays when playing scenes containing mixed formats of ARRIRAW media \[bug 38797]
* Fixed "LUT data" errors reading ALEXA Mini MXF files \[bug 36987]
* Fixed video memory overallocation when rendering, this could cause slow rendering or replay \[bug 38834]
