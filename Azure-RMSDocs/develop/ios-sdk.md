---
# required metadata

title: iOS 및 OS X 설치 | Azure RMS
description: iOS 및 OS X 응용 프로그램에서 RMS SDK 4.2를 통해 AAD RM을 사용하여 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# iOS 및 OS X 설정

iOS 및 OS X 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 AAD RM(Azure Active Directory Rights Management)을 사용하여 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.

이 항목에서는 새 앱을 만들기 위한 환경을 설정하는 과정을 안내합니다.

**참고** 이 SDK는 iPod Touch를 지원하지 않습니다.


-   [필수 구성 요소](#prerequisites)
-   [선택 사항입니다.](#optional)
-   [개발 환경 구성](#configuring_your_development_environment)
-   [참고 항목](#see_also)

## 필수 구성 요소

다음 소프트웨어는 개발 시스템에서 사용하는 것이 좋습니다.

-   OS X은 모든 iOS 개발에 필요합니다.
-   Xcode 버전 6.0 이상

    Xcode는 [Mac 앱 스토어](https://developer.apple.com/technologies/mac/)를 통해 사용할 수 있습니다.

-   iOS 및 OS X용 MS RMS SDK 4.2 패키지. 자세한 내용은 [시작](get-started.md)을 참조하세요.

    이 SDK는 iOS 7.0 및 OS X 10.8 이상용 개발에 사용할 수 있습니다.

-   인증 라이브러리: [Azure ADAL(AD 인증 라이브러리)](https://msdn.microsoft.com/en-us/library/jj573266.aspx)을 사용하는 것이 좋습니다. 그러나 OAuth 2.0을 지원하는 다른 인증 라이브러리도 사용할 수 있습니다.

    자세한 내용은 [iOS용 ADAL](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) 또는 [OS X용 ADAL](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal)을 참조하세요.

API 업데이트, 릴리스 정보 및 FAQ(질문과 대답)에 대한 자세한 내용은 [새로운 기능](release-notes.md) 항목을 참조하세요.

## 선택 사항입니다.

UI 라이브러리는 고유한 사용자 지정 UI를 만들지 않으려는 개발자에게 사용 및 보호 작업을 위한 다시 사용 가능한 UI를 제공합니다([iOS용 UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-ios)).

## 개발 환경 구성

-   새 프로젝트를 만들려면 **File** 메뉴에서 **New**를 클릭한 다음 **Project**를 클릭합니다.
-   **Single View Application**을 선택합니다.

    ![새 프로젝트 만들기](../media/iOS-Project.png)

-   새 프로젝트의 이름과 식별자를 입력합니다.

    ![프로젝트 이름 지정](../media/iOS-project-options.png)

-   **Next**를 클릭하고 프로젝트 위치를 선택합니다.
-   iOS 프레임워크용 **MSRightsManagement** 프레임워크를 추가하려면 SDK 설치 폴더에서 **Project Navigator**의 **Frameworks** 섹션으로 .framework 폴더를 끌어다 놓습니다.

    ![위치 설정](../media/ios-add-dependencies-01a.png)

-   **Create groups for any added folders** 옵션 단추를 선택하고 **Copy items into destination group's folder (if needed)** 확인란을 선택 취소합니다.

    이 작업은 복사본을 만들지 않고 SDK 설치 폴더에 대한 참조를 유지 관리합니다.

    ![SDK 설치 폴더에 대한 참조 설정](../media/iOS-create-groups.png)

-   리소스 번들용 MS RMS SDK 4.2를 추가하려면 MSRightsManagement.framework/Resources 폴더에서 Project Navigator의 **Frameworks** 섹션으로 MSRightsManagementResources.bundle 파일을 끌어다 놓습니다.

    ![리소스 번들 추가](../media/iOS-add-resource-bundle-02a.png)

-   Framework를 복사할 때와 마찬가지로 **Create groups for any added folders** 옵션 단추를 선택하고 **Copy items into destination group's folder (if needed)** 확인란을 선택 취소합니다.
-   SDK는 **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** 및 **Security**를 비롯한 다른 프레임워크를 사용합니다. 이러한 프레임워크를 추가하려면 대상 **Summary** 창의 **Linked Frameworks and Libraries** 섹션으로 이동한 다음 해당 섹션을 확장하여 프레임워크를 추가합니다.

    **UIKit** 및 **Foundation** 프레임워크는 필수이며, 일반적으로 기본적으로 표시됩니다.

    ![리소스 추가](../media/iOS-add-libraries.png)

-   대상 **Build Settings**의 **Other Linker Flags**에 **-ObjC** 플래그를 추가합니다.

    ![빌드 설정 추가](../media/iOS-linker-flags.png)

-   **Project Navigator**가 다음 트리와 같이 표시됩니다.

    ![프로젝트 검토](../media/iOS-verify-setup-01a.png)

-   이제 새 iOS/OS X 앱을 만들 준비가 되었습니다.

### 참고 항목

* [시작](get-started.md)

* [새로운 기능](release-notes.md)

* [개발자 용어 및 개념](core-concepts.md)

* [iOS/OS X API 참조](/rights-management/sdk/4.2/api/ios/ios)

 

 





<!--HONumber=Apr16_HO4-->


