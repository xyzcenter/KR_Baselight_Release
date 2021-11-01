# Baselight Release 4.4.7370 (2015-05-01)



## Bug Fixes Since Baselight 4.4.7317

* Fixed problem with SDI setting options appearing blank in the Setups editor \[bug 31857]
* Fixed compatibility issues reading and writing Avid DNxHR QuickTime files \[bug 31877]
* Changing any of the SDI setup parameters in the Display panel of the Setups editor will not reset the other settings if those settings are still valid. For example, changing the SDI frame rate will no longer reset the Signal Format or Speed options \[bug 30640]
* Added 'nodirect' option to volume.cfg to disable direct io on a per-volume basis (e.g. 'limit san\_rt0 nodirect') \[bug 31316]
* Fixed problem that could cause EXR files to be identified as plain files rather than a sequence when copying \[bug 31969]
* Fixed problems rendering to movie files when the system's hostname has been modified so it is not fully-qualified \[bug 32297]
