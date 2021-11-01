# Baselight Release 4.4.6806 (2014-06-06)



## New Features Since Baselight 4.4.6767

* Sequence Browser now allows Mark In/Out using Timecode or Timecode 2 \[bug 16240]
* Changed behaviour of Render Layer/Track options. "Input Only" now renders the input sequence, with no colour space conversion to the sequence Output Format, and no Grade Result Colour Space. "Layer 0 Only" preserves the previous behaviour \[bug 27121]
* Improved decode of Phantom cine files (existing sequences created in older Baselight releases are unaffected; these changes only affect newly-added sequences):
  * Added support for Flex4K
  * Fixed incorrect colours on some files
  * Improved colour
  * Added repair of bad pixels.
* Added "Soft Clip To Full" Video LUT option on Render View, to give a soft rolloff of values above 1.0 and below 0.0 \[bug 25952]
* Added S-Gamut3, S-Gamut3.Cine and S-Log3 options to Sony RAW Params \[bug 26423]

## Bug Fixes Since Baselight 4.4.6767

* When loading a scene, the progress bar no longer goes from 0-100% twice \[bug 27745]
* Improved the speed of submitting certain scenes for rendering, when the database server is using PostgreSQL 8.2 or later \[bug 27693]
* Improved error message when an ARRIRAW sequence is replaced with a non-ARRIRAW sequence \[bug 27778]
* Fixed failures in tracking when a shot's Comment metadata contains a string that can be interpreted as an escape sequence (e.g. "\005") \[bug 27731]
* The render panel now only allows selection of audio sample rates that are actually supported by the corresponding codec \[bug 27660]
* Reduced uneven playback behaviour of movies \[bug 27551]
* Removed incorrect error message when opening DNx444 movies in QuickTime containers on Linux \[bug 27437]
* Prevent nodemon from producing too much console output \[bug 27575]
* Add support in flux for copying to target directories that contain a % character \[bug 27747]
* Disabled support for writing the DNx100 codec to MXF container since the encoder is too unstable \[bug 25918]
* Reduced time taken to update Slate desk screens over USB \[bug 27773]
* Fixed crash with deleting a blend layer via the layer manager \[bug 27812]
* Fixed bug where "New Shape" button on Slate desks failed to respond to being pressed \[bug 27684]
* Added Slate desk support for Matte Merge and added "Matte Merge" button to "Stack Manager" section of Chalk for Slate \[bug 27827]
* Fixed brightness of Six Vector keyer mode display \[bug 27871]
* Fixed crash when exporting a CMX EDL with pulldown \[bug 27632]
* 'flint' parallel barrier driver can now use a shared interrupt \[bug 27855]
* Slate connection diagnostic now returns a more meaningful message on failure \[bug 27723]
* Fixed slow playback performance on multinode systems when using DPX files that have large headers \[bug 27876]
* Removed access to Blackboard 2 specific buttons in Chalk for Slate \[bug 27547]
* Fixed crash that could occur when rendering DNxHD to Avid OP-Atom MXF files \[bug 27892]
* Fixed green mask area when rendering with Hard Black mask to most movie codecs \[bug 27917]
* Fixed unwanted switch to Movies Video+Audio when changing movie file type on Render View \[bug 27672]
* Fixed Colour Space Journey when the stack only contains one operator (e.g. a Blank) \[bug 27933]
* Fixed initial values of Scene Settings set when upgrading scenes, which could cause changes in scene rendering \[bug 27929]
* Updated xfs-repair to version 3.2.0 \[bug 27642]
* Fix for crash when undo-ing changes involving deleted Custom Buttons in Chalk \[Bug 26931]
* Fixed Low-res proxy option on Sequence Browser \[bug 27995]
* Fixed crash due to 'unimplemented format conversion' when writing QuickTimes on Linux \[bug 28035]
* Fixed incorrect orientation of some DPX files (e.g. from Flame 2015) \[bug 28030]
* Fixed flio diagnostic utility 'no space left on device' error due to a full xfs allocation group \[bug 27805]
* Fixed render failure using symbolic link option \[bug 28084]
* Fixed bug with cursor not being drawn on the SDI output when using "Sony 4K" or "DCI 4096x2160" video modes \[bug 27967]
* Fixed occasional hang in Sequence Browser when scanning several folders of movies \[bug 28093]
