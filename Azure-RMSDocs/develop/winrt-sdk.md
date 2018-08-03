---
title: Windows 스토어 설정 | Azure RMS
description: Windows 스토어 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 330ce41da93004209e6fe00c46fa8491d0fbcd49
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39375200"
---
# <a name="windows-store-setup"></a>Windows 스토어 설정

Windows 스토어 응용 프로그램에서 Microsoft Rights Management SDK 4.2를 통해 AAD RM(Azure Active Directory Rights Management)을 사용하여 해당 응용 프로그램에서 통합 정보 보호를 사용할 수 있습니다.

이 항목에서는 새 앱을 만들기 위한 환경을 설정하는 과정을 안내합니다.

-   [필수 구성 요소](#prerequisites)
-   [선택 사항](#optional)
-   [개발 환경 구성](#configuring-your-development-environment)
-   [참고 항목](#see-also)

## <a name="prerequisites"></a>전제 조건


개발 시스템에 다음 소프트웨어가 있어야 합니다.

-   [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet) 운영 체제
-   [Windows 8.1용 Windows SDK](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) 이상 또는 Windows 8.0/8.1용 Windows SDK에 포함되어 있는 Visual Studio Express 2012
-   Windows 스토어 응용 프로그램용 MS RMS SDK 4.2 패키지 자세한 내용은 [시작](get-started.md)을 참조하세요.
-   인증 라이브러리: [Azure AD 인증 라이브러리](https://msdn.microsoft.com/library/jj573266.aspx)를 사용하는 것이 좋으며 다른 인증 라이브러리를 사용할 수도 있습니다.

API 업데이트, 장치 및 환경 정보, 릴리스 정보 및 FAQ(질문과 대답)에 대한 자세한 내용은 [새로운 기능](release-notes.md) 항목을 참조하세요.

## <a name="optional"></a>선택 사항

UI 라이브러리는 고유한 사용자 지정 UI를 만들지 않으려는 개발자에게 사용 및 보호 작업을 위한 다시 사용 가능한 UI를 제공합니다([Windows 스토어 앱용 UI 라이브러리](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore)). 또한 Windows 스토어 앱 샘플 응용 프로그램인 [Windows 스토어용 RMS 샘플 응용 프로그램](https://github.com/AzureADSamples/rms-samples-for-windowsstore)도 제공합니다.

## <a name="configuring-your-development-environment"></a>개발 환경 구성


-   Visual Studio를 엽니다.
-   **파일**, **새로 만들기**를 차례로 클릭한 다음 **프로젝트**를 클릭합니다.
-   **새 프로젝트** 대화 상자에서 **Visual C\#** 을 클릭하고 **비어 있는 앱(Windows)** 을 선택한 다음 **확인**을 클릭합니다.

    ![새 프로젝트 만들기](../media/winrtsetup-newproj.png)

-   **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택하여 **참조 추가** 대화 상자를 엽니다.

    ![참조 추가](../media/winrtsetup-addref.png)

-   **참조 추가** 대화 상자에서 **찾아보기**를 클릭하고 SDK 패키지를 추출한 폴더에 있는 *Microsoft.RightsManagement.dll* 파일을 선택합니다.
-   **관리되는 앱** - 관리되는 앱을 빌드하려면 이 참조를 추가하고 **Windows 8.1**-&gt;**확장**을 선택한 다음 **Windows용 Windows Visual C++ 런타임 패키지** 확인란을 선택해야 합니다.

    ![확장 추가](../media/winrtsetup-refmngr.png)

-   **기능 추가** - 응용 프로그램에서 SDK를 사용하려면 "인터넷(클라이언트 및 서버)" 기능이 필요합니다. 이 기능을 앱에 추가하려면 프로젝트에서 *Package.appxmanifest* 파일을 열고 **기능** 탭으로 이동하여 추가합니다.

이제 새 Windows 스토어 앱을 만들 준비가 되었습니다.

### <a name="see-also"></a>참고 항목

[시작](get-started.md)

[새로운 기능](release-notes.md)

[개발자 용어 및 개념](core-concepts.md)

[Windows 8](http://windows.microsoft.com/en-US/windows-8/meet)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Windows API 참조](https://msdn.microsoft.com/library/dn891914.aspx)
