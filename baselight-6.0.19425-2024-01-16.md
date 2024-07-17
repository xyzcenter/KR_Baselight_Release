# 😀 Baselight 릴리스 6.0.19425 (2024-01-16)

### Bug Fixes Since Baselight 6.0.19342

* Fixed rendering failure with some BRAW media. Bug 66987
* Fixed issue where the Presets View would list all presets saved from OFX effects in the same page, and a similar issue for presets saved from Shader effects.\
  **Important: This change will remove access to previously saved OFX and Shader presets**. Bug 65999
* Fixed flit service (used for FLUX Manage file copies) on macOS 14 Sonoma. Bug 67023
* Fixed crash in Dolby Vision Analysis of a Dissolve to or from black. Bug 67030

### 버그 수정 사항 (Baselight 6.0.19342 이후)

* 일부 BRAW 미디어의 렌더링 실패 문제를 수정했습니다. (버그 66987)
* 프리셋 뷰에서 OFX 효과로 저장된 모든 프리셋이 같은 페이지에 나열되는 문제와 Shader 효과로 저장된 프리셋과 관련된 유사한 문제를 수정했습니다. 중요한: 이 변경으로 인해 이전에 저장된 OFX 및 Shader 프리셋에 접근할 수 없습니다. (버그 65999)
* macOS 14 Sonoma에서 FLUX Manage 파일 복사에 사용되는 flit 서비스를 수정했습니다. (버그 67023)
* 검정색으로의 또는 검정색에서의 디졸브에 대한 Dolby Vision Analysis에서 발생하는 크래시를 수정했습니다. (버그 67030)
