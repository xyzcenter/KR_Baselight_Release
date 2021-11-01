# Baselight Release 4.3.5546 (2012-08-21)



## New Features Since Baselight 4.3.5530

* Added support for using %P for clip name when editing Name and Tape fields in Shots View.
*   Added support for utilising RED Rocket cards in several machines; typically one in each node of a Baselight FOUR or EIGHT. To configure this, edit /usr/fl/etc/cloud.cfg and add the 'redrocket' flag against each machine containing a RED Rocket.

    It is also possible to configure other Baselight systems to make use of multiple machines containing RED Rockets by adding multiple hostnames to an 'option redrocket' line in /usr/fl/etc/cloud.cfg.
*   Added support for reading Canon C500 RAW data in RMF and DPX files.

    PLEASE NOTE this should be considered "beta" functionality until advised otherwise. If you encounter issues please report them to baselight-support@filmlight.ltd.uk

## Bug Fixes Since Baselight 4.3.5530

* Layer Manager now shows "T" when current layer is a Tracker strip \[bug 21306]
* Fixed issue with Blackboard 2 buttons not updating in rare circumstances \[bug 21528]
* Fixed memory leak on multi-node systems
* Fixed keyframe movement using Ctrl+\[ and Ctrl+] not ending properly, causing subsequent arrow key presses to continue moving keyframes until a different operator was selected \[bug 21561]
