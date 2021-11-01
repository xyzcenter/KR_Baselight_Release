# Baselight Release 4.4.6673 (2014-04-01)



## New Features Since Baselight 4.4.6600

* Updated to RED SDK v4.6. This addresses some issues in earlier SDK releases, and adds:
  * Support for ACES Linear output
  * Support for new Dragon OLPF
  * Rocket-X support for RED ONE clips
  * Rocket-X driver for FLOS 6.4
  * Additional metadata support
* Updated to ARRIRAW SDK v4.5. This addresses some issues in earlier SDK releases.
* The Operations Queue in Baselight and bl-render now processes renders submitted by all users, not just the user running the application (does not apply to Baselight PORTABLE).
* Added "Lock Y Positions" toggle to shape strips. This prevents shapes & edges from being dragged vertically on the image or moved vertically from the trackballs \[bug 23514]
*   Added horizontal left/right bumps for shapes to the numeric keypad (using the '8' and '/' keys respectively, to match stereo grade). These are available when 'Numeric Keypad for Grading' is enabled (from the 'Edit' menu). These bumps are also available on the middle Blackboard trackball reset/top row buttons.

    The bump amount can be set from the "Customise" menu and half bumps are available using the "Control" modifier \[bug 23514]
* Translating shapes that have been stereo split now applies the opposite change to the other eye's shape if grouped grading is enabled \[bug 23514]
* Added functionality to support grading for Dolby Vision. This is beta functionality and is currently visible only to customers with an appropriate licence.
* Added option on Scene Settings (and Setups New Scene tab) to control the bit depth of the timeline cache and display pipeline. Switching to 16-bit floating-point increases the size of the timeline cache by 50% which can impact performance. The default setting of 10-bit integer is recommended unless you are: 1. grading HDR material and wish to pick negative or >1.0 colour values 2. grading for Dolby Vision \[bug 26094]
* A new option on the Display menu allows the brightness of mattes, shapes, control elements and the cursor to be reduced. This is useful on displays where the maximum brightness is uncomfortable to view. By default the brightness is scaled to the white point of the cursor's Viewing Colour Space. Please note this functionality requires a combiner or DVI2SDI box; it has no effect on Baselight PORTABLE \[bug 26839]

## Bug Fixes Since Baselight 4.4.6600

* Fixed incorrect rendering of Text and Burnin entries when one % expansion follows immediately after another \[bug 27097]
* Fixed white thumbnails for OpenEXR files; if you continue to see white thumbnails, please use "bl-reset-cache -thumb" to clear the cached thumbnails \[bug 26541]
* When changing movie file type when rendering with audio, the audio codec is no longer left in an invalid state \[bug 27109]
* Fixed permissions on directories created when rendering to volumes hosted on Baselight Kompressors \[bug 27099]
* Fixed an issue where QuickTime movies containing large blocks of NULL bytes took a long time to open \[bug 27098]
* Reduced disk space required by operations queue, by compacting operations once they have completed \[bug 26083]
* Fixed incorrect ICC profile information written into TIFF files using colour spaces without ICC profiles \[bug 27162]
* Fixed crash when duplicating a mask or burnin \[bug 27164]
* Fixed pfs2 service script failure on initial Baselight install \[bug 27150]
* Increased speed of renders using "Link To Unchanged Input Files" option to create symbolic links \[bug 26257]
* Fixed render corruption when loading the same (large) image multiple times per frame \[bug 26477]
* Fixed problem with X server startup on Baselight nodes \[bug 27137]
* Fixed problem that prevented access to text consoles on Baselight nodes whilst X server is running \[bug 27183]
* Fixed problem with starting applications on Baselight workstation systems after running bl-config-xorg for the first time \[bug 27154]
* Fix conforming by 'Tape Name in Header' when remote conform is active \[bug 27182]
* VTRE no longer continuously attempts to reconnect to a server. It now waits 10 seconds between attempts \[bug 27055]
* Fix sending of crash reports; it is now less verbose when reporting is turned off \[bug 11257]
* sshfs-based network mounts now work on Flos 6 systems \[bug 27210]
* Disabled Shuffle's 'Input 2' button when used in an Inside/Outside layer \[bug 27212]
* Fixed issues with some operator presets (e.g. Add Grain) when a value was negative \[bug 27095]
* Ensure graphical boot screen is finished before starting X server on nodes \[bug 27223]
* Fixed occasional Server Failure errors when using file panel in directories containing dangling symbolic links \[bug 27249]
* Fixed occasional crash when writing DNxHD movies.
* Fixed corrupt audio reading from MXF movie files with 1000/1001 frame rates (such as 23.976, 29.97 and 59.94 fps) \[bug 27211]
* Fixed support for integrated motherboard audio outputs \[bug 27258]
* Fixed problem that prevented certain tools from using the correct GPU on Baselight ONE systems \[bug 27259]
* Fixed command-line render submission using bl-render -queue ignoring a supplied frame range \[bug 27290]
* Fixed problem with Blackboard tablet mapping after running bl-config-xorg on a UI host \[bug 27345]
* Fixed rare diag warning for nvidia or combiner firmware caused by race condition \[bug 27369]
* Fixed problem starting bl-render on Mac OS X \[bug 27061]
* Fixed problem with error reporting in bl-config-video and bl-config-xorg \[bug 27061]
* Fixed problem with bl-config-tablet not running. bl-config-tablet is responsible for mapping the tablet area to the primary UI monitor on startup/login \[bug 27214]
* Fixed issue with applying to a blank in Replace mode causing a crash \[bug 27234]
* Prevented some queued renders from repeatedly failing and restarting \[bug 27401]
* Fixed "parse failed" errors when rendering using a mask \[bug 27421]
