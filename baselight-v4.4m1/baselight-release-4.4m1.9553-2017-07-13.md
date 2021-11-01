# Baselight Release 4.4m1.9553 (2017-07-13)



## New Features Since Baselight 4.4m1.9480

* Added support for nvme-based storage \[bug 42991]

## Bug Fixes Since Baselight 4.4m1.9480

* Added support for reading audio from Op1B MXF-files. Previously, these files tended to cause movie reader crashes when attempting to read audio \[bug 43113]
* Fixed a problem where rendering XAVC or XDCAM to Sony MXF did not set the duration correctly in the file header \[bug 43464]
* Linking a tracker to a transform strip for a stabilization no longer resets the transform parameters \[bug 43663]
* Fixed a memory leak that could cause mxfproxy processes to consume a lot of memory over time \[bug 43726]
