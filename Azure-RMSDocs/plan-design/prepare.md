---
title: "Azure Information Protection에 대한 사용자 및 그룹 준비"
description: "조직의 문서와 이메일을 분류하고, 레이블을 지정하고, 보호해야 하는 사용자 및 그룹 계정이 있는지 확인합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: de06bc202ff60e6850ba217fe7ded79c0753d925
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="preparing-users-and-groups-for-azure-information-protection"></a>Azure Information Protection에 대한 사용자 및 그룹 준비

>*적용 대상: Azure Information Protection, Office 365*

조직의 Azure Information Protection을 배포하기 전에, 조직의 테넌트에 대한 Azure AD의 사용자 및 그룹 계정이 있는지 확인합니다.

다음을 포함하여 사용자 및 그룹에 대한 계정을 만드는 여러 가지 방법이 있습니다.

- Office 365 관리 센터에서 사용자를 만들고, Exchange Online 관리 센터에서 그룹을 만듭니다.

- Azure Portal에서 사용자 및 그룹을 만듭니다.

- Azure AD PowerShell 및 Exchange Online cmdlet을 사용하여 사용자 및 그룹을 만듭니다.

- 온-프레미스 Active Directory에 사용자 및 그룹을 만들고 Azure AD와 동기화합니다.

- 다른 디렉터리에 사용자 및 그룹을 만들고 Azure AD와 동기화합니다.

이 목록의 처음 세 가지 방법으로 사용자 및 그룹을 만들면 Azure AD에도 자동으로 생성되고 Azure Information Protection에서 이러한 계정을 직접 사용할 수 있습니다. 하지만 많은 엔터프라이즈 네트워크에서 온-프레미스 디렉터리를 사용하여 사용자 및 그룹을 만들고 관리합니다. Azure Information Protection은 이러한 계정을 직접 사용할 수 없으므로 계정을 Azure AD와 동기화해야 합니다.

## <a name="how-users-and-groups-are-used-by-azure-information-protection"></a>Azure Information Protection에서 사용자 및 그룹을 사용하는 방식

Azure Information protection에서 사용자 및 그룹을 사용하는 세 가지 시나리오가 있습니다.

- **사용자에게 레이블 할당** - 레이블 및 분류를 사용하는 경우. 오직 관리자만이 다음과 같은 그룹을 선택할 수 있습니다.

    - 기본 Azure Information Protection 정책이 테넌트의 Azure AD에 있는 모든 사용자에게 자동으로 할당됩니다. 그러나 범위 지정 정책을 사용하면 지정된 사용자 또는 그룹에 레이블을 추가로 할당할 수 있습니다.     

- **사용 권한 및 액세스 제어 할당** - 문서와 이메일을 보호하기 위해 Azure Rights Management 서비스를 사용하는 경우. 관리자와 사용자는 다음과 같은 사용자 및 그룹을 선택할 수 있습니다.

    - 사용 권한은 사용자가 문서 또는 이메일을 열 수 있는지 여부와 사용 방법을 결정합니다. 예를 들어 읽기만 가능하도록 또는 읽고 인쇄할 수 있도록 또는 읽고 편집할 수 있도록 지정할 수 있습니다.

    - 액세스 제어는 만료 날짜 및 액세스하려면 인터넷 연결이 필요한지 여부를 포함합니다.

- **Azure Rights Management 서비스 구성** - 특정 시나리오를 지원하려는 경우. 따라서 오직 관리자만이 이러한 그룹을 선택합니다. 다음 구성을 예로 들 수 있습니다.

    - eDiscovery 또는 데이터 복구에 필요한 경우 지정된 서비스 또는 사람이 암호화된 콘텐츠를 열 수 있도록 슈퍼 사용자를 구성합니다.

    - Azure Rights Management 서비스의 위임된 관리를 구성합니다.

    - 단계별 배포를 지원하기 위한 온보딩 컨트롤을 구성합니다.

**사용자에게 레이블 할당** - 문서 및 이메일에 레이블을 적용할 수 있도록 Azure Information Protection 정책을 구성하는 경우. 오직 관리자만이 다음과 같은 사용자 및 그룹을 선택할 수 있습니다.

- 기본 Azure Information Protection 정책이 테넌트의 Azure AD에 있는 모든 사용자에게 자동으로 할당됩니다. 그러나 범위 지정 정책을 사용하면 지정된 사용자 또는 그룹에 레이블을 추가로 할당할 수 있습니다.     

**사용 권한 및 액세스 제어 할당** - 문서와 이메일을 보호하기 위해 Azure Rights Management 서비스를 사용하는 경우. 관리자와 사용자는 다음과 같은 사용자 및 그룹을 선택할 수 있습니다.

- 사용 권한은 사용자가 문서 또는 이메일을 열 수 있는지 여부와 사용 방법을 결정합니다. 예를 들어 읽기만 가능하도록 또는 읽고 인쇄할 수 있도록 또는 읽고 편집할 수 있도록 지정할 수 있습니다. 

- 액세스 제어는 만료 날짜 및 액세스하려면 인터넷 연결이 필요한지 여부를 포함합니다. 

**Azure Rights Management 서비스 구성** - 특정 시나리오를 지원하려는 경우. 따라서 오직 관리자만이 이러한 그룹을 선택합니다. 다음 구성을 예로 들 수 있습니다.

- eDiscovery 또는 데이터 복구에 필요한 경우 지정된 서비스 또는 사람이 암호화된 콘텐츠를 열 수 있도록 슈퍼 사용자를 구성합니다.

- Azure Rights Management 서비스의 위임된 관리를 구성합니다.

- 단계별 배포를 지원하기 위한 온보딩 컨트롤을 구성합니다.

## <a name="azure-information-protection-requirements-for-user-accounts"></a>사용자 계정에 대한 Azure Information Protection 요구 사항

레이블 할당:

- Azure AD의 모든 사용자 계정은 사용자에게 추가 레이블을 할당하는 범위 지정 정책을 구성하는 데 사용할 수 있습니다.

사용 권한 및 액세스 제어를 할당하고 Azure Rights Management 서비스 구성:

- 사용자 인증에는 Azure AD의 두 가지 특성 **proxyAddresses** 및 **userPrincipalName**이 사용됩니다.

- **Azure AD proxyAddresses** 특성은 계정의 모든 이메일 주소를 저장하며 다른 방법으로 채울 수 있습니다. 예를 들어 Exchange Online 사서함을 갖고 있는 Office 365 사용자는 이 특성에 저장된 이메일 주소를 자동으로 갖습니다. Office 365 사용자에 대한 대체 이메일 주소를 할당하는 경우 그 주소도 이 특성에 저장됩니다. 온-프레미스 계정에서 동기화되는 이메일 주소로 채워질 수도 있습니다. 
    
    도메인이 테넌트에 추가된 경우("확인된 도메인") Azure Information Protection은 이 Azure AD proxyAddresses 특성의 아무 값이나 사용할 수 있습니다. 도메인 확인에 대한 자세한 내용은 다음 항목을 참조하세요.
    
    - Azure AD: [Azure Active Directory에 사용자 지정 도메인 이름 추가](/active-directory/active-directory-add-domain)

    - Office 365: [Office 365에 도메인 및 사용자 추가](https://go.microsoft.com/fwlinkid/?linkid=847121)

- **Azure AD userPrincipalName** 특성은 테넌트의 계정이 Azure AD proxyAddresses 특성에서 값을 갖지 않는 경우에만 사용됩니다. 예를 들어 Azure Portal에서 사용자를 만들거나 사서함이 없는 Office 365 사용자를 만듭니다.

### <a name="assigning-usage-rights-and-access-controls-to-external-users"></a>외부 사용자에게 사용 권한 및 액세스 제어 할당

Azure Information Protection은 Azure AD proxyAddresses 및 Azure AD userPrincipalName 특성을 테넌트의 사용자에게 사용할 때와 동일한 방식으로 사용하여 다른 테넌트의 사용자를 인증합니다.

새 기능이 추가된 Office 365 메시지 암호화를 사용하여 Azure AD에 계정이 없는 사용자에게 이메일이 발송되면 해당 사용자는 먼저 소셜 ID 공급자와 함께 페더레이션을 사용하여 또는 일회용 암호를 사용하여 인증됩니다. 그리고 보호된 이메일에 지정된 이메일 주소를 사용하여 사용자에게 권한을 부여합니다.

## <a name="azure-information-protection-requirements-for-group-accounts"></a>그룹 계정에 대한 Azure Information Protection 요구 사항

레이블 할당:

- 그룹 구성원에게 추가 레이블을 할당하는 범위 지정 정책을 구성하려면 Azure AD의 그룹 중에서 사용자의 테넌트에 대한 확인된 도메인이 포함된 이메일 주소가 있는 그룹 유형을 사용하면 됩니다. 이메일 주소가 있는 그룹을 메일 사용이 가능한 그룹이라고도 합니다.
    
    예를 들어 메일 사용이 가능한 보안 그룹, 배포 목록(정적 또는 동적) 및 Office 365 그룹을 사용할 수 있습니다. 보안 그룹(동적 또는 정적)은 이메일 주소가 없기 때문에 사용할 수 없습니다.

사용 권한 및 액세스 제어 할당:

- Azure AD의 그룹 중에서 사용자의 테넌트에 대한 확인된 도메인이 포함된 이메일 주소가 있는 그룹 유형을 사용할 수 있습니다. 이메일 주소가 있는 그룹을 메일 사용이 가능한 그룹이라고도 합니다. 

Azure Rights Management 서비스 구성:

- Azure AD의 그룹 중에서 테넌트에서 확인된 도메인의 이메일 주소가 있는 그룹 유형을 사용할 수 있지만, 한 가지 예외가 있습니다. 그룹을 사용하도록 온보딩 컨트롤을 구성하는 경우 그 그룹은 테넌트의 Azure AD에 있는 보안 그룹이어야 합니다.

- 테넌트에 있는 확인된 도메인에서 Azure AD의 아무 그룹이나(이메일 주소 유무에 관계없이) Azure Rights Management 서비스의 위임된 관리에 사용할 수 있습니다.

### <a name="assigning-usage-rights-and-access-controls-to-external-groups"></a>외부 그룹에 사용 권한 및 액세스 제어 할당

Azure Information Protection은 Azure AD proxyAddresses 특성을 테넌트의 그룹에 사용할 때와 동일한 방식으로 사용하여 다른 테넌트의 그룹을 인증합니다.

## <a name="using-accounts-from-active-directory-on-premises-for-azure-information-protection"></a>Active Directory 온-프레미스의 계정을 Azure Information Protection에 사용

온-프레미스에서 관리되는 계정을 Azure Information Protection에 사용하려면 계정을 Azure AD에 동기화해야 합니다. [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect)를 사용하면 간편하게 배포할 수 있습니다. 하지만 같은 결과를 얻을 수 있다면 다른 디렉터리 동기화 방법을 사용해도 됩니다.

계정을 동기화할 때 모든 특성을 동기화할 필요는 없습니다. 동기화해야 하는 특성 목록은 Azure Active Directory 설명서의 [Azure RMS 단원](/azure/active-directory/connect/active-directory-aadconnectsync-attributes-synchronized#azure-rms)을 참조하세요.

Azure Rights Management의 특성 목록에서 사용자의 경우 동기화에 **mail**, **proxyAddresses** 및 **userPrincipalName** 온-프레미스 AD 특성이 필요합니다. **mail** 및 **proxyAddresses**의 값은 Azure AD proxyAddresses 특성에 동기화됩니다. 자세한 내용은 [Azure AD에서 proxyAddresses 특성이 채워지는 방식](https://support.microsoft.com/help/3190357/how-the-proxyaddresses-attribute-is-populated-in-azure-ad)을 참조하세요.

## <a name="confirming-your-users-and-groups-are-prepared-for-azure-information-protection"></a>Azure Information Protection에 대한 사용자 및 그룹의 준비 상태 확인

Azure AD PowerShell을 사용하여 사용자 및 그룹을 Azure Information Protection에 사용할 수 있는지 확인할 수 있습니다. PowerShell을 사용하여 사용자 및 그룹 인증에 사용할 수 있는 값을 확인할 수도 있습니다. 

예를 들어 Azure Active Directory에 대한 V1 PowerShell 모듈을 사용하면 [MSOnline](/powershell/module/msonline/?view=azureadps-1.0)이 PowerShell 세션에서 서비스에 연결하고 전역 관리자 자격 증명을 제공합니다.

    Connect-MsolService


참고: 이 명령이 작동하지 않으면 `Install-Module MSOnline` 명령을 실행하여 MSOnline 모듈을 설치할 수 있습니다.

다음으로, 값이 잘리지 않도록 PowerShell 세션을 구성합니다.

    $Formatenumerationlimit =-1

### <a name="confirm-user-accounts-are-ready-for-azure-information-protection"></a>사용자 계정을 Azure Information Protection에 사용할 수 있는지 확인

사용자 계정을 확인하려면 다음 명령을 실행합니다.

    Get-Msoluser | select DisplayName, UserPrincipalName, ProxyAddresses

우선 Azure Information Protection에 사용할 사용자가 표시되는지 확인합니다.

그 후 **ProxyAddresses** 열이 채워져 있는지 확인합니다. 채워져 있으면 이 열의 이메일 값을 사용하여 사용자에게 Azure Information Protection에 대한 권한을 부여 할 수 있습니다.

**ProxyAddresses** 열이 채워져 있지 않으면 **UserPrincipalName**의 값을 사용하여 사용자에게 Azure Rights Management 서비스에 대한 권한이 부여됩니다.

예를 들어 다음과 같이 사용할 수 있습니다.

|표시 이름|UserPrincipalName|ProxyAddresses
|-------------------|-----------------|--------------------|
|Jagannath Reddy |jagannathreddy@contoso.com|{}|
|Ankur Roy|ankurroy@contoso.com|{SMTP:ankur.roy@contoso.com, smtp: ankur.roy@onmicrosoft.contoso.com}|

이 예에서는 다음과 같습니다.

- Jagannath Reddy의 사용자 계정은 **jagannathreddy@contoso.com**을 사용하여 승인됩니다.

-  Ankur Roy의 사용자 계정은 **ankur.roy@contoso.com** 및 **ankur.roy@onmicrosoft.contoso.com**을 사용하여 승인할 수 있지만 **ankurroy@contoso.com**으로는 승인할 수 없습니다.

대부분의 경우 UserPrincipalName의 값이 ProxyAddresses 필드의 값 중 하나와 일치합니다. 이 구성을 권장하지만, 이메일 주소와 일치하도록 UPN을 변경할 수 없는 경우 다음 단계를 수행해야 합니다.

1. UPN 값의 도메인 이름이 Azure AD 테넌트에 대해 확인된 도메인인 경우 Azure AD에서 UPN 값을 또 다른 이메일 주소로 추가해야만 UPN 값을 사용하여 Azure Information Protection에 대해 사용자 계정을 인증할 수 있습니다.

    UPN 값의 도메인 이름이 테넌트에 대해 확인되지 않은 도메인인 경우 Azure Information Protection에 사용할 수 없습니다. 그러나 그룹 이메일 주소에서 확인된 도메인 이름을 사용하는 경우에는 계속해서 사용자를 그룹 구성원으로 인증할 수 있습니다.

2. UPN을 라우팅할 수 없는 경우(예를 들어 **ankurroy@contoso.local**) 사용자의 대체 로그인 ID를 구성하고 이 대체 로그인을 사용하여 Office에 로그인하는 방법을 알려주어야 합니다. Office에 대한 레지스트리 키도 설정해야 합니다.

    자세한 내용은 [대체 로그인 ID 구성](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) 및 [Office 응용 프로그램에서 주기적으로 SharePoint Online, OneDrive 및 Lync Online 자격 증명 요청](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online)을 참조하세요.

> [!TIP]
> Export-csv cmdlet을 사용하여 결과를 스프레드시트로 내보내면 관리가 용이합니다. 예를 들어 가져올 데이터를 검색하고 대량으로 편집할 수 있습니다.
>
> 예: `Get-MsolGroup | select DisplayName, ProxyAddresses | Export-Csv -Path UserAccounts.csv`

### <a name="confirm-group-accounts-are-ready-for-azure-information-protection"></a>그룹 계정을 Azure Information Protection에 사용할 수 있는지 확인

그룹 계정을 확인하려면 다음 명령을 사용합니다.

    Get-MsolGroup | select DisplayName, ProxyAddresses

Azure Information Protection에 사용할 그룹이 표시되는지 확인합니다. 표시되는 그룹의 경우 **ProxyAddresses** 열의 이메일 주소를 사용하여 그룹 구성원에게 Azure Rights Management 서비스에 대한 권한을 부여할 수 있습니다.

그런 다음, Azure Information Protection에 사용할 사용자(또는 다른 그룹)가 그룹에 포함되어 있는지 확인합니다. 이 작업은 PowerShell을 사용해도 되고(예: [Get-msolgroupmember](/powershell/module/msonline/Get-MsolGroupMember?view=azureadps-1.0)), 관리 포털을 사용해도 됩니다.

보안 그룹을 사용하는 두 가지 Azure Rights Management 서비스 구성 시나리오의 경우 다음 PowerShell 명령을 사용하여 이러한 그룹을 식별하는 데 사용 가능한 개체 ID 및 표시 이름을 찾을 수 있습니다. 또한 Azure Portal을 사용하여 이러한 그룹을 찾은 후 개체 ID 및 표시 이름의 값을 복사할 수 있습니다.

    Get-MsolGroup | where {$_.GroupType -eq "Security"}

## <a name="considerations-for-azure-information-protection-if-email-addresses-change"></a>이메일 주소 변경 시 Azure Information Protection에 대해 고려할 사항

사용자 또는 그룹의 이메일 주소를 변경하는 경우 기존 이메일 주소를 사용자 또는 그룹에 보조 이메일 주소(프록시 주소, 별칭 또는 대체 이메일 주소라고도 함)로 추가하는 것이 좋습니다. 이렇게 하면 기존 이메일 주소가 Azure AD proxyAddresses 특성에 추가됩니다. 계정을 이렇게 관리하면 기존 이메일 주소가 사용될 때 저장된 사용 권한 또는 기타 구성에 대한 비즈니스 연속성이 보장됩니다. 

이렇게 할 수 없는 경우 새 이메일 주소를 사용하는 사용자 또는 그룹은 이전에 기존 이메일 주소로 보호된 문서와 이메일에 대한 액세스가 거부될 수 있습니다. 이 경우 새 이메일 주소를 저장하도록 보호 구성을 반복해야 합니다. 예를 들어 템플릿 또는 레이블에서 사용자 또는 그룹에 사용 권한이 부여된 경우 해당 템플릿 또는 레이블을 편집하고 기존 이메일 주소에 부여한 것과 동일한 사용 권한으로 새 이메일 주소를 지정합니다.

그룹이 이메일 주소를 변경하는 일은 매우 드물게 있으며 개별 사용자가 아닌 그룹에 사용 권한을 할당하면 사용자의 이메일 주소가 변경되어도 아무 문제 없습니다. 이 시나리오에서는 사용 권한이 개별 사용자 이메일 주소가 아닌 그룹 이메일 주소에 할당됩니다. 관리자가 문서와 이메일을 보호하는 사용 권한을 구성할 때 가장 많이 사용되는(그리고 권장되는) 방법입니다. 그러나 사용자가 늘 하던 식으로 개별 사용자에 대한 사용자 지정 권한을 할당할 수도 있습니다. 액세스 권한 부여에 사용자 계정이 사용되었는지 아니면 그룹이 사용되었는지 항상 알 수는 없으므로 기존 이메일 주소를 보조 이메일 주소로 추가하는 것이 가장 안전한 방법입니다.

## <a name="group-membership-caching-by-azure-information-protection"></a>Azure Information Protection으로 그룹 멤버 자격 캐싱

성능상의 이유로 Azure Information Protection에서는 그룹 멤버 자격을 캐싱합니다. 즉, Azure Information Protection에서 이러한 그룹을 사용하는 경우 Azure AD에 있는 그룹 멤버 자격의 변경 내용이 적용될 때까지 최대 3시간이 걸릴 수 있으며 이 시간은 달라질 수 있습니다. 

그룹을 사용하여 사용 권한을 부여하거나 Azure Rights Management 서비스를 구성할 때 또는 범위 지정 정책을 구성할 때 수행하는 변경 작업이나 테스트에서 이러한 지연 시간을 고려해야 합니다.


## <a name="next-steps"></a>다음 단계

사용자 및 그룹을 Azure Information Protection에 사용할 수 있는 것으로 확인한 후에는 문서 및 이메일을 보호하고, 이 데이터 보호 서비스를 사용하도록 Rights Management 서비스를 활성화할 수 있습니다. 자세한 내용은 [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
