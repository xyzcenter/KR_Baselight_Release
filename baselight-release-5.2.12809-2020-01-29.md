# 베이스라이트 릴리즈 노트 5.2.12809 (2020-01-29)

## 최신 기능 (Baselight 5.2.12770 이후)

*   Added support for extracting CDL SOP and SAT values individually in column expressions in Shots View. You can fetch the CDL value for each layer using the syntax:

    ```
    %{CDL#} for Slope, Offset, Power and Saturation

    %{CDL#.SOP} for Slope, Offset and Power together

    %{CDL#.SAT} or %{CDL#.Saturation} for Saturation

    %{CDL#.Slope}, %{CDL#.Offset}, %{CDL#.Power} for Slope, Offset
          and Power individually
    ```

    The # indicates the layer number containing the CDL \[bug 53931]
* Added support for overriding the values exported by the ALE exporter with values from columns in Shots View. If any column is defined in Shots View with an "EDL Name" matching a built-in ALE column, the value will be taken from the Shots View column instead of the default value generated by the ALE exporter \[bug 53931]
* Added support to Media Import Rules for mapping from file metadata into numeric custom columns \[bug 53933]

## 버그 개선 (Baselight 5.2.12770이후)

* Fixed behaviour of Sequence operator "Browse for new sequence" button when grouped grading is enabled and multiple Sequence operators are selected \[bug 53903]
* Fixed obscure cuda errors when using 418 nvidia driver \[bug 53807]
* Fixed crash when filtering numeric custom columns \[bug 53936]
* Fixed bug when using numeric custom column as the matching criteria in Media Import Rules \[bug 53933]
* Added "Sensor Rate" to the list of known ARRI File Metadata keys available in Media Import Rules \[bug 53956]
* Fixed potential crash when opening a scene in the Gallery \[bug 53958]
* Fixed incorrect uncompressed OpenEXR renders when rendering from OpenEXR source media with more than RGB channels \[bug 53971]
* Updated the Sony XAVC Encoder to version 1.1.11 on macOS \[bug 53983]