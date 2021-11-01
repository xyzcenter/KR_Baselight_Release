# Baselight Release 4.4.7274 (2015-03-09)



## New Features Since Baselight 4.4.7262

*   Added support for reading big-endian 32-bit floating-point RGB TIFF

    files \[bug 26656]

## Bug Fixes Since Baselight 4.4.7262

* Relaxed bitrate limitations in the codec parameters for DCP and DCI MXF writing. It is now possible to specify any bitrate greater than zero \[bug 31469]
* Fixed colour issues with very old Phantom cine files \[bug 31352]
* Fixed failures caused by inserting removable media with a long name \[bug 31473]
* Fixed bug which could cause an flfsd assertion error (have\_handles) when changing the permissions of a file with missing pfs2 attributes \[bug 31454]
* Fixed internal error in the disk performance diagnostic \[bug 31507]
