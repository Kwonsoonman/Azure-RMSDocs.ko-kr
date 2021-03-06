---
title: Azure Information Protection 레이블을 Office 365 보안 및 준수 센터로 마이그레이션
description: Azure Information Protection 레이블을 통합 레이블 지정을 지원하는 클라이언트용 Office 365 보안 및 준수 센터로 마이그레이션합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 771cbb26a842cbf19184ace94ae47ba9d549a33f
ms.sourcegitcommit: b4118cd75db6478f86b9994e8d84d0ada15c7f95
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52953332"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Azure Information Protection 레이블을 Office 365 보안 및 준수 센터로 마이그레이션하는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> 이 기능은 미리 보기로 제공되며, 테넌트를 역시 미리 보기로 제공되는 새로운 플랫폼으로 마이그레이션합니다. 이 마이그레이션은 되돌릴 수 없습니다. 새 플랫폼은 통합 레이블 지정을 지원하므로 만들어 관리하는 레이블을 여러 클라이언트 및 서비스에서 사용할 수 있습니다.

Office 365 보안 및 준수 센터에서 레이블을 사용하려면 레이블을 마이그레이션합니다. 그러면 이 센터에서 레이블을 게시할 수 있으며 [통합 레이블 지정을 지원하는 클라이언트](#clients-that-support-unified-labeling)가 레이블을 다운로드할 수 있습니다. Azure Information Protection 클라이언트는 Azure Portal에서 Azure Information Protection 정책을 사용하여 레이블을 계속 다운로드합니다. 

레이블을 마이그레이션한 후에는 Azure Portal 또는 Office 365 보안 및 준수 센터에서 변경할 수 있으며 해당 클라이언트는 동일한 변경 내용을 다운로드합니다.

### <a name="important-information-about-administrative-roles"></a>관리 역할에 대한 중요 정보

**보안 관리자** 및 **Information Protection 관리자**의 [Azure AD 역할](/active-directory/users-groups-roles/directory-assign-admin-roles)은 통합 레이블 지정 플랫폼에서 지원하지 않습니다. 조직에서 이러한 관리 역할을 사용하는 경우 레이블을 마이그레이션하기 전에 이러한 역할을 가진 사용자를 Office 365 보안 및 준수 센터의 **준수 관리자** 또는 **조직 관리** 역할 그룹에 추가합니다. 또는 이러한 사용자를 위한 새 역할 그룹을 만들고 이 그룹에 **보존 관리** 또는 **조직 구성** 역할을 추가할 수 있습니다. 자세한 내용은 [Give users access to the Office 365 Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center)(사용자에게 Office 365 보안 및 준수 센터에 대한 액세스 권한 제공)를 참조하세요.

이러한 구성 중 하나를 사용했는데도 사용자에게 보안 및 준수 센터에 대한 액세스 권한을 제공하지 못하면 레이블이 마이그레이션된 뒤에 사용자가 Azure Portal에서 레이블 및 정책에 액세스할 수 없게 됩니다.

테넌트의 전역 관리자는 레이블이 마이그레이션된 뒤 Azure Portal과 보안 및 준수 센터 둘 다에서 레이블과 정책을 계속해서 관리할 수 있습니다.


## <a name="considerations-for-unified-labels"></a>통합 레이블 고려 사항

레이블을 마이그레이션하기 전에 다음 변경 내용 및 고려 사항을 인지하고 있는지 확인합니다.

- 현재, 모든 클라이언트가 통합 레이블을 지원하는 것은 아닙니다. [지원되는 클라이언트](#clients-that-support-unified-labeling)가 있고 Azure Portal(통합 레이블을 지원하지 않는 클라이언트)와 보안 및 준수 센터(통합 레이블을 지원하는 클라이언트) 둘 다에서 관리 준비가 완료되었는지 확인합니다.

- 사용하려는 레이블을 정의 및 구성하는 동안 Azure Portal을 사용하여 이 프로세스를 완료한 후, 레이블을 마이그레이션하는 것이 좋습니다. 이러한 전략은 마이그레이션 프로세스 동안 레이블이 중복되지 않도록 합니다. 중복된 레이블은 보안 및 준수 센터에서 편집해야 합니다.

- 정책 설정과 해당 정책(범위가 지정된 정책)에 대해 액세스 권한이 있는 사용자 및 모든 고급 클라이언트 설정을 포함하는 정책은 마이그레이션되지 않습니다. 마이그레이션되지 않는 이러한 변경 사항의 경우, 레이블을 마이그레이션한 후 보안 및 준수 센터에서 관련 옵션을 구성해야 합니다.
    
    좀 더 일관된 사용자 환경을 사용하려면 보안 및 준수 센터에서 동일한 범위에 동일한 레이블을 게시하는 것이 좋습니다.

- 마이그레이션된 레이블의 모든 설정을 보안 및 준수 센터에서 지원하는 것은 아닙니다. [보안 및 준수 센터에서 지원되지 않는 레이블 설정](#label-settings-that-are-not-supported-in-the-security--compliance-center) 섹션에 있는 표를 참고하여 보안 및 준수 센터에서 지원되지 않는 설정을 확인하세요.

- 보호 템플릿:
    
    - 클라우드 기반 키를 사용하며, 레이블 구성에 속하는 템플릿은 레이블과 함께 마이그레이션됩니다. 다른 보호 템플릿은 마이그레이션되지 않습니다. 
    
    - 클라우드 기반 보호 설정을 포함하는 레이블을 마이그레이션한 후 보호 템플릿의 결과 범위는 Azure Portal의 정의에 따라(또는 AADRM PowerShell 모듈을 사용하여) 지정되며, 보안 및 준수 센터에 정의된 범위가 적용됩니다. 

- 레이블을 마이그레이션하면, 마이그레이션 결과에 레이블이 중복으로 인해 **생성**, **업데이트** 또는 **이름 변경**되었는지가 표시됩니다.

    - 레이블을 만들어질 때 응용 프로그램 및 서비스를 사용할 수 있도록 하려면 보안 및 준수 센터에서 게시해야 합니다.
    
    - 레이블 이름이 바뀐 경우 보안 및 준수 센터나 Azure Portal에서 편집해야 합니다. 

- 각 레이블에 대해 Azure Portal은 레이블 표시 이름만 표시하며 이 이름은 편집 가능합니다. 보안 및 준수 센터에는 레이블의 이 표시 이름과 레이블 이름이 모두 표시합니다. 레이블 이름은 레이블을 처음 만들 때 지정한 초기 이름이며, 이 속성은 식별을 위해 백 엔드 서비스에서 사용됩니다.

- 레이블의 현지화된 문자열은 마이그레이션되지 않습니다. 보안 및 준수 센터에서 마이그레이션된 레이블의 지역화된 문자열을 새로 정의해야 합니다.

- 마이그레이션 후 Azure Portal에서 마이그레이션된 레이블을 편집하는 경우 동일한 변경 내용이 보안 및 준수 센터에서도 자동으로 반영됩니다. 단, 보안 및 준수 센터에서 마이그레이션된 레이블을 편집한 경우에는 Azure Portal의 **Azure Information Protection - 통합 레이블 지정** 블레이드로 돌아가서 **게시**를 선택해야 합니다. Azure Information Protection 클라이언트에 레이블 변경 사항이 반영되도록 하려면 이 추가 작업이 필요합니다.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>보안 및 준수 센터에서 지원되지 않는 레이블 설정

아래 표를 참고하여 통합 레이블 지정 클라이언트가 지원하지 않거나 제한적으로 지원하는 마이그레이션된 레이블의 구성 설정을 확인하세요. 혼동을 피하기 위해 통합 레이블 지정 클라이언트에 영향을 주지 않는 설정은 구성하지 않을 것을 권장합니다.

Azure Information Protection 클라이언트는 Azure Portal에서 레이블을 계속 다운로드하므로 아무 문제 없이 이러한 레이블 설정을 사용할 수 있습니다.

|레이블 구성|통합 레이블 지정 클라이언트가 지원함|보안 및 준수 센터에서 편집하지 않도록 제외|
|-------------------|---------------------------------------------|-------------------------|
|사용 또는 사용 안 함 상태<br /><br />참고: 보안 및 준수 센터에 동기화되지 않음 |해당 없음|해당 없음|
|레이블 색상: 목록에서 선택하거나 RGB 코드를 사용하여 지정합니다.<br /><br />참고: 레이블 색은 보안 및 준수 센터에서 지원되지 않습니다. |해당 없음|해당 없음|
|미리 정의된 템플릿을 사용하는 클라우드 기반 보호 또는 HYOK 기반 보호 |아니요|예|
|Word, Excel 및 PowerPoint에서 사용자 정의 권한을 사용하는 클라우드 기반 보호 |아니요|예|
|전달 금지에 대한 Outlook의 사용자 정의 권한을 사용하는 HYOK 기반 보호 |아니요|예|
|보호 제거 |아니요|예|
|시각적 표시(머리글, 바닥글, 워터마크): RGB 코드별 사용자 지정 글꼴 및 사용자 지정 글꼴 색|아니요|변수를 사용하는 경우 권장됩니다.<br /><br />- 클라이언트에서 변수는 동적 값을 표시하지 않고 텍스트로 표시됩니다.|
|앱별 시각적 표시|아니요|변수를 사용하는 경우 권장됩니다.<br /><br />- 클라이언트에서 변수는 동적 값을 표시하지 않고 텍스트로 표시됩니다.|
|조건 및 관련 설정 <br /><br />참고: 자동 및 권장 레이블과 해당 도구 설명을 포함합니다.|해당 없음|아니요|


## <a name="to-migrate-azure-information-protection-labels"></a>Azure Information Protection 레이블을 마이그레이션하려면

다음 지침에 따라 테넌트 및 Azure Information Protection 레이블이 새로운 통합 레이블 지정 스토리지를 사용하도록 마이그레이션합니다.

레이블을 마이그레이션하려면 전역 관리자여야 합니다.

1. 새 브라우저 창을 열고 https://portal.azure.com/?ActivateMigration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/migrationActivationBlade 링크를 사용하여 Azure Portal에 로그인합니다. 

2. **Azure Information Protection - 통합 레이블 지정** 블레이드에서 **활성화**를 선택하고 온라인 지침을 따릅니다.

마이그레이션된 레이블의 경우 이제 [통합 레이블 지정을 지원하는 클라이언트](#clients-that-support-unified-labeling)가 사용할 수 있습니다. 그러나 먼저 보안 및 준수 센터에서 이러한 레이블을 게시해야 합니다.

> [!IMPORTANT]
> Azure Portal 외부에서 Azure Information Protection 클라이언트의 레이블을 편집한 경우, 이 **Azure Information Protection - 통합 레이블 지정** 블레이드로 돌아와서 **게시**를 선택하세요.

### <a name="clients-that-support-unified-labeling"></a>통합 레이블 지정을 지원하는 클라이언트

현재 통합 레이블 지정을 지원하는 클라이언트는 다음과 같습니다.

- [Windows용 Azure Information Protection 통합 레이블 지정 클라이언트](./rms-client/unifiedlabelingclient-version-release-history.md) - 미리 보기

- Office Insiders 프로그램의 앱. 자세한 내용은 Office 설명서의 [현재 이 기능을 사용할 수 있는 위치](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable) 섹션을 참조하세요.
    
- [MIP SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference)를 사용하는 소프트웨어 공급업체 및 개발자의 클라이언트


## <a name="next-steps"></a>다음 단계

이제 Office 365 보안 및 준수 센터에서 구성 및 게시할 수 있는 마이그레이션된 레이블에 대한 자세한 내용은 [민감도 레이블 개요](/Office365/SecurityCompliance/sensitivity-labels)를 참조하세요.

발표 블로그 게시물 [Announcing the availability of unified labeling management in the Security & Compliance Center](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)(보안 및 준수 센터에서 사용 가능한 통합 레이블 지정 관리 발표)를 읽어보세요.