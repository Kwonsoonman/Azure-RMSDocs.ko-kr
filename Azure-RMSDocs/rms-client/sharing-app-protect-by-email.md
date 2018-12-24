---
title: RMS 공유 앱으로 보호되는 공유 - AIP
description: 메일을 통해 문서를 안전하게 공유하는 방법에 대한 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 157a08ea1d30a7ff515e76cfd21f2393f2a16202
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44148582"
---
# <a name="protect-a-file-that-you-share-by-email-by-using-the-rights-management-sharing-application"></a>Rights Management 공유 응용 프로그램을 사용하여 메일로 공유하는 파일 보호

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

메일을 통해 공유하는 파일을 보호하는 경우 원래 파일의 새 버전이 만들어집니다. 원래 파일은 보호되지 않은 상태로 유지되고 새 버전이 보호되며 보내는 메일에 자동으로 첨부됩니다.

경우에 따라서는 Microsoft Word, Excel, PowerPoint에서 만드는 파일에 대해 RMS 공유 응용 프로그램이 메일 메시지에 첨부하는 파일 버전 두 개를 만들기도 합니다. 두 번째 파일 버전은 파일 이름 확장명이 **.ppdf** 이며 파일의 PDF 섀도 복사본입니다. 이 파일 버전이 만들어지므로 받는 사람은 파일을 만든 사람이 사용한 것과 같은 응용 프로그램을 설치하지 않아도 항상 파일을 읽을 수 있습니다. 종종 모바일 디바이스에서 메일을 읽고 해당 메일 첨부 파일을 보려는 경우가 여기에 해당합니다. 파일을 열려면 RMS 공유 응용 프로그램만 있으면 됩니다. 첨부된 파일을 읽을 수 있지만 Rights Management 서비스를 지원하는 응용 프로그램을 사용하여 다른 버전의 파일을 열 때까지 파일을 변경할 수는 없습니다.

조직에서 Azure Information Protection을 사용하는 경우에는 다음과 같은 방법으로 공유를 통해 보호하는 파일을 추적할 수 있습니다.

-   이와 같은 보호된 첨부 파일을 다른 사람이 열려고 할 때 메일을 받는 옵션을 선택합니다. 그러면 해당 파일에 액세스할 때마다 파일 열기를 시도한 사람과 시간, 그리고 파일이 열렸는지(사용자가 정상적으로 인증되었는지)에 대한 알림을 받게 됩니다.

-   문서 추적 사이트를 사용합니다. 문서 추적 사이트에서 문서 액세스를 취소하여 파일 공유를 중지할 수도 있습니다. 자세한 내용은 [RMS 공유 응용 프로그램을 사용하는 경우 문서 추적 및 취소](sharing-app-track-revoke.md)를 참조하세요.

## <a name="using-outlook-to-protect-a-file-that-you-share-by-email"></a>Outlook 사용: 메일을 통해 공유하는 파일을 보호하려면

1.  메일 메시지를 만들고 파일을 첨부합니다. 그런 다음 **메시지** 탭의 **RMS** 그룹에서 **보호된 항목 공유** 를 클릭하고 **보호된 항목 공유** 를 다시 클릭합니다.

    ![RMS 공유 응용 프로그램용 Outlook 추가 기능](../media/ADRMS_MSRMSApp_SP_OutlookToolbar.png)

    이 단추가 표시되지 않으면 RMS 공유 응용 프로그램이 컴퓨터에 설치되어 있지 않거나, 최신 버전을 설치하지 않았거나, 컴퓨터를 다시 시작하여 설치를 완료해야 하는 것일 수 있습니다. 공유 응용 프로그램을 설치하는 방법에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)를 참조하세요.

2.  [보호된 항목 공유 대화 상자](sharing-app-dialog-box.md)에서 이 파일에 대해 사용할 옵션을 지정하고 **지금 보내기**를 클릭합니다.

### <a name="other-ways-to-protect-a-file-that-you-share-by-email"></a>메일을 통해 공유하는 파일을 보호하는 다른 방법
Outlook을 사용하여 보호된 파일을 공유하는 방법 외에 다음과 같은 방법을 대신 사용할 수도 있습니다.

-   파일 탐색기: 모든 파일에 대해 사용할 수 있는 방법입니다.

-   Office 응용 프로그램에서 이 방법은 리본에 **RMS** 그룹이 표시되도록 Office 추가 기능을 사용하여 RMS 공유 응용 프로그램이 지원하는 응용 프로그램에 사용할 수 있습니다.

#### <a name="using-file-explorer-or-an-office-application-to-protect-a-file-that-you-share-by-email"></a>파일 탐색기 또는 Office 응용 프로그램 사용: 메일을 통해 공유하는 파일을 보호하려면

1.  다음 옵션 중 하나를 사용합니다.

    -   파일 탐색기에서 파일을 마우스 오른쪽 단추로 클릭하고 **RMS로 보호**를 선택한 다음 **보호된 항목 공유**를 선택합니다.

        ![보호된 항목 공유 메뉴 옵션](../media/ADRMS_MSRMSApp_ShareProtectedMenu.png)

    -   Office 응용 프로그램, Word, Excel, PowerPoint의 경우 먼저 파일을 저장했는지 확인합니다. 그런 다음 **홈** 탭의 **RMS** 그룹에서 **보호된 항목 공유** 를 클릭하고 **보호된 항목 공유** 를 다시 클릭합니다.

        ![Office 도구 모음 추가 기능](../media/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

    이러한 보호 옵션이 표시되지 않으면 RMS 공유 응용 프로그램이 컴퓨터에 설치되어 있지 않거나, 최신 버전을 설치하지 않았거나, 컴퓨터를 다시 시작하여 설치를 완료해야 하는 것일 수 있습니다. 공유 응용 프로그램을 설치하는 방법에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)를 참조하세요.

2.  [보호된 항목 공유 대화 상자](sharing-app-dialog-box.md)에서 이 파일에 대해 사용할 옵션을 지정하고 **보내기**를 클릭합니다.

3.  파일이 보호되고 있음을 나타내는 대화 상자가 잠깐 표시될 수 있으며, 그 후에는 자동으로 작성된 메일 메시지가 표시됩니다. 이 메시지에는 받는 사람에게 첨부 파일이 Microsoft RMS로 보호되어 있으며 로그인을 해야 함을 알려 주는 정보가 포함되어 있습니다. 받는 사람이 링크를 클릭하여 로그인하면 보호된 첨부 파일을 열 수 있는 지침과 링크가 표시됩니다.

    예:

    ![Azure Information Protection에 대한 메일 메시지](../media/ADRMS_MSRMSApp_EmailMessage.PNG)

    [자동으로 만들어지는 .ppdf 파일이란 무엇인가요?](sharing-app-dialog-box.md#whats-the-ppdf-file-thats-automatically-created)를 참조하세요.

4.  선택 사항: 이 메일 메시지에 있는 모든 항목을 변경할 수 있습니다. 예를 들어 메시지에서 제목이나 텍스트를 추가 또는 변경할 수 있습니다.

    > [!WARNING]
    > 이 메일 메시지에서 사용자를 추가하거나 제거할 수는 있지만, 이렇게 해도 **보호된 항목 공유** 대화 상자에서 지정한 첨부 파일의 권한은 변경되지 않습니다. 새 사용자에게 파일 열기 권한을 제공하려는 등 해당 권한을 변경하려는 경우에는 메일 메시지를 저장하거나 보내지 않고 닫은 후 1단계로 돌아갑니다.

5.  메일 메시지를 보냅니다.

## <a name="examples-and-other-instructions"></a>예제 및 기타 지침
예를 들어 Rights Management 공유 응용 프로그램 및 방법 지침을 사용하는 방법에 대한 예는 Rights Management 공유 응용 프로그램 사용자 가이드에서 다음 섹션을 참조하세요.

-   [RMS 공유 응용 프로그램 사용 예제](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [원하는 옵션을 선택하](sharing-app-user-guide.md#what-do-you-want-to-do)세요.

## <a name="see-also"></a>참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)
