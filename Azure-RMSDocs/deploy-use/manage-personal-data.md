---
title: Azure Information Protection을 위한 개인 데이터 관리
description: Azure Information Protection에서 사용되는 개인 데이터 및 개인 데이터를 보고, 내보내고, 삭제하는 방법에 대한 정보입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: f42e1318e8be0d805216cffd402a9b87a1259e1e
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473851"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Azure Information Protection을 위한 개인 데이터 관리

Azure Information Protection을 구성하고 사용하는 경우 메일 주소 및 IP 주소는 Azure Information Protection 서비스에서 저장 및 사용됩니다. 이 개인 데이터는 다음 항목에서 찾을 수 있습니다.

- Azure Information Protection 정책

- Azure Rights Management 서비스에 대한 보호 템플릿

- Azure Rights Management 서비스에 대한 슈퍼 사용자 및 위임된 관리자 

- Azure Rights Management 서비스에 대한 관리 로그

- Azure Rights Management 서비스에 대한 사용 로그

- 문서 추적 로그

- Azure Information Protection 클라이언트 및 RMS 클라이언트에 대한 사용 로그 


[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Azure Information Protection에서 사용하는 개인 데이터 보기

관리자는 Azure Portal을 사용하여 범위 지정 정책에 대한 메일 주소와 레이블 구성 내 보호 정책에 대한 메일 주소를 지정할 수 있습니다. 자세한 내용은 [범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법](../deploy-use/configure-policy-scope.md) 및 [Rights Management 보호를 위한 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요. 

Azure Rights Management 서비스에서 보호를 적용하도록 구성된 레이블의 경우 [AADRM 모듈](/powershell/module/aadrm)에서 PowerShell cmdlet을 사용하여 보호 템플릿에서 메일 주소를 찾을 수도 있습니다. 또한 이 PowerShell 모듈을 통해 관리자는 [슈퍼 사용자](../deploy-use/configure-super-users.md) 또는 Azure Rights Management 서비스의 관리자가 되도록 메일 주소로 사용자를 지정할 수 있습니다. 

Azure Information Protection을 사용하여 문서 및 메일을 분류하고 보호하는 경우 메일 주소와 사용자의 IP 주소는 로그 파일에 저장됩니다.


### <a name="protection-templates"></a>보호 템플릿

[Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) cmdlet을 실행하여 보호 템플릿 목록을 가져옵니다. 템플릿 ID를 사용하여 특정 템플릿의 세부 정보를 가져올 수 있습니다. `RightsDefinitions` 개체는 개인 데이터를 표시합니다(있는 경우). 

예:
```
PS C:\Users> Get-AadrmTemplate -TemplateId fcdbbc36-1f48-48ca-887f-265ee1268f51 | select *


TemplateId              : fcdbbc36-1f48-48ca-887f-265ee1268f51
Names                   : {1033 -> Confidential}
Descriptions            : {1033 -> This data includes sensitive business information. Exposing this data to
                          unauthorized users may cause damage to the business. Examples for Confidential information
                          are employee information, individual customer projects or contracts and sales account data.}
Status                  : Archived
RightsDefinitions       : {admin@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT,
                          REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER,
                          AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@aip500.onmicrosoft.com -> VIEW,
                          VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT,
                          EDITRIGHTSDATA, OBJMODEL, OWNER, admin2@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT,
                          DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER}
ContentExpirationDate   : 1/1/0001 12:00:00 AM
ContentValidityDuration : 0
ContentExpirationOption : Never
LicenseValidityDuration : 7
ReadOnly                : False
LastModifiedTimeStamp   : 1/26/2018 6:17:00 PM
ScopedIdentities        : {}
EnableInLegacyApps      : False
LabelId                 :
```

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Azure Rights Management 서비스에 대한 슈퍼 사용자 및 위임된 관리자

[Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) cmdlet 및 [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) cmdlet을 실행하여 Azure Rights Management 서비스에 대한 슈퍼 사용자 역할이나 전역 관리자 역할이 할당된 사용자를 확인합니다. 이러한 역할 중 하나가 할당된 사용자의 경우, 해당 메일 주소가 표시됩니다.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Azure Rights Management 서비스에 대한 관리 로그

[Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) cmdlet을 실행하여 Azure Information Protection에 대한 데이터를 보호하는 Azure Rights Management 서비스에 대한 관리자 작업 로그를 가져옵니다. 이 로그에는 메일 주소 및 IP 주소 형태의 개인 데이터가 포함됩니다. 로그는 일반 텍스트로서, 다운로드된 후 특정 관리자의 세부 정보를 오프라인으로 검색할 수 있습니다.

예를 들면 다음과 같습니다.
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Azure Rights Management 서비스에 대한 사용 로그
[Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) cmdlet을 실행하여 Azure Rights Management 서비스를 사용하는 최종 사용자 작업의 로그를 검색합니다. 이 서비스는 Azure Information Protection에 대한 데이터를 보호합니다. 로그에는 메일 주소 및 IP 주소 형태의 개인 데이터가 포함될 수 있습니다. 로그는 일반 텍스트로서, 다운로드된 후 특정 관리자의 세부 정보를 오프라인으로 검색할 수 있습니다.

예를 들면 다음과 같습니다.
```
PS C:\Users> Get-AadrmUserLog -Path '.\Desktop\' -FromDate 4/1/2018 -ToDate 4/30/2018 -NumberOfThreads 10
Acquiring access to your user log…
Downloading the log for 2018-04-01.
Downloading the log for 2018-04-03.
Downloading the log for 2018-04-06.
Downloading the log for 2018-04-09.
Downloading the log for 2018-04-10.
Downloaded the log for 2018-04-01. The log is available at .\Desktop\rmslog-2018-04-01.log.
Downloaded the log for 2018-04-03. The log is available at .\Desktop\rmslog-2018-04-03.log.
Downloaded the log for 2018-04-06. The log is available at .\Desktop\rmslog-2018-04-06.log.
Downloaded the log for 2018-04-09. The log is available at .\Desktop\rmslog-2018-04-09.log.
Downloaded the log for 2018-04-10. The log is available at .\Desktop\rmslog-2018-04-10.log.
Downloading the log for 2018-04-12.
Downloading the log for 2018-04-13.
Downloading the log for 2018-04-14.
Downloading the log for 2018-04-16.
Downloading the log for 2018-04-18.
Downloaded the log for 2018-04-12. The log is available at .\Desktop\rmslog-2018-04-12.log.
Downloaded the log for 2018-04-13. The log is available at .\Desktop\rmslog-2018-04-13.log.
Downloaded the log for 2018-04-14. The log is available at .\Desktop\rmslog-2018-04-14.log.
Downloaded the log for 2018-04-16. The log is available at .\Desktop\rmslog-2018-04-16.log.
Downloaded the log for 2018-04-18. The log is available at .\Desktop\rmslog-2018-04-18.log.
Downloading the log for 2018-04-24.
Downloaded the log for 2018-04-24. The log is available at .\Desktop\rmslog-2018-04-24.log.
```   

### <a name="document-tracking-logs"></a>문서 추적 로그

[Get-AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) cmdlet을 실행하여 특정 사용자에 대한 문서 추적 사이트에서 정보를 검색합니다. 문서 로그와 연관된 추적 정보를 가져오려면 [Get-AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps) cmdlet을 사용합니다.

예를 들면 다음과 같습니다.
```
PS C:\Users> Get-AadrmDocumentLog -UserEmail "admin@aip500.onmicrosoft.com"


ContentId             : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer                : admin@aip500.onmicrosoft.com
Owner                 : admin@aip500.onmicrosoft.com
ContentName           :
CreatedTime           : 3/6/2018 10:24:00 PM
Recipients            : {
                        PrimaryEmail: johndoe@contoso.com
                        DisplayName: JOHNDOE@CONTOSO.COM
                        UserType: External,
                        PrimaryEmail: alice@contoso0110.onmicrosoft.com
                        DisplayName: ALICE@CONTOSO0110.ONMICROSOFT.COM
                        UserType: External
                        }
TemplateId            :
PolicyExpires         :
EULDuration           :
SendRegistrationEmail : True
NotificationInfo      : Enabled: False
                        DeniedOnly: False
                        Culture:
                        TimeZoneId:
                        TimeZoneOffset: 0
                        TimeZoneDaylightName:
                        TimeZoneStandardName:

RevocationInfo        : Revoked: False
                        RevokedTime:
                        RevokedBy:


PS C:\Users> Get-AadrmTrackingLog -UserEmail "admin@aip500.onmicrosoft.com"

ContentId            : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer               : admin@aip500.onmicrosoft.com
RequestTime          : 3/6/2018 10:45:57 PM
RequesterType        : External
RequesterEmail       : johndoe@contoso.com
RequesterDisplayName : johndoe@contoso.com
RequesterLocation    : IP: 167.220.1.54
                       Country: US
                       City: redmond
                       Position: 47.6812453974602,-122.120736471666

Rights               : {VIEW,OBJMODEL}
Successful           : False
IsHiddenInfo         : False
```

ObjectID에 의한 검색이 없습니다. 그러나 `-UserEmail` 매개 변수로는 제한되지 않고 제공한 메일 주소는 테넌트에 포함될 필요가 없습니다. 제공된 메일 주소가 문서 추적 로그에 저장되는 경우 문서 추적 항목이 cmdlet 출력으로 반환됩니다.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Azure Information Protection 클라이언트 및 RMS 클라이언트에 대한 사용 로그

레이블 및 보호를 문서 및 메일에 적용하면 메일 주소와 IP 주소를 다음 위치에 있는 사용자 컴퓨터의 로그 파일에 저장할 수 있습니다.

- Azure Information Protection 클라이언트: %localappdata%\Microsoft\MSIP\Logs

- RMS 클라이언트: %localappdata%\Microsoft\MSIPC\msip\Logs

또한 Azure Information Protection 클라이언트는 이 개인 데이터를 로컬 Windows 이벤트 로그 **응용 프로그램 및 서비스 로그** > **Azure Information Protection**에 기록합니다.

Azure Information Protection 클라이언트가 스캐너를 실행할 경우, 개인 데이터는 스캐너를 실행하는 Windows Server 컴퓨터의 %localappdata%\Microsoft\MSIP\Scanner\Reports에 저장됩니다.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>개인 정보에 대한 액세스 보호 및 제어
Azure Portal에서 보고 지정하는 개인 데이터는 [Azure Active Directory에서 다음 관리자 역할](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) 중 하나가 할당된 사용자만 액세스할 수 있습니다.
    
- **Information Protection 관리자**

- **보안 관리자**

- **전역 관리자 / 회사 관리자**

AADRM 모듈을 사용하여 보고 지정하는 개인 데이터는 Azure Active Directory의 **Information Protection 관리자** 역할이나 **전역 관리자/회사 관리자** 역할 또는 Azure Rights Management 서비스의 전역 관리자 역할이 할당된 사용자만 액세스할 수 있습니다.  

## <a name="updating-personal-data"></a>개인 데이터 업데이트

Azure Information Protection 정책의 범위 지정 정책 및 보호 설정에 대한 메일 주소를 업데이트할 수 있습니다. 자세한 내용은 [범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법](../deploy-use/configure-policy-scope.md) 및 [Rights Management 보호를 위한 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요. 

보호 설정의 경우, [AADRM 모듈](/powershell/module/aadrm)에서 PowerShell cmdlet을 사용하여 동일한 정보를 업데이트할 수 있습니다.

슈퍼 사용자 및 위임된 관리자에 대한 메일 주소는 업데이트할 수 없습니다. 대신에 지정된 사용자 계정을 제거하고 업데이트된 메일 주소로 사용자 계정을 추가합니다. 

### <a name="protection-templates"></a>보호 템플릿

[Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet을 실행하여 보호 템플릿을 업데이트합니다. 개인 데이터는 `RightsDefinitions` 속성 내에 있으므로 [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet을 사용하여 업데이트된 정보로 RightsDefinitions 개체를 만들고 `Set-AadrmTemplateProperty` cmdlet에서 RightsDefinitions 개체를 사용해야 합니다.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Azure Rights Management 서비스에 대한 슈퍼 사용자 및 위임된 관리자

슈퍼 사용자의 메일 주소를 업데이트해야 하는 경우:

1. [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser)를 사용하여 사용자 및 이전 메일 주소를 제거합니다.

2. [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser)를 사용하여 사용자 및 새 메일 주소를 추가합니다.

위임된 관리자의 메일 주소를 업데이트해야 하는 경우:

1. [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator)를 사용하여 사용자 및 이전 메일 주소를 제거합니다.

2. [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator)를 사용하여 사용자 및 새 메일 주소를 추가합니다.

## <a name="deleting-personal-data"></a>개인 데이터 삭제
Azure Information Protection 정책의 범위 지정 정책 및 보호 설정에 대한 메일 주소를 삭제할 수 있습니다. 자세한 내용은 [범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법](../deploy-use/configure-policy-scope.md) 및 [Rights Management 보호를 위한 레이블을 구성하는 방법](configure-policy-protection.md)을 참조하세요. 

보호 설정의 경우, [AADRM 모듈](/powershell/module/aadrm)에서 PowerShell cmdlet을 사용하여 동일한 정보를 삭제할 수 있습니다.

슈퍼 사용자 및 위임된 관리자의 메일 주소를 삭제하려면 [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) cmdlet 및 [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator)를 사용하여 이러한 사용자를 제거합니다. 

Azure Rights Management 서비스에 대한 문서 추적 로그, 관리 로그 또는 사용 로그에서 개인 데이터를 삭제하려면 다음 섹션을 사용하여 Microsoft 지원에 대한 요청을 제출합니다.

컴퓨터에 저장된 클라이언트 로그 파일 및 스캐너 로그에서 개인 데이터를 삭제하려면 표준 Windows 도구를 사용하여 파일 또는 파일 내의 개인 데이터를 삭제합니다. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Microsoft 지원을 통해 개인 데이터를 삭제하려면

다음 세 단계를 사용하여 Microsoft에서 Azure Rights Management 서비스에 대한 문서 추적 로그, 관리 로그 또는 사용 로그에서 개인 데이터를 삭제하도록 요청합니다. 

**1: 삭제 요청 시작**
[Microsoft 지원에 문의](../information-support.md#to-contact-microsoft-support)하여 테넌트에서 데이터를 삭제하기 위한 요청이 포함된 Azure Information Protection 지원 케이스를 엽니다. Azure Information Protection 테넌트의 관리자임을 증명하고, 이 프로세스를 확인하는 데 며칠이 걸린다는 것을 이해해야 합니다. 요청을 제출하는 동안 삭제해야 하는 데이터에 따라 추가 정보를 제공해야 합니다.

- 관리 로그를 삭제하려면 **종료 날짜**를 제공합니다. 해당 종료 날짜까지 모든 관리 로그가 삭제됩니다.
- 사용 로그를 삭제하려면 **종료 날짜**를 제공합니다. 해당 종료 날짜까지 모든 사용 로그가 삭제됩니다.
- 문서 추적 로그를 삭제하려면 **UserEmail**을 제공합니다. UserEmail과 관련된 모든 문서 추적 정보가 삭제됩니다.

이 데이터를 삭제하는 것은 영구적인 작업입니다. 삭제 요청이 처리된 후에는 데이터를 복구할 수 없습니다. 관리자가 삭제 요청을 제출하기 전에 필요한 데이터를 내보내는 것이 좋습니다.

**2단계: 확인 대기** Microsoft에서는 하나 이상의 로그를 삭제하는 요청이 적절한지 확인합니다. 이 프로세스는 최대 5일의 작업일이 걸릴 수 있습니다.

**3단계: 삭제 확인 가져오기** Microsoft CSS(고객 지원 서비스)는 데이터가 삭제되었다는 확인 메일을 사용자에게 보냅니다. 

## <a name="exporting-personal-data"></a>개인 데이터 내보내기
AADRM PowerShell cmdlet을 사용하는 경우 개인 데이터는 PowerShell 개체로 검색하고 내보낼 수 있습니다. PowerShell 개체를 JSON으로 변환하고 `ConvertTo-Json` cmdlet을 사용하여 저장할 수 있습니다.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>동의 없는 프로파일링 또는 마케팅에 대한 개인 데이터 사용 제한
Azure Information Protection은 개인 데이터를 기반으로 한 프로파일링 또는 마케팅에 대한 Microsoft [개인정보처리방침](https://privacy.microsoft.com/privacystatement)을 따릅니다.

## <a name="auditing-and-reporting"></a>감사 및 보고
[관리자 권한](#securing-and-controlling-access-to-personal-information)이 할당된 사용자만 개인 데이터 검색 및 내보내기에 AADRM 모듈을 사용할 수 있습니다. 이러한 작업은 다운로드 가능한 관리 로그에 기록됩니다.

삭제 작업의 경우 지원 요청은 Microsoft에서 수행한 작업에 대한 감사 및 보고 내역으로 사용됩니다. 삭제 후 삭제된 데이터는 검색 및 내보내기에 사용할 수 없으며 관리자는 AADRM 모듈에서 Get cmdlet을 사용하여 이를 확인할 수 있습니다.

