---
# required metadata

title: 방법&#58; 오류 및 성능 로깅 사용 | Azure RMS
description: Microsoft Rights Management SDK 4.2에서는 단일 장치 속성을 통해 진단 및 성능 로그 업로드를 관리합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 방법: 오류 및 성능 로깅 사용
Microsoft Rights Management SDK 4.2에서는 단일 장치 속성을 통해 진단 및 성능 로그 업로드를 관리합니다.

## 개요 ##
Microsoft로 자동 진단 및 성능 로깅 업로드를 사용하여 사용자 환경과 문제 해결을 개선할 수 있습니다. 사용자 개인 정보를 보호하기 위해 앱 개발자는 자동 로깅을 사용하도록 설정하기 전에 동의하도록 요청해야 합니다.

두 가지 속성을 통해 로깅 제어를 관리합니다.

-   **IpcCustomerExperienceDataCollectionEnabled** 속성을 통해 로깅을 사용하도록 설정합니다. 이 설정은 장치를 초기화해도 유지됩니다.
-   다음 설정을 사용하여 **IpcLogLevel** 속성을 통해 로깅 수준을 제어합니다.

    * 1 - 자세한 정보 표시
    * 2 - 정보
    * 3 - 경고
    * 4 - 오류
    * 5 - 중요

뒤에 나오는 각 예제 코드 조각에서는 호출 응용 프로그램이 속성을 설정하거나 쿼리할 수 있습니다.

### Android ###
자동 로깅 사용

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

현재 로깅 제어 플래그 설정 가져오기

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## iOS ##
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
 

## Windows ##
자동 로깅 사용

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

선택적 설정에 대한 자세한 내용은 [CustomerExperienceOptions](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_customerexperienceoptions) 섹션을 참조하세요.

현재 로깅 제어 플래그 설정 가져오기

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**참고** - 위의 Windows 코드 조각은 C++로 작성되었습니다. C\#의 경우 '::' 대신 '.'을 사용하여 구문을 업데이트합니다 .

**Linux/C++** - 이 SDK의 기본 로깅은 다른 플랫폼의 로깅만큼 광범위하지 않습니다. 자세한 내용은 [이식 가능한 C++용 RMS SDK](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting)에서 "README.md"의 **문제 해결** 섹션을 참조하세요.

 

 


<!--HONumber=Apr16_HO4-->


