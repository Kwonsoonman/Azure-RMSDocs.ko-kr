---
title: "Azure Information Protection을 위한 사용자 및 그룹 준비"
description: "조직의 문서와 메일의 분류, 레이블 지정 및 보호를 시작하는 데 필요한 사용자 및 그룹 계정이 있는지 확인합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 45f75834d687247808107708e082ff61d8510899
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="preparing-users-and-groups-for-azure-information-protection"></a>Azure Information Protection을 위한 사용자 및 그룹 준비

>*적용 대상: Azure Information Protection, Office 365*

조직에 Azure Information Protection을 배포하기 전에 조직에 있는 테넌트의 Azure AD에 사용자 및 그룹 계정이 있는지 확인합니다.

사용자 및 그룹에 이러한 계정을 만드는 방법에는 다음을 포함한 여러 가지가 있습니다.

- Office 365 관리 센터에서 사용자를 만들고 Exchange Online 관리 센터에서 그룹을 만듭니다.

- Azure Portal에서 사용자 및 그룹을 만듭니다.

- Azure AD PowerShell 및 Exchange Online cmdlet을 사용하여 사용자 및 그룹을 만듭니다.

- 온-프레미스 Active Directory에 사용자 및 그룹을 만들고 Azure AD로 동기화합니다.

- 다른 디렉터리에 사용자 및 그룹을 만들고 Azure AD로 동기화합니다.

이 목록에 있는 처음 세 방법을 사용하여 사용자 및 그룹을 만들면 Azure AD에 자동으로 생성되며, Azure Information Protection에서 이러한 계정을 직접 사용할 수 있습니다. 그러나 온-프레미스 디렉터리를 사용하여 사용자 및 그룹을 만들고 관리하는 엔터프라이즈 네트워크가 많습니다. Azure Information Protection에서는 이러한 계정을 직접 사용할 수 없고, Azure AD로 동기화해야 합니다.

## <a name="how-users-and-groups-are-used-by-azure-information-protection"></a>Azure Information Protection에서 사용자 및 그룹을 사용하는 방법

Azure Information Protection에서 사용자 및 그룹을 사용하는 시나리오는 세 가지입니다.

- 레이블 지정 및 분류를 사용할 때 **사용자에게 레이블을 할당하는 경우**. 관리자만 이러한 그룹을 선택합니다.
    
    - 기본 Azure Information Protection 정책이 테넌트의 Azure AD에 있는 모든 사용자에게 자동으로 할당됩니다. 그러나 범위가 지정된 정책을 사용하여 추가 레이블을 지정된 사용자나 그룹에 할당할 수도 있습니다.

- Azure Rights Management 서비스를 사용하여 문서 및 메일을 보호할 때 **사용 권한 및 액세스 제어를 할당하는 경우**. 관리자 및 사용자가 이러한 사용자 및 그룹을 선택할 수 있습니다.

    - 사용 권한은 사용자가 문서 또는 메일을 열 수 있는지 여부와 사용할 수 있는 방법을 결정합니다. 예를 들어, 읽기만 가능한지, 읽고 인쇄할 수 있는지, 읽고 편집할 수 있는지를 정합니다.

    - 액세스 제어에는 만료 날짜, 그리고 액세스에 인터넷 연결이 필요한지 여부가 포함됩니다.

- 특정 시나리오를 지원하도록 **Azure Rights Management 서비스를 구성하는 경우**에는 관리자만 이러한 그룹을 선택할 수 있습니다. 다음을 구성하는 경우의 예가 포함됩니다.

    - eDiscovery 또는 데이터 복구를 위해 필요한 경우 지정된 서비스나 사람이 암호화된 콘텐츠를 열 수 있도록 슈퍼 사용자 구성.

    - Azure Rights Management 서비스의 위임된 관리 구성.

    - 단계적 배포를 지원하기 위한 등록 컨트롤 구성.

Azure Information Protection을 구성할 때 문서와 메일에 레이블을 적용할 수 있도록 **사용자에게 레이블을 할당하는 경우**입니다. 이러한 사용자 및 그룹은 관리자만 선택할 수 있습니다.

- 기본 Azure Information Protection 정책이 테넌트의 Azure AD에 있는 모든 사용자에게 자동으로 할당됩니다. 그러나 범위가 지정된 정책을 사용하여 추가 레이블을 지정된 사용자나 그룹에 할당할 수도 있습니다.     

Azure Rights Management 서비스를 사용하여 문서 및 메일을 보호할 때 **사용 권한 및 액세스 제어를 할당하는 경우**. 관리자 및 사용자가 이러한 사용자 및 그룹을 선택할 수 있습니다.

- 사용 권한은 사용자가 문서 또는 메일을 열 수 있는지 여부와 사용할 수 있는 방법을 결정합니다. 예를 들어, 읽기만 가능한지, 읽고 인쇄할 수 있는지, 읽고 편집할 수 있는지를 정합니다. 

- 액세스 제어에는 만료 날짜, 그리고 액세스에 인터넷 연결이 필요한지 여부가 포함됩니다. 

특정 시나리오를 지원하도록 **Azure Rights Management 서비스를 구성하는 경우**에는 관리자만 이러한 그룹을 선택할 수 있습니다. 다음을 구성하는 경우의 예가 포함됩니다.

- eDiscovery 또는 데이터 복구를 위해 필요한 경우 지정된 서비스나 사람이 암호화된 콘텐츠를 열 수 있도록 슈퍼 사용자 구성.

- Azure Rights Management 서비스의 위임된 관리 구성.

- 단계적 배포를 지원하기 위한 등록 컨트롤 구성.

## <a name="azure-information-protection-requirements-for-user-accounts"></a>사용자 계정에 대한 Azure Information Protection 요구 사항

레이블을 할당하는 경우:

- Azure AD에 있는 모든 사용자 계정은 사용자에게 추가 레이블을 할당하는, 범위가 지정된 정책을 구성하는 데 사용할 수 있습니다.

사용자 권한 및 액세스 제어를 할당하고 Azure Rights Management 서비스를 구성하는 경우:

- 사용자 인증에는 Azure AD에 있는 두 특성 **proxyAddresses** 및 **userPrincipalName**이 사용됩니다.

- **Azure AD proxyAddresses** 특성은 계정의 모든 메일 주소를 저장하며 다른 방법으로 채울 수 있습니다. 예를 들어 Office 365에서 Exchange Online 사서함이 있는 사용자에게는 이 특성에 저장되는 메일 주소가 자동으로 부여됩니다. Office 365 사용자의 대체 메일 주소를 할당하면, 그 주소도 이 특성에 저장됩니다. 온-프레미스 계정에서 동기화되는 메일 주소를 여기에 채울 수도 있습니다. 
    
    도메인이 테넌트에 추가되어 있으면("확인된 도메인") Azure Information Protection에서 이 Azure AD proxyAddresses 특성에 있는 모든 값을 사용할 수 있습니다. 도메인 확인에 대한 자세한 내용은 다음을 참조하십시오.
    
    - Azure AD: [Azure Active Directory에 사용자 지정 도메인 이름 추가](/active-directory/active-directory-add-domain)

    - Office 365: [Office 365에 도메인 및 사용자 추가](https://go.microsoft.com/fwlinkid/?linkid=847121)

- **Azure AD userPrincipalName** 특성은 테넌트에 있는 계정에 Azure AD proxyAddresses 특성의 값이 없는 경우에만 사용됩니다. 예를 들어, Azure Portal에 사용자를 만들거나 Office 365에 사서함이 없는 사용자를 만듭니다.

### <a name="assigning-usage-rights-and-access-controls-to-external-users"></a>외부 사용자에게 사용 권한 및 액세스 제어 할당

테넌트에 있는 사용자에게 Azure AD proxyAddresses 및 Azure AD userPrincipalName을 사용하기도 하지만, Azure Information Protection에서는 이러한 특성을 같은 방식으로 사용하여 다른 테넌트의 사용자에게 권한을 부여하기도 합니다.

Azure AD에 계정이 없는 사용자에게 새로운 기능을 갖춘 Office 365 메시지 암호화를 사용하여 전자 메일을 보내면 소셜 ID 공급자와의 페더레이션을 사용하거나 일회용 암호를 사용하여 먼저 사용자를 인증합니다. 그런 다음 보호된 전자 메일에 지정된 이메일 주소를 사용하여 사용자를 인증합니다.

## <a name="azure-information-protection-requirements-for-group-accounts"></a>그룹 계정에 대한 Azure Information Protection 요구 사항

레이블을 할당하는 경우:

- 그룹 구성원에 추가 레이블을 할당하는 범위 지정 정책을 구성하려면 Azure AD에서 사용자의 테넌트에 대한 확인된 도메인이 포함된 메일 주소를 가진 모든 유형의 그룹을 사용할 수 있습니다. 메일 주소가 있는 그룹을 메일 사용이 가능한 그룹이라고도 합니다.
    
    예를 들어, 메일 사용이 가능한 보안 그룹, 메일 그룹(정적 또는 동적) 및 Office 365 그룹을 사용할 수 있습니다. 보안 그룹(동적 또는 정적) 유형은 메일 주소가 없으므로 사용할 수 없습니다.

사용 권한 및 액세스 제어 할당의 경우:

- Azure AD에서 사용자의 테넌트에 대한 확인된 도메인이 포함된 이메일 주소를 가진 모든 유형의 그룹을 사용할 수 있습니다. 메일 주소가 있는 그룹을 메일 사용이 가능한 그룹이라고도 합니다. 

Azure Rights Management 서비스를 구성하는 경우:

- 테넌트의 확인된 도메인에 메일 주소가 있는 Azure AD의 모든 그룹 유형을 사용할 수 있지만, 한 가지 예외가 있습니다. 그 예외는 등록 컨트롤에서 그룹을 사용하도록 구성하는 경우입니다. 이 때의 그룹은 테넌트의 Azure AD에 있는 보안 그룹이어야 합니다.

- Azure Rights Management 서비스의 위임된 관리에 대한 테넌트에서 확인된 도메인에 있는 Azure AD(이메일 주소 유무는 무관)의 모든 그룹을 사용할 수 있습니다.

### <a name="assigning-usage-rights-and-access-controls-to-external-groups"></a>외부 그룹에 사용 권한 및 액세스 제어 할당

테넌트에 있는 그룹에 Azure AD proxyAddresses를 사용하기도 하지만, Azure Information Protection에서는 이러한 특성을 같은 방식으로 사용하여 다른 테넌트의 그룹에 권한을 부여하기도 합니다.

## <a name="using-accounts-from-active-directory-on-premises-for-azure-information-protection"></a>Azure Information Protection에 대해 Active Directory 온-프레미스의 계정 사용

온-프레미스에서 관리되며 Azure Information Protection에 사용할 계정이 있는 경우에는 해당 계정을 Azure AD로 동기화해야 합니다. 쉬운 배포를 위해서는 [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect)를 사용할 것을 권장합니다. 그러나 같은 결과를 달성하는 모든 디렉터리 동기화 방법을 사용할 수 있습니다.

계정을 동기화할 때 모든 특성을 동기화할 필요는 없습니다. 동기화해야 하는 특성 목록은 Azure Active Directory 설명서에서 [Azure RMS 섹션](/azure/active-directory/connect/active-directory-aadconnectsync-attributes-synchronized#azure-rms)을 참조하세요.

Azure Rights Management의 특성 목록을 보면 사용자를 동기화하기 위해 온-프레미스 AD 특성 **mail**, **proxyAddresses** 및 **userPrincipalName**이 필요한 것을 알 수 있습니다. **mail** 및 **proxyAddresses** 값은 Azure AD proxyAddresses 특성으로 동기화됩니다. 자세한 내용은 [How the proxyAddresses attribute is populated in Azure AD](https://support.microsoft.com/help/3190357/how-the-proxyaddresses-attribute-is-populated-in-azure-ad)(Azure AD에서 proxyAddresses 특성을 채우는 방법)를 참조하세요.

## <a name="confirming-your-users-and-groups-are-prepared-for-azure-information-protection"></a>Azure Information Protection을 위한 사용자 및 그룹이 준비되었는지 확인

Azure AD PowerShell을 사용하여 사용자 및 그룹을 Azure Information Protection에 사용할 수 있는지 확인할 수 있습니다. PowerShell을 사용하여 권한 부여에 사용할 수 있는 값을 확인할 수도 있습니다. 

예를 들어, Azure Active Directory에 대한 V1 PowerShell 모듈 [MSOnline](/powershell/module/msonline/?view=azureadps-1.0)을 PowerShell 세션에서 사용할 경우 먼저 서비스에 연결하고 전역 관리자 자격 증명을 입력합니다.

    Connect-MsolService


참고: 이 명령을 사용할 수 없을 경우 `Install-Module MSOnline`을 실행하여 MSOnline 모듈을 설치할 수 있습니다.

다음으로는 PowerShell 세션에서 값을 자르지 않도록 구성합니다.

    $Formatenumerationlimit =-1

### <a name="confirm-user-accounts-are-ready-for-azure-information-protection"></a>사용자 계정을 Azure Information Protection에 사용할 준비가 되었는지 확인

사용자 계정을 확인하려면 다음 명령을 실행합니다.

    Get-Msoluser | select DisplayName, UserPrincipalName, ProxyAddresses

먼저 Azure Information Protection에 사용할 사용자가 표시되어 있는지 확인합니다.

그런 다음 **ProxyAddresses** 열이 채워져 있는지 확인합니다. 채워져 있으면 이 열에 있는 전자 메일 값을 사용하여 사용자에게 Azure Information Protection에 대한 권한을 부여할 수 있습니다.

**ProxyAddresses** 열이 채워져 있지 않으면 Azure Rights Management 서비스에 대한 사용자의 권한 부여에 **UserPrincipalName**에 있는 값이 사용됩니다.

예를 들면 다음과 같습니다.

|표시 이름|UserPrincipalName|ProxyAddresses
|-------------------|-----------------|--------------------|
|Jagannath Reddy |jagannathreddy@contoso.com|{}|
|Ankur Roy|ankurroy@contoso.com|{SMTP:ankur.roy@contoso.com, smtp: ankur.roy@onmicrosoft.contoso.com}|

이 예에서는 다음과 같습니다.

- **jagannathreddy@contoso.com**으로 Jagannath Reddy의 사용자 계정에 권한이 부여됩니다.

-  Ankur Roy의 사용자 계정에는 **ankur.roy@contoso.com** 및 **ankur.roy@onmicrosoft.contoso.com**으로 권한을 부여할 수 있지만 **ankurroy@contoso.com**으로는 할 수 없습니다.

대부분의 경우 UserPrincipalName의 값은 ProxyAddresses 필드에 있는 값 중 하나와 일치합니다. 이 구성이 권장되지만, UPN을 메일 주소와 일치하도록 변경할 수 없는 경우에는 다음 단계를 수행해야 합니다.

1. UPN 값에 있는 도메인 이름이 Azure AD 테넌트에 대해 확인된 도메인인 경우는 이제 UPN 값을 사용하여 Azure Information Protection에 대한 사용자 계정의 권한을 부여할 수 있도록 UPN 값을 Azure AD에 있는 다른 메일 주소로 추가합니다.

    UPN 값에 있는 도메인 이름이 테넌트에 대해 확인된 도메인이 아닌 경우는 Azure Information Protection에 사용할 수 없습니다. 그러나, 그룹 메일 주소에서 확인된 도메인 이름을 사용할 경우 사용자는 그룹 구성원으로서 권한이 부여될 수 있습니다.

2. UPN을 라우팅할 수 없는 경우(예: **ankurroy@contoso.local**), 사용자의 대체 로그인 ID를 구성하고 이 대체 로그인 정보로 Office에 로그인하는 방법을 알려주세요. Office의 레지스트리 키도 설정해야 합니다.

    자세한 내용은 [대체 로그인 ID 구성](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) 및 [Office applications periodically prompt for credentials to SharePoint Online, OneDrive, and Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online)(Office 응용 프로그램에서 주기적으로 SharePoint Online, OneDrive 및 Lync Online의 자격 증명 요구)을 참조하세요.

> [!TIP]
> Export-Csv cmdlet을 사용하여 결과를 스프레드시트로 내보내면 검색과 가져오기를 위한 대량 편집 등을 보다 쉽게 관리할 수 있습니다.
>
> 예를 들어 `Get-MsolGroup | select DisplayName, ProxyAddresses | Export-Csv -Path UserAccounts.csv`를 구성할 수 있습니다.

### <a name="confirm-group-accounts-are-ready-for-azure-information-protection"></a>그룹 계정을 Azure Information Protection에 사용할 준비가 되었는지 확인

그룹 계정을 확인하려면 다음 명령을 사용합니다.

    Get-MsolGroup | select DisplayName, ProxyAddresses

Azure Information Protection에 사용할 그룹이 표시되어 있는지 확인합니다. 표시된 그룹에 대해 **ProxyAddresses** 열에 있는 메일 주소를 사용하여 Azure Rights Management 서비스의 그룹 구성원에게 권한을 부여할 수 있습니다.

그런 다음 Azure Information Protection에 사용할 사용자(또는 다른 그룹)가 그룹에 포함되어 있는지 확인합니다. 여기에 PowerShell을 사용할 수도 있고(예: [Get-MsolGroupMember](/powershell/module/msonline/Get-MsolGroupMember?view=azureadps-1.0)) 관리 포털을 사용할 수도 있습니다.

보안 그룹을 사용하는 두 Azure Rights Management 구성 시나리오에서, 다음 PowerShell 명령을 사용하여 이러한 그룹의 식별에 사용할 수 있는 개체 ID와 표시 이름을 찾을 수 있습니다. Azure Portal을 사용하여 이러한 그룹을 찾고 개체 ID와 표시 이름의 값을 복사할 수도 있습니다.

    Get-MsolGroup | where {$_.GroupType -eq "Security"}

## <a name="considerations-for-azure-information-protection-if-email-addresses-change"></a>메일 주소가 변경된 경우 Azure Information Protection에 대한 고려 사항

사용자 또는 그룹의 메일 주소를 변경할 경우 사용자 또는 그룹에 이전 메일 주소를 두 번째 메일 주소(일명 프록시 주소, 별칭 또는 대체 메일 주소)로 추가할 것을 권장합니다. 이렇게 하면 이전 메일 주소가 Azure AD proxyAddresses 특성에 추가됩니다. 이 계정 관리를 사용하면 이전 메일 주소를 사용할 때 저장된 사용 권한이나 기타 구성에 대한 비즈니스 연속성을 보장할 수 있습니다. 

그럴 수 없는 경우는 새 메일 주소를 사용하는 사용자 또는 그룹에서 이전에 이전 메일 주소로 보호된 문서 및 메일에 대한 액세스가 거부될 위험이 있습니다. 이 경우, 보호 구성을 반복하여 새 메일 주소를 저장해야 합니다. 예를 들어, 사용자 또는 그룹에게 템플릿 또는 레이블에 대한 사용 권한이 부여된 경우 이러한 템플릿 또는 레이블을 편집하고 이전 전자 메일 주소에 부여한 것과 동일한 사용 권한으로 새 전자 메일 주소를 지정합니다.

그룹에서 메일 주소를 변경하는 일은 드물며, 개별 사용자가 아닌 그룹에 사용 권한을 할당하면 사용자의 메일 주소가 변경되어도 상관이 없습니다. 이 시나리오에서는 사용 권한이 개별 사용자 메일 주소가 아닌 그룹 메일 주소에 할당됩니다. 이 방법은 관리자가 문서 및 메일을 보호하기 위한 사용 권한을 구성할 때 가장 많이 사용하는 권장 방법입니다. 그러나 사용자가 개별 사용자에 사용자 지정 권한을 할당하는 경우가 더 일반적입니다. 액세스 권한을 부여하는데 사용자 계정과 그룹 중에서 어느 쪽이 사용되었는지 알기 어려운 경우도 있으므로, 항상 이전 메일 주소를 두 번째 메일 주소로 추가하는 것이 안전합니다.

## <a name="group-membership-caching-by-azure-information-protection"></a>Azure Information Protection에 의한 그룹 멤버 자격 캐싱

성능상의 이유로 Azure Information Protection은 그룹 멤버 자격을 캐시합니다. 즉, Azure AD에 있는 그룹 멤버 자격을 Azure Information Protection에서 사용하는 경우, 변경 내용이 적용되는 데 최대 3시간이 걸릴 수 있으며 이 시간은 변경될 수 있습니다. 

사용 권한을 부여하거나 Azure Rights Management 서비스를 구성하기 위해 그룹을 사용할 때 또는 범위가 지정된 정책을 구성할 때 모든 변경이나 테스트에 이러한 지연을 고려해야 합니다.


## <a name="next-steps"></a>다음 단계

사용자와 그룹을 Azure Information Protection에 사용할 수 있는 것을 확인하고 문서 및 이메일 보호를 시작할 준비가 되면, Azure Rights Management 서비스를 활성화해야 하는지 여부를 학인합니다. 조직의 문서 및 이메일을 보호하려면 먼저 이 서비스를 활성화해야 합니다. 

- 2018년 2월부터: 이달 또는 그 이후에 Azure Rights Management 또는 Azure Information Protection이 포함된 구독을 얻은 경우 서비스가 자동으로 활성화됩니다. 

- 2018년 2월 이전에 구독을 얻은 경우에는, 직접 서비스를 활성화해야 합니다. 

활성화 상태 확인을 포함한 자세한 내용은, [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
