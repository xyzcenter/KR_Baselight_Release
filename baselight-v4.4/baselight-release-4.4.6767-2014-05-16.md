# Baselight Release 4.4.6767 (2014-05-16)



## New Features Since Baselight 4.4.6757

*   Changed the R3D Params operator to offer general Linear output in

    any R3D Output Colour Space, in addition to the existing ACES Linear

    option. Both the Linear options cause the R3D decode to generate

    true linear floating-point images \[bug 27848]

## Bug Fixes Since Baselight 4.4.6757

* Fixed slow reading of some MXF files \[bug 27832]
* Reading QuickTime movies with multiple sample descriptions no longer generates an error when opening the file \[bug 27786]
* Improved speed of rendering movies to ISIS filesystems mounted on Linux \[bug 27864]
