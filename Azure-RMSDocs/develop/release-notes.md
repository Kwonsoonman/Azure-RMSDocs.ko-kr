---
# required metadata

title: 새로운 기능 및 릴리스 정보 | Azure RMS
description: 이 새로운 버전의 RMS SDK에 포함된 중요한 변경 내용과 기능을 간략하게 설명합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3b482c5f-fd40-47d5-acdc-13d2e80d5171

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# 새로운 기능 및 릴리스 정보

## 새로운 기능
Microsoft 권한 관리 SDK 4.2에서는 RMS 응용 프로그램 사용이 훨씬 쉽고 유연해졌습니다. 이 항목에서는 이 새로운 버전의 RMS SDK에 포함된 중요한 변경 내용과 기능을 간략하게 설명합니다.

-   [2015년 12월 업데이트의 새로운 기능](#new_for_our_december_2015_update)
-   [2015년 7월 업데이트 - Linux/C++ 개발에 대한 지원 추가](#july_2015_update_-_adds_support_for_linux___c___development)
-   [2015년 5월 업데이트 - 로깅 제어 추가](#may_2015_update_-_adds_logging_control)
-   [2015년 2월 업데이트 - Windows 스토어 응용 프로그램 지원 추가](#february_2015_update_-_adds_windows_store_application_support)
-   [2015년 1월 업데이트 - WinPhone 플랫폼 지원 추가](#january_2015_update_-_adds_winphone_platform_support)
-   [2014년 10월 업데이트 - Microsoft RMS SDK 4.1로 업그레이드](#october_2014_update_-_upgrade_to_microsoft_rms_sdk_4.1)
-   [릴리스 정보](#release-notes)
-   [질문과 대답](#frequently_asked_questions)

### 2015년 12월 업데이트의 새로운 기능

이 릴리스에서는 장치용 RMS SDK가 이제 버전 4.2이며 다음 기능이 추가되었습니다.

-   iOS/OS X 및 Android 운영 체제에 대한 문서 추적(RMS 온라인에만 해당).

    iOS/OS X에 대한 자세한 내용과 사용 지침은 [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc)에 대한 추적 정보 및 추가 문서 추적 등록 메서드를 제공하는 [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc) 클래스를 참조하세요. [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) 및 [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy)에는 유사한 Android용 항목이 추가되었습니다.

    문서 추적 기능에 대한 자세한 내용은 [**방법: 문서 추적 사용**](how-to-use-document-tracking.md)을 참조하세요.

-   Android API의 비동기 버전을 병렬화하는 동기 메서드 집합:

    [**CustomProtectedInputStream.create 동기 메서드**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_create_synchronous_method_java)

    [**CustomProtectedOutputStream.create 동기 메서드**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**ProtectedFileInputStream.create 동기 메서드**](/rights-management/sdk/4.2/api/android/protectedfileinputstream#msipcthin2_protectedfileinputstream_create_synchronous_method)

    [**ProtectedFileOutputStream.create 동기 메서드**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**TemplateDescriptor.getTemplates 동기 메서드**](/rights-management/sdk/4.2/api/android/templatedescriptor#msipcthin2_templatedescriptor_gettemplates_synchronous_method_java)

    [**UserPolicy.acquire 동기 메서드**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_acquire_synchronous_method_java)

    [**UserPolicy.create(PolicyDescriptor...) 동기 메서드**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_policydescriptor_______synchronous_method_java)

    [**UserPolicy.create(TempalteDescriptor...) 동기 메서드**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_templatedescriptor_______synchronous_method_java)

-   새 [**ProtectedBuffer**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedbuffer_class) 클래스가 Android API에 추가되었습니다.
-   오류 메시지 및 문제 해결 환경을 개선하기 위한 업데이트
-   암호화 작업 성능 향상

### 2015년 7월 업데이트 - Linux/C++ 개발에 대한 지원 추가

이 릴리스에서는 다음 기능이 추가되었습니다.

-   Linux 플랫폼용 RMS SDK 4.1

    자세한 내용은 [시작](get-started.md)을 참조하세요.

### 2015년 5월 업데이트 - 로깅 제어 추가

이 릴리스에서는 다음 기능에 대한 지원이 추가되었습니다.

-   iOS

    앱 암호화 및 암호 해독이 독립적으로 및 병렬로 작동할 수 있습니다.

    자세한 내용은 [**MSProtector**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msprotector_class_objc)를 참조하세요.

    로그 수준 제어 설정을 사용할 수 있습니다.

    자세한 내용은 [방법: 오류 및 성능 로깅 사용](enabling-logging.md)을 참조하세요.

    캐시 지우기 지원이 추가되었습니다.

    자세한 내용은 [**MSProtection:resetStateWithCompletionBlock**](/rights-management/sdk/4.2/api/iOS/msprotection#msipcthin2_msprotection_resetstatewithcompletionblock_method_objc)을 참조하세요.

### 2015년 2월 업데이트 - Windows 스토어 응용 프로그램 지원 추가

이 릴리스에서는 Windows 스토어 응용 프로그램에 대한 지원이 추가되었으며 Windows Phone, Android 및 iOS/OS X 릴리스의 RMS SDK 4.1과 기능 패리티를 제공합니다.

### 2015년 1월 업데이트 - WinPhone 플랫폼 지원 추가

이 릴리스에서는 Windows Phone 운영 체제에 대한 지원이 추가되었으며 Android 및 iOS/OS X 릴리스의 RMS SDK 4.1과 기능 패리티를 제공합니다.

## 2014년 10월 업데이트 - Microsoft RMS SDK 4.1로 업그레이드

버전 4.1 릴리스의 RMS SDK에서는 Google Android 및 Apple iOS/OS X에 에는 다음과 같은 새로운 기능이 추가되었습니다.

-   SDK 동작의 사용자 확인을 허용하는 사용자 동의 처리를 위한 Android 및 iOS/OS X SDK API 확장. 현재 지원되는 동의 형식은 문서 추적 및 알 수 없는 AD RMS 서비스 URL 액세스입니다.

    자세한 내용을 보려면 Android API 버전의 [**ConsentCallback 인터페이스**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_consentcallback_interface_java)를 예제로 참조하세요.

-   이제 iOS 8 및 OS X 10.10(Yosemite)이 지원됩니다. 또한 Xcode 6에 필요한 몇 가지 속성 이름 변경이 있었습니다.

    예를 들어 MSUserPolicy.name이 [**MSUserPolicy.policyName**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_name_property_objc)으로 변경되었습니다.

## 릴리스 정보

이 섹션에서는 개발자가 알고자 하는 현재 및 이전 릴리스의 Microsoft Rights Management SDK 4.x API에 대한 정보를 간략하게 설명합니다.

**AD RMS SDK 4.1 - iOS/OS X 및 Android 플랫폼 글로벌 가용성 릴리스**

-   **AD RMS 지원** - IT 관리자는 모바일 장치에서 새 AD RMS 서버의 모바일 장치 확장과 함께 RMS 사용 앱을 사용할 수 있습니다.
-   **오프라인 사용** - 최종 사용자는 RMS 보호된 데이터를 오프라인으로 액세스할 수 있습니다.
-   **분리된 인증** - 개발자는 Azure RMS 및 AD RMS에 대해 고유한 인증 라이브러리를 사용하거나 권장 [Azure ADAL(AD 인증 라이브러리)](https://MSDN.Microsoft.Com/en-us/library/jj573266.aspx)을 사용할 수 있습니다.
-   **분리된 UI** - 개발자는 RMS 보호된 문서를 보호하고 사용할 사용자 인터페이스를 빌드할 수 있습니다.
-   **다시 디자인된 API** – 이제 개발자는 최소한의 노력으로 일관된 RMS 동작과 사용자 환경을 제공하는 간단하고 투명한 암호화 및 암호 해독 API를 이용할 수 있습니다.

**모든 플랫폼에 공통적으로 적용**

-   RMS SDK 4.x API는 스레드로부터 안전하지 않습니다.

**Android**

-   Amazon® Kindle 장치에서 샘플 앱을 사용하여 .ptxt 첨부 파일을 보는 경우 파일을 보기 전에 먼저 다운로드해야 합니다.

    **해결 방법** - 알려진 문제이며 나중에 해결할 예정입니다.

-   다중 인스턴스가 허용되는 경우 SDK를 사용하는 응용 프로그램이 충돌할 수 있습니다.

    **해결 방법** - 응용 프로그램에서 Android API에 대한 다중 인스턴스 호출을 허용하지 않도록 합니다.

-   [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] 배열, int 오프셋, int 길이)** 메서드를 array.length 값과 다른 길이로 사용하는 경우 나중에 SDK를 통해 콘텐츠를 사용할 수 없습니다.

    **해결 방법** - 알려진 문제입니다. 문제를 완화하려면 항상 **byte \[\]** 배열을 length 매개 변수와 동일한 길이 값으로 전달하거나, [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] 배열)** 메서드를 사용합니다.

**iOS 및 OS X**

-   iOS 및 OS X SDK에서 지원하는 두 가지 포르투갈어 언어가 있습니다. 버그로 인해 현재 첫 번째 지역화는 완전히 지원되지 않습니다. 이 버그 때문에 포르투갈어는 완전히 지원되지 않습니다. 대부분의 텍스트가 번역되었지만 UI는 번역되지 않았습니다.

    1. 포르투갈어

    2. 포르투갈어(포르투갈)

**iOS에만 해당**

-   RMS SDK 4.x에서는 네트워크 활동 표시기를 표시하지 않습니다.

    이는 Apple Human Interface Guidelines에 따른 iOS에 대해 알려진 선택적 동작입니다.

**OS X에만 해당**

-   RMS SDK 4.x에서는 네트워크 활동 표시기를 표시하지 않습니다.

    이는 Apple Human Interface Guidelines에 따른 OS X에 대해 알려진 선택적 동작입니다.

-   **해결 방법** - OS X SDK를 사용하여 MDI(다중 문서 인터페이스) 응용 프로그램을 만들려면 다음 지침을 따르세요.

    다음 메서드는 동시에 실행하면 안 됩니다. 실행 완료를 모니터링하려면 설명된 대로 완료 블록 방법을 사용합니다.

    - [**protectedDataWithProtectedFile**](https://stage.docs.microsoft.com/en-us/rights-management/sdk/4.2/api/iOS/msprotecteddata#msipcthin2_msprotecteddata_protecteddatawithprotectedfile_completionblock_method_objc)
    - [**customProtectedDataWithPolicy**](/rights-management/sdk/4.2/api/iOS/mscustomprotecteddata#msipcthin2_mscustomprotecteddata_customprotecteddatawithpolicy_protecteddata_contentstartposition_contentsize_completionblock_method_objc)



**참고** MDI 응용 프로그램은 iOS API에서 지원되지 않습니다.

## 질문과 대답

**모든 플랫폼**

**Q**: 보호 워크플로에 **사용자 지정 권한** 선택 UI가 표시되지 않습니다. 그 이유는 무엇일까요?

**A**: 알려진 문제이며 나중에 해결할 예정입니다.

**Q**: SDK와 샘플 응용 프로그램을 사용하기 위해 새 조직 테넌트를 얻으려면 어떻게 하나요?

**A**: Azure AD RMS 테스트 조직에 대한 자격 증명을 요청하려면 <rmcstbeta@microsoft.com>으로 메일을 보내세요.

**Q**: 여기 설명서에 테스트 계층 구조 설명이 보이지 않습니다. 그 이유는 무엇일까요?

**A**: 새 AD RMS SDK에는 테스트 계층 구조 개념이 없습니다. 항상 프로덕션 계층 구조를 사용합니다.

**Q**: 2.1 버전의 RMS SDK에서는 정보 보호를 구현하는 각 응용 프로그램에 대해 생성된 매니페스트가 필요했습니다. 4.0 이상 버전의 SDK에서도 마찬가지인가요?

**A**: 아니요, 3.0 이상 버전의 권한 관리 SDK에서는 매니페스트가 더 이상 필요하지 않습니다.

**Android**

**Q**: SDK가 테스트된 개발 환경은 무엇인가요.

**A**: Google API 15 이상을 사용하는 Eclipse Juno입니다.

**Q**: UI 스레드에서 취소 메서드인 cancel()을 호출할 수 있나요?
**A**: 네트워크 연결이 중단될 수 있으므로 비 UI 스레드에서 cancel()을 호출해야 합니다.

**iOS**

**Q**: SDK 개발에 대해 검증된 플랫폼은 무엇인가요?

**A**: iOS 7 이상을 사용하는 Xcode 5.0입니다.

**Q**: 작업에 대해 cancel() 메서드를 호출했는데 작업이 완료되었다는 알림이 표시되었습니다. 그 이유는 무엇일까요?

**A**: 일부 작업은 취소할 수 없으므로 취소 작업은 가능한 경우에만 실행됩니다.

**OS X**

**Q**: 샘플 앱 프레임워크는 Xcode 5에 맞게 조정되었습니다. Xcode 4.6에서도 사용할 수 있나요?

**A**: OS X SDK는 Xcode 4.6 이상과 OS X 10.8 이상에서만 작동합니다.

 

 


<!--HONumber=Apr16_HO3-->

