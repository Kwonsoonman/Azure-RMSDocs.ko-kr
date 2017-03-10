---
title: "Azure RMS 템플릿 새로 고침 - AIP"
description: "Azure Rights Management 서비스를 사용하는 경우 사용자가 응용 프로그램에서 선택할 수 있도록 템플릿이 자동으로 클라이언트 컴퓨터로 다운로드됩니다. 그렇지만 템플릿을 변경하려면 다음의 추가 단계를 진행해야 할 수도 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e3f80781c9e998e3d7d0d515ed1b0b13b9656ab4
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="refreshing-templates-for-users"></a>사용자를 위한 템플릿 새로 고침

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection의 Azure Rights Management 서비스를 사용하는 경우 사용자가 응용 프로그램에서 선택할 수 있도록 템플릿이 자동으로 클라이언트 컴퓨터로 다운로드됩니다. 그렇지만 템플릿을 변경하려면 다음의 추가 단계를 진행해야 할 수도 있습니다.

|응용 프로그램 또는 서비스|템플릿을 변경한 후 새로 고침하는 방법|
|--------------------------|---------------------------------------------|
|Exchange Online|템플릿을 새로 고침하려면 수동 구성이 필요함<br /><br />구성 단계는 [Exchange Online에만 해당: 변경된 사용자 지정 템플릿을 다운로드하기 위한 Exchange 구성 방법](#exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates) 섹션을 참조하세요.|
|Office 365|자동으로 새로 고침 - 추가 단계 불필요|
|Office 2016 및 Office 2013<br /><br />Windows용 RMS 공유 응용 프로그램|일정에 따라 자동으로 새로 고침:<br /><br />이러한 최신 버전 Office의 경우: 기본 새로 고침 간격은 7일입니다.<br /><br />Windows용 RMS 공유 응용 프로그램: 1.0.1784.0 버전부터 기본 새로 고침 간격은 1일입니다. 이전 버전의 기본 새로 고침 간격은 7일입니다.<br /><br />이 일정보다 자주 새로 고침을 강제로 적용하려면 [Office 2016, Office 2013 및 Windows용 RMS 공유 응용 프로그램: 변경된 사용자 지정 템플릿을 강제로 새로 고치는 방법](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template) 섹션을 참조하세요.|
|Office 2010|사용자 로그인 시 새로 고침됨<br /><br />강제로 새로 고침하려면 사용자에게 로그오프한 후 다시 로그인하도록 요청하거나 강제로 적용합니다. 또는 [Office 2010에만 해당: 변경된 사용자 지정 템플릿을 강제로 새로 고치는 방법](#office-2010-only-how-to-force-a-refresh-for-a-changed-custom-template) 섹션을 참조하세요.|
RMS 공유 응용 프로그램을 사용하는 모바일 장치의 경우 템플릿은 추가 구성이 필요 없이 자동으로 다운로드되고 필요한 경우 새로 고침됩니다.

## <a name="exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates"></a>Exchange Online에만 해당: 변경된 사용자 지정 템플릿을 다운로드하기 위한 Exchange 구성 방법
Exchange Online을 위해 이미 IRM(정보 Rights Management)을 구성했다면 Exchange Online의 Windows PowerShell을 사용해 다음과 같이 변경할 때까지 사용자는 사용자 지정 템플릿을 다운로드할 수 없습니다.

> [!NOTE]
> Exchange Online에서 Windows PowerShell을 사용하는 방법에 대한 자세한 내용은 [Exchange Online에서 PowerShell 사용](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx)을 참조하세요.

템플릿을 변경할 때마다 이 절차를 진행해야 합니다.

### <a name="to-update-templates-for-exchange-online"></a>Exchange Online을 위해 템플릿을 업데이트하려면

1.  Exchange Online에서 Windows PowerShell을 사용하여 서비스에 연결:

    1.  Office 365 사용자 이름 및 암호 입력:

        ```
        $UserCredential = Get-Credential
        ```

    2.  다음 두 명령을 실행하여 Exchange Online 서비스에 연결합니다.

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Azure RMS에서 TPD(트러스트된 게시 도메인)를 다시 가져오려면 [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) cmdlet을 사용합니다.

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    예를 들어 TPD 이름이 대부분의 조직에서 일반적으로 사용하는 이름인 **RMS Online - 1**이라면 다음과 같이 입력합니다. **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > TPD 이름이 유효한지 확인하려면 [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) cmdlet을 사용합니다.

3.  템플릿이 성공적으로 가져오기 되었는지 확인하려면 몇 분 정도 기다린 후 [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) cmdlet을 실행하고 Type을 All로 설정합니다. 예를 들면 다음과 같습니다.

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > 나중에 템플릿을 보관하는 경우 템플릿 이름이나 GUID를 쉽게 복사할 수 있도록 출력 복사본을 유지하는 것이 유용합니다.

4.  Outlook Web App에서 사용할 수 있게 하려는 가져온 각 템플릿에 대해 [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet을 사용하고 Type을 Distributed로 설정해야 합니다.

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Outlook Web Access에서 24시간 동안 UI를 캐시하므로 사용자에게 새 템플릿이 최대 하루 동안 표시되지 않을 수 있습니다.

또한 템플릿(사용자 지정 또는 기본)을 보관하고 Office 365가 포함된 Exchange Online을 사용하는 경우, Exchange ActiveSync 프로토콜을 사용하는 모바일 장치 또는 Outlook Web App을 이용하는 사용자는 보관된 템플릿을 계속 볼 수 있습니다.

이러한 템플릿이 사용자에게 더 이상 표시되지 않으므로, 사용자는 Exchange Online에서 Windows PowerShell을 사용하여 서비스에 연결하고 다음 명령을 실행하여 [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) cmdlet을 사용합니다.

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

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

    **레지스트리 경로:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **형식:** REG_SZ

    **값:** LastUpdatedTime

    > [!TIP]
        > 레지스트리 경로에서 <*MicrosoftRMS_FQDN*>은 사용자의 Microsoft RMS 서비스 FQDN을 가리킵니다. 이 값을 확인하려면:

    > 1.  Azure RMS에 대해 [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet을 실행합니다. Azure RMS용 Windows PowerShell 모듈을 아직 설치하지 않은 경우 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.
    > 2.  출력에서 **LicensingIntranetDistributionPointUrl** 값을 식별합니다.
    > 
    >     예: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  이 값의 문자열에서 **https://** 및 **/_wmcs/licensing**을 제거합니다. 나머지 값이 Microsoft RMS 서비스 FQDN입니다. 이 예에서 Microsoft RMS 서비스 FQDN 값은 다음과 같습니다.
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  다음 폴더와, 그 안의 모든 파일을 삭제합니다. **%localappdata%\Microsoft\MSIPC\Templates**

3.  Office 응용 프로그램과 파일 탐색기 인스턴스를 지금 시작합니다.

## <a name="office-2010-only-how-to-force-a-refresh-for-a-changed-custom-template"></a>Office 2010에만 해당: 변경된 사용자 지정 템플릿을 강제로 새로 고치는 방법
Office 2010을 실행하는 컴퓨터에서 레지스트리를 편집하면 사용자가 로그오프하고 다시 로그인할 때까지 기다리지 않고 컴퓨터에서 변경된 템플릿을 새로 고치도록 값을 설정할 수 있습니다. 또한 레지스트리의 기존 데이터를 삭제하여 즉각적인 새로 고침을 강제 실행할 수 있습니다.

> [!WARNING]
> 레지스트리 편집기를 잘못 사용하면 운영 체제를 재설치해야 할 만큼 심각한 문제가 유발될 수 있습니다. 레지스트리 편집기를 잘못 사용하여 발생하는 문제는 해결할 수 있다는 보장이 없습니다. 레지스트리 편집기 사용에 따른 위험은 사용자가 책임져야 합니다.

### <a name="to-change-the-update-frequency"></a>업데이트 주기를 변경하려면

1.  레지스트리 편집기에서 이름이 **UpdateFrequency** 인 새 레지스트 값을 만들고 데이터에 정수 값을 정의합니다. 즉 다운로드한 템플릿에 대한 모든 변경 사항을 다운로드하는 주기를 일 단위로 지정합니다. 다음 표를 사용하여 새 레지스트리 값을 만들기 위한 레지스트리 경로를 확인합니다.

    **레지스트리 경로:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **형식:** REG_DWORD

    **값:** UpdateFrequency

2.  템플릿의 즉시 새로 고침을 강제 실행한 경우 다음 절차를 진행합니다. 그렇지 않은 경우 Office 응용 프로그램을 지금 다시 시작합니다.

### <a name="to-force-an-immediate-refresh"></a>즉시 새로 고침을 강제 실행하려면

1.  레지스트리 편집기에서 **LastUpdatedTime** 값의 데이터를 삭제합니다. 예를 들어 데이터가 **2015-04-20T15:52**로 표시된다면 2015-04-20T15:52를 삭제하여 아무 데이터도 표시되지 않게 합니다. 다음 표를 사용하여 이 레지스트리 값 데이터를 삭제하기 위한 레지스트리 경로를 확인합니다.

    **레지스트리 경로:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **형식:** REG_SZ

    **값:** lastUpdatedTime


2.  다음 폴더와, 그 안의 모든 파일을 삭제합니다. **%localappdata%\Microsoft\MSIPC\Templates**

3.  Office 응용 프로그램을 다시 시작합니다.

## <a name="see-also"></a>참고 항목
[Azure 권한 관리용 사용자 지정 템플릿 구성](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]