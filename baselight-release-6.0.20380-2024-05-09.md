# Baselight Release 6.0.20380 (2024-05-09)

##

### New Features Since Baselight 6.0.20256

* Added support for the NVIDIA RTX 5000 Ada Lovelace GPU. Bug 68211

### Bug Fixes Since Baselight 6.0.20256

* Improved compatibility of metadata written to QuickTime files; other tools should now be able to read it. Bug 68174
* Fixed image errors in some situations when working on a multiple-GPU system with an input sequence stored on a remote system which is connected by dual-link networking. Bug 68001
* Fixed crash when selecting a Paint operator in some scenes. Bug 67090
* Fixed issue where opening non-gallery scenes in the gallery would require the '\_v6' suffix. Bug 67893
* Fixed incorrect drawing of dimmed filtered-out ranges in the Timeline View, especially when changing the zoom level. Bug 67057
