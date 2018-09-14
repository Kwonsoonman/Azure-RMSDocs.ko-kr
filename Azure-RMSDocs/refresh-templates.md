---
title: Azure RMS 템플릿 새로 고침 - AIP
description: Azure Rights Management 서비스를 사용하는 경우 사용자가 응용 프로그램에서 선택할 수 있도록 템플릿이 자동으로 클라이언트 컴퓨터로 다운로드됩니다. 그렇지만 템플릿을 변경하려면 다음의 추가 단계를 진행해야 할 수도 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b801266dfb757286599b5bd2fd3b36c9590717f2
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44148514"
---
# <a name="refreshing-templates-for-users-and-services"></a>사용자 및 서비스를 위한 템플릿 새로 고침

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection의 Azure Rights Management 서비스를 사용하는 경우 사용자가 응용 프로그램에서 선택할 수 있도록 템플릿이 자동으로 클라이언트 컴퓨터로 다운로드됩니다. 그렇지만 템플릿을 변경하려면 다음의 추가 단계를 진행해야 할 수도 있습니다.

|응용 프로그램 또는 서비스|템플릿을 변경한 후 새로 고침하는 방법|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />전송 규칙 및 Outlook Web App에 적용 가능 |1 시간 내에 자동으로 새로 고침 - 추가 단계가 필요하지 않습니다.<br /><br />이것은 [새로운 기능을 갖춘 Office 365 메시지 암호화](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)를 사용하는 경우입니다. 이전에 TPD(트러스트된 게시 도메인)를 가져와서 Azure Rights Management 서비스를 사용하도록 Exchange Online을 구성한 경우 동일한 지침 집합을 사용하여 Exchange Online의 새로운 기능을 사용하도록 설정하십시오.|
|Azure Information Protection 클라이언트|클라이언트에서 Azure Information Protection 정책을 새로 고칠 때마다 자동으로 새로 고침:<br /><br /> - Azure Information Protection 막대를 지원하는 Office 응용 프로그램이 열릴 때. <br /><br /> - 마우스 오른쪽 단추를 클릭하여 파일 또는 폴더를 분류 및 보호하려 할 때. <br /><br /> - 레이블 지정 및 보호를 위해 PowerShell cmdlet을 실행할 때(Get-AIPFileStatus 및 Set-AIPFileLabel).<br /><br /> - Azure Information Protection 스캐너 서비스가 시작될 때 및 로컬 정책이 1시간보다 오래되었을 때. 또한 스캐너 서비스는 매시간 변경 내용을 확인하고 이러한 변경 내용을 다음 검색 주기에 사용합니다.<br /><br /> - 24시간마다.<br /><br /> 또한 Azure Information Protection 클라이언트가 Office와 긴밀하게 통합되어 있기 때문에, Office 2016 또는 Office 2013에서 새로 고친 템플릿은 Azure Information Protection 클라이언트에서도 새로 고쳐집니다.|
|Office 2016 및 Office 2013<br /><br />Windows용 RMS 공유 응용 프로그램|일정에 따라 자동으로 새로 고침:<br /><br />- 이러한 최신 버전 Office의 경우: 기본 새로 고침 간격은 7일입니다.<br /><br />- Windows용 RMS 공유 응용 프로그램: 1.0.1784.0 버전부터 기본 새로 고침 간격은 1일입니다. 이전 버전의 기본 새로 고침 간격은 7일입니다.<br /><br />이 일정보다 자주 새로 고침을 강제로 적용하려면 [Office 2016, Office 2013 및 Windows용 RMS 공유 응용 프로그램: 변경된 사용자 지정 템플릿을 강제로 새로 고치는 방법](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template) 섹션을 참조하세요.|
|Office 2010|사용자가 Windows에서 로그아웃했다가 다시 로그인하고 1시간까지 기다리면 자동으로 새로 고침됩니다.|
|Exchange 온-프레미스와 Rights Management 커넥터<br /><br />전송 규칙 및 Outlook Web App에 적용 가능|자동으로 새로 고침 - 추가 단계 불필요 Outlook Web App은 하루 동안 UI를 캐시합니다.|
|Mac용 Office 2016|자동으로 새로 고침 - 추가 단계 불필요|
|Mac 컴퓨터용 RMS 공유 앱|자동으로 새로 고침 - 추가 단계 불필요|

클라이언트 응용 프로그램에서 템플릿을 다운로드해야 하는 경우(처음에 또는 변경 내용을 위해 새로 고칠 때) 다운로드가 완료되고 새 또는 업데이트된 템플릿이 완전히 작동하기까지 최대 15분이 걸립니다. 실제 시간은 템플릿 구성의 크기 및 복잡도, 네트워크 연결 등 여러 요소에 따라 다릅니다. 

## <a name="office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template"></a>Office 2016, Office 2013 및 Windows용 RMS 공유 응용 프로그램: 변경된 사용자 지정 템플릿을 강제로 새로 고치는 방법
Office 2016, Office 2013 또는 Windows용 RMS(Rights Management) 공유 응용 프로그램을 실행 중인 컴퓨터에서 레지스트리를 편집하여 컴퓨터에서 변경된 템플릿을 기본값보다 더 자주 새로 고치도록 자동 일정을 변경할 수 있습니다. 또한 레지스트리의 기존 데이터를 삭제하여 즉각적인 새로 고침을 강제 실행할 수 있습니다.

> [!WARNING]
> 레지스트리 편집기를 잘못 사용하면 운영 체제를 재설치해야 할 만큼 심각한 문제가 유발될 수 있습니다. 레지스트리 편집기를 잘못 사용하여 발생하는 문제는 해결할 수 있다는 보장이 없습니다. 레지스트리 편집기 사용에 따른 위험은 사용자가 책임져야 합니다.

### <a name="to-change-the-automatic-schedule"></a>자동 일정을 변경하려면

1.  레지스트리 편집기를 사용하여 다음 레지스트리 값 중 하나를 만들고 설정합니다.

    - 업데이트 빈도(일)를 설정하려면(최소 1일):  이름이 **TemplateUpdateFrequency** 인 새 레지스트 값을 만들고 데이터에 정수 값을 정의합니다. 즉 다운로드한 템플릿에 대한 모든 변경 사항을 다운로드하는 주기를 일 단위로 지정합니다. 다음 정보를 사용하여 새 레지스트리 값을 만들기 위한 레지스트리 경로를 확인합니다.

        **레지스트리 경로:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **형식:** REG_DWORD

        **값:** TemplateUpdateFrequency

    - 업데이트 주기를 초 단위로 설정하려면(최소 1초):  이름이 **TemplateUpdateFrequencyInSeconds** 인 새 레지스트 값을 만들고 데이터에 정수 값을 정의합니다. 즉 다운로드한 템플릿에 대한 모든 변경 사항을 다운로드하는 주기를 초 단위로 지정합니다. 다음 정보를 사용하여 새 레지스트리 값을 만들기 위한 레지스트리 경로를 확인합니다.

        **레지스트리 경로:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **형식:** REG_DWORD

        **값:** TemplateUpdateFrequencyInSeconds

    두 레지스트리 값 모두가 아니라 둘 중 하나만 만들어 설정해야 합니다. 모두 있는 경우 **TemplateUpdateFrequency** 를 무시합니다.

2.  템플릿의 즉시 새로 고침을 강제 실행한 경우 다음 절차를 진행합니다. 그렇지 않으면 Office 응용 프로그램과 파일 탐색기 인스턴스를 지금 다시 시작합니다.

### <a name="to-force-an-immediate-refresh"></a>즉시 새로 고침을 강제 실행하려면

1.  레지스트리 편집기에서 **LastUpdatedTime** 값의 데이터를 삭제합니다. 예를 들어 데이터가 **2015-04-20T15:52**로 표시된다면 2015-04-20T15:52를 삭제하여 아무 데이터도 표시되지 않게 합니다. 다음 정보를 참조하여 이 레지스트리 값 데이터를 삭제할 레지스트리 경로를 찾습니다.

    **레지스트리 경로:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*MicrosoftRMS_FQDN*>\Template\\<*user_alias*>

    **형식:** REG_SZ

    **값:** LastUpdatedTime

    > [!TIP]
    > 레지스트리 경로에서 <*MicrosoftRMS_FQDN*>은 사용자의 Microsoft RMS 서비스 FQDN을 가리킵니다. 이 값을 확인하려면:

    > Azure RMS에 대해 [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet을 실행합니다. Azure RMS용 Windows PowerShell 모듈을 아직 설치하지 않은 경우 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.
    >
    > 출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.
    >
    > 예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 
    > 이 값의 문자열에서 **https://** 및 **/_wmcs/licensing**을 제거합니다. 나머지 값이 Microsoft RMS 서비스 FQDN입니다. 이 예에서 Microsoft RMS 서비스 FQDN 값은 다음과 같습니다.
    >
    >**5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  다음 폴더와, 그 안의 모든 파일을 삭제합니다. **%localappdata%\Microsoft\MSIPC\Templates**

3.  Office 응용 프로그램과 파일 탐색기 인스턴스를 지금 시작합니다.


## <a name="see-also"></a>참고 항목
[Azure Information Protection 정책의 템플릿 구성 및 관리](configure-policy-templates.md)

