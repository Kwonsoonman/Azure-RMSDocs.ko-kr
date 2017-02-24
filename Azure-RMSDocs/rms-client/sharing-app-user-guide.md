---
title: "Rights Management 공유 응용 프로그램 사용자 가이드 | Azure Information Protection"
description: "Windows용 Microsoft RMS(Rights Management) 공유 응용 프로그램을 사용하면 중요한 문서와 사진을 보아서는 안 되는 사용자에게 전자 메일로 보내거나 다른 장치에 저장한 경우에도 해당 사용자로부터 안전하게 보관할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: eaf6d02c-aa36-4915-856e-49bb71ab1484
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ffed64826982756072456be18cced0226b6bb6cc
ms.openlocfilehash: 1acc6563f8b5da498cb58db46a93160a1fa94022


---

# <a name="rights-management-sharing-application-user-guide"></a>Rights Management 공유 응용 프로그램 사용자 가이드

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

> [!IMPORTANT]
> **지원 종료 알림**: Windows용 Rights Management 공유 응용 프로그램은 [Azure Information Protection 클라이언트](aip-client.md)로 대체될 예정입니다. 이 이전 응용 프로그램에 대한 지원은 2018년 1월 31일에 중지됩니다. 

Windows용 Microsoft Rights Management(RMS) 공유 응용 프로그램을 사용하면 중요한 문서와 사진을 전자 메일로 보내거나 다른 장치에 저장하는 경우에도 보아서는 안 되는 사용자로부터 안전하게 보관할 수 있습니다. 이 응용 프로그램을 사용하여 동일한 Rights Management 보호 기술을 통해 다른 사용자가 보호한 파일을 열어서 사용할 수도 있습니다.

Windows 7 서비스 팩 1 이상을 실행하는 컴퓨터만 있으면 됩니다. 이러한 항목을 준비한 후 Microsoft에서 이 무료 응용 프로그램을 [다운로드 및 설치](http://go.microsoft.com/fwlink/?LinkId=303970) 합니다.

이 가이드에 대답이 나와 있지 않은 질문이 있는 경우 [Windows용 Microsoft Rights Management 공유 응용 프로그램 FAQ](http://go.microsoft.com/fwlink/?LinkId=303971)를 참조하세요. 또한 이 페이지에는 문제가 발생할 경우 몇 가지 문제 해결 정보가 포함됩니다.

## <a name="examples-for-using-the-rms-sharing-application"></a>RMS 공유 응용 프로그램 사용 예제
아래에는 RMS 공유 응용 프로그램을 사용해 파일을 보호할 수 있는 방법의 몇 가지 예제가 나와 있습니다.

|수행하려는 작업|작업 방법|
|----------------|------------------|
|**…다른 조직에서 근무하는 신뢰하는 사용자와 재무 정보를 안전하게 공유하려는 경우**<br /><br />파트너 회사와 작업할 때 예상 판매액이 포함된 Excel 스프레드시트를 파트너 회사 직원에게 전자 메일로 보내려고 합니다. 그리고 해당 직원들이 수치를 확인만 하고 변경할 수는 없도록 하려고 합니다.|Excel의 리본에서 **보호된 항목 공유** 단추를 사용하여 함께 작업을 하는 파트너 회사 직원 두 명의 전자 메일 주소를 입력하고 **뷰어 - 보기만 가능**을 선택한 후에 **보내기**를 클릭합니다.<br /><br />파트너 회사에 전자 메일이 도착하면 전자 메일의 받는 사람만이 스프레드시트를 볼 수 있으며 해당 스프레드시트를 저장, 편집, 인쇄, 전달할 수는 없습니다.<br /><br />단계별 지침: [Rights Management 공유 응용 프로그램을 사용하여 메일을 통해 공유하는 파일 보호](sharing-app-protect-by-email.md)|
|**…iOS 장치 사용자에게 메일로 문서를 안전하게 보내려는 경우**<br /><br />iOS 장치에서 정기적으로 전자 메일을 확인하는 동료에게 일급 기밀 Word 문서를 전자 메일로 보내려고 합니다.|파일 탐색기에서 파일을 마우스 오른쪽 단추로 클릭한 다음 **보호된 항목 공유**를 선택하여 파일을 동료에게 첨부 파일로 보냅니다.<br /><br />받는 사람이 iOS 장치에서 메일을 받습니다. 받는 사람은 iPad 및 iPhone용 Office를 사용하고 있지 않으므로 공유 응용 프로그램을 다운로드하는 방법을 알려 주는 전자 메일 내의 링크를 클릭해서 iOS 장치용 버전을 설치한 후 문서를 봅니다¹.<br /><br />단계별 지침: [Rights Management 공유 응용 프로그램을 사용하여 메일을 통해 공유하는 파일 보호](sharing-app-protect-by-email.md)|
|**… 자신이 보호한 문서를 연 사용자와 해당 시기를 확인하고 필요하면 액세스를 취소하려는 경우**<br /><br />잠재적 공급업체와 기밀 디자인 문서를 안전하게 공유한 후 해당 문서에 액세스한 사용자와 액세스 시간 및 위치를 확인하려고 합니다. 그런 다음 공급업체 중 하나와 거래 계약을 체결하면 원본 문서를 공유했던 사용자들이 더 이상 해당 문서를 읽을 수 없도록 문서에 대한 액세스를 취소하려고 합니다.|전자 메일을 통해 문서를 공유한 후 [문서 추적 사이트](http://go.microsoft.com/fwlink/?LinkId=529562) 로 이동하여 해당 문서에 액세스한 사용자 및 액세스 시간을 확인합니다. 문서 공유를 중지해야 하는 경우에는 액세스를 취소하는 옵션을 선택합니다.<br /><br />단계별 지침: [RMS 공유 응용 프로그램을 사용하는 경우 문서 추적 및 취소](sharing-app-track-revoke.md)|
|**… 안전하게 공유된 파일이 첨부되어 있는 메일 메시지를 받았는데 회사에서 Rights Management를 사용하지 않아 읽을 수 없는 첨부 파일을 읽으려는 경우**<br /><br />전자 메일 보낸 사람은 이전에 같이 일한 적이 있어 신뢰하는 사용자인데, 새로운 비즈니스 기회 가능성에 대한 정보를 보낸 것으로 보입니다.|전자 메일의 지침에 따라 Microsoft Rights Management에 등록하는 링크를 클릭합니다. Microsoft에서 조직에 Azure Information Protection이 포함된 구독이 없음을 확인하고 무료 등록 프로세스를 완료할 수 있는 전자 메일을 보냅니다. 그러면 사용자는 새 계정을 사용하여 로그인합니다. 전자 메일의 두 번째 링크를 클릭하여 Rights Management 공유 앱을 설치합니다. 그리고 나면 전자 메일 첨부 파일을 열어 새 비즈니스 기회에 대한 정보를 읽을 수 있습니다.<br /><br />단계별 지침: [Rights Management로 보호된 파일 보기 및 사용](sharing-app-view-use-files.md)|
|**…회사 외부 사용자가 액세스할 수 없도록 노트북의 회사 기밀 파일을 보호하려는 경우**<br /><br />출장을 자주 다니며, 노트북을 사용하여 무단 액세스로부터 보호해야 하는 파일의 폴더를 액세스 및 업데이트합니다.|노트북에 RMS 공유 응용 프로그램을 설치한 다음 파일 탐색기를 사용하여 템플릿을 통해 파일을 보호합니다. 이렇게 하면 파일을 빠르게 보호할 수 있습니다. 노트북을 도난당해도 회사 외부 사용자는 이러한 문서에 액세스할 수 없으므로 걱정할 필요가 없습니다.<br /><br />단계별 지침: [Rights Management 공유 응용 프로그램을 사용하여 장치에서 파일 보호(바로 보호)](sharing-app-protect-in-place.md)|
¹ PDF 렌더링 기능은 Foxit에서 제공합니다. Copyright © 2003–2014 by Foxit Corporation.

## <a name="what-do-you-want-to-do"></a>원하는 옵션을 선택하세요.
> [!NOTE]
> [지원되는 파일 형식](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) 및 [엔터프라이즈 네트워크에서 이 응용 프로그램을 설치하는 방법](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)과 같은 추가 기술 정보는 [Rights Management 공유 응용 프로그램 관리자 가이드](sharing-app-admin-guide.md)를 참조하세요.

- [공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)

- [장치에서 파일 보호(바로 보호)](sharing-app-protect-in-place.md)

- [메일을 통해 공유하는 파일 보호](sharing-app-protect-by-email.md)

- [보호된 파일에 대한 사용 권한 변경](sharing-app-reprotect-files.md)

- [문서 추적 및 취소](sharing-app-track-revoke.md)

- [보호된 파일 보기 및 사용](sharing-app-view-use-files.md)

- [파일에서 보호 제거](sharing-app-remove-protection.md)

- [바로 가기 키 사용](sharing-app-keyboard-shortcuts.md)

- [대화 상자에서 설정 지정](sharing-app-dialog-box.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Feb17_HO2-->


