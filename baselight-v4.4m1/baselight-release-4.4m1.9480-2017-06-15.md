# Baselight Release 4.4m1.9480 (2017-06-15)



## Bug Fixes Since Baselight 4.4m1.9418

* Fixed failure to render image sequences to paths which are not within /vol \[bug 43256]
*   The Avid DNxHD/DNxHR SDK crashes when used on older CPUs which lack SSSE 3 and/or SSE 4.1, including some Generation III and older Baselight systems. To prevent this, the SDK is no longer available on these systems, which means DNx media can no longer be read or written using these systems.

    We apologise for this loss of functionality, which is due to the behaviour of a 3rd-party SDK \[bug 43240]
* Turned off CRC generation in DNx encoding, and CRC checking in DNx reading, due to ambiguities between the VC3 specification and Avid's SDK leading to false reporting of CRC errors in both Baselight and other software \[bug 43236]
* Fixed decoding using RED Rocket on Baselight FOUR/EIGHT systems, and when using a RED Rocket installed in a remote system \[bug 43369]
* Added support for NVIDIA 375.66 driver for Titan Xp GPUs
* Allow baselight systems running 367.44 driver to use 375.66 driver to fix incorrect RED GPU decoding \[bug 42821]
* Fix problem pasting existing formats \[bug 42975]
