# Baselight Release 4.4.6259 (2013-10-08)



## New Features Since Baselight 4.4.6237

*   Added the option to decode ARRIRAW files using the ARRI SDK. This is slower than using the Baselight decode, but should enable matching to the decode from other applications.

    To simplify operation, the Sharpen which is added to the Baselight decode is now controlled from the ARRIRAW Decode operator.

    PLEASE NOTE: The ARRI SDK is not supported on Mac OS X 10.5. This means that ARRIRAW files accessed by or via a Baselight Kompressor running Mac OS X 10.5 will not support decoding using the ARRI SDK \[bug 25673]
* Added keyframe indicators for layer blend amount slider to keyframe bar \[bug 25497]
* Added support for reading MXF files containing 2K Sony F5 RAW and 2K Sony F55 RAW \[bug 25439]
* Added ACES RRT 0.2.1 as an option for Display Rendering Transform. This is the recommended DRT to use for most situations, and is now the default DRT for new scenes (edit this in bl-setups or the Baselight Setups window) \[bug 25614]
* Added No Conversion option for Output Colour Space on Render View. This causes no colour conversion to be applied during rendering, by setting the output colour space to be the same as the Grade Result Colour Space \[bug 25701]
* Added support for decoding XDCAM HD, XDCAM EX and XDCAM HD422 in QuickTime movies without requiring a Baselight Kompressor, and for encoding XDCAM HD422 into QuickTime on Linux.

## Bug Fixes Since Baselight 4.4.6237

* Fixed bug which would cause animated layer blend amount keyframes to be incorrectly positioned after a strip had been split \[bug 25642]
* Fixed problems creating the database user on OS X when the user name includes upper case characters \[bug 25633]
* Fixed problem with selecting the display menu with no scene open \[bug 25651]
* Fixed problem with Stereo Grade not setting the keyframe mode on the other eye \[bug 25655]
* Improved RED Rocket-X support \[bug 23716]
* Fixed problem where convergence was getting set to the same value in both eyes \[bug 25662]
* Stereo Grade now auto-splits on a group-graded action \[bug 25665]
* Rendering using Both Eyes now always renders from the bottom of the other eye stack \[bug 25680]
* Fixed slow performance caused by Video Grade continually updating the Blackboard graph selector \[bug 25631]
* Fixed Apply of a single blend layer \[bug 25479]
* Fixed failures caused by QuickTime files with bad timecode data that has no frame rate \[bug 25607]
* Fixed bug where incorrect functions could occasionally be activated when using the 'Ctrl' modifier on Blackboard desks \[bug 25682]
* Fixed orientation of rear screens and incorrectly displayed buttons on Blackboard 2 ONE \[bug 25623]
* Fixed crash at end of commandline bl-render -tocache \[bug 25699]
* Fixed Queue Monitor incorrectly displaying "Rendering suspended" \[bug 25703]
* AAF relink failures now cause a render to be marked as failed.
* Fix for values in Video Grade occasionally jumping to extreme values \[bug 25683]
* Fixed invalid right eye cache produced by bl-render -tocache on single-stack stereo scenes \[bug 25707]
* Fixed bug in grouped grading of keyframed blend amount slider \[bug 25715]
* Fixed a bug where invalid 'edts' atoms in QuickTime movies could result in different reported lengths on Linux and Mac \[bug 25602]
* Fixed occasional unnecessary re-caching of stacks using Sony RAW, R3D or ARRIRAW material with Automatic colour space \[bug 25707]
* Fixed broken rendering of glow strips when using the 'Dark Glow' effect \[bug 25752]
