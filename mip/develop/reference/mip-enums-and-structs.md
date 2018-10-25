---
title: 요약
description: 요약
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5af209d5a627263399c8c60f474495dcadab24a0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446501"
---
# <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
**공용** |
enum Consent       |  서비스 엔드포인트에 연결하기 위해 동의를 요청하는 경우 사용자의 응답입니다.
struct ApplicationInfo  |  응용 프로그램 특정 정보를 포함하는 구조체입니다.
**mip** |
enum ErrorType       | _아직 문서화되지 않았습니다._
enum HttpRequestType       |  HTTP 요청 유형입니다.
enum LogLevel       |  MIP SDK에서 사용되는 여러 로그 수준입니다.
enum ProtectionHandlerCreationOptions       |  추가 정책 생성 동작을 지시하는 비트 플래그입니다.
enum ProtectionType       |  보호가 템플릿 또는 임시(사용자 지정) 정책을 기반으로 하는지 여부를 기술합니다.
enum ActionType       |  다양한 동작 유형입니다.
struct mip::PublishingLicenseContext | 보호 처리기를 만드는 데 사용되는 게시 라이선스의 세부 정보를 포함합니다.

  
## <a name="enumerations-common"></a>열거형(공통)
  
### <a name="consent"></a>Consent
서비스 엔드포인트에 연결하는 데 동의하는 사용자 결정을 나타냅니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
AcceptAlways            | 동의하고 이 결정을 기억합니다.
동의            | 한 번만 동의합니다.
거부            | 동의하지 않습니다.
  
## <a name="enumerations-mip"></a>열거형(mip)

### <a name="actiontype"></a>ActionType

다양한 동작 유형입니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | 문서 동작 유형에 콘텐츠 바닥글을 추가합니다.
ADD_CONTENT_HEADER            | 문서 동작 유형에 콘텐츠 헤더를 추가합니다.
ADD_WATERMARK            | 전체 문서 동작 유형에 워터마크를 추가합니다.
사용자 지정            | 사용자 지정 동작 유형입니다.
JUSTIFY            | 근거 제공 동작 유형입니다.
METADATA            | 메타 데이터 변경 동작 유형입니다.
PROTECT_ADHOC            | 임시 정책 기반의 보호 동작 유형입니다.
PROTECT_BY_TEMPLATE            | 템플릿 기반의 보호 동작 유형입니다.
PROTECT_DO_NOT_FORWARD            | 전달 금지 기반의 보호 동작 유형입니다.
REMOVE_CONTENT_FOOTER            | 콘텐츠 바닥글 동작 유형을 제거합니다.
REMOVE_CONTENT_HEADER            | 콘텐츠 헤더 동작 유형을 제거합니다.
REMOVE_PROTECTION            | 보호 동작 유형을 제거합니다.
REMOVE_WATERMARK            | 워터마크 동작 유형을 제거합니다.
APPLY_LABEL            | 레이블 적용 동작 유형입니다.
RECOMMEND_LABEL            | 레이블 권장 동작 유형입니다.

CUSTOM은 일반 동작 유형입니다. 모든 동작 유형은 특정 의미가 있는 특정 작업입니다.

다음 연산자를 사용하여 ActionType 값을 조합할 수 있습니다.

- [동작](class_mip_action.md)에 대한 And(&) 연산자(`operator &(ActionType a, ActionType b)`)
- [동작](class_mip_action.md)에 대한 Logical Or(Xor)(^) 연산자 (`operator ^(ActionType a, ActionType b)`)


### <a name="errortype"></a>ErrorType
 값                         | 설명                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | 호출자가 잘못된 입력을 전달했습니다.
FILE_IO_ERROR            | 일반 파일 IO 오류입니다.
NETWORK_ERROR            | 일반 네트워크 문제입니다(예: 연결할 수 없는 서비스).
TRANSIENT_NETWORK_ERROR            | 일시적인 네트워크 문제(예: 잘못된 게이트웨이)입니다.
INTERNAL_ERROR            | 예기치 않은 내부 오류입니다. 예: 클라이언트 - 서버 프로토콜에서 발생하는 오류(예기치 않은 응답 수신)
JUSTIFICATION_REQUIRED            | 파일에 대한 작업을 완료하려면 근거를 제공해야 합니다.
NOT_SUPPORTED_OPERATION            | 요청한 작업이 지원되지 않습니다.
PRIVILEGED_REQUIRED            | 새 레이블 메서드가 표준일 때 권한이 부여된 레이블을 재정의할 수 없습니다.
ACCESS_DENIED            | 사용자가 콘텐츠에 액세스할 수 없습니다. 예: 권한 없음, 콘텐츠가 취소됨 등
CONSENT_DENIED            | 사용자 동의가 필요한 작업에 동의가 부여되지 않았습니다.
  
### <a name="httprequesttype"></a>HttpRequestType
HTTP 요청 유형입니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
get            | GET
Post            | POST
  
### <a name="loglevel"></a>로그 수준

MIP SDK에서 사용되는 여러 로그 수준입니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
추적            | 
정보            | 
경고            | 
오류            | 
mip sdk에서 사용되는 여러 로그 레벨입니다.
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

추가 정책 생성 동작을 지시하는 비트 플래그입니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
없음            | 없음
OfflineOnly            | UI 및 네트워크 작업을 허용하지 않습니다.
AllowAuditedExtraction            | 콘텐츠는 비보호 SDK 인식 앱에서 열 수 있습니다.
PreferDeprecatedAlgorithms            | 이전 버전과의 호환성을 위해 더 이상 사용되지 않는 암호 알고리즘(ECB)을 사용합니다.


### <a name="protectiontype"></a>ProtectionType
보호가 템플릿 또는 임시(사용자 지정) 정책을 기반으로 하는지 여부를 기술합니다.

 값                         | 설명                                
--------------------------------|---------------------------------------------
TemplateBased            | 핸들이 템플릿에서 생성되었습니다.
사용자 지정            | 핸들이 임시로 생성되었습니다.

  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions
ProtectionHandlerCreationOptions 비트 OR 연산자입니다.

매개 변수:  
* **a**: 왼쪽 값 

* **b**: 오른쪽 값

### <a name="releaseallresources"></a>ReleaseAllResources
종료하기 전에 모든 리소스(예: 스레드)를 해제합니다.
MIP 동적 라이브러리가 응용 프로그램에 의해 지연 로드되는 경우 응용 프로그램이 이 MIP 라이브러리를 명시적으로 언로드하기 전에 교착 상태를 방지하기 위해 이 함수를 호출해야 합니다. 예를 들어 win32에서 FreeLibrary 또는 \__FUnloadDelayLoadedDLL2를 통해 명시적으로 MIP DLL을 언로드하는 호출이 발생하기 전에 이 함수를 호출해야 합니다. 응용 프로그램에서 이 함수를 호출하기 전에 모든 MIP 개체(예: 프로필, 엔진, 처리기)에 대한 참조를 해제해야 합니다.
  
**반환**: 매개 변수의 비트 OR
  
## <a name="structures"></a>구조

### <a name="applicationinfo"></a>ApplicationInfo 
응용 프로그램 특정 정보를 포함하는 구조체입니다.

 필드                        | 설명                                
--------------------------------|---------------------------------------------
 public std::string applicationId  |  Azure AD 포털에서 설정된 응용 프로그램 식별자입니다.
 public std::string applicationName  |  응용 프로그램 이름
 public std::string applicationVersion  |  사용 중인 응용 프로그램의 버전입니다.
  
### <a name="mippublishinglicensecontext"></a>mip::PublishingLicenseContext 
보호 처리기를 만드는 데 사용되는 게시 라이선스의 세부 정보를 포함합니다.
  
 필드                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector<uint8_t> licenseInfo  | _아직 문서화되지 않았습니다._
public const std::vector<uint8_t> serializedPublishingLicense  | _아직 문서화되지 않았습니다._
public PublishingLicenseContext(const std::vector<uint8_t>& licenseInfo, const std::vector<uint8_t>& serializedPublishingLicense)  | _아직 문서화되지 않았습니다._
  
