---
title: ADAL 인증을 위한 앱 구성 - AIP
description: Azure ADAL 기반 인증을 사용하기 위한 Azure Information Protection 앱 구성 단계
keywords: 인증, RMS, ADAL, Information Protection,
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 01202f34d31569d7835ad57a70e2a2d0d49a9678
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473419"
---
# <a name="configure-your-app-for-adal-authentication"></a>ADAL 인증을 위한 앱 구성

이 항목에서는 ADAL(Azure Active Directory Authentication Library) 기반 인증을 위한 앱을 구성하는 단계를 설명합니다.

## <a name="azure-authentication-setup"></a>Azure 인증 설정

다음이 필요합니다.

- [Microsoft Azure에 대한 구독](https://azure.microsoft.com/)(무료 평가판이면 충분). 자세한 내용은 [사용자가 개인용 RMS를 등록하는 방법](../rms-for-individuals-user-sign-up.md)을 참조하세요.
- Microsoft Azure 권한 관리에 대한 구독(무료 [개인용 RMS](https://technet.microsoft.com/library/dn592127.aspx) 계정이면 충분)

> [!NOTE]
> Microsoft Azure 권한 관리에 대한 구독이 있는지 여부에 대해서는 IT 관리자에게 문의하고 다음 단계를 수행하도록 요청하세요. 조직에 구독이 없는 경우 IT 관리자에게 만들어 달라고 요청해야 합니다. 또한 IT 관리자는 *Microsoft 계정*(예: Hotmail)이 아닌 *회사 또는 학교 계정*으로 가입되어 있어야 합니다.

Microsoft Azure에 등록한 후

- 관리자 권한이 있는 계정을 사용하여 조직에 대한 [Azure 관리 포털](https://manage.windowsazure.com)에 로그인합니다.

![Azure 로그인](../media/AzurePortalLogin.png)

- 포털의 왼쪽에 있는 **Active Directory** 응용 프로그램까지 이동합니다.

![Active Directory 선택](../media/AzureADPick.png)

- 디렉터리를 아직 만들지 않은 경우 포털의 왼쪽 아래 모서리에 있는 **새로 만들기** 단추를 선택합니다.

![새로 만들기 선택](../media/AzureNewBtn.png)

- **권한 관리** 탭을 선택하고 **권한 관리 상태**가 **활성**, **알 수 없음** 또는 **권한 없음**인지 확인합니다. 상태가 **비활성**인 경우 포털의 아래, 가운데에 있는 **활성화** 단추를 선택하고, 선택 사항을 확인합니다.

![활성화 선택](../media/RMTab.png)

- 이제 디렉터리와 응용 프로그램을 차례로 선택하여 새로운 *네이티브 응용 프로그램*을 만듭니다.

![응용 프로그램 선택](../media/CreateNativeApp.png)

- 이제 포털의 아래쪽, 가운데 부분에 있는 **추가** 단추를 선택합니다.

![추가 선택](../media/AddAppBtn.png)

- 프롬프트에서 **내 조직에서 개발 중인 응용 프로그램 추가**를 선택합니다.

![내 조직에서 개발 중인 응용 프로그램 추가 선택](../media/AddAnAppPick.png)

- **네이티브 클라이언트 응용 프로그램**과 **다음** 단추를 차례로 선택하여 응용 프로그램 이름을 지정합니다.

![앱 이름 지정](../media/TellUsInput.png)

- 리디렉션 URI를 추가하고 다음을 선택합니다.
  리디렉션 URI는 유효한 URI여야 하며 디렉터리에 고유합니다. 예를 들어 `https://contoso.azurewebsites.net/.auth/login/done`와 같은 항목을 사용할 수 있습니다.

![리디렉션 URI 추가](../media/RedirectURI.png)

- 디렉터리에서 응용 프로그램을 선택하고 **구성**을 선택합니다.

![구성 선택](../media/ConfigYourApp.png)

>[!NOTE]
> **클라이언트 ID** 및 **리디렉션 URI**를 복사하고 RMS 클라이언트를 구성할 때 사용할 수 있도록 저장합니다.

- 응용 프로그램 설정의 아래쪽으로 이동하고 **다른 응용 프로그램에 대한 권한**에서 **응용 프로그램 추가** 단추를 선택합니다.

>[!NOTE]
> Windows Azure Active Directory용으로 표시된 **위임된 권한**은 기본적으로 올바릅니다. **로그인 및 사용자 프로필 읽기** 옵션 하나만 선택해야 합니다.

![응용 프로그램 추가 선택](../media/PermissionsToOtherBtn.png)

- **Microsoft Rights Management** 옆에 있는 더하기(+) 단추를 선택합니다.

![+ 단추 선택](../media/ChoosePlusBtn.png)

- 이제 대화 상자의 왼쪽 아래 모서리에 있는 확인 표시를 선택합니다.

![확인 표시 선택](../media/choosecheck01.png)

- 이제 Azure RMS용 응용 프로그램에 대한 종속성을 추가할 준비가 되었습니다. 종속성을 추가하려면 **다른 응용 프로그램에 대한 사용 권한**에서 새로운 **Microsoft Rights Management Services** 항목을 선택하고 **위임된 권한:** 드롭 상자에서 **Create and access protected content for users(사용자의 보호된 콘텐츠 만들기 및 액세스)** 확인란을 선택합니다.

![사용 권한 설정](../media/AddDependency.png)

- 포털의 아래쪽 가운데에 있는 **저장** 아이콘을 선택하여 응용 프로그램의 변경 사항을 유지합니다.

![저장 선택](../media/SaveApplication.png)

