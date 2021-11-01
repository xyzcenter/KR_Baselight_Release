# Baselight Release 4.4m1.8932 (2016-12-13)



## Bug Fixes Since Baselight 4.4m1.8800

* Updated Dolby Vision analysis algorithm to match latest Dolby specification \[bug 39428]
* Updated Slate firmware to 1.0.21.25. This new firmware resolves some USB connection issues experienced at a few customer sites. Please contact FilmLight support before updating your Slate. \[bug 39614]
* Fixed startup crash on BLX systems during "Starting Renderer" \[bug 38505]
* Fixed a bug that could cause fl-diag to fail on the Adaptec Remote Access check \[bug 33146]
* The Adaptec StorMan services can affect disk performance; run only when required (via the raidadaptec diagnostic's 'launch web interface' button) \[bug 39944]
* Fixed bug that caused the Blackboard output on a Quadro K1200 GPU to be mapped to the wrong connector \[bug 39689]
