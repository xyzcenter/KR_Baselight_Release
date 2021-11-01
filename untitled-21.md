# Baselight Release 4.3.5380 (2012-06-07)



## New Features Since Baselight 4.3.5378

* Added button to Sequence parameters to update sequence and layer operators after the type of input file is changed (using the Change button, or through use of bl-shots). All selected sequences are updated if Grouped Grading is enabled. This is particularly useful if you change from an image sequence to a movie or vice versa.
* Moved 'Blur', 'Copy', and 'Paste' buttons on Blackboard 2 to bottom row of button group. Allows easier access by operators by touch.
* Moved 'Cache' button on Blackboard 2 / ONE to top right button panel.
* Added 'Layer 0' button for Blackboard 2 / ONE.
* Added 'Previous Frame' & 'Next Frame' buttons to bottom right transport button panel on Blackboard 2 / ONE.
* Added Up/Down buttons to keypad area of soft keypad on Blackboard 2 to allow bumping of numerical values in edit boxes. Also only keypad area of soft keyboard now appears when a numeric edit box has focus.
* Added 'Cursor 1..9' buttons on Blackboard 2 / ONE to allow fast access to cursors with left hand.
* Added 'UI 1/2' and 'Image' buttons on Blackboard 2 / ONE to allow fast switching between display image and UI screens.
* Added -tapenames, -clipnames and -comments options to bl-shots, allowing the user to extract more metadata from a scene using the command line.

## Bug Fixes Since Baselight 4.3.5378

* Fixed crash when exiting Machine Control on Blackboard 1 \[bug 20872]
* Fixed display of Machine Control buttons on Blackboard 2.
* Fixed divide-by-zero crash when using "Apply Transform" in FCP XML conform \[bug 20706]
* Field information (interlaced/progressive) is now correctly written to QuickTime movies on Linux.
* Fixed crash when accessing the matte curve in MatteTool without a Blackboard attached \[bug 20902]
* Fixed Modify AAF/XML not functioning \[bug 20913]
