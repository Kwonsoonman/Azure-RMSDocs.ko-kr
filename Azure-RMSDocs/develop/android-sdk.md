---
title: "Android 설정 | Azure RMS"
description: "Android 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: 90c8c97c720c624ba8f1ca7703b6c79a66f77d08


---

# Android 설정

Android 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 AAD RM(Azure Active Directory Rights Management)을 사용하여 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.

이 항목에서는 새 앱을 만들기 위한 환경을 설정하는 과정을 안내합니다.

-   [필수 구성 요소](#prerequisites)
-   [선택 사항입니다.](#optional)
-   [개발 환경 구성](#configuring-your-development-environment)
-   [참고 항목](#see-also)

## 필수 구성 요소

다음 소프트웨어는 개발 시스템에서 사용하는 것이 좋습니다.

-   [Eclipse](http://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html) 개발 환경을 실행할 Windows 또는 OS X 운영 체제.
-   이 가이드에서는 Eclipse Juno 4.2 이상의 Eclipse SDK 및 기본 설치를 사용한다고 가정합니다.
-   Java 1.6 이상의 Java
-   [ADT(Android 개발자 도구) 플러그 인](http://developer.android.com/sdk/installing/index.html) 참고 - 설치를 완료하려면 Eclipse를 다시 시작하라는 메시지가 표시될 수도 있습니다.

     

-   Android용 MS RMS SDK 4.2 패키지. 자세한 내용은 [시작](get-started.md)을 참조하세요.

    이 SDK는 Android 4.0.3(API 수준 15) 이상용 개발에 사용할 수 있습니다.

-   인증 라이브러리: [Azure ADAL(AD 인증 라이브러리)](https://msdn.microsoft.com/library/jj573266.aspx)을 사용하는 것이 좋습니다. 그러나 OAuth 2.0을 지원하는 다른 인증 라이브러리도 사용할 수 있습니다.

    자세한 내용은 [Android용 ADAL](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)을 참조하세요.

    **참고** 응용 프로그램에서 ADAL 라이브러리를 OAuth 2.0 인증 라이브러리로 사용하지 않는 경우 Android 지침인 [일부 SecureRandom 아이디어](http://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html)를 검토해야 합니다.

     

API 업데이트, 릴리스 정보 및 FAQ(질문과 대답)에 대한 자세한 내용은 [새로운 기능](release-notes.md) 항목을 참조하세요.

## 선택 사항입니다.

UI 라이브러리는 고유한 사용자 지정 UI를 만들지 않으려는 개발자에게 사용 및 보호 작업을 위한 다시 사용 가능한 UI를 제공합니다([Android용 UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-android)).

## 개발 환경 구성

**참고** MS RMS SDK 4.2 미리 보기 릴리스: 이 미리 보기 릴리스에서는 스크린샷이 com/microsoft/protection에서 com/microsoft/rightsmanagment로의 경로 이름 변경을 표시하도록 업데이트되지 않았습니다. 하지만 텍스트는 업데이트되었습니다.

 
-   Eclipse 개발 환경을 엽니다.
-   새 Android 응용 프로그램 프로젝트를 만들려면 **File** 메뉴에서 **New**를 클릭하고 **Project**를 클릭한 다음 **Android Application Project**를 선택합니다.

    ![새 Android 응용 프로그램 만들기](../media/Android-setup-01c.png)

-   응용 프로그램 이름을 입력합니다. 응용 프로그램 이름에 따라 프로젝트 이름 및 패키지 이름이 채워집니다.
-   **Next**를 클릭하고 작업 영역을 만들려는 위치를 선택합니다.

    ![응용 프로그램 이름 입력](../media/Android-setup-02a.jpg)

-   **Next**를 클릭하고 앱 아이콘을 선택합니다.

    ![앱의 아이콘 선택](../media/Android-setup-03.png)

-   **Next**를 클릭하고 **Blank Activity**를 선택하여 활동을 만듭니다.

    ![활동 만들기](../media/Android-setup-04.png)

-   **Next**를 클릭하고 활동 이름을 입력합니다. 레이아웃 이름을 *activity\_main*으로 사용하여 *MainActivity*를 기본 이름으로 유지할 수 있습니다.

    ![정책의 이름 제공](../media/Android-setup-05a.jpg)

-    **마침**을 클릭합니다.

    ![만들기 완료](../media/Android-setup-06.jpg)

-   기본 활동 클래스인 *MainActivity.java*와 함께 프로젝트가 만들어졌습니다.

**SDK 참조**

-   *adrms\_android\_sdk.zip*을 추출한 폴더로 이동합니다. "SDK > com > microsoft > rightsmanagement" 폴더에서 *.classpath*, *.project* 및 *project.properties* 파일이 읽기 전용으로 표시되지 않았는지 확인합니다.
-   SDK를 참조하려면 작업 영역으로 가져와야 합니다.

    Eclipse에서 **File**을 클릭합니다. **File** 메뉴에서 **Import**를 클릭합니다. **Import** 대화 상자에서 **Android / Existing Android Code into Workspace**를 선택합니다.

    ![작업 영역으로 가져오기](../media/Android-setup-07.png)

-    **다음**을 클릭합니다. *adrms\_android\_sdk.zip*을 추출한 폴더로 이동하여 선택합니다. SDK가 목록에 **com.microsoft.rightsmanagement**로 표시되어야 합니다.

    ![폴더를 선택하도록 이동](../media/Android-setup-08c.jpg)

-   **Finish**를 클릭하면 SDK 프로젝트가 이전에 만든 응용 프로그램의 형제로 나타납니다.

    ![응용 프로그램의 형제로 표시되는 SDK 프로젝트](../media/Android-setup-09.jpg)

-   **Project** 아이콘을 마우스 오른쪽 단추로 클릭하고 프로젝트의 속성을 봅니다.
-   **Android** 탭으로 이동합니다.
-   **Add**를 클릭하고 작업 영역에서 *com.microsoft.rightsmanagement* 라이브러리를 선택합니다.

    ![라이브러리 추가](../media/Android-setup-10b.jpg)

-   **확인**을 클릭합니다.

    MS RMS SDK 4.2는 AAD RM에 연결하기 때문에 응용 프로그램에 **INTERNET** 및 **ACCESS\_NETWORK\_STATE** 권한을 부여해야 합니다. 이렇게 하려면 프로젝트 루트에 있는 *AndroidManifest.xml* 파일을 엽니다.

    사용 권한을 추가하려면 **Add**를 클릭하고 **Uses Permissions**를 선택합니다.

    ![권한 추가](../media/Android-setup-11d.jpg)

-   텍스트 편집기 보기에서 매니페스트를 보면 매니페스트 단계를 확인할 수 있습니다. 다음 줄이 나타나는지 확인합니다.


    <uses-sdk      android:minSdkVersion="15"      android:targetSdkVersion="19"/> <uses-permission android:name="android.permission.INTERNET"/> <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/> <uses-permission/>


**참고** SDK는 *android.support.v4*를 사용합니다.

-   이제 새 Android 앱을 만들 준비가 되었습니다.

### 참고 항목

[시작](get-started.md)

[새로운 기능](release-notes.md)

[개발자 용어 및 개념](core-concepts.md)

[Android API 참조](https://msdn.microsoft.com/library/dn758245.aspx)

 

 



<!--HONumber=Sep16_HO5-->


