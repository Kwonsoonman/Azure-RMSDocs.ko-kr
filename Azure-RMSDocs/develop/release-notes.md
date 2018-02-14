---
title: "새로운 기능 및 릴리스 정보"
description: "이 버전과 이전 버전의 중요한 변경 내용 및 기능을 간략하게 설명합니다."
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 09/25/2017
ms.topic: article
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 130da5ecf3fb95297f9bc335b1ea5023d53c589f
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="whats-new-and-release-notes"></a>새로운 기능 및 릴리스 정보

## <a name="whats-new"></a>새로운 기능

이 항목에서는 RMS SDK v4.x 새 버전의 중요한 변경 내용 및 기능을 간략하게 설명합니다.

-   [2017년 7월 새 버전](#new-for-july-2017)
-   [2016년 10월 업데이트](#October-2016-update)
-   [2016년 6월 업데이트](#new-for-June-2016)
-   [2015년 12월 업데이트](#december-2015-update)
-   [2015년 7월 업데이트 - Linux/C++ 개발을 위한 지원 추가](#july-2015-update-adds-support-for-linux-c-developm)
-   [2015년 5월 업데이트 - 로깅 제어 추가](#may-2015-update-adds-logging-control)
-   [2015년 2월 업데이트 - Windows 스토어 응용 프로그램 지원](#february-2015-update-adds-windows-store-application-support)
-   [2015년 1월 업데이트 - WinPhone 플랫폼 지원 추가](#january-2015-update-adds-winphone-platform-support)
-   [2014년 10월 업데이트 - Microsoft RMS SDK 4.1로 업그레이드](#october-2014-update-upgrade-to-microsoft-rms-sdk-4-1)
-   [릴리스 정보](#release-notes)
-   [질문과 대답](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>2017년 7월 새 버전

7월 릴리스 업데이트에는 SDK 수정 버전이 포함되어 있으며 현재 버전은 4.2.5입니다.

- Android SDK: 이제 앱에서 Android SDK를 사용하여 **로깅 수준을 즉시 설정**할 수 있습니다. 자세한 내용은 [방법: 오류 및 성능 로깅 사용](https://docs.microsoft.com/information-protection/develop/enabling-logging)을 참조하세요.
- IOS SDK는 로깅 수준을 지원하지 않습니다. 
- 이제 SDK는 NULL 액세스 토큰에 대한 오류를 반환합니다.

### <a name="october-2016-update"></a>2016년 10월 업데이트

- 몇 가지 백 엔드 버그가 수정되었습니다.
- Apple iOS/OSX SDK에 bitcode를 사용합니다.

### <a name="june-2016-update"></a>2016년 6월 업데이트

- **최신 인증 지원** - RMS 지원 앱에 ADAL(Active Directory 인증 라이브러리) 기반 로그인을 사용합니다. MFA(Multi-Factor Authentication), SAML 기반 타사 ID 공급자와 RMS 클라이언트 응용 프로그램, 스마트 카드, 인증서 기반 인증 등의 로그인 기능을 지원하므로 RMS 지원 앱에서 기본 인증 프로토콜을 사용할 필요가 없습니다.
- **문서 추적 지원** - 이제 개발자는 앱에서 문서를 보호할 때 문서 추적을 사용할 수 있습니다.
- 성능 향상
- 버그 수정

### <a name="december-2015-update"></a>2015년 12월 업데이트

이 릴리스에서 장치용 RMS SDK는 이제 버전 4.2에 있으며 다음 기능이 추가되었습니다.

-   RMS 온라인 전용, iOS/OS X용, Android 운영 체제용 문서 추적.

    iOS/OS X에 대한 세부 정보 및 사용 지침은 [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx)에 대한 추적 정보 및 추가 문서 추적 등록 메서드를 제공하는 [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx) 클래스를 참조하세요. Android에서도 [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) 및 [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx)에 비슷한 기능이 추가되었습니다.

    문서 추적 기능에 대한 자세한 내용은 [방법: 문서 추적 사용](how-to-use-document-tracking.md)을 참조하세요.

-   Android API에 대한 비동기 버전을 병렬화하는 동기 메서드 집합:

    [CustomProtectedInputStream.create synchronous method](https://msdn.microsoft.com/library/mt631362.aspx)

    [CustomProtectedOutputStream.create synchronous method](https://msdn.microsoft.com/library/mt631363.aspx)

    [ProtectedFileInputStream.create synchronous method](https://msdn.microsoft.com/library/mt631375.aspx)

    [ProtectedFileOutputStream.create synchronous method](https://msdn.microsoft.com/library/mt631376.aspx)

    [TemplateDescriptor.getTemplates synchronous method](https://msdn.microsoft.com/library/mt631380.aspx)

    [UserPolicy.acquire synchronous method](https://msdn.microsoft.com/library/mt631384.aspx)

    [UserPolicy.create (PolicyDescriptor…) synchronous method**](https://msdn.microsoft.com/library/mt631385.aspx)

    [UserPolicy.create (TempalteDescriptor…) synchronous method](https://msdn.microsoft.com/library/mt631386.aspx)

-   새 [ProtectedBuffer](https://msdn.microsoft.com/library/mt631369.aspx) 클래스가 Android API에 추가되었습니다.
-   오류 메시지 및 문제 해결 환경을 개선하는 업데이트입니다.
-   암호화 작업의 성능이 크게 향상됩니다.

### <a name="july-2015-update---adds-support-for-linux--c-development"></a>2015년 7월 업데이트 - Linux/C++ 개발을 위한 지원 추가

이 릴리스는 다음 업데이트를 추가합니다.

-   Linux 플랫폼용 RMS SDK 4.1

    자세한 내용은 [시작](get-started.md)을 참조하세요.

### <a name="may-2015-update---adds-logging-control"></a>2015년 5월 업데이트 - 로깅 제어 추가

이 릴리스는 다음 업데이트에 대한 지원을 추가합니다.

-   iOS

    앱 암호화 및 암호 해독은 독립적으로, 병렬로 작동할 수 있습니다.

    자세한 내용은 [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx)를 참조하세요.

    로그 수준 제어 설정이 사용됩니다.

    자세한 내용은 [방법: 오류 및 성능 로깅 사용](enabling-logging.md)을 참조하세요.

    캐시 지우기 지원이 추가되었습니다.

    자세한 내용은 [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx)을 참조하세요.

### <a name="february-2015-update---adds-windows-store-application-support"></a>2015년 2월 업데이트 - Windows 스토어 응용 프로그램 지원

이 릴리스는 Windows 스토어 응용 프로그램에 대한 지원을 추가하고 RMS SDK 4.1의 Windows Phone, Android 및 iOS/OS X 릴리스를 통해 기능 패리티를 제공합니다.

### <a name="january-2015-update---adds-winphone-platform-support"></a>2015년 1월 업데이트 - WinPhone 플랫폼 지원 추가

이 릴리스는 Windows Phone 운영 체제에 대한 지원을 추가하고 RMS SDK 4.1의 Android 및 iOS/OS X 릴리스를 통해 기능 패리티를 제공합니다.

### <a name="october-2014-update---upgrade-to-microsoft-rms-sdk-41"></a>2014년 10월 업데이트 - Microsoft RMS SDK 4.1로 업그레이드

RMS SDK 버전 4.1 릴리스는 Google Android 및 Apple iOS/OS X에 다음과 같은 새 기능을 추가합니다.

-   *사용자 동의*를 처리하기 위한 Android 및 iOS/OS X SDK API 확장. 사용자가 SDK 동작을 확인할 수 있습니다. 현재 문서 추적 및 알 수 없는 AD RMS 서비스 URL 액세스는 지원되는 동의 형식입니다.

    자세한 내용은 [ConsentCallback 인터페이스](https://msdn.microsoft.com/library/dn833503.aspx) Android API 버전을 예제로 참조하세요.

-   이제 iOS 8 및 OS X 10.10(Yosemite)이 지원됩니다. 또한 Xcode 6에 필요한 몇 가지 속성 이름이 변경되었습니다.

    예를 들어 MSUserPolicy.name이 [MSUserPolicy.policyName](https://msdn.microsoft.com/library/dn790799.aspx)으로 변경되었습니다.

## <a name="release-notes"></a>릴리스 정보

이 섹션에서는 개발자가 알아야 하는 Microsoft Rights Management SDK 4.x API의 현재 릴리스 및 이전 릴리스에 대한 정보를 간략하게 설명합니다.

**AD RMS SDK 4.1 - iOS/OS X 및 Android 플랫폼 전역 가용성 릴리스**

-   **AD RMS 지원** - IT 관리자는 새 AD RMS 서버의 모바일 장치 확장을 사용하여 모바일 장치에서 RMS 지원 앱을 사용할 수 있습니다.
-   **오프라인에서 사용** - 최종 사용자는 RMS로 보호되는 데이터에 오프라인으로 액세스할 수 있습니다.
-   **분리된 인증** - 개발자는 자신만의 고유한 Azure RMS 및 AD RMS용 인증 라이브러리(또는 권장 [ADAL(Azure AD 인증 라이브러리)](https://MSDN.Microsoft.Com/library/jj573266.aspx))를 사용할 수 있습니다.
-   **분리된 UI** - 개발자는 RMS로 보호되는 문서를 보호하고 사용하는 자신만의 고유한 사용자 인터페이스를 빌드할 수 있습니다.
-   **새롭게 디자인된 API** - 이제 개발자는 최소한의 노력으로 일관적인 RMS 동작과 사용자 환경을 제공하는 간단하고 투명한 암호화 및 암호 해독 API를 사용할 수 있습니다.

**모든 플랫폼에 공통**

-   RMS SDK 4.x API는 *스레드로부터 안전*하지 않습니다.

**Android**

-   Amazon® Kindle 장치에서 샘플 응용 프로그램을 사용하여 .ptxt 첨부 파일을 보려면 먼저 파일을 다운로드해야 합니다.

    **해결 방법** - 알려진 문제로 나중에 해결할 예정입니다.

-   다중 인스턴스를 허용하면 SDK를 사용하는 응용 프로그램에서 충돌이 발생할 수 있습니다.

    **해결 방법** - 응용 프로그램에서 Android API에 대한 다중 인스턴스 호출을 허용하지 않도록 합니다.

-   [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write( byte\[\] array, int offset, int length ) 메서드를 *array.length* 값과 다른 길이로 사용하면 나중에 SDK를 사용하여 콘텐츠를 소비할 수 없습니다.

    **해결 방법** - 이것은 알려진 문제입니다. 이 문제를 완화하려면 항상 길이 값이 길이 매개 변수와 동일한 *byte \[\]* 배열을 사용하거나, [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array) 메서드를 사용합니다.

**iOS 및 OS X**

-   iOS 및 OS X SDK에서 지원하는 두 가지 포르투갈어가 있습니다. 그러나 버그로 인해 현재는 첫 번째 지역화가 완벽하게 지원되지 않습니다. 이 버그 때문에 포르투갈어가 완벽하게 지원되지 않습니다. 대부분의 텍스트가 번역되었지만 UI는 번역되지 않았습니다.

    1. 포르투갈어

    2. 포르투갈어(포르투갈)

**iOS만 해당**

-   RMS SDK 4.x는 네트워크 활동 표시기를 표시하지 않습니다.

    이것은 Apple Human Interface Guidelines에 따른 iOS에 대한 알려진 선택적 동작입니다.

**OS X만 해당**

-   RMS SDK 4.x는 네트워크 활동 표시기를 표시하지 않습니다.

    이것은 Apple Human Interface Guidelines에 따른 OS X에 대한 알려진 선택적 동작입니다.

-   **해결 방법** - OS X SDK를 사용하여 MDI(다중 문서 인터페이스)를 만들려면 다음 지침을 따르세요.

    다음 메서드는 동시에 실행하면 안 됩니다. 실행 완료를 모니터링하려면 완료 블록 접근 방식을 설명에 따라 사용하세요.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**참고** MDI 응용 프로그램은 iOS API에서 지원되지 않습니다.

## <a name="frequently-asked-questions"></a>질문과 대답

**모든 플랫폼**

**Q:**: 보호 워크플로에 **사용자 지정 권한** 선택 UI가 보이지 않습니다. 이유가 무엇일까요?

**A**: 알려진 문제로 나중에 해결할 예정입니다.

**Q:**: 새로운 조직 테넌트를 가져와서 SDK와 샘플 응용 프로그램을 사용해 보려면 어떻게 해야 하나요?

**A**: Azure AD RMS 테스트 조직에 대한 자격 증명을 요청하려면 <rmcstbeta@microsoft.com>으로 이메일을 보내주세요.

**Q**: 설명서에 테스트 계층 구조 설명이 보이지 않습니다. 이유가 무엇일까요?

**A**: 새 AD RMS SDK에는 테스트 계층 구조 개념이 없습니다. 항상 프로덕션 계층 구조와 함께 사용됩니다.

**Q:**: RMS SDK 2.1 버전에서, 생성된 매니페스트는 정보 보호를 구현하는 각 응용프로그램에 필요했습니다. SDK 버전 4.0 이상에서도 마찬가지인가요?

**A**: 아니요, Rights Management SDK 3.0 이상 버전에서는 더 이상 매니페스트가 필요 없습니다.

**Android**

**Q:**: 어떤 개발 환경에서 SDK를 테스트했나요?

**A**: Google API 15 이상을 사용하는 Eclipse Juno에서 테스트했습니다.

**Q:**: UI 스레드에서 cancel() a cancel 메서드를 호출할 수 있나요?
**A**: 네트워크 연결이 중단될 수 있으므로 비 UI 스레드에서 cancel() 메서드를 호출해야 합니다.

**iOS**

**Q:**: SDK 개발용으로 검증된 플랫폼은 무엇인가요?

**A**: iOS 7 이상을 사용하는 Xcode 5.0입니다.

**Q:**: 작업에서 cancel() 메서드를 호출했는데, 작업이 완료되었다는 알림이 계속 표시됩니다. 이유가 무엇일까요?

**A**: 일부 작업은 취소할 수 없으며, 따라서 취소 작업은 최대한 가능한 만큼 실행됩니다.

**OS x**

**Q:**: Xcode 5에 샘플 앱 프레임워크가 도입되었습니다. Xcode 4.6을 사용해도 되나요?

**A**: OS X SDK는 Xcode 4.6 이상, OS X 10.8 이상에서만 작동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
