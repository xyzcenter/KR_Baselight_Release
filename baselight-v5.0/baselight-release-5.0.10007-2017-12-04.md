# 베이스라이트 릴리즈 노트 5.0.10007 (2017-12-04)



## New Features Since Baselight 5.0.9964

* Added second vectorscope to allow viewing at multiple scales simultaneously \[bug 45831]
* Added ability to recover an older version of a scene that cannot be opened because it has been saved from a future Baselight release (e.g. 5.1) \[bug 45583]

## Bug Fixes Since Baselight 5.0.9964

* Fixed an issue that prevented creation of non-encrypted DCPs due to invalid errors about certificates \[bug 45768]
* Improved display of vectorscope graticule \[bug 45831]
* Addressed corruption of font textures on the blackboard \[bug 44755]
* Fixed issues on Render View when cloud media volumes have names containing special characters such as parentheses \[bug 45793]
* Fixed hang in OFX, for example when using a custom preset dialog \[bug 45952]
* Fixed out of memory condition when using scopes and a blackboard \[bug 45717]
* Fixed crash when multi-pasting BLGs \[bug 45163]
