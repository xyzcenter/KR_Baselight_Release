# Baselight Release 4.4m1.8951 (2017-01-05)



## Bug Fixes Since Baselight 4.4m1.8932

* Fixed "excessive recursive invocations" error seen with some scenes when opening Shots View \[bug 34400]
* Fixed an issue in conform with saved EDL search directories that would cause conform to fail with a 'canonical path' error \[bug 34987]
* Fixed failures on "Not connected to Audio System" errors \[bug 20213]
* Fixed bright pixels caused by bad sensor data in non-packed Phantom Cine RAW files \[bug 40187]
* Fixed an issue that could cause 4:2:0 material in QuickTime and MP4 containers to be stretched from legal to full on read. Notably affected AVC/H264 \[bug 39525]
* Fixed remote rendering on a multi-GPU FLUX Store \[bug 40086]
