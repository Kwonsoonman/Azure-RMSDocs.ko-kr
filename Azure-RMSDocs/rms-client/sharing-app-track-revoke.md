---
title: "RMS 공유 응용 프로그램을 사용하는 경우 문서 추적 및 취소 | Azure Information Protection"
description: "RMS 공유 응용 프로그램을 사용하여 문서를 보호하고 나면 사용자들이 보호된 문서를 사용하는 방식을 추적할 수 있습니다. 필요한 경우 공유를 중지하고 싶을 때 이러한 문서에 대한 액세스 권한을 취소할 수도 있습니다."
author: cabailey
manager: mbaldwin
ms.date: 10/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 13579b8cb5516a1d7390db81957c140b8e980982
ms.openlocfilehash: 1cd55e9c6200876a4d9921e3b60eb8fb58845d0c


---

# RMS 공유 응용 프로그램을 사용하는 경우 문서 추적 및 취소

>*적용 대상: Azure Information Protection, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

조직에서 Active Directory Rights Management Services가 아닌 Azure Information Protection을 사용하고 있다면 RMS 공유 응용 프로그램을 사용하여 문서를 보호한 후에 보호된 문서가 사용되는 방식을 추적할 수 있습니다. 필요한 경우 공유를 중지하고 싶을 때 이러한 문서에 대한 액세스 권한을 취소할 수도 있습니다. 이렇게 하려면 Windows 컴퓨터와 Mac 컴퓨터뿐 아니라 태블릿과 휴대폰에서도 액세스할 수 있는 **문서 추적 사이트**를 사용합니다.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

이 사이트에 액세스할 때 로그인하여 문서를 추적할 수 있습니다. 조직에 [문서 추적 및 취소를 지원하는 구독](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features)이 있으며 사용자에게 이 구독에 대한 라이선스가 할당되었으면 보호한 파일을 열려고 하는 사람과 시도의 성공(인증) 여부를 확인할 수 있습니다. 이러한 사용자가 각각 문서 액세스를 시도한 시간과 해당 시간의 위치도 표시됩니다. 또한,

-   문서 공유를 중지해야 하는 경우 **허용 취소**를 클릭하고 문서를 계속 사용할 수 있는 기간을 확인한 다음, 이전에 공유했던 문서에 대한 액세스를 취소함을 사용자에게 알릴지와 사용자 지정된 메시지를 제공할지 여부를 결정합니다. 문서를 해지하는 경우 공유한 문서가 삭제되지는 않지만, 권한 있는 사용자가 이 문서를 더 이상 열 수 없게 됩니다.

-   Excel로 내보내려는 경우 **CSV로 내보내기**를 클릭합니다. 그러면 데이터를 수정하고 보기와 그래프를 직접 만들 수 있습니다.

-   전자 메일 알림을 구성하려는 경우 **설정** 을 클릭하고 문서 액세스 시 전자 메일로 알림을 받을지 여부와 해당 방법을 선택합니다.

- 다른 사용자에 대한 공유 문서를 추적 및 취소하려는 경우 Azure Information Protection의 관리자는 관리 아이콘을 클릭하여 다른 사용자에 대한 문서를 추적 및 취소할 수 있습니다. 이 아이콘은 관리자에게만 표시됩니다.

-   문서 추적 사이트에 대한 질문이 있거나 피드백을 제공하려는 경우 도움말 아이콘을 클릭하여 [문서 추적 FAQ](http://go.microsoft.com/fwlink/?LinkId=523977)에 액세스합니다.

## Office를 사용하여 문서 추적 사이트 액세스

-   Office 응용 프로그램, Word, Excel, PowerPoint의 경우 **홈** 탭의 **RMS** 그룹에서 **보호된 항목 공유**를 클릭하고 **사용량 추적**을 클릭합니다.

    ![RMS 공유 응용 프로그램을 사용하는 경우 Office 응용 프로그램에서 사용 추적 ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

-   Outlook의 경우 **홈** 탭의  **RMS** 그룹에서 **사용량 추적**을 클릭합니다.

    ![RMS 공유 응용 프로그램을 사용하는 경우 Outlook에서 사용 추적 선택 ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

이러한 RMS 옵션이 표시되지 않으면 RMS 공유 응용 프로그램이 컴퓨터에 설치되어 있지 않거나, 최신 버전을 설치하지 않았거나, 컴퓨터를 다시 시작하여 설치를 완료해야 하는 것일 수 있습니다. 공유 응용 프로그램을 설치하는 방법에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)를 참조하세요.

> [!NOTE] 
> [Azure Information Protection 클라이언트](../rms-client/info-protect-client.md)를 설치한 경우 **보호** 단추를 사용하여 문서 추적 사이트에 액세스할 수도 있습니다. 
> 
> - Office 응용 프로그램의 **홈** 탭, **보호** 그룹에서 **보호** > **사용 현황 추적**을 클릭합니다. 

### 문서를 추적 및 취소하는 다른 방법
Office 응용 프로그램을 사용하여 Windows 컴퓨터에서 문서를 추적할 수 있을 뿐 아니라 다음과 같은 대체 방법을 사용할 수도 있습니다.

-   **웹 브라우저 사용**: 지원되는 모든 장치에서 사용할 수 있는 방법입니다.

-   **파일 탐색기 사용**: Windows 컴퓨터에서 사용할 수 있는 방법입니다.

-   **Outlook 전자 메일 메시지 사용**: Windows 컴퓨터에서 사용할 수 있는 방법입니다.

#### 웹 브라우저를 사용하여 문서 추적 사이트 액세스

-   지원되는 브라우저를 사용하여 [문서 추적 사이트](http://go.microsoft.com/fwlink/?LinkId=529562)로 이동합니다.

    지원되는 브라우저: Internet Explorer 버전 10 이상을 사용하는 것이 좋지만 다음 브라우저를 통해서도 문서 추적 사이트를 사용할 수 있습니다.

    -   Internet Explorer: 버전 10 이상

    -   Internet Explorer 9 MS12-037 이상: Internet Explorer용 누적 보안 업데이트: 2012년 6월 12일

    -   Mozilla Firefox: 버전 12 이상

    -   Apple Safari 5: 버전 5 이상

    -   Google Chrome: 버전 18 이상

#### 파일 탐색기를 사용하여 문서 추적 사이트에 액세스

-   파일을 마우스 오른쪽 단추로 클릭하고 **RMS로 보호**를 선택한 다음 **사용량 추적**을 선택합니다.

    ![RMS 공유 응용 프로그램을 사용하는 경우 탐색기에서 사용 추적 선택](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### Outlook 전자 메일 메시지를 사용하여 문서 추적 사이트에 액세스

-   전자 메일 메시지의 **메시지** 탭  **RMS** 그룹에서 **보호된 항목 공유**를 클릭하고 **사용량 추적**을 클릭합니다.

    ![RMS 공유 응용 프로그램을 사용하는 경우 Outlook에서 사용 추적 선택](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## 예제 및 기타 지침
예를 들어 Rights Management 공유 응용 프로그램 및 방법 지침을 사용하는 방법에 대한 예는 Rights Management 공유 응용 프로그램 사용자 가이드에서 다음 섹션을 참조하세요.

-   [RMS 공유 응용 프로그램 사용 예제](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [원하는 옵션을 선택하세요.](sharing-app-user-guide.md#what-do-you-want-to-do)

## 참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)



<!--HONumber=Oct16_HO1-->


