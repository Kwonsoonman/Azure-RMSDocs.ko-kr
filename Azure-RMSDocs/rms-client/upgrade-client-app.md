---
title: RMS 공유 응용 프로그램으로 수행한 작업 - AIP
description: RMS 공유 응용 프로그램에서 Azure Information Protection 클라이언트로 업그레이드한 사용자를 위한 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/29/2018
ms.topic: article
ms.service: information-protection
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 423d462c44296f806d4024bdbdebcd9d51325145
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42803989"
---
# <a name="user-guide-tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>사용자 가이드: RMS 공유 응용 프로그램으로 수행해왔던 작업

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

최근에 Rights Management 공유 응용 프로그램("RMS 공유 앱"이라고도 함)에서 Azure Information Protection 클라이언트로 업그레이드했나요? 

다음 정보를 참조하여 빠르게 작업을 시작하는 방법을 배우세요.

|RMS 공유 앱|Azure Information Protection 클라이언트로 이 작업을 수행하는 방법
|-----------|--------------------|
|장치에서 파일 보호 <br /><br />"바로 보호"라고도 합니다.|Office 앱의 경우: 필요한 보호를 적용하거나 사용자 지정 권한을 설정하는 레이블을 선택합니다.<br /><br />다른 파일의 경우: 파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. 그런 다음 필요한 보호를 적용하는 레이블을 선택하거나 자체 사용자 지정 권한을 지정합니다. <br /><br />자세한 내용은 [파일 또는 전자 메일 분류 및 보호](client-classify-protect.md)를 참조하세요.
|전자 메일을 통해 공유하는 파일 보호 <br /><br />"보호된 공유"라고도 합니다.|Outlook을 사용하여 전자 메일 메시지에 필요한 보호를 제공하는 레이블을 적용하거나 Outlook의 **전달 금지** 옵션을 선택합니다. [지원되는 파일 형식](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM)이 있는 보호되지 않은 첨부 파일은 자동으로 보호됩니다.<br /><br />참고: 전자 메일로 보호된 문서를 추적하려면 먼저 보호한 다음 전자 메일 메시지에 첨부하십시오.<br /><br />자세한 내용은 [파일 또는 전자 메일 분류 및 보호](client-classify-protect.md)를 참조하세요.
|보호된 파일에 대한 사용 권한 변경 <br /><br />"다시 보호"라고도 합니다.|Azure Information Protection 표시줄을 표시하는 Office 앱: 필요한 보호를 적용하는 레이블을 선택합니다.<br /><br />다른 파일의 경우 및 Azure Information Protection 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)인 경우: 파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. 그런 다음 필요한 보호를 적용하는 레이블을 선택하거나 자체 사용자 지정 권한을 지정합니다.<br /><br />자세한 내용은 [파일 또는 전자 메일 분류 및 보호](client-classify-protect.md)를 참조하세요.
|문서 추적 및 해지|Word, Excel 및 PowerPoint: 문서를 열고 **홈** 탭 > **보호** 그룹 > **보호** > **추적 및 해지**를 선택합니다.<br /><br />파일 탐색기: 파일 또는 폴더를 마우스 오른쪽 단추로 클릭하고 **분류 및 보호**를 선택합니다. 그런 후 **분류 및 보호 - Azure Information Protection** 대화 상자에서 **추적 및 해지**를 클릭합니다. <br /><br />자세한 내용은 [문서 추적 및 해지](client-track-revoke.md)를 참조하세요.
|보호된 파일 보기 및 사용|보호된 Office 문서를 위해 Office가 설치되어 있어야 합니다. Azure Information Protection 뷰어에서는 다른 많은 보호된 파일을 열어서 읽을 수 있으며, 이러한 작업을 수행할 권한이 있으면 파일을 인쇄하고 저장할 수도 있습니다. 이 뷰어는 클라이언트와 함께 자동으로 설치되거나 별도로 설치할 수 있습니다.<br /><br />자세한 내용은 [보호된 파일 열기](client-view-use-files.md)를 참조하세요.
|파일에서 보호 제거|파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. <br /><br />그런 후 단일 파일에 대해 **사용자 지정 권한으로 보호** 옵션을 선택 취소합니다. 여러 파일 또는 폴더에 대해서는 **사용자 지정 권한 제거**를 클릭합니다.<br /><br />자세한 내용은 [파일 및 전자 메일에서 레이블 및 보호 제거](client-remove-label-protection.md)를 참조하세요.|

## <a name="cant-find-the-option-youre-looking-for"></a>원하는 옵션을 찾을 수 없나요?

RMS 공유 응용 프로그램에서 선택하는 데 사용했던 특정 옵션을 찾고 있는 경우 다음 표를 확인하세요.

|RMS 공유 앱의 옵션|정보
|-----------|--------------------|
|**보호된 공유**|이 옵션은 Office 리본에서 더 이상 사용할 수 없습니다. Office 응용 프로그램 내에서 직접 공유하는 대신, 파일 탐색기의 오른쪽 클릭 옵션인 **분류 및 보호**를 사용하여 사용자 지정 권한으로 문서 사본을 보호하고 선택한 전자 메일 클라이언트 및 공유 위치를 사용하여 파일을 공유합니다. <br /><br /> 또한 보호하는 메일에 보호되지 않은 Office 문서를 첨부할 수 있습니다. 그러면 해당 문서는 동일한 제한으로 자동 보호됩니다. 하지만 이 문서를 추적하거나 해지할 수는 없습니다.
|**누군가가 이 문서를 열려고 하면 내게 메일을 보냅니다.**|문서 추적 사이트를 사용하여 기본 전자 메일 알림 설정 구성: 공유한 보호된 문서를 찾은 후 **설정** > **전자 메일 알림**을 클릭합니다.
|**이러한 문서에 대한 액세스를 즉시 취소할 수 있도록 허용합니다.**|이 옵션은 더 이상 사용할 수 없습니다. 오프라인 액세스를 허용하지 않는 관리자 정의 보호 설정을 사용하세요. 또한 관리자는 [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)을 실행하여 테넌트에 대한 라이선스 사용 유효 기간을 줄일 수 있습니다.
|Outlook에서 **사용 추적**|Outlook에서 문서 추적 사이트에 액세스하는 기능을 더 이상 사용할 수 없습니다. 대신 Word, PowerPoint, Excel 또는 파일 탐색기에서 **추적 및 해지** 옵션을 사용하세요. 또는 브라우저를 사용하여 [문서 추적 사이트](https://go.microsoft.com/fwlink/?LinkId=529562)로 바로 이동할 수 있습니다.

## <a name="next-steps"></a>다음 단계
Azure Information Protection 사용자 가이드의 사용 방법 지침:

- [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

## <a name="additional-information-for-administrators"></a>관리자용 추가 정보    
[Azure Information Protection 클라이언트 관리자 가이드](client-admin-guide.md)를 참조하세요.

  
