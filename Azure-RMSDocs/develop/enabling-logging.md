---
title: 방법&#58; 오류 및 성능 로깅 사용 | Azure RMS
description: Microsoft Rights Management SDK 4.2에서는 단일 장치 속성을 통해 진단 및 성능 로그 업로드를 관리합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6b8bbae656ec84441c5ae411b639b1f4bf64021c
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804124"
---
# <a name="how-to-enable-error-and-performance-logging"></a>방법: 오류 및 성능 로깅 사용
Microsoft Rights Management SDK 4.2에서는 단일 장치 속성을 통해 진단 및 성능 로그 업로드를 관리합니다.

## <a name="overview"></a>개요 ##
Microsoft로 자동 진단, 성능 및 원격 분석 로깅 데이터 업로드를 사용하여 사용자 환경과 문제 해결을 개선할 수 있습니다. 

> [!IMPORTANT] 
> 사용자 개인 정보를 보호하기 위해 앱 개발자는 자동 로깅을 사용하도록 설정하기 전에 동의하도록 요청해야 합니다.

> [!NOTE]
> 예를 들어 Microsoft에서 로깅 알림에 사용하는 일반적인 메시지는 다음과 같습니다. 
>
> *오류 및 성능 로깅을 설정함으로써 Microsoft에 오류 및 성능 데이터를 보내는 것에 동의하게 됩니다.  Microsoft는 인터넷을 통해 오류 및 성능 데이터(“데이터”)를 수집합니다.  Microsoft는 이 데이터를 사용하여 Microsoft 제품 및 서비스의 품질, 보안 및 무결성을 제공하고 향상합니다.  예를 들어, Microsoft는 사용하는 기능, 기능의 응답 속도, 장치 성능, 사용자 인터페이스 조작, 제품에서 발생하는 문제 등 성능 및 안정성을 분석합니다.  데이터에는 현재 실행 중인 소프트웨어, IP 주소처럼 소프트웨어의 구성에 대한 정보도 포함됩니다.*  

두 가지 속성을 통해 로깅 제어를 관리합니다.

-   **IpcCustomerExperienceDataCollectionEnabled** 속성을 통해 로깅을 사용하도록 설정합니다. 이 설정은 장치를 초기화해도 유지됩니다.
-   다음 설정을 사용하여 **IpcLogLevel** 속성을 통해 로깅 수준을 제어합니다.

    * 1 - 자세한 정보 표시
    * 2 - 정보
    * 3 - 경고
    * 4 - 오류
    * 5 - 중요

뒤에 나오는 각 예제 코드 조각에서는 호출 응용 프로그램이 속성을 설정하거나 쿼리할 수 있습니다.

### <a name="android"></a>Android ###
자동 로깅 사용

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

현재 로깅 제어 플래그 설정 가져오기

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## <a name="ios"></a>iOS ##
자동 로깅 사용

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

현재 로깅 제어 플래그 설정 가져오기

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

로그 수준 제어 설정

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

로그 수준 제어 설정 가져오기

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## <a name="windows"></a>Windows ##
자동 로깅 사용

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

선택적 설정에 대한 자세한 내용은 [CustomerExperienceOptions](https://msdn.microsoft.com/library/microsoft.rightsmanagement.customerexperienceoptions.aspx) 섹션을 참조하세요.

현재 로깅 제어 플래그 설정 가져오기

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**참고** - 위의 Windows 코드 조각은 C++로 작성되었습니다. C\#의 경우 '::' 대신 '.'을 사용하여 구문을 업데이트합니다.

**Linux/C++** - 이 SDK의 기본 로깅은 다른 플랫폼의 로깅만큼 광범위하지 않습니다. 자세한 내용은 [이식 가능한 C++용 RMS SDK](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting)에서 "README.md"의 **문제 해결** 섹션을 참조하세요.
