# Baselight Release 6.0.21452 (2024-10-28)

## Important Notes&#x20;

Baselight 6.0 no longer supports FilmLightOS 6. Please contact FilmLight Support to discuss upgrading to FilmLightOS 8. Bug 60176\
\
Baselight now supports macOS 15 Sequoia; the minimum supported version is now macOS 13 Ventura. Bug 69501\
\
RED Rocket hardware is no longer supported. Bug 65725

Using a Grade Result Colour Space is deprecated and this functionality may be removed in a future release. Please watch this video for information about recommended workflows for telecine-style grading. Bug 64729

Dolby Vision external CMU devices are no longer supported. Bug 62581

The vtre application is no longer included. Bug 66448

Many colour spaces have been updated with higher precision matrices. Scenes upgraded from Baselight 5.3 will use the older colour spaces and warn about that in the console. Visual output is consistent between original and new colour spaces. Bug 67302

## 중요 참고 사항&#x20;

Baselight 6.0은 더 이상 FilmLightOS 6을 지원하지 않습니다. FilmLight 지원 팀에 연락하여 FilmLightOS 8로 업그레이드에 대해 논의하시기 바랍니다. 버그 60176

Baselight는 이제 macOS 15 <mark style="color:red;">Sequoia</mark>를 지원하며, 최소 지원 버전은 macOS 13 <mark style="color:red;">Ventura</mark>입니다. 버그 69501\
\
RED Rocket 하드웨어는 더 이상 지원되지 않습니다. 버그 65725

Grade Result Colour Space 사용은 더 이상 권장되지 않으며, 이 기능은 향후 릴리스에서 제거될 수 있습니다. 텔레시네 스타일 그레이딩에 대한 권장 워크플로에 대한 정보는 이 비디오를 참조하십시오. 버그 64729

Dolby Vision 외부 CMU 장치는 더 이상 지원되지 않습니다. 버그 62581

vtre 애플리케이션이 더 이상 포함되지 않습니다. 버그 66448

많은 컬러 스페이스가 더 높은 정밀도의 매트릭스로 업데이트되었습니다. Baselight 5.3에서 업그레이드된 장면은 이전 컬러 스페이스를 사용하며 콘솔에 경고 메시지가 표시됩니다. 시각적 출력은 원본과 새로운 컬러 스페이스 간에 일관성을 유지합니다. 버그 67302



## New Features Since Baselight 6.0.21211&#x20;



### Automated Issue Reporting&#x20;

A new 'Issue Report' feature has been added to Baselight and Daylight. It allows users to report software or system issues in an easy-to-use web interface.

Using the feature will ensure that the support team automatically receives important system and application information that could help with the resolution of the issue.

Creating a report will automatically collate system diagnostics, preferences, console logs, licenses, and information about the operating system and hardware. (Users have the option to check and remove files at any time.)

Users can also attach multiple scenes, screenshots, and other supporting files and list download locations for material on file sharing sites.

The package needs to be installed before use:

In the menu bar, select 'Views', then select 'Scripts View'.

Navigate to the Packages tab and select the 'fl-automated-issue-reporting' package and click on 'Install package'.

After installation, the 'Report Issue' menu item will be visible in the Baselight/Daylight menu.

Select 'Report Issue' to launch the web-based reporting application. Baselight/Daylight must remain open while reporting any issues.

If the system is online, once you submit the report, all information and attached data will be uploaded to our servers, and a support ticket will be created.

If the reporting system is offline, complete the web form, and create the report. The application will create a metadata file that can be emailed to FilmLight support. This will contain the basic information to create a support ticket. Upon receipt, the support system will create a ticket and will provide the location of the supporting files so they can be retrieved by the support team.

Please note, no personal or private data is collected at any time.\
\


### 자동 이슈 보고

Baselight와 Daylight에 새로운 ‘이슈 보고’ 기능이 추가되었습니다. 사용자는 간단한 웹 인터페이스를 통해 소프트웨어 또는 시스템 문제를 보고할 수 있습니다.

이 기능을 통해 지원팀은 문제 해결에 도움이 될 수 있는 중요한 시스템 및 애플리케이션 정보를 자동으로 수신하게 됩니다.

보고서를 생성하면 시스템 진단, 환경 설정, 콘솔 로그, 라이선스, 운영 체제 및 하드웨어 정보가 자동으로 수집됩니다. (사용자는 언제든지 파일을 확인하고 삭제할 수 있습니다.)

사용자는 여러 장면, 스크린샷 및 기타 지원 파일을 첨부하거나 파일 공유 사이트에서 자료 다운로드 위치를 나열할 수 있습니다.

사용 전 패키지 설치 필요:

```
1.	메뉴 바에서 ‘Views’를 선택한 후 ‘Scripts View’를 선택합니다.
2.	Packages 탭에서 ‘fl-automated-issue-reporting’ 패키지를 선택하고 ‘Install package’를 클릭합니다.
3.	설치가 완료되면 Baselight/Daylight 메뉴에 ‘Report Issue’ 항목이 표시됩니다.
```

문제 보고 절차:

```
•	‘Report Issue’를 선택하여 웹 기반 보고 애플리케이션을 시작합니다. 문제 보고 중에는 Baselight/Daylight가 열려 있어야 합니다.
•	시스템이 온라인 상태일 경우, 보고서를 제출하면 모든 정보와 첨부 데이터가 서버에 업로드되고 지원 티켓이 생성됩니다.
•	보고 시스템이 오프라인일 경우, 웹 양식을 작성하고 보고서를 생성합니다. 이 애플리케이션은 FilmLight 지원팀에 이메일로 보낼 수 있는 메타데이터 파일을 생성합니다. 이를 통해 지원 시스템은 티켓을 생성하고, 지원팀이 첨부 파일의 위치에 접근할 수 있게 됩니다.
```

개인 정보 보호: 개인 정보나 사적 데이터는 전혀 수집되지 않으니 안심하셔도 됩니다.\


### Layer Matte Improvements&#x20;

Up to 4 matte inputs/channels can now be accessed/configured directly from the "Matte Operators" grid and desk's Stack Manager section.

On the grid, there are now left and right arrow buttons on either side of the "Matte Operators" heading. Each grid column (except for the last, which is reserved for adding new matte inputs) is labelled with the matte input/channel number it represents. When there are more than 2 matte inputs, the arrow buttons can be used to "scroll" the 2 columns through the layer's matte channels.

On a desk, holding the Stack Manager's matte merge key will cause the layer up/down keys to flash. They can then be used to "scroll" the desk's 2 rows (1 on a Slate) of matte keys through the layer's matte channels. Bug 67417

Unused matte operators can now be removed from the "Matte Operators" grid by right clicking on an operator in the grid and selecting the "Remove XXX Operator From Grid" menu option. Operators can be added back to the grid from its Customise menu.

Specific OFX Filter and Flexi Effect matte operators can now be saved as default options in the grid. This allows them to be inserted directly into a layer's matte without first invoking the effect picker dialog. To do this, first select the generic (OFX Filter or Flexi Effect) operator and use the picker to insert the specific operator required. That operator will then appear in the grid above the generic type. It can then be saved to the grid as a default option from the Customise menu's "Add Matte Operator To Grid" submenu.

Which matte (filter) operators are available from the desk keys can now be customised. This is done using the "Configure Desk Matte Operators" dialog, available from the Matte Operator grid's Customise menu.

This dialog has dropdowns representing the first 2 matte (filter operator) desk keys, which can be used to select the operator assigned to those keys.

If the operator selected is one of the 2 generic types (OFX Filter or Flexi Effect), the key can be further configured to recall a specific operator type (avoiding having to first invoke the effect picker dialog). To do this, first insert the desired, specific operator type via the picker dialog. Then, press and hold the desk key (which should now show the type of the operator inserted). Alternatively, return to the "Configure Desk Matte Operators" dialog and use the "Default OFX Filter" or "Default Flexi Effect" dropdown.

The default for the key can be returned to the generic type by pressing and holding the desk key again (or from the dialog).

Once a specific Flexi/OFX operator type has been assigned to a desk key, the picker can still be used to select a different type by holding the "Ctrl" modifier while pressing the key.



### 레이어 매트 개선

이제 “매트 연산자(Matte Operators)” 그리드와 데스크의 스택 매니저(Stack Manager) 섹션에서 최대 4개의 매트 입력/채널에 직접 액세스하고 구성할 수 있습니다. 그리드에서는 “매트 연산자” 제목의 양쪽에 왼쪽 및 오른쪽 화살표 버튼이 추가되었습니다. 각 그리드 열(새 매트 입력 추가를 위해 예약된 마지막 열 제외)은 해당하는 매트 입력/채널 번호가 표시됩니다. 2개 이상의 매트 입력이 있는 경우 화살표 버튼을 사용해 2개의 열을 레이어의 매트 채널로 “스크롤”할 수 있습니다.

데스크에서 스택 매니저의 매트 병합 키를 누르고 있으면 레이어 상하 키가 깜빡입니다. 그런 다음, 이 키들을 사용하여 데스크의 2개 행(슬레이트에서는 1개 행) 매트 키를 레이어의 매트 채널로 “스크롤”할 수 있습니다. 버그 67417

사용되지 않는 매트 연산자는 그리드에서 연산자를 마우스 오른쪽 버튼으로 클릭하고 “그리드에서 XXX 연산자 제거” 메뉴 옵션을 선택해 “매트 연산자” 그리드에서 제거할 수 있습니다. 연산자는 커스터마이즈 메뉴에서 그리드에 다시 추가할 수 있습니다.

특정 OFX 필터 및 Flexi 이펙트 매트 연산자를 그리드의 기본 옵션으로 저장할 수 있습니다. 이를 통해 이펙트 선택 대화상자를 열지 않고도 레이어의 매트에 직접 삽입할 수 있습니다. 이를 위해 먼저 일반 연산자(OFX 필터 또는 Flexi 이펙트)를 선택한 후, 선택기를 사용해 필요한 특정 연산자를 삽입합니다. 그 후 그리드에서 일반 유형 위에 나타나는 연산자를 기본 옵션으로 저장하려면 커스터마이즈 메뉴의 “그리드에 매트 연산자 추가” 하위 메뉴를 사용하면 됩니다.

데스크 키에서 사용할 수 있는 매트(필터) 연산자는 이제 사용자 정의할 수 있습니다. 이는 매트 연산자 그리드의 커스터마이즈 메뉴에서 제공되는 “데스크 매트 연산자 구성” 대화상자를 통해 가능합니다. 이 대화상자에는 첫 번째 2개 매트(필터 연산자) 데스크 키를 나타내는 드롭다운이 있으며, 이를 통해 해당 키에 할당된 연산자를 선택할 수 있습니다.

선택된 연산자가 2개의 일반 유형(OFX 필터 또는 Flexi 이펙트) 중 하나인 경우, 해당 키를 특정 연산자 유형을 호출하도록 추가 구성할 수 있습니다(이펙트 선택 대화상자를 먼저 호출할 필요 없이). 이를 위해 먼저 선택 대화상자를 통해 원하는 특정 연산자 유형을 삽입합니다. 그런 다음, 데스크 키를 누르고 있으면(삽입된 연산자 유형이 표시됨), 또는 “데스크 매트 연산자 구성” 대화상자로 돌아가 “기본 OFX 필터” 또는 “기본 Flexi 이펙트” 드롭다운을 사용할 수 있습니다.

키의 기본 설정을 일반 유형으로 되돌리려면 키를 다시 누르고 있거나(또는 대화상자에서) 기본 설정으로 되돌릴 수 있습니다. 특정 Flexi/OFX 연산자 유형이 데스크 키에 할당된 경우, “Ctrl” 키를 누른 상태에서 키를 눌러 선택기를 통해 다른 유형을 선택할 수도 있습니다.



### Scope Enhancements&#x20;

Zoned Vectorscope/Chromaticity is a new scope view which shows three plots split based on luminance zones.

Clicking on the image shows a yellow cross only on the appropriate plot.

The zone thresholds can be set for each plot type from the right-click menu. For the CbCr vectorscope the default zone thresholds are at Y'=0.25 and Y'=0.75; for the chromaticity scopes the default zone thresholds are at -2 and +2 stops relative to 18% grey. Bug 65176

Chromaticity plots can now be rotated in the same way as the CbCr vectorscope. Bug 68050

The adjustment sliders in the Scope View right-click menus now have reset buttons. Bug 68846



### 스코프 향상

영역별 벡터스코프/색도(Zoned Vectorscope/Chromaticity)는 밝기 영역에 따라 세 개의 플롯을 나누어 보여주는 새로운 스코프 뷰입니다. 이미지를 클릭하면 해당 플롯에만 노란 십자가가 표시됩니다. 각 플롯 유형의 영역 임계값은 오른쪽 클릭 메뉴에서 설정할 수 있습니다. CbCr 벡터스코프의 기본 영역 임계값은 Y’=0.25 및 Y’=0.75이며, 색도 스코프의 기본 영역 임계값은 18% 회색을 기준으로 -2 및 +2 스톱입니다. 버그 65176

색도 플롯은 이제 CbCr 벡터스코프와 동일한 방식으로 회전할 수 있습니다. 버그 68050

스코프 뷰의 오른쪽 클릭 메뉴에 있는 조정 슬라이더에 이제 리셋 버튼이 추가되었습니다. 버그 68846



### Miscellaneous&#x20;

DNxHR codecs in MXF and QuickTime deliverables now support RGBA/YCCA channels, for including opacity (alpha) data in renders. Bug 68400

IMF and Broadcast Contribution Profile JPEG 2000 can now be rendered using custom bitrates, as well as constant bitrate (CBR). Bug 68286

Invalid settings for IMF and Broadcast Contribution Profile JPEG 2000 deliverables now show a warning in Render View and during render verification. Bug 55911

Added a new (icon) button that simplifies configuring a layer to grade the raw image on top of the layer(s) above. This is typically combined with a matte to specify the area of the raw image to reveal/grade. A layer configured this way provides similar functionality to "layer mixer" mode in other systems.

If the Ctrl (Cmd on a Mac) modifier is held when the mode is activated, an explicit "Blend Source" reference (to the raw image) is added above the layer. This allows more complex grades to be applied to the raw image by inserting additional grade layers directly below the Blend Source.

The button is located in a layer's "Result Blending" section, to the right of the blend type dropdown. Bug 68771

Added 65x65x65 option for LUT generation. Bug 63113

MXF and QuickTime raw metadata now includes additional information about DNx codecs. Bug 68764

Added support for reading "User Comment" metadata in JPEG files. Bug 69156

Added "With Filename If No Tape Name" to Overwrite Tape Name conform option, to support updating the tape name only when it is empty. Bug 63867

Additional metadata is now read from PNG media. PNG files whose metadata identifies them as sRGB are now assigned an sRGB colour space by default. Bug 69254

Colour spaces in opened scenes that are different from any colour spaces known to the application are no longer written out to .flspace files in /vol/.support/etc/colourspaces because that is rarely useful and causes clutter in colour space menus. Instead these spaces are indicated with a scene icon in menus, and are available for use in other open scenes until you quit the application. Bug 68763

The R3D Params operator now supports Extended Highlights for RED media from cameras which support Extended Highlights (e.g. V-RAPTOR \[X]). Decoding with Extended Highlights requires a lot of GPU memory so may fail on systems with smaller GPUs. Bug 69169

Added support for reading HDE-compressed ARRIRAW MXF files from older (pre-ALEXA 35) cameras. Bug 69213

Updated the conform behaviour of transforms in an AAF so that it sets the interpolation mode read from the AAF. Bug 61149

When running in REMOTE mode, the IP address of the machine hosting the Blackboard Classic, Slate or Tangent control panels can now be determined automatically for systems using NICE DCV or HP Anyware/PCoIP.

REMOTE mode can be enabled by setting "Auto-detect REMOTE Mode" in the "REMOTE" section of the "System" page in Baselight Preferences.

Tangent Element and Wave panels are also supported when running Baselight via remote desktop.

The IP address of the machine hosting the Tangent control panels can either be specified via the "Remote USB server IP Address" setting in Preferences, or determined automatically when using NICE DCV or HP Anyware/PCoIP if REMOTE mode is enabled. Bug 69648

Added support to copy and paste AAF/XML Shot ID Metadata. When replacing media in a scene conformed from an AAF or XML, the metadata allowing Baselight to associate a shot with its equivalent event in the AAF/XML file could be lost. The Edit menu items "Copy AAF/XML Shot ID Metadata" and "Paste AAF/XML Shot ID Metadata" allows the metadata to be copied from the selected strip to the replacement strip, this allows media to be replaced in the scene and still maintain the Modify AAF/XML workflow.

The new 'Has AAF/XML Shot ID Metadata' column in Shots View can be used to check if a shot contains metadata. Bug 63830

Added 'get\_channels' to the FLAPI 'SequenceDescriptor' class. When called on OpenEXR media, it will return an array of all channel names. Bug 69723

Added 'update\_matte\_references' to the FLAPI 'Shot' class. This method updates matte channel names in any Reference operators within the Shot. Bug 69735



### 기타 사항



MXF 및 QuickTime 전달 형식에서 DNxHR 코덱이 이제 RGBA/YCCA 채널을 지원하여 렌더링에 불투명도(알파) 데이터를 포함할 수 있습니다. 버그 68400



IMF 및 방송 기여 프로필(Broadcast Contribution Profile) JPEG 2000은 이제 사용자 정의 비트레이트 및 일정 비트레이트(CBR)로 렌더링할 수 있습니다. 버그 68286

IMF 및 방송 기여 프로필 JPEG 2000 전달 형식의 유효하지 않은 설정은 렌더 뷰 및 렌더 검증 중 경고로 표시됩니다. 버그 55911



레이어에서 상위 레이어의 원본 이미지를 등급 조정할 수 있도록 설정하는 간단한 (아이콘) 버튼이 추가되었습니다. 이는 일반적으로 원본 이미지의 특정 영역을 나타내기 위한 매트와 결합됩니다. 이렇게 구성된 레이어는 다른 시스템의 “레이어 믹서” 모드와 유사한 기능을 제공합니다.

이 모드를 활성화할 때 Ctrl(맥에서는 Cmd) 수정 키를 누르고 있으면, 레이어 상단에 명시적인 “Blend Source”(원본 이미지에 대한 참조)가 추가됩니다. 이를 통해 Blend Source 아래에 추가 등급 레이어를 삽입하여 원본 이미지에 더 복잡한 등급 조정을 적용할 수 있습니다. 이 버튼은 레이어의 “Result Blending” 섹션에서 혼합 유형 드롭다운 오른쪽에 있습니다. 버그 68771



LUT 생성을 위한 65x65x65 옵션이 추가되었습니다. 버그 63113



MXF 및 QuickTime 원본 메타데이터에 DNx 코덱에 대한 추가 정보가 포함됩니다. 버그 68764



JPEG 파일의 “사용자 코멘트” 메타데이터 읽기 지원이 추가되었습니다. 버그 69156



“테이프 이름 덮어쓰기” 옵션에 “테이프 이름이 없으면 파일 이름 사용” 기능이 추가되어 테이프 이름이 비어 있을 때만 업데이트할 수 있도록 지원합니다. 버그 63867



PNG 미디어에서 추가 메타데이터를 읽을 수 있습니다. 메타데이터에서 sRGB로 식별된 PNG 파일은 기본적으로 sRGB 색상 공간으로 할당됩니다. 버그 69254



열린 장면의 색상 공간이 애플리케이션에서 알고 있는 색상 공간과 다를 경우, 해당 색상 공간이 .flspace 파일로 저장되지 않습니다(/vol/.support/etc/colourspaces). 이는 색상 공간 메뉴에 불필요한 항목이 추가되는 것을 방지하기 위함이며, 대신 해당 공간이 메뉴에서 장면 아이콘으로 표시되어 다른 열린 장면에서 애플리케이션을 종료할 때까지 사용할 수 있습니다. 버그 68763

\


R3D 파라미터 연산자는 이제 Extended Highlights를 지원하는 RED 카메라(예: V-RAPTOR \[X]) 미디어에 대해 Extended Highlights를 지원합니다. Extended Highlights로 디코딩하려면 많은 GPU 메모리가 필요하므로 메모리가 작은 GPU에서는 실패할 수 있습니다. 버그 69169

\


이전 카메라(Pre-ALEXA 35)에서 생성된 HDE 압축 ARRIRAW MXF 파일 읽기 지원이 추가되었습니다. 버그 69213

\


AAF에서 변환의 동작이 업데이트되어 AAF에서 읽어들인 보간 모드를 설정할 수 있도록 했습니다. 버그 61149



REMOTE 모드 실행 시 Blackboard Classic, Slate 또는 Tangent 제어 패널을 호스팅하는 머신의 IP 주소가 NICE DCV 또는 HP Anyware/PCoIP를 사용하는 시스템에서 자동으로 감지될 수 있습니다. REMOTE 모드는 Baselight Preferences의 “System” 페이지에서 “REMOTE” 섹션에 있는 “Auto-detect REMOTE Mode” 설정을 통해 활성화할 수 있습니다.



Baselight를 원격 데스크톱에서 실행할 때 Tangent Element 및 Wave 패널도 지원됩니다. Tangent 제어 패널을 호스팅하는 머신의 IP 주소는 Preferences의 “Remote USB server IP Address” 설정을 통해 지정하거나, NICE DCV 또는 HP Anyware/PCoIP를 사용할 때 REMOTE 모드가 활성화된 경우 자동으로 감지할 수 있습니다. 버그 69648



AAF/XML 샷 ID 메타데이터를 복사 및 붙여넣는 기능이 추가되었습니다. AAF 또는 XML에서 컨포밍된 장면의 미디어를 교체할 때, Baselight가 샷을 AAF/XML 파일의 해당 이벤트와 연관시키는 메타데이터가 손실될 수 있습니다. “Edit” 메뉴의 “Copy AAF/XML Shot ID Metadata” 및 “Paste AAF/XML Shot ID Metadata” 항목을 통해 선택한 스트립에서 교체할 스트립으로 메타데이터를 복사하여 장면의 미디어를 교체하면서도 AAF/XML 워크플로우를 유지할 수 있습니다. Shots View에 새로 추가된 ‘Has AAF/XML Shot ID Metadata’ 열을 사용해 샷에 메타데이터가 포함되어 있는지 확인할 수 있습니다. 버그 63830



OpenEXR 미디어에서 모든 채널 이름 배열을 반환하는 FLAPI의 ‘SequenceDescriptor’ 클래스에 ‘get\_channels’가 추가되었습니다. 버그 69723



FLAPI의 ‘Shot’ 클래스에 ‘update\_matte\_references’가 추가되어 Shot 내의 Reference 연산자에 있는 매트 채널 이름을 업데이트할 수 있습니다. 버그 69735



## Bug Fixes Since Baselight 6.0.21211&#x20;

Boost Contrast with large Scale is faster. Bug 62973

Improved GPU JPEG 2000 accelerated compression speed for high resolution deliverables. This also fixes an issue where acceleration was not used when rendering image sequences to remote volumes. Bug 67783

Fixed channel naming when rendering to single-channel OpenEXR deliverables. Bug 68364

The fl-diag hostname test is now compatible with the zoneless-hostnames option in cloud.cfg. Bug 68657

The fl-diag cloud test now accepts the 'nara' flag for ws hosts in cloud.cfg. Bug 68862

fl-fsr no longer ignores sequences which have extended attributes. Bug 68698

Fixed crash in Presets View when the current strip is shorter than other strips in the stack. Bug 68659

Jobs can no longer be created with, or renamed to, an empty name. Bug 68776

Fixed crash rendering XAVC or XDCAM codecs in Sony MXF. Bug 23576

Fixed issues with metadata in Cuts View, for example the Text operator. Bug 68966

Fixed crash exporting LUTs in some situations. Bug 68723

Improved the performance of Gallery and Shots View when nothing relevant has changed. Bug 68498

Fixed various Image Viewer/Clean Output related bugs in Stereo and Dual Output display layouts. Bug 67929

Fixed various Image Viewer/Clean Output related bugs in Dual Colour Space display layouts. Bug 67877

In bl-config-xorg with the -v option it now prints out the command line used to determine which control surface is connected. Bug 69091

Fixed Image Viewer updating of custom mouse pointer and showing/hiding of previous strokes when setting a clone brush offset in Paint. Bug 67932

Fixed behaviour of %{SceneNameOnly} token in Render View and Reports View with scenes nested in more than one folder. Bug 69130

Fixed issue where if overlays were disabled in the Transform operator UI, they would still appear/flash on the image when the operator was deselected. Bug 69131

Fixed crash if a Matchbox/ShaderToy GLSL file cannot be opened. Bug 69100

Fixed crash when a ProRes RAW Params operator is selected when quitting the application. Bug 66276

Edge Crop now shows more precision for "Current Aspect Ratio". Bug 69188

The icon used for Client Sessions has been updated. Bug 69284

Added 8k formats to bl-benchmark. Bug 59634

Improved error messages when a licence cannot be obtained. Bug 69334

Suppressed warnings about storage fragmentation when accessing solid-state media. Bug 69322

Fixed unnecessary re-caching of cached strips caused by changes below them in the grading stack. Bug 69381

Fixed crash on starting Matte Tool if the default config was damaged. Bug 69455

Fixed layer matte viewing modes when used in conjunction with explicit strip caching (the cache wasn't being used). Bug 69416

Fixed Kona 5 firmware switching on macOS. Bug 69485

Fixed issue where GPU JPEG 2000 acceleration could incorrectly be shown as unlicensed in the About dialog. Bug 69422

Fixed issue with renders using GPU JPEG 2000 acceleration at resolutions higher than UHD. Bug 68914

Fixed issue reading QuickTime movies containing unused fragments. Bug 69570

Console warnings about "Fma" from the ARRI Image SDK are no longer seen. Bug 69019

Fixed issue where drawing the face overlays on very long shots would take a long time. Bug 69523

Fixed issues with BLGs exported from Dolby Vision scenes. Bug 59952

Fixed "Too many connection values" error when loading some scenes saved in older versions. Bug 68517

Fixed crash on macOS when Display View has a very large zoom-in. Bug 67806

Prevented the cache state of input strips from being copied to the destination. Bug 69488

Fixed issue where the render service (on FLUX Store and Baselight RENDER system) would not relaunch itself after an error. Bug 60823

Fixed Pane Description getting stuck in the 'Scratchpad Original Version'. Bug 69266

Fixed incorrect behaviour in Shader operators when using the "Output Alpha: From Shader" option. Bug 69662

Fixed crash when a corrupt TIFF file is encountered. Bug 57949

Fixed error crosses in the Image Viewer having a random colour unless the Setup's Error Cross Colour was changed. Bug 69797

Fixed slight green shift on some thumbnails, notably Apple ProRes 4444. Bug 68589

Fixed Colour Crosstalk operator not being included in LUT Export. Bug 69214

Fixed an issue where shots before or after the DBS in the Gallery could no longer be selected by holding the 'Select' button and a directional arrow on a Blackboard or Slate. Bug 69415



## 버그 수정 (Baselight 6.0.21211 이후)

• 큰 스케일로 Boost Contrast 사용 시 속도가 빨라졌습니다. 버그 62973

• 고해상도 전달물의 GPU JPEG 2000 가속 압축 속도가 개선되었습니다. 이미지 시퀀스를 원격 볼륨으로 렌더링할 때 가속이 적용되지 않는 문제도 해결되었습니다. 버그 67783

• 단일 채널 OpenEXR 전달물로 렌더링할 때 채널 이름 지정이 수정되었습니다. 버그 68364

• fl-diag의 hostname 테스트가 cloud.cfg의 zoneless-hostnames 옵션과 호환되도록 업데이트되었습니다. 버그 68657

• fl-diag의 클라우드 테스트에서 cloud.cfg의 ws 호스트에 대해 ‘nara’ 플래그를 허용합니다. 버그 68862

• fl-fsr이 확장 속성이 있는 시퀀스를 무시하지 않도록 수정되었습니다. 버그 68698

• 현재 스트립이 스택 내 다른 스트립보다 짧을 때 Presets View에서 발생하는 충돌이 수정되었습니다. 버그 68659

• 빈 이름으로 작업을 생성하거나 이름을 변경할 수 없도록 수정되었습니다. 버그 68776

• Sony MXF에서 XAVC 또는 XDCAM 코덱을 렌더링할 때 발생하는 충돌이 수정되었습니다. 버그 23576

• Cuts View의 메타데이터 관련 문제(예: 텍스트 연산자) 수정. 버그 68966

• 특정 상황에서 LUT 내보내기 시 발생하는 충돌이 수정되었습니다. 버그 68723

• Gallery 및 Shots View의 성능이 개선되었습니다(관련 변경 사항이 없을 때). 버그 68498

• Stereo 및 Dual Output 디스플레이 레이아웃에서 Image Viewer/Clean Output 관련 다양한 버그가 수정되었습니다. 버그 67929

• Dual Colour Space 디스플레이 레이아웃에서 Image Viewer/Clean Output 관련 다양한 버그가 수정되었습니다. 버그 67877

• bl-config-xorg의 -v 옵션이 연결된 제어 표면을 결정하는 명령줄을 출력하도록 수정되었습니다. 버그 69091

• Paint에서 클론 브러시 오프셋을 설정할 때 사용자 지정 마우스 포인터 업데이트 및 이전 스트로크 표시/숨기기 관련 문제가 수정되었습니다. 버그 67932

• Render View 및 Reports View에서 %{SceneNameOnly} 토큰의 동작이 수정되었습니다(여러 폴더에 중첩된 장면에 대해). 버그 69130

• Transform 연산자 UI에서 오버레이를 비활성화해도 연산자를 선택 해제할 때 이미지에 오버레이가 나타나는 문제가 수정되었습니다. 버그 69131

• Matchbox/ShaderToy GLSL 파일을 열 수 없을 때 발생하는 충돌이 수정되었습니다. 버그 69100

• 애플리케이션 종료 시 ProRes RAW Params 연산자를 선택할 때 발생하는 충돌이 수정되었습니다. 버그 66276

• Edge Crop에서 “Current Aspect Ratio”의 정확도가 향상되었습니다. 버그 69188

• 클라이언트 세션에 사용되는 아이콘이 업데이트되었습니다. 버그 69284

• bl-benchmark에 8k 포맷이 추가되었습니다. 버그 59634

• 라이선스를 획득할 수 없을 때의 오류 메시지가 개선되었습니다. 버그 69334

• SSD 미디어에 액세스할 때 저장소 단편화 경고가 억제되었습니다. 버그 69322

• 그레이딩 스택의 하단에서 변경이 발생했을 때 캐시된 스트립이 불필요하게 다시 캐시되는 문제가 수정되었습니다. 버그 69381

• Matte Tool을 시작할 때 기본 설정이 손상된 경우 발생하는 충돌이 수정되었습니다. 버그 69455

• 레이어 매트 보기 모드와 명시적 스트립 캐싱을 함께 사용할 때 캐시가 사용되지 않는 문제가 수정되었습니다. 버그 69416

• macOS에서 Kona 5 펌웨어 전환 문제가 수정되었습니다. 버그 69485

• GPU JPEG 2000 가속 기능이 About 대화상자에서 라이선스 미보유로 잘못 표시되는 문제가 수정되었습니다. 버그 69422

• UHD 이상의 해상도에서 GPU JPEG 2000 가속 기능을 사용하는 렌더링 문제 수정. 버그 68914

• 사용되지 않는 프래그먼트를 포함하는 QuickTime 무비 읽기 문제 수정. 버그 69570

• ARRI Image SDK의 “Fma”와 관련된 콘솔 경고가 더 이상 표시되지 않도록 수정되었습니다. 버그 69019

• 매우 긴 샷에서 얼굴 오버레이를 그리는 시간이 오래 걸리는 문제 수정. 버그 69523

• Dolby Vision 장면에서 내보낸 BLGs 관련 문제 수정. 버그 59952

• 이전 버전에서 저장된 일부 장면을 로드할 때 발생하는 “Too many connection values” 오류 수정. 버그 68517

• macOS에서 Display View의 확대가 매우 큰 경우 발생하는 충돌 수정. 버그 67806

• 입력 스트립의 캐시 상태가 대상에 복사되지 않도록 방지. 버그 69488

• 렌더 서비스(FLUX Store 및 Baselight RENDER 시스템)가 오류 후 자동으로 재시작되지 않는 문제 수정. 버그 60823

• Scratchpad Original Version에 Pane Description이 고정되는 문제 수정. 버그 69266

• Shader 연산자에서 “Output Alpha: From Shader” 옵션 사용 시 발생하는 동작 오류 수정. 버그 69662

• 손상된 TIFF 파일을 만나면 발생하는 충돌 수정. 버그 57949

• Image Viewer의 오류 교차 표시가 Setup의 Error Cross Colour를 변경하지 않으면 임의의 색상을 가지는 문제 수정. 버그 69797

• 일부 썸네일(특히 Apple ProRes 4444)에서 약간의 녹색 색조가 나타나는 문제 수정. 버그 68589

• LUT 내보내기에 Colour Crosstalk 연산자가 포함되지 않는 문제 수정. 버그 69214

• Gallery에서 DBS 전후의 샷을 Blackboard 또는 Slate에서 ‘Select’ 버튼과 방향 화살표를 눌러 선택할 수 없게 되는 문제 수정. 버그 69415



## Known Issues&#x20;

Internal Image Viewer on MacOS is now tagged as sRGB Display. To get accurate colour reproduction on MacOS, the cursor colour space must be set to sRGB Display: 2.2 Gamma / Rec.709 in all cases. Previously, the viewing colour space needed to match the physical calibration of the attached monitor. Bug 69661

Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237

Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

Open System Preferences from the Dock or the Apple menu Choose "Security & Privacy" Click the padlock icon and use your password or Touch ID to allow changes to be made Select "Full Disk Access" in the list on the left Click the + button on the right to open a file browser On your keyboard, press / to open the "Go to the folder" dialog Enter /sbin and click Go Select the file called nfsd and click Open After restarting your Mac, the volume(s) should now work correctly. Bug 62601

The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798

Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406

Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016

Using "Network Stream" as the Primary Video Output on Intel Mac Pro systems with AMD GPUs is currently unsupported. This will be addressed in a future release of Baselight 6.0. Bug 68727





## 알려진 문제

• macOS의 내부 이미지 뷰어가 이제 sRGB 디스플레이로 태그되었습니다. macOS에서 정확한 색상 재현을 위해, 커서 색상 공간을 항상 sRGB 디스플레이: 2.2 감마 / Rec.709로 설정해야 합니다. 이전에는 연결된 모니터의 물리적 캘리브레이션과 일치하는 보기 색상 공간이 필요했습니다. 버그 69661

• macOS 13 Ventura를 실행하는 Intel macOS 시스템에서 특히 RED 및 ARRIRAW 미디어를 사용할 때 심각한 이미지 손상이 발생합니다. 이는 macOS 14 Sonoma에서 해결된 것으로 보입니다. 버그 62237

• macOS 시스템에서 공유된 볼륨이 원격 시스템에서 접근할 때 macOS의 버그로 인해 실패할 수 있습니다. 이 문제를 해결하려면:

1\. Dock 또는 Apple 메뉴에서 시스템 환경설정을 엽니다.

2\. “보안 및 개인정보”를 선택합니다.

3\. 자물쇠 아이콘을 클릭하고 암호 또는 Touch ID를 사용해 변경을 허용합니다.

4\. 왼쪽 목록에서 “전체 디스크 접근”을 선택합니다.

5\. 오른쪽의 + 버튼을 클릭하여 파일 브라우저를 엽니다.

6\. 키보드에서 /를 눌러 “폴더로 이동” 대화 상자를 엽니다.

7\. /sbin을 입력하고 이동을 클릭합니다.

8\. nfsd 파일을 선택하고 열기를 클릭합니다.

9\. Mac을 재시작한 후, 볼륨이 올바르게 작동해야 합니다. 버그 62601

• Relight 연산자는 현재 글로벌 스케일을 설정할 때 드래그 시 예상치 못한 동작을 보입니다. 버그 63798

• Blackboard Classic 제어 표면은 연산자 간 전환 시 간헐적으로 깜빡임 현상이 발생합니다. 이는 향후 베타 릴리스에서 수정될 예정입니다. 버그 62406

• RIFE ML Retime(시퀀스 또는 Retime 연산자에서 사용) 샷은 “작업 형식으로 처리”가 선택된 것처럼 동작합니다. 이로 인해 렌더링 형식이 작업 형식보다 큰 경우 낮은 품질의 출력이 발생할 수 있으며, 이러한 샷은 이미지를 작업 형식으로 자릅니다. 버그 66016

• AMD GPU가 장착된 Intel Mac Pro 시스템에서 “네트워크 스트림”을 주 비디오 출력으로 사용하는 것은 현재 지원되지 않습니다. 이는 향후 Baselight 6.0 릴리스에서 해결될 예정입니다. 버그 68727

