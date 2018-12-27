---
title: C++용 MIP SDK(미리 보기) 참조
description: C++용 MIP SDK(미리 보기) 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06d8bb26a8e3026562006d68d4ae8d1630eba81c
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446331"
---
# <a name="mip-sdk-for-c-preview-reference"></a>C++용 MIP SDK(미리 보기) 참조

C++용 MIP(Microsoft Information Protection) SDK(미리 보기)를 사용하여 개발자는 데이터 보호 정책을 관리하고 데이터 및 기타 디지털 자산에 적용할 수 있습니다.  

자세한 내용은 [MIP 개발자 블로그](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->를 참조하세요.

C++에 대한 MIP SDK에는 다음이 포함됩니다.

- [열거형 및 구조체](mip-enums-and-structs.md)
- [Functions (함수)](mip-functions.md)
- 다음 클래스:

| 클래스 이름 | 설명 |
| :----------|:------------|
[AccessDeniedError](class_mip_accessdeniederror.md)  |  사용자가 콘텐츠에 액세스할 수 없습니다. 예: 권한 없음, 콘텐츠가 취소됨
[작업](class_mip_action.md)  |  동작에 대한 인터페이스입니다. 각 작업은 애플리케이션이 레이블(정책에 정의된 대로)을 적용하는 데 필요한 단계로 변환됩니다.
[AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  문서에 콘텐츠 바닥글을 추가하도록 지정하는 동작 클래스입니다.
[AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  콘텐츠 헤더를 추가하도록 지정하는 동작 클래스입니다.
[AddWatermarkAction](class_mip_addwatermarkaction.md)  |  워터마크를 추가하도록 지정하는 동작 클래스입니다.
[ApplyLabelAction](class_mip_applylabelaction.md)  |  레이블 적용 동작에 따라 호출 애플리케이션은 특정 레이블을 적용해야 합니다.
[BadInputError](class_mip_badinputerror.md)  |  잘못된 입력 오류입니다. SDK API에 대한 입력이 잘못된 경우에 이 오류가 throw됩니다.
[ClassificationResult](class_mip_classificationresult.md)  |  실행 상태에서 분류 호출의 결과를 포함하는 클래스입니다.
[ConsentDelegate](class_consentdelegate.md)  |  동의 관련 작업에 대한 대리자입니다.
[ConsentDeniedError](class_mip_consentdeniederror.md)  |  사용자 동의가 필요한 작업에 동의가 부여되지 않았습니다.
[ContentLabel](class_mip_contentlabel.md)  |  콘텐츠 조각, 일반적으로 문서에 적용되는 Microsoft Information Protection 레이블의 추상화입니다.
[CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md)은 동작의 모든 하위 속성을 속성 모음으로 캡처하는 일반 동작 클래스입니다. 호출자는 동작의 의미를 이해해야 합니다.
[오류](class_mip_error.md)  |  MIP SDK에서 보고(throw 또는 반환)되는 모든 오류의 기본 클래스입니다.
[ExecutionState](class_mip_executionstate.md)  |  엔진을 실행하는 데 필요한 모든 상태에 대한 인터페이스입니다.
[FileEngine::Settings](class_mip_fileengine_settings.md)  | _아직 문서화되지 않았습니다._
[FileEngine](class_mip_fileengine.md)  |  이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
[FileHandler::Observer](class_mip_filehandler_observer.md)  |  클라이언트가 파일 처리기 관련 알림 이벤트를 가져오기 위한 [Observer](class_mip_filehandler_observer.md) 인터페이스입니다.
[FileHandler](class_mip_filehandler.md)  |  모든 파일 처리 함수에 대한 인터페이스입니다.
[FileIOError](class_mip_fileioerror.md)  |  파일 IO 오류입니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)  |  클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_fileprofile_observer.md) 인터페이스입니다.
[FileProfile::Settings](class_mip_fileprofile_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [FileProfile](class_mip_fileprofile.md)에서 사용되는 [설정](class_mip_fileprofile_settings.md)입니다.
[FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다.
[HttpDelegate](class_mip_httpdelegate.md)  |  HTTP 처리를 재정의하기 위한 인터페이스입니다.
[HttpRequest](class_mip_httprequest.md)  |  단일 HTTP 요청을 설명하는 인터페이스입니다.
[HttpResponse](class_mip_httpresponse.md)  |  [HttpDelegate](class_mip_httpdelegate.md)를 재정의할 때 클라이언트 앱에서 구현하는, 단일 HTTP 응답을 설명하는 인터페이스입니다.
[InternalError](class_mip_internalerror.md)  |  내부 오류입니다. 이 오류는 실행 중 예기치 않은 상황이 발생할 때 throw됩니다.
[JustificationRequiredError](class_mip_justificationrequirederror.md)  | _아직 문서화되지 않았습니다._
[JustifyAction](class_mip_justifyaction.md)  |  근거 제공 [동작](class_mip_action.md)에는 레이블 다운그레이드에 대한 근거 제공이 필요하고 실행 상태에서 응답을 설정해야 합니다.
[Label](class_mip_label.md)  |  단일 Microsoft Information Protection 레이블에 대한 추상화입니다.
[LabelingOptions](class_mip_labelingoptions.md)  |  SetLabel/DeleteLabel 메서드에 대한 레이블 옵션을 구성하기 위한 인터페이스입니다.
[LoggerDelegate](class_mip_loggerdelegate.md)  |  MIP SDK 로거에 대한 인터페이스를 정의하는 클래스입니다.
[MetadataAction](class_mip_metadataaction.md)  |  콘텐츠에 메타데이터 정보를 추가하는 [동작](class_mip_action.md)입니다.
[NetworkError](class_mip_networkerror.md)  |  네트워킹 오류입니다. 서비스 엔드포인트에 대한 네트워크 호출을 수행할 때 예기치 않은 동작에 의해 발생했습니다.
[NotSupportedError](class_mip_notsupportederror.md)  |  애플리케이션에서 요청한 작업이 SDK에서 지원되지 않습니다.
[PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  [PolicyEngine](class_mip_policyengine.md)과 연결된 설정을 정의합니다.
[PolicyEngine](class_mip_policyengine.md)  |  이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
[PolicyHandler](class_mip_policyhandler.md)  |  이 클래스는 파일에 대한 모든 정책 처리기 함수의 인터페이스를 제공합니다.
[PolicyProfile::Observer](class_mip_policyprofile_observer.md)  |  클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_policyprofile_observer.md) 인터페이스입니다.
[PolicyProfile::Settings](class_mip_policyprofile_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [PolicyProfile](class_mip_policyprofile.md)에서 사용되는 [설정](class_mip_policyprofile_settings.md)입니다.
[PolicyProfile](class_mip_policyprofile.md)  |  [PolicyProfile](class_mip_policyprofile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다. 일반적인 애플리케이션은 하나의 [PolicyProfile](class_mip_policyprofile.md)만 필요하지만 필요한 경우 여러 프로필을 만들 수 있습니다.
[PolicySyncError](class_mip_policysyncerror.md)  |  정책 데이터를 동기화하려는 시도가 실패했습니다.
[PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  현재 레이블이 권한 있는 작업(관리자 작업에 해당)으로 할당되었으므로 재정의될 수 없습니다.
[ProtectAdhocAction](class_mip_protectadhocaction.md)  |  문서에 임시 보호를 추가하도록 지정하는 동작 클래스입니다.
[ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  문서에 템플릿에 의한 보호를 추가하도록 지정하는 동작 클래스입니다.
[ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  문서에 전달 안 함 보호를 추가하도록 지정하는 동작 클래스입니다.
[ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  콘텐츠와 연관된 보호에 대한 설명입니다.
[ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  콘텐츠 부분과 관련된 보호를 설명하는 [ProtectionDescriptor](class_mip_protectiondescriptor.md)를 생성합니다.
[ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  [ProtectionEngine](class_mip_protectionengine.md)과 관련된 알림을 받는 인터페이스입니다.
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  만드는 동안 그리고 수명 기간 내내 [ProtectionEngine](class_mip_protectionengine.md)에서 사용되는 [설정](class_mip_protectionengine_settings.md)입니다.
[ProtectionEngine](class_mip_protectionengine.md)  |  특정 ID와 관련된 보호 관련 작업을 관리합니다.
[ProtectionHandler::Observer](class_mip_protectionhandler.md)  |  [ProtectionHandler](class_mip_protectionhandler.md)와 관련된 알림을 받는 인터페이스입니다.
[ProtectionHandler](class_mip_protectionhandler.md)  |  특정 보호 구성에 대한 보호 관련 작업을 관리합니다.
[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  [ProtectionProfile](class_mip_protectionprofile.md)에 관련된 알림을 받는 인터페이스입니다.
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  만드는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 [설정](class_mip_protectionprofile_settings.md)입니다.
[ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md)은 보호 작업을 수행하기 위한 루트 클래스입니다.
[RecommendLabelAction](class_mip_recommendlabelaction.md)  |  레이블 권장 동작은 사용자에게 레이블을 제안하기 위한 것입니다. 사용자가 권장 레이블을 무시한 후 이 호출을 표시하지 않는 것은 실행 상태에서 지원되는 작업을 통해 수행되어야 합니다.
[RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  문서에서 콘텐츠 바닥글을 제거하도록 지정하는 동작 클래스입니다.
[RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  문서에서 콘텐츠 헤더를 제거하도록 지정하는 동작 클래스입니다.
[RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  문서에서 보호를 제거하도록 지정하는 동작 클래스입니다.
[RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  문서에서 워터마크를 제거하도록 지정하는 동작 클래스입니다.
[Stream](class_mip_stream.md)  |  MIP SDK와 스트림 기반 콘텐츠 간에 인터페이스를 정의하는 클래스입니다.
[TransientNetworkError](class_mip_transientnetworkerror.md)  |  일시적인 네트워킹 오류입니다. 서비스 엔드포인트에 대한 네트워크 호출을 수행할 때 예기치 않은 동작에 의해 발생했습니다. 이 오류는 일시적인 오류이므로 작업을 다시 시도할 수 있습니다.
[UserRights](class_mip_userrights.md)  |  사용자 그룹 및 이들과 연결된 권한입니다.
[UserRoles](class_mip_userroles.md)  |  사용자 그룹 및 이들과 연결된 역할입니다.
