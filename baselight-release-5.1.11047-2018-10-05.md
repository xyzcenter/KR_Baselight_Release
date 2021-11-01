# 베이스라이트 릴리즈 노트 5.1.11047 (2018-10-05)

## New Features Since Baselight 5.1.10917

*   Added new Overlay Grids for Luma Waveform and YCbCr parade to display the luminance in cd/m2. Five new overlays are available to adapt the spacing of the luminance grid for specific use cases and customer needs:

    * nits base2 This mode will draw lines at every stop (twice the luminance)
    * nits base10 - 1 This mode will draw lines for every order of magnitude (0.1, 1, 10, 100 etc) and one divider line between these steps
    * nits base10 - 2 Same as "nits base10 - 1" but with two divider lines
    * nits base10 - 3 Same as "nits base10 - 1" but with three divider lines
    * nits base10 - Perceptual Same as "nits base10 - 1" but with approximated perceptual equidistant steps. That means it will draw fewer divider lines in the low luminance range and more in the high luminance range

    In addition lines are always drawn for the creative-, clip- and peak-white luminance levels of the selected viewing colour space \[bug 46999]
* Added Balance Offset function to CDL Grade, which allows a colour picked from the image to be made neutral \[bug 30497]
* Added "Colour Space of Rendered HDR Media" option when exporting Dolby Vision XML, to support workflows where the Dolby Vision Mastering Display is P3/D65 but the rendered HDR media is Rec.2020 \[bug 48895]
*   Added "Linked Property" setting for columns in Shots view. This allows you to configure a bi-directional link between a column in Shots view and decode parameters. For example, if you set the "Linked Property" setting for a column to "ARRIRAW.WhiteBalance", the White Balance value will be available via the column, and any changes to the value in the column will be propagated back to the White Balance parameter of the ARRIRAW Params operator.

    This allows decode parameters to be transferred between scenes, or updated via EDL/ALE, using the Multi-Paste view \[bug 49059]
* Added a Subsequence tile to FLUX Manage, which is shown when Mark In/Out has been used. This tile allows subsequences to be copied, deleted etc \[bug 44863]
* It is now possible to drag from the Non-media files list in FLUX Manage \[bug 41928]
*   Baselight can now connect to PostgreSQL services using a PostgreSQL service name. Just use the service name instead of a host name in the Job Manager etc. PostgreSQL service definitions can include alternate ports, login credentials and so on. They are useful when using SSH tunnels to connect to remote database servers. An example minimal .pg\_service.conf file could contain:

    \[my\_tunnel] host=localhost port=54321

    This would be useful if the local port 54321 is tunnelled to some remote system. With this in place, using "my\_tunnel" instead of a regular host name would allow Baselight to connect through the tunnel to the remote server.

    For more details on the .pg\_service.conf file format, see the PostgreSQL documentation, "The Connection Service File", at [https://www.postgresql.org/docs/9.2/static/libpq-pgservice.html](https://www.postgresql.org/docs/9.2/static/libpq-pgservice.html) \[bug 48920]
* Added the ability to export BLGs containing only the operator values for the current eye. In addition, added %e and %{Eye} substitutions to BLG Export to allow the eye name (L/R) to be included in the filename \[bug 49087]
*   Added a new operator to the Matte Tool called "Edge Filter". This is designed primarily for use on keyer derived mattes and can be used to restore low frequency detail from the keyer's source image. It is particularly helpful with contours and hard keys, where it can help bring back edge gradient levels from the original image.

    The Edge Filter has 2 controls:

    * Radius: determines how localised the treatment should be
    *   Blur:   controls how much smoothing needs to be done

        \[bug 49082]

## Bug Fixes Since Baselight 5.1.10917

* Fixed issue with incorrect Time Reference value calculation in Broadcast WAV metadata when writing WAV files \[bug 48876]
* Fixed an issue where AAC-encoded audio in MP4-files could fail to decode at the end of the file \[bug 48835]
* Fixed failure to apply Software CMU to Secondary Output when the primary output is not also using Software CMU \[bug 48857]
* Fixed issue causing slow down when scrolling through shots in Cuts View with Try held down \[bug 48854]
* Fixed incorrect timecode handling when using QuickTime movies with timecodes that cross midnight \[bug 48647]
* Fixed DPX image corruption when writing to an SMB share from OSX \[bug 39929]
* Fixed behaviour of multi-stage Shader operators that distort or blur the image, when using a viewing format whose mapping uses an area smaller than the entire input image \[bug 48951]
* Fixed crash when displaying error message as burnin text \[bug 47605]
* Fixed crash when tracking with YCrCb 420 scene format \[bug 48466]
* Fixed arbitrary failures of Modify AAF render \[bug 48919]
* Fixed failure when viewing a gallery grab of offline media which was grabbed from a Sequence whose Input Format was a crop \[bug 48467]
* Fixed issue with playback due to picking being enabled in some operators \[bug 45876]
* Fixed failure to correctly switch versions of flux and/or render services when operations in the queue require a different application version \[bug 48524]
* Fixed an issue where audio could fail to read from trimmed ALEXA mini MXF-files \[bug 48982]
* Fixed "CL\_OUT\_OF\_RESOURCES" errors when decoding R3D and Canon RAW media \[bug 47669]
* Fixed Job Manager sometimes starting with blank columns \[bug 45113]
* Fixed errors in FLUX Manage when attempting to copy a file with a " in its filename \[bug 48832]
* Fixed 1 pixel jumps observed when editing blurred mattes \[bug 48983]
* Fixed occasional hang when using Sony RAW media \[bug 48769]
* Fixed artefacts that can appear at the edges of Shader operators, particularly when their output is blurred. Note that this fix only applies to newly-inserted Shader operators; existing scenes are unchanged unless you re-insert the Shader operator(s) \[bug 48950]
* Fixed crash in Nuke script generation which would occur if the filename of the generated BLG didn't end in ".blg.exr" \[bug 48401]
* Fixed issue with fl-config-master attempting to restart disabled service \[bug 48569]
* Fixed FLUX Manage showing out-of-date thumbnails for files which have been overwritten \[bug 49096]
* Fixed crash when conforming from cloud media \[bug 49075]
* Fixed errors in Dolby Vision display menus that could occur when using a Hardware CMU \[bug 48855]
* Improved error reporting in "Database access" diagnostic \[bug 49078]
* Improved Job Manager connection time & reliability \[bug 46456]
* Fixed bug with audio channel mapping not refreshing correctly when creating new channel mappings or deleting existing channel mappings via the Edit Channel Mappings window \[bug 49132]
* Increased disk cache maximum size \[bug 49154]
* Fixed issue with Dual Colour Space Layout outputs becoming unsynchronised during playback when using the option to show scopes/histogram from the secondary output \[bug 48850]
* Fixed the command line conform tool 'bl-conform', the diagnostic option '-v' could cause it to fail with an error \[bug 49140]
* Fixed occasional assertion in layout by converting it to a diagnostic message which will hopefully help narrow down the cause \[bug 49216]
