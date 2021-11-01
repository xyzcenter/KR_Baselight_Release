# 베이스라이트 릴리즈 노트 5.2.11761 (2019-05-07)

## 최신 기능 Baselight 5.2.11675이후

*   You can now use the individual start/end timecodes from "Source TC" and "Record TC" variables in expressions by suffixing the variable name with '\[0]' and '\[1]' array index operators.

    For example, you can use '%{Source TC\[0]}' to get the start source timecode of a shot in an expression \[bug 51162]

## 버그 개선 Baselight 5.2.11675이후&#x20;

* Fixed occasional crash in Text operator when no strip is selected during playback \[bug 51116]
* Fixed crash when dynamically generated burnin text is empty \[bug 50603]
* Fixed bug where using %{Source TC} in expressions would result in an empty string \[bug 51162]
* Fixed failure to start application on a system using an older nvidia driver \[bug 51161]
* Added a missing MXF tag that prevented some flavours of AVC-Intra from being decoded \[bug 51196]
* Fixed crash with protected strips inside a matte channel \[bug 50412]
* Fixed failure to use Dolby Vision Software CMU when rendering more than 500 frames \[bug 51269]
* Fixed excessive memory use when rapidly opening & closing scenes \[bug 51288]
* Fixed issues opening Chalk Layout files created by earlier versions of Chalk \[bug 51125]
