# Baselight Release 4.3.5996 (2013-05-29)



## Bug Fixes Since Baselight 4.3.5962

* Fixed occasional hang on Baselight PORTABLE when rendering to movies using "Prefer Source Codec" and/or "Frame Rate From Source Movies" \[bug 23196]
* Fixed crash in thumbnail rendering on the Mac for stacks containing certain HueShift 3 values \[bug 24147]
* Fixed hang in "fl-systemmonitor -live" and possibly other command line utilities \[bug 23969]
* Improved speed of movie decoding (e.g. R3D) on systems with more than 16 processor cores \[bug 24198]
* Fixed fl-rm when specifying a frame range with leading "0" digits \[bug 23602]
* Fixed creation of scenes with invalid names through pasting into the New Scene dialog \[bug 24263]
* Fixed middle-button paste into text fields \[bug 14]
* Worked around a bug in the Avid ISIS filesystem that prevented conform from finding all relevant files \[bug 23604]
* Fixed occasional crash when clicking the "Edit" menu, if the Multi-Paste setting was in "BLG" mode \[bug 24264]
