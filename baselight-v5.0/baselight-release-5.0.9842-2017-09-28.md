# 베이스라이트 릴리즈 노트 5.0.9842 (2017-09-28)



## Bug Fixes Since Baselight 5.0.9754

* Fixed an issue that could cause FLUX Manage to fail to show all the available sequences and movies in a directory \[bug 44789]
* Fixed an issue that could cause FLUX Manage to report the file size of some movies to be zero \[bug 44795]
* Fixed crash when attempting to track missing media \[bug 44767]
* Fixed crash in FLUX Manage after using a USB device in Chalk for Slate \[bug 44839]
* Fixed pattern matching in conform for subdirectories and file names that could cause some files to be ignored incorrectly \[bug 44625]
* Changed event track in exported CMX EDLs from "V1" to "V" \[bug 44804]
* Fixed metadata loss through Shader operator \[bug 44945]
* Fixed colour spaces not being correctly embedded in scenes when they are saved, which can cause failures to load when loaded on other systems without the necessary spaces installed \[bug 45010]
* Fixed bug which made it difficult to select text to edit in the LUT export panel's 'Name' control \[bug 44806]
* Fixed memory leak in burnin \[bug 44988]
* Fixed playback issues when Paint Colour brush was selected \[bug 45007]
