---
title: "문서 추적 및 취소 - Azure Information Protection"
description: "문서를 보호한 후에는 사용자들이 해당 문서를 사용하는 방식을 추적할 수 있습니다. 그리고 필요에 따라 사용자들이 더 이상 이러한 문서를 읽을 수 없도록 문서 액세스 권한을 해지할 수도 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b95b699b63e6a30cdec0af11670a973eb24323dc
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
---
# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Azure Information Protection 사용 시 보호된 문서 추적 및 액세스 권한 해지

>*적용 대상: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

Azure Information Protection을 사용하여 문서를 보호한 후에는 사용자들이 해당 문서를 사용하는 방식을 추적할 수 있습니다. 그리고 필요에 따라 사용자들이 더 이상 이러한 문서를 읽을 수 없도록 문서 액세스 권한을 해지할 수도 있습니다. 이렇게 하려면 Windows 컴퓨터와 Mac 컴퓨터뿐 아니라 태블릿과 휴대폰에서도 액세스할 수 있는 **문서 추적 사이트**를 사용합니다.

이 사이트에 액세스할 때 로그인하여 문서를 추적할 수 있습니다. 조직에 [문서 추적 및 취소를 지원하는 구독](https://www.microsoft.com/cloud-platform/azure-information-protection-features)이 있으며 사용자에게 이 구독에 대한 라이선스가 할당되었으면 보호한 파일을 열려고 하는 사람과 시도의 성공(인증) 여부를 확인할 수 있습니다. 이러한 사용자가 각각 문서 액세스를 시도한 시간과 해당 시간의 위치도 표시됩니다. 이 밖에도 다음 지침을 따릅니다.

-   문서 공유를 중지해야 하는 경우 **허용 취소**를 클릭하고 문서를 계속 사용할 수 있는 기간을 확인한 다음, 이전에 공유했던 문서에 대한 액세스를 취소함을 사용자에게 알릴지와 사용자 지정된 메시지를 제공할지 여부를 결정합니다. 문서를 해지하는 경우 공유한 문서가 삭제되지는 않지만, 권한 있는 사용자가 이 문서를 더 이상 열 수 없게 됩니다.
    
    ![문서 추적 사이트의 해지 액세스 아이콘](../media/tracking-site-revoke-access-icon.png)

-   Excel로 내보내려는 경우: **CSV로 내보내기**를 클릭합니다. 그러면 데이터를 수정하고 보기와 그래프를 직접 만들 수 있습니다.
    
    ![문서 추적 사이트의 CSV로 내보내기 아이콘](../media/tracking-site-export-icon.png)

-   전자 메일 알림을 구성하려는 경우: **설정** 을 클릭하고 문서 액세스 시 전자 메일로 알림을 받을지 여부와 해당 방법을 선택합니다.
    
    ![문서 추적 사이트의 CSV로 내보내기 아이콘](../media/tracking-site-settings-email.png)

- 공유 문서를 추적하고 다른 사용자의 문서 액세스 권한을 해지하려는 경우 Azure Information Protection의 관리자는 관리 아이콘을 클릭하여 보호된 문서를 추적하고 다른 사용자의 해당 문서 액세스 권한을 해지할 수 있습니다. 이 아이콘은 관리자에게만 표시됩니다.
    
    ![문서 추적 사이트의 관리자 아이콘](../media/tracking-site-admin-icon.png)

보호된 문서를 추적하려면 문서 추적 사이트에 등록되어야 합니다. 이렇게 하려면 파일 탐색기 또는 Office 앱을 사용합니다.

## <a name="using-office-to-track-or-revoke-the-document"></a>Office를 사용하여 문서 추적 또는 해지

Office 응용 프로그램 Word, Excel, PowerPoint 및 Outlook의 경우: 

1. 추적 또는 해지하려는 보호된 문서를 엽니다.

2. **홈** 탭, **보호** 그룹에서 **보호** > **추적 및 해지**를 클릭합니다.

    ![추적 사용 옵션](../media/track-usage-callout.png)

사용 중인 Office 응용 프로그램에서 이러한 옵션이 표시되지 않으면 Azure Information Protection 클라이언트가 컴퓨터에 설치되어 있지 않거나, Office 응용 프로그램을 다시 시작해야 하거나, 컴퓨터를 다시 시작하여 설치를 완료해야 하는 것일 수 있습니다. Azure Information Protection 클라이언트를 설치하는 방법에 대한 자세한 내용은 [Azure Information Protection 클라이언트 다운로드 및 설치](install-client-app.md)를 참조하세요.

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>파일 탐색기를 사용하여 문서 추적 또는 해지

1. 보호된 파일을 마우스 오른쪽 단추로 클릭하고 **분류 및 보호**를 선택합니다.

2. **분류 및 보호 - Azure Information Protection** 대화 상자에서 **추적 및 해지**를 선택합니다.

    ![분류 및 보호 - Azure Information Protection 대화 상자의 추적 및 해지 아이콘](../media/track-and-revoke.png)


### <a name="using-a-web-browser-track-and-revoke-documents-that-you-have-registered"></a>웹 브라우저를 사용하여 등록한 문서 추적 및 해지

Office 앱 또는 파일 탐색기를 사용하여 보호된 문서를 등록한 후에 지원되는 웹 브라우저를 사용하여 이러한 문서를 추적 및 해지할 수 있습니다.

- Windows PC, Mac 컴퓨터 또는 모바일 장치를 사용하여 [문서 추적 사이트](https://go.microsoft.com/fwlink/?LinkId=529562)를 방문합니다.

    **지원되는 브라우저**: Internet Explorer 버전 10 이상을 사용하는 것이 좋지만 다음 브라우저를 통해서도 문서 추적 사이트를 사용할 수 있습니다.

    -   Internet Explorer: 버전 10 이상

    -   Internet Explorer 9 MS12-037 이상: Internet Explorer용 누적 보안 업데이트: 2012년 6월 12일

    -   Mozilla Firefox: 버전 12 이상

    -   Apple Safari 5: 버전 5 이상

    -   Google Chrome: 버전 18 이상


## <a name="other-instructions"></a>기타 지침
Azure Information Protection 사용자 가이드의 사용 방법 지침:

- [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]