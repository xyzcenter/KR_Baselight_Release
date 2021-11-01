# Baselight Release 4.4m1.8800 (2016-11-08)



## Bug Fixes Since Baselight 4.4m1.8766

* Fixed OpenEXR writing on FilmLightOS 2.1 systems \[bug 38977]
* Fixed ARRIRAW Params "Colour Primaries" setting in legacy scenes using Baselight decode \[bug 39154]
* Fixed access to 2560x2145 decode of ALEXA Mini MXF files captured at this resolution \[bug 39104]
* Fixed a misnamed XML tag in KDMs generated for encrypted DCPs. KDMs created prior to this fix will no longer be usable, but can be recovered by manually editing the KDM XML file to rename DCinemaSecturityMessage to DCinemaSecurityMessage \[bug 39158]
* Fixed crash reading latest 8K R3D media \[bug 39156]
* Fixed video memory over allocation \[bug 39152]
* Fixed Dolby Vision operation in stereo modes with AJA Kona4 hardware \[bug 38187]
* Fixed crash when reading audio from some cloud-media movie files \[bug 38494]
* Reduced video memory usage to fix playback slowdowns \[bug 39168]
* New Blackboard2 firmware is available for customers having specific DVI issues. Contact FilmLight support for important instructions on how to apply this. Do not attempt this update without FilmLight involvement, as you risk damage to the Blackboard2 \[bug 39058]
* Reliability fixes to slate-update-firmware \[bug 39105]
* New Slate firmware (1.0.16.16). Please contact FilmLight support before updating to prevent damage to the Slate. New Slate firmware displays logo on back screens when baselight is not running, and improves reliability of Slate. \[bug 27724] \[bug 38997] \[bug 39108]
* Fixed "Error processing RED data" errors when rendering some R3D media \[bug 37705]
