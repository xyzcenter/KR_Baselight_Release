# 베이스라이트 릴리즈 노트 5.2.12424 (2019-10-11)

## 버그 개선 ( Baselight 5.2.12393이후)&#x20;

* Fixed an issue with dual network link discovery which caused file copy to use a slow interface in error \[bug 52633]\
  **듀얼 네트워트 링크 검색문제로 인해서 파일 복사에 오류가 발생되었을때 느린 인터페이스를 사용하는 문제가 해결**
* Fixed transfer service (flit-daemon) out-of-memory termination when copying a large file to another location on the same machine (typically to or from a SAN) \[bug 52839]\
  **대용량 파일 복사를 같은 시스템에서 다른 장소(특히 SAN으로 또는 SAN으로 부터) 복사할 때 전송서비스(FLIT 데몬)의 메모리 부족 문제 해결**
* Fixed an occasional hang in file copy \[bug 52856]\
  파일 복사 도중에 가끔씩 멈추는(Hang) 현상 수정
* Fixed inability to use FLIT copying to or from media mounted on the UI host of a Baselight TWO/X \[bug 52891]\
  ** 베이스라이트 TWO/X의 호스트피씨에 마운트된 미디어에서 또는 미디어로 FLIT 복사를 사용하지 못하는 문제 해결**
* Fixed an issue where reconstruction of 4:2:2 or 4:2:0 Y'CbCr data was incorrect in some codecs. This produced lines along the sides and slightly changed the colour of the resulting image \[bug 52917]\
  **일부 코덱에서 422 또는 420 Y'CbCr data를 올바르지 않게 구성하는 이슈를 수정. 이로 인해서 측면을 따라서 결과 이미지와 다른 선이 생기는 문제가 있었습니다.**
