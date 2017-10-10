---
title: "Azure Information Protection의 Azure Rights Management 서비스용 Exchange Online IRM 구성"
description: "Office 365 테넌트가 Office 365 메시지 암호화의 새로운 기능을 지원하지 않을 때 관리자가 Azure Rights Management 서비스를 위해 Exchange Online을 구성하기 위한 정보 및 지침."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a0c6fe7f7b6a34eea21b646ce5573ca03b13be3c
ms.sourcegitcommit: cd3320fa34acb90f05d5d3e0e83604cdd46bd9a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2017
---
# <a name="exchange-online-irm-configuration-when-you-have-imported-a-trusted-publishing-domain"></a>트러스트된 게시 도메인을 가져온 경우 Exchange Online IRM 구성

>*적용 대상: Azure Information Protection, Office 365*

이전에 TPD(트러스트된 게시 도메인)를 가져와서 IRM용 Exchange Online을 미리 구성한 경우에만 이 지침을 사용하며, 이전에 암호화된 전자 메일의 암호를 해독할 수 있어야 합니다.

이러한 조건이 모두 해당되지 않는 경우 이 지침을 사용하지 말고 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)의 지침을 사용하십시오.

## <a name="exchange-online-irm-configuration-if-you-have-an-imported-tpd"></a>가져온 TPD가 있는 경우 Exchange Online IRM 구성

Azure Rights Management 서비스를 지원하도록 Exchange Online을 구성하려면 Exchange Online에 대해 IRM(정보 권한 관리) 서비스를 구성해야 합니다. 이렇게 하려면 Windows PowerShell을 사용하고(별도 모듈을 설치할 필요 없음) [Exchange Online용 PowerShell 명령](https://technet.microsoft.com/library/jj200677.aspx)을 실행합니다.

> [!NOTE]
> Microsoft가 Office 365 테넌트를 마이그레이션할 때까지 Azure Information Protection에 대해 Microsoft에서 관리하는 테넌트 키의 기본 구성이 아니라 고객이 관리하는 테넌트 키(BYOK)를 사용하는 경우 Azure Rights Management 서비스를 지원하도록 Exchange Online을 구성할 수 없습니다.
>
> Azure Rights Management 서비스가 BYOK를 사용하는 경우 Exchange Online을 구성하려고 하면 키를 가져오는 명령(다음 절차의 5단계)이 실패하고 **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]** 오류 메시지가 표시됩니다.

다음 단계에서는 Exchange Online에서 이 시나리오에 대해 Azure Rights Management 서비스를 사용하도록 하기 위해 실행하는 일반적인 명령 집합을 제공합니다.

1.  컴퓨터에서 Exchange Online에 대해 Windows PowerShell을 처음 사용하는 경우에는 서명된 스크립트를 실행하도록 Windows PowerShell을 구성해야 합니다. **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell 세션을 시작한 후 다음을 입력합니다.

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  Windows PowerShell 세션에서 원격 셸 액세스에 대해 사용하도록 설정된 계정을 사용하여 Exchange Online으로 로그인합니다. 기본적으로 Exchange Online에서 만든 모든 계정은 원격 셸 액세스에 사용하도록 설정되지만, [Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) 명령을 이용해 사용하지 않도록 설정(및 사용하도록 설정)할 수 있습니다.

    로그인하려면 다음을 입력합니다.

    ```
    $UserCredential = Get-Credential
    ```
    **Windows PowerShell 자격 증명 요청** 대화 상자에 Office 365 사용자 이름과 암호를 제공합니다.

3.  다음 두 명령을 실행하여 Exchange Online 서비스에 연결합니다.

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  조직의 테넌트가 생성된 위치에 따라 Azure Information Protection 테넌트 키의 위치를 지정합니다.

    북아메리카의 경우:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    유럽의 경우:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    아시아의 경우:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    남아메리카의 경우:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Office 365 Government(Government Community Cloud)의 경우:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  TPD(트러스트된 게시 도메인)의 형태로 Azure Rights Management 서비스에서 Exchange Online으로 구성 데이터를 가져옵니다. 여기에는 Azure Information Protection 테넌트 키와 Azure Rights Management 템플릿이 포함됩니다.

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    이 명령에서는 Exchange Online의 Azure Rights Management에 대한 TPD의 기본 이름으로 **RMS 온라인**을 사용했습니다. TPD를 가져오면 Exchange Online에서 **RMS Online - 1**로 이름이 지정됩니다.

6.  Exchange Online에서 IRM 기능을 사용할 수 있도록 Azure Rights Management 기능을 사용하도록 설정합니다.

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    이 명령을 실행한 후 Outlook 클라이언트, Outlook Web App, Exchange Active Sync에 대해 권한 관리가 자동으로 사용되도록 설정됩니다.

7.  필요에 따라 다음 명령을 사용하여 이 구성을 성공적으로 수행되었는지 테스트합니다.

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    예: **Test-IRMConfiguration -Sender  adams@contoso.com**

    이 명령은 서비스에 대한 연결 확인, 구성 검색, URL, 라이선스 및 템플릿 검색을 포함하는 일련의 검사를 실행합니다. Windows PowerShell 세션에 각 검사의 결과가 표시되며 이러한 모든 검사를 통과하면 맨 마지막에 다음 결과가 표시됩니다. **OVERALL RESULT: PASS**

8.  원격 PowerShell 세션 연결 끊기:

    ```
    Remove-PSSession $Session
    ```

이제 사용자는 Azure Rights Management 서비스를 사용하여 자신의 전자 메일 메시지를 보호할 수 있습니다. 예를 들어 Outlook Web App의 확장된 메뉴(**...**)에서**사용 권한 설정**을 선택한 다음 **전달 금지**를 선택하거나 전자 메일 메시지 및 첨부 파일에 정보 보호를 적용할 사용 가능한 템플릿 중 하나를 선택합니다. 그러나 Outlook Web App은 하루 동안 UI를 캐시하므로, 이러한 구성 명령을 실행하고 하루 동안 기다렸다가 전자 메일 메시지에 정보 보호를 적용합니다. 새 구성을 반영하도록 UI가 업데이트되기 전에는 **사용 권한 설정** 메뉴의 옵션이 표시되지 않습니다.

> [!IMPORTANT]
> Azure Rights Management용 [사용자 지정 템플릿](configure-custom-templates.md)을 새로 만들거나 템플릿을 업데이트하는 경우 매번 다음 Exchange Online PowerShell 명령을 실행(필요한 경우 2단계 및 3단계 먼저 실행)하여 이러한 변경 내용을 Exchange Online과 동기화해야 합니다. `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Exchange 관리자는 이제 [전송 규칙](https://technet.microsoft.com/library/dd302432.aspx), [DLP(데이터 손실 방지) 정책](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) 및 [보호된 음성 메일](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx)(통합 메시징)과 같이 정보 보호를 자동으로 적용하는 기능을 구성할 수 있습니다.


### <a name="office-365-message-encryption"></a>Office 365 메시지 암호화
이전 섹션에 설명된 동일한 단계를 실행합니다. 그렇지만 템플릿을 표시하지 않으려면 6단계 이전에 다음 명령을 실행하여 Outlook Web App 및 Outlook 클라이언트에서 IRM 템플릿을 사용할 수 없게 합니다. `Set-IRMConfiguration -ClientAccessServerEnabled $false`

그런 후에 받는 사람이 조직 외부에 있고 [Office 365 메시지 암호화 적용](https://technet.microsoft.com/library/dd302432.aspx) 옵션을 선택한 경우 메시지 보안을 자동으로 수정하도록 **전송 규칙** 을 구성할 수 있습니다.

메시지 암호화에 대한 자세한 내용은 Exchange 라이브러리의 [Office 365의 암호화](https://technet.microsoft.com/library/dn569286.aspx) 를 참조하세요.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
