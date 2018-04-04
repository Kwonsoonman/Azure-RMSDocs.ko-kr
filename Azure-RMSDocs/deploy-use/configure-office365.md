---
title: AIP의 Azure RMS를 사용하도록 Office 365 클라이언트 및 온라인 서비스 구성
description: 관리자가 Azure Information Protection의 Azure Rights Management 서비스에서 작동하도록 Office 365를 구성하는 방법 및 지침을 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/27/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ecf30ece9370a732e0bf302be5733273b64eea1a
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="office-365-configuration-for-clients-and-online-services-to-use-the-azure-rights-management-service"></a>Office 365: 클라이언트와 온라인 서비스가 Azure Rights Management 서비스를 사용하도록 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Office 365는 기본적으로 Azure Information Protection의 Azure Rights Management 서비스를 지원하므로 Word, Excel, PowerPoint, Outlook 및 웹의 Outlook과 같은 응용 프로그램에 대해 IRM(정보 권한 관리) 기능을 지원하기 위해 클라이언트 컴퓨터를 구성할 필요가 없습니다. 모든 사용자가 수행해야 하는 작업은 [!INCLUDE[o365_1](../includes/o365_1_md.md)] 자격 증명으로 Office 응용 프로그램에 로그인하는 것입니다. 그러면 파일과 메일을 보호하고 다른 사용자가 보호한 파일과 메일을 사용할 수 있습니다.

그러나 사용자가 Office 추가 기능 및 추가 파일 형식 지원에 따른 이점을 얻을 수 있도록 Azure Information Protection 클라이언트로 이러한 응용 프로그램을 보완하는 것이 좋습니다. 자세한 내용은 [Azure Information Protection 클라이언트: 클라이언트 설치 및 구성](configure-client.md)을 참조하세요.

## <a name="exchange-online-irm-configuration"></a>Exchange Online: IRM 구성
Exchange Online IRM이 Azure Rights Management 서비스와 함께 작동하는 방식에 대한 자세한 내용은 **이해 및 탐색** 섹션에서 [Exchange Online 및 Exchange Server](../understand-explore/office-apps-services-support.md#exchange-online-and-exchange-server)를 참조하세요.

Exchange Online는 Azure Rights Management 서비스를 이미 사용하도록 설정한 상태일 수 있습니다. 확인하려면 다음 명령을 실행합니다.

1. 컴퓨터에서 Exchange Online에 대해 Windows PowerShell을 처음 사용하는 경우에는 서명된 스크립트를 실행하도록 Windows PowerShell을 구성해야 합니다. **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell 세션을 시작한 후 다음을 입력합니다.
    
        Set-ExecutionPolicy RemoteSigned
    
    **Y** 키를 눌러 확인합니다.

2. Windows PowerShell 세션에서 원격 셸 액세스에 대해 사용하도록 설정된 계정을 사용하여 Exchange Online으로 로그인합니다. 기본적으로 Exchange Online에서 만든 모든 계정은 원격 셸 액세스에 사용하도록 설정되지만, [Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) 명령을 이용해 사용하지 않도록 설정(및 사용하도록 설정)할 수 있습니다.
    
    로그인하려면 먼저 다음을 입력합니다.
    
        $Cred = Get-Credential
   
    그런 다음, **Windows PowerShell 자격 증명 요청** 대화 상자에 Office 365 사용자 이름과 암호를 제공합니다.

3. 먼저 변수를 설정하여 Exchange Online 서비스에 연결합니다.
    
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    
    그런 다음
    
        Import-PSSession $Session

4. [Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160\).aspx) 명령을 실행하여 보호 서비스의 Exchange Online 구성을 봅니다.
    
        Get-IRMConfiguration
    
    출력에서 **AzureRMSLicensingEnabled** 값을 찾을 수 있습니다.
    
    - AzureRMSLicensingEnabled를 **True**로 설정하면 Azure Rights Management 서비스에 Exchange Online을 사용하도록 설정합니다. 
    
    - AzureRMSLicensingEnabled를 **False**로 설정하면 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)에서 명령을 실행하세요. 

5. Exchange Online이 성공적으로 구성되었는지 테스트하려면 다음 명령을 실행합니다.
    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    예: **Test-IRMConfiguration -Sender  adams@contoso.com**
    
    이 명령은 서비스에 대한 연결 확인, 구성 검색, URL, 라이선스 및 템플릿 검색을 포함하는 일련의 검사를 실행합니다. Windows PowerShell 세션에 각 검사의 결과가 표시되며 이러한 모든 검사를 통과하면 맨 마지막에 다음 결과가 표시됩니다. **OVERALL RESULT: PASS**

Azure Rights Management 서비스를 사용하도록 Exchange Online을 구성할 때 [전송 규칙](https://technet.microsoft.com/library/dd302432.aspx), [DLP(데이터 손실 방지) 정책](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) 및 [보호된 음성 메일](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx)(통합 메시징)과 같이 Information Protection을 자동으로 적용하는 기능을 구성할 수 있습니다.

## <a name="sharepoint-online-and-onedrive-for-business-irm-configuration"></a>SharePoint Online 및 비즈니스용 OneDrive: IRM 구성

SharePoint Online IRM이 Azure Rights Management 서비스와 함께 작동하는 방식에 대한 자세한 내용은 **이해 및 탐색** 섹션에서 [SharePoint Online 및 SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server)를 참조하세요.

Azure Rights Management 서비스를 지원하도록 SharePoint Online 및 비즈니스용 OneDrive를 구성하려면 먼저 SharePoint 관리 센터를 통해 SharePoint Online에 대해 IRM(정보 권한 관리) 서비스가 사용되도록 해야 합니다. 그러면 사이트 소유자는 SharePoint 목록 및 문서 라이브러리를 IRM으로 보호할 수 있으며, 사용자는 비즈니스용 OneDrive 라이브러리를 IRM으로 보호하여 해당 라이브러리에 저장된 문서와 다른 사람과 공유하는 문서가 Azure Rights Management 서비스를 통해 자동으로 보호되도록 할 수 있습니다.

> [!NOTE]
> IRM으로 보호되는 SharePoint용 라이브러리 및 비즈니스용 OneDrive에는 새 OneDrive 동기화 클라이언트(OneDrive.exe)의 최신 버전이 필요합니다. 자세한 내용은 [엔터프라이즈 환경에서 새 OneDrive 동기화 클라이언트 배포](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668)를 참조하세요.

SharePoint Online에 대한 IRM(정보 권한 관리) 서비스를 사용하도록 설정하려면 Office 웹 사이트의 다음 지침을 참조하세요.

- [SharePoint 관리 센터의 IRM(정보 권한 관리) 설정](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

이 구성은 Office 365 관리자가 수행합니다.

### <a name="configuring-irm-for-libraries-and-lists"></a>라이브러리 및 목록에 대한 IRM 구성
SharePoint용 IRM 서비스를 사용하도록 설정하면 사이트 소유자는 SharePoint 문서 라이브러리 및 목록을 IRM으로 보호할 수 있습니다. 지침을 보려면 Office 웹 사이트의 다음 리소스를 참조하세요.

- [목록이나 라이브러리에 정보 권한 관리 적용](https://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

이 구성은 SharePoint 사이트 관리자가 수행합니다.

### <a name="configuring-irm-for-onedrive-for-business"></a>비즈니스용 OneDrive에 대한 IRM 구성
SharePoint Online용 IRM 서비스를 사용하도록 설정하면 Rights Management 보호를 위해 사용자의 비즈니스용 OneDrive 문서 라이브러리 또는 개별 폴더를 구성할 수 있습니다. 사용자는 해당 OneDrive 웹 사이트를 사용하여 이 기능을 스스로 구성할 수 있습니다. 관리자는 SharePoint 관리 센터를 이용하여 구성할 수는 없지만, Windows PowerShell을 사용하여 이 작업을 수행할 수 있습니다. 

> [!NOTE]
> 비즈니스용 OneDrive를 구성하는 방법에 대한 자세한 내용은 Office 설명서, [Office 365에서 비즈니스용 OneDrive 설정](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb)을 참조하세요.

#### <a name="configuration-for-users"></a>사용자를 위한 구성
비즈니스용 OneDrive로 보호되는 비즈니스 파일을 구성할 수 있도록 사용자에게 다음 지침을 제공합니다.

1. 회사 또는 학교 계정으로 Office 365에 로그인하고 [OneDrive 웹 사이트](https://portal.office.com/onedrive)로 이동합니다.

2. 탐색 창 아래쪽에서 **클래식 OneDrive로 돌아가기**를 선택합니다.

3. **설정** 아이콘을 선택합니다. **설정** 창에서 **리본**이 **꺼짐**으로 설정된 경우, 이 설정을 선택하여 리본을 켭니다.

4. 비즈니스용 OneDrive 파일을 모두 보호하도록 구성하려면 리본에서 **라이브러리** 탭을 선택한 다음, **라이브러리 설정**을 선택합니다. 보호할 특정 폴더의 모든 파일을 선택하려면 먼저 해당 폴더를 선택합니다.

5. **문서 > 설정** 페이지의 **사용 권한 및 관리** 섹션에서 **정보 권한 관리**를 선택합니다.

6. **정보 권한 관리 설정** 페이지에서 **다운로드 시 라이브러리의 사용 권한 제한** 확인란을 선택합니다. 사용 권한에 대한 이름 및 설명을 지정하고, 필요에 따라 선택적 구성을 구성하려면 **SHOW OPTIONS**를 클릭한 다음, **확인**를 클릭합니다.

    구성 옵션에 대한 자세한 내용은 Office 설명서에서 [목록이나 라이브러리에 정보 권한 관리 적용](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) 의 지침을 참조하세요.

이 구성에서 관리자가 아닌 사용자는 비즈니스용 OneDrive 파일을 IRM으로 보호해야 하므로 파일을 보호할 때의 이점과 보호 방법을 사용자에게 교육합니다. 예를 들어 비즈니스용 OneDrive에서 문서를 공유하는 경우 파일 이름을 바꾸고 다른 위치로 복사하더라도 권한을 받은 사람만 구성된 제한에 따라 문서에 액세스할 수 있습니다.

#### <a name="configuration-for-administrators"></a>관리자를 위한 구성
관리자가 SharePoint 관리 센터를 이용해 사용자의 비즈니스용 OneDrive에 대한 IRM을 구성할 수는 없지만, Windows PowerShell을 이용해 구성할 수는 있습니다. 이러한 라이브러리에 대한 IRM을 사용하도록 설정하려면 다음 단계를 수행합니다.

1.  [SharePoint Online 클라이언트 구성 요소 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=42038)를 다운로드하여 설치합니다.

2.  [SharePoint Online 관리 셸](https://www.microsoft.com/en-us/download/details.aspx?id=35588)을 다운로드하여 설치합니다.

3.  다음 스크립트의 콘텐츠를 복사하고 컴퓨터에 Set-IRMOnOneDriveForBusiness.ps1 파일의 이름을 지정합니다.

    *&#42;&#42;고지 사항&#42;&#42;*: 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.

    ```
    # Requires Windows PowerShell version 3

    <#
      Description:

        Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

     Script Installation Requirements:

       SharePoint Online Client Components SDK
       https://www.microsoft.com/en-us/download/details.aspx?id=42038

       SharePoint Online Management Shell
       https://www.microsoft.com/en-us/download/details.aspx?id=35588

    ======
    #>

    # URL will be in the format https://<tenant-name>-admin.sharepoint.com
    $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

    $tenantAdmin = "admin@contoso.com"

    $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user3_contoso_com")

    <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
       Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

    #>

    $listTitle = "Documents"

    function Load-SharePointOnlineClientComponentAssemblies
    {
        [cmdletbinding()]
        param()

        process
        {
            # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
            try
            {
                Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                return $true
            }
            catch
            {
                if($_.Exception.Message -match "Could not load file or assembly")
                {
                    Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
                }
                else
                {
                    Write-Error -Exception $_.Exception
                }
                return $false
            }
        }
    }

    function Load-SharePointOnlineModule
    {
        [cmdletbinding()]
        param()

        process
        {
            do
            {
                # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
                $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

                if(-not $spoModule)
                {
                    try
                    {
                        Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                        return $true
                    }
                    catch
                    {
                        if($_.Exception.Message -match "Could not load file or assembly")
                        {
                            Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                        }
                        else
                        {
                            Write-Error -Exception $_.Exception
                        }
                        return $false
                    }
                }
                else
                {
                    return $true
                }
            }
            while(-not $spoModule)
        }
    }

    function Set-IrmConfiguration
    {
        [cmdletbinding()]
        param(
            [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List,
            [parameter(Mandatory=$true)][string]$PolicyTitle,
            [parameter(Mandatory=$true)][string]$PolicyDescription,
            [parameter(Mandatory=$false)][switch]$IrmReject,
            [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate,
            [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView,
            [parameter(Mandatory=$false)][switch]$AllowPrint,
            [parameter(Mandatory=$false)][switch]$AllowScript,
            [parameter(Mandatory=$false)][switch]$AllowWriteCopy,
            [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays,
            [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays,
            [parameter(Mandatory=$false)][string]$GroupName
        )

        process
        {
            Write-Verbose "Applying IRM Configuration on '$($List.Title)'"

            # reset the value to the default settings
            $list.InformationRightsManagementSettings.Reset()

            $list.IrmEnabled = $true

            # IRM Policy title and description

                $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle
                $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription

            # Set additional IRM library settings

                # Do not allow users to upload documents that do not support IRM
                $list.IrmReject = $IrmReject.IsPresent

                $parsedDate = Get-Date
                if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate))
                {
                    # Stop restricting access to the library at <date>
                    $list.IrmExpire = $true
                    $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate
                }

                # Prevent opening documents in the browser for this Document Library
                $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent

            # Configure document access rights

                # Allow viewers to print
                $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent

                # Allow viewers to run script and screen reader to function on downloaded documents
                $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent

                # Allow viewers to write on a copy of the downloaded document
                $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent

                if($DocumentAccessExpireDays)
                {
                    # After download, document access rights will expire after these number of days (1-365)
                    $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true
                    $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays
                }

            # Set group protection and credentials interval

                if($LicenseCacheExpireDays)
                {
                    # Users must verify their credentials using this interval (days)
                    $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true
                    $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays
                }

                if($GroupName)
                {
                    # Allow group protection. Default group:
                    $list.InformationRightsManagementSettings.EnableGroupProtection = $true
                    $list.InformationRightsManagementSettings.GroupName             = $GroupName
                }
        }
        end
        {
            if($list)
            {
                Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
                $list.InformationRightsManagementSettings.Update()
                $list.Update()
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()
            }
        }
    }

    function Get-CredentialFromCredentialCache
    {
        [cmdletbinding()]
        param([string]$CredentialName)

        #if( Test-Path variable:\global:CredentialCache )
        if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
        {
            if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
            {
                Write-Verbose "Credential Cache Hit: $CredentialName"
                return $global:O365TenantAdminCredentialCache[$CredentialName]
            }
        }
        Write-Verbose "Credential Cache Miss: $CredentialName"
        return $null
    }

    function Add-CredentialToCredentialCache
    {
        [cmdletbinding()]
        param([System.Management.Automation.PSCredential]$Credential)

        if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
        {
            Write-Verbose "Initializing the Credential Cache"
            $global:O365TenantAdminCredentialCache = @{}
        }

        Write-Verbose "Adding Credential to the Credential Cache"
        $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
    }

    # load the required assemblies and Windows PowerShell modules

        if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

    # Add the credentials to the client context and SharePoint Online service connection

        # check for cached credentials to use
        $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

        if(-not $o365TenantAdminCredential)
        {
            # when credentials are not cached, prompt for the tenant admin credentials
            $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

            if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
            {
                Write-Error -Message "Could not validate the supplied tenant admin credentials"
                return
            }

            # add the credentials to the cache
            Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
        }

    # connect to Office365 first, required for SharePoint Online cmdlets to run

        Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

    # enumerate each of the specified site URLs

        foreach($webUrl in $webUrls)
        {
            $grantedSiteCollectionAdmin = $false

            try
            {
                # establish the client context and set the credentials to connect to the site
                $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
                $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

                # initialize the site and web context
                $script:clientContext.Load($script:clientContext.Site)
                $script:clientContext.Load($script:clientContext.Web)
                $script:clientContext.ExecuteQuery()

                # load and ensure the tenant admin user account if present on the target SharePoint site
                $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
                $script:clientContext.Load($tenantAdminUser)
                $script:clientContext.ExecuteQuery()

                # check if the tenant admin is a site admin
                if( -not $tenantAdminUser.IsSiteAdmin )
                {
                    try
                    {
                        # grant the tenant admin temporary admin rights to the site collection
                        Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                        $grantedSiteCollectionAdmin = $true
                    }
                    catch
                    {
                        Write-Error $_.Exception
                        return
                    }
                }

                try
                {
                    # load the list orlibrary using CSOM

                    $list = $null
                    $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                    $script:clientContext.Load($list)
                    $script:clientContext.ExecuteQuery()

                    # **************  ADMIN INSTRUCTIONS  **************
                    # If necessary, modify the following Set-IrmConfiguration parameters to match your required values
                    # The supplied options and values are for example only
                    # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90

                    Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users"  
                }
                catch
                {
                    Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
                }
           }
           finally
           {
                if($grantedSiteCollectionAdmin)
                {
                    # remove the temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
                }
           }
        }

    Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  스크립트를 검토하고 다음과 같이 변경합니다.

    1.  `$sharepointAdminCenterUrl`을 검색하고 예제 값을 SharePoint 관리 센터 URL로 바꿉니다.

        이 값은 SharePoint 관리 센터로 이동할 때 기준 URL로 확인되며, https://*&lt;tenant_name&gt;*-admin.sharepoint.com 형식을 사용합니다.

        예를 들어 테넌트 이름이 "contoso"인 경우 다음을 지정합니다. **https://contoso-admin.sharepoint.com**

    2.  `$tenantAdmin`을 검색하고 예제 값을 Office 365에 대해 정규화된 전역 관리자 계정으로 바꿉니다.

        이 값은 전역 관리자로 Office 365 관리 포털에 로그인하는 데 사용하는 값과 같으며, user_name@*&lt;테넌트 도메인 이름&gt;*.com 형식을 사용합니다.

        예를 들어 "contoso.com" 테넌트 도메인에 대한 Office 365 전역 관리자 사용자 이름이 "admin"인 경우 **admin@contoso.com**으로 지정합니다.

    3.  `$webUrls`를 검색하고 필요한 만큼 항목을 추가하거나 삭제하여 예제 값을 사용자의 비즈니스용 OneDrive 웹 URL로 바꿉니다.

        또는 구성하는 데 필요한 URL이 모두 포함된 .CSV 파일을 가져와 이 배열을 바꾸는 방법에 대한 스크립트의 설명을 참조하세요.  자동으로 검색하고 URL을 추출하여 이 .CSV 파일을 채울 수 있는 또 다른 샘플 스크립트를 제공했습니다. 이 작업을 수행할 준비가 되었으면 이러한 단계 바로 뒤에 있는 [모든 비즈니스용 OneDrive URL을 .CSV 파일로 출력하는 추가 스크립트](#additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file) 섹션을 사용합니다.

        사용자의 비즈니스용 OneDrive에 대한 웹 URL의 형식은 https://*&lt;테넌트 이름&gt;*-my.sharepoint.com/personal/*&lt;사용자_이름&gt;*_*&lt;테넌트 이름&gt;*_com입니다.

        예를 들어 contoso 테넌트의 사용자 이름이 "rsimone"인 경우 다음을 지정합니다. **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  비즈니스용 OneDrive를 구성하는 스크립트를 사용 중이므로 `$listTitle` 변수의 값 **Documents**를 변경하지 마세요.

    5.  `ADMIN INSTRUCTIONS`를 검색합니다. 이 섹션의 변경 사항을 적용하지 않으면 사용자의 비즈니스용 OneDrive가 "보호된 파일"이라는 정책 제목과 "이 정책은 권한 있는 사용자에 대한 액세스 권한을 제한합니다."라는 설명으로 IRM에 대해 구성됩니다.  대부분의 환경에 적합한 다른 IRM 옵션은 설정되지 않습니다. 그러나 제안된 정책 제목과 설명을 변경할 수 있고, 사용 중인 환경에 적합한 다른 IRM 옵션을 추가할 수도 있습니다. Set-IrmConfiguration 명령에 고유한 매개 변수 집합을 생성하려면 스크립트에 설명된 예제를 참조하세요.

5.  스크립트를 저장한 후 서명합니다. 스크립트에 서명(더 안전)하지 않은 경우 컴퓨터에서 Windows PowerShell을 구성하여 서명되지 않은 스크립트를 실행해야 합니다. 이렇게 하려면 **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell 세션을 실행하고 **Set-ExecutionPolicy Unrestricted**를 입력합니다. 그러나 이 구성에서는 서명되지 않은 모든 스크립트를 실행할 수 있으므로 보안 수준이 낮습니다.

    Windows PowerShell 스크립트에 서명을 하는 방법에 대한 자세한 내용은 PowerShell 문서 라이브러리에서 [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) 을 참조하세요.

6.  스크립트를 실행하고 메시지가 표시되면 Office 365 관리자 계정의 암호를 입력합니다. 스크립트를 수정하고 동일한 Windows PowerShell 세션에서 실행 하는 경우 자격 증명을 입력하라는 메시지가 표시되지 않습니다.

> [!TIP]
> 이 스크립트를 사용하여 SharePoint Online 라이브러리에 대한 IRM도 구성할 수 있습니다. 이 구성에서는 라이브러리에 보호된 문서만 포함되도록 추가 옵션인 **IRM을 지원하지 않는 문서의 업로드 허용 안 함**을 사용하도록 설정할 수 있습니다.    이렇게 하려면 스크립트의 Set-IrmConfiguration 명령에 `-IrmReject` 매개 변수를 추가합니다.
>
> 또한 `$webUrls` 변수(예: **https://contoso.sharepoint.com**) 및 `$listTitle`변수(예:**$Reports**)를 수정해야 합니다.

사용자의 비즈니스용 OneDrive 라이브러리에 대해 IRM을 사용하지 않도록 설정해야 하는 경우 [비즈니스용 OneDrive에 대해 IRM을 사용하지 않도록 설정하는 스크립트](#script-to-disable-irm-for-onedrive-for-business) 섹션을 참조하세요.

##### <a name="additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file"></a>모든 비즈니스용 OneDrive URL을 .CSV 파일로 출력하는 추가 스크립트
4c 위의 단계에서 다음 Windows PowerShell 스크립트를 사용해 모든 사용자의 Business용 OneDrive 라이브러리의 URL을 추출할 수 있습니다. 그런 다음 확인해서 필요한 경우 편집하여 기본 스크립트로 가져올 수 있습니다.

이 스크립트에는 [SharePoint Online 클라이언트 구성 요소 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038)와 [SharePoint Online 관리 셸](http://www.microsoft.com/en-us/download/details.aspx?id=35588)도 필요합니다. 동일한 지침에 따라 복사하여 붙여넣고 파일을 로컬로 저장(예: "Report-OneDriveForBusinessSiteInfo.ps1")한 다음 `$sharepointAdminCenterUrl` 및 `$tenantAdmin` 값을 이전과 마찬가지로 수정하고 스크립트를 실행합니다.

*&#42;&#42;고지 사항&#42;&#42;*: 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv").

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

# URL will be in the format https://<tenant-name>-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.onmicrosoft.com"                           

$reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv"

$oneDriveForBusinessSiteUrls= @()
$resultsProcessed = 0

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# establish the client context and set the credentials to connect to the site

    $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl)
    $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

# run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs

    do
    {
        # build the query object
        $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext)
        $query.TrimDuplicates        = $false
        $query.RowLimit              = 500
        $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site"
        $query.StartRow              = $resultsProcessed
        $query.TotalRowsExactMinimum = 500000

        # run the query
        $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext)
        $queryResults = $searchExecutor.ExecuteQuery($query)
        $clientContext.ExecuteQuery()

        # enumerate the search results and store the site URLs
        $queryResults.Value[0].ResultRows | % {
            $oneDriveForBusinessSiteUrls += $_.Path
            $resultsProcessed++
        }
    }
    while($resultsProcessed -lt $queryResults.Value.TotalRows)

$oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

##### <a name="script-to-disable-irm-for-onedrive-for-business"></a>비즈니스용 OneDrive에 대한 IRM를 사용하지 않도록 설정하는 스크립트
사용자의 비즈니스용 OneDrive에 대한 IRM을 사용하지 않도록 설정해야 하는 경우 다음 샘플 스크립트를 사용합니다.

이 스크립트에는 [SharePoint Online 클라이언트 구성 요소 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038)와 [SharePoint Online 관리 셸](http://www.microsoft.com/en-us/download/details.aspx?id=35588)도 필요합니다. 콘텐츠를 복사하여 붙여넣고 파일을 로컬로 저장(예: "Disable-IRMOnOneDriveForBusiness.ps1")한 다음 `$sharepointAdminCenterUrl` 및 `$tenantAdmin` 값을 수정합니다. 비즈니스용 OneDrive URL을 수동으로 지정하거나 이전 섹션의 스크립트를 사용하여 해당 URL을 가져온 다음 스크립트를 실행합니다.

*&#42;&#42;고지 사항&#42;&#42;*: 이 샘플 스크립트는 Microsoft 표준 지원 프로그램 또는 서비스를 통해 지원되지 않습니다. 이 샘플 스크립트는 어떤 종류의 보증도 없이 있는 그대로 제공됩니다.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/person3_contoso_com")

<# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#>

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Remove-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List
    )

    process
    {
        Write-Verbose "Disabling IRM Configuration on '$($List.Title)'"

        $List.IrmEnabled = $false
        $List.IrmExpire  = $false
        $List.IrmReject  = $false
        $List.InformationRightsManagementSettings.Reset()
    }
    end
    {
        if($List)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false

        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin )
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()

               Remove-IrmConfiguration -List $list                 
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue
```

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
