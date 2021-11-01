# Baselight Release 4.4m1.9274 (2017-04-06)



## New Features Since Baselight 4.4m1.9217

*   Sony RAW media (from F5, F55, F65, FS700 cameras) is now decoded

    using the Sony SDK. This makes the image quality match the decode

    from other applications using the same SDK. In addition, supersize

    decodes of F65 media are now supported (to 8192x4320, 7680x4320,

    8192x2160 and 6144x3240). Note that existing Sony RAW media in

    existing scenes will continue to decode as they did before; this

    change only applies to newly-added media \[bug 41256]

## Bug Fixes Since Baselight 4.4m1.9217

* Fixed application lock-up issues when using a Dolby Vision CMU on a network where DNS lookups produce a very long delay \[bug 36823]
* Fixed an issue in 'Import EDL' that can occur when filenames in an AAF contain special characters \[bug 38820]
* Fixed crash when conforming using Keycode \[bug 41267]
* Fixed a bug in conform that affected some EDLs with zero length events, when conforming with relative frame offsets \[bug 30483]
* Fixed occasional "Discontinuous timecode" errors when rendering to ProRes or DNxHD QuickTime \[bug 41518]
