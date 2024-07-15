# Baselight Release 5.3.18523 (2023-09-04)



## New Features Since Baselight 5.3.18465

* Added preference to fl-diag for the NVIDIA GPUs test, to check the number of installed render GPUs matches the expected number \[bug 65466]

## Bug Fixes Since Baselight 5.3.18465

* Fixed issue where IMF package metadata configured in Render View was not applied to the created package. Notably this affected CPL and PKL filenames, OPL file creation and other metadata such as "Title" and "Issuer" \[bug 65450]
* Fixed errors reading CLF files containing 1D or 3D LUTs \[bug 65446]
* Fixed memory leak which could occur when closing scenes \[bug 65467]
* Fixed failure to start some applications e.g. fl-queue \[bug 65489]
* Fixed possible crash conforming CMX EDLs with locator marks containing an empty comment \[bug 65438]
* Fixed errors rendering using a queue on a remote system when the user ID of the user submitting the render does not exist on the remote system \[bug 65469]

***
