---
title: Azure Information Protection 정책 구성
description: 분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/02/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 57c410432377d5a98c132239ac1805293d1a5133
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151489"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Azure Information Protection 정책 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다. 이 정책은 [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치한 컴퓨터에 다운로드됩니다.

정책에는 다음과 같은 레이블 및 설정이 포함됩니다.

- 레이블은 문서 및 이메일에 분류 값을 적용하고, 선택적으로 이 콘텐츠를 보호할 수 있습니다. Azure Information Protection 클라이언트는 사용자가 파일 탐색기에서 마우스 오른쪽 단추로 클릭하는 경우 Office 앱의 사용자에게 이러한 레이블을 표시합니다. PowerShell 및 Azure Information Protection 스캐너를 사용하여 이러한 레이블은 적용할 수도 있습니다.

- 이렇게 설정하면 Azure Information Protection 클라이언트의 기본 동작을 변경합니다. 예를 들어 모든 문서와 이메일에 레이블이 있어야 하는지 여부 및 Office 앱에서 Azure Information Protection 표시줄이 표시되는지 여부에 관계 없이 기본 레이블을 선택할 수 있습니다.

## <a name="subscription-support"></a>구독 지원

Azure Information Protection은 다음과 같은 다양한 수준의 구독을 지원합니다.

- Azure Information Protection P2: 분류, 레이블 지정 및 보호 기능을 지원합니다.

- Azure Information Protection P1: 대부분의 분류, 레이블 지정 및 보호 기능을 지원하지만 자동 분류 또는 HYOK는 지원하지 않습니다.

- Azure 권한 관리 서비스를 포함하는 Office 365: 보호 기능을 지원하지만 분류 및 레이블 지정은 지원하지 않습니다.

Azure Information Protection P2 구독을 필요로 하는 옵션은 포털에서 확인할 수 있습니다.

조직에 여러 구독이 있는 경우 사용자 계정으로 사용이 허가되지 않은 기능을 사용하지 않도록 하는 것은 관리자의 책임입니다. Azure Information Protection 클라이언트는 라이선스 확인 및 적용을 수행하지 않습니다. 일부 사용자에게는 사용이 허가되지 않는 옵션을 구성하는 경우, 범위가 지정된 정책이나 레지스트리 설정을 사용하여 조직이 라이선스를 계속 준수하도록 합니다.

- **조직에 Azure Information Protection P1 및 Azure Information Protection P2 라이선스가 있는 경우**: P2 라이선스가 있는 사용자에 대해 Azure Information Protection P2 라이선스가 필요한 옵션을 구성할 때 하나 이상의 [범위가 지정된 정책](configure-policy-scope.md)을 만들고 사용합니다. 전역 정책에 Azure Information Protection P2 라이선스를 필요로 하는 옵션이 포함되지 않도록 합니다.

- **조직에 Azure Information Protection에 대한 구독이 있지만 일부 사용자에게는 Azure Rights Management 서비스가 포함되는 Office 365 라이선스만 있는 경우**: Azure Information Protection 라이선스가 없는 사용자에 대해 Azure Information Protection 정책을 다운로드하지 않도록 컴퓨터의 레지스트리를 편집합니다. 지침은 다음 사용자 지정에 대한 관리자 가이드를 참조하세요. [조직에 혼합 라이선스가 있을 때 보호 전용 모드 적용](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses)

구독에 대한 자세한 내용은 [Azure Information Protection을 사용하려면 어떤 구독이 필요하며, 포함된 기능은 무엇인가요?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)를 참조하세요.

## <a name="signing-in-to-the-azure-portal"></a>Azure Portal에 로그인

Azure Portal에 로그인인하고 Azure Information Protection을 구성 및 관리하려면

- https://portal.azure.com의 다음 링크를 참조하세요.

- 다음 [관리자 역할](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) 중 하나가 있는 계정을 사용합니다.
    
    - **Information Protection 관리자**

    - **보안 관리자**

    - **전역 관리자 / 회사 관리자**


## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Azure Information Protection 블레이드에 처음으로 액세스하려면

1. Azure Portal에 로그인합니다.

2. 허브 메뉴에서 **리소스 만들기**를 선택한 다음, Marketplace 검색 상자에 **Azure Information Protection**을 입력합니다. 
    
3. 결과 목록에서 **Azure Information Protection**을 선택합니다. **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.
    
    > [!TIP] 
    > 또는 다음에 포털에 로그인할 때 서비스 찾아보기 단계를 건너뛸 수 있도록 **대시보드에 고정**을 선택하여 대시보드에 **Azure Information Protection** 타일을 만듭니다.
    
    다시 **만들기**를 클릭합니다.

4. 서비스에 처음으로 연결할 때 자동으로 열리는 **빠른 시작** 페이지를 확인하세요. 제안된 리소스를 찾아보거나 다른 메뉴 옵션을 사용합니다. 사용자가 선택할 수 있는 레이블을 구성하려면 다음 절차를 사용합니다.

다음에 **Azure Information Protection** 블레이드에 액세스하는 경우 모든 사용자에 대한 레이블을 보고 구성할 수 있도록 **레이블** 옵션을 자동으로 선택합니다. **일반** 메뉴에서 선택하여 **빠른 시작** 페이지로 돌아갈 수 있습니다.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Azure Information Protection 정책을 구성하는 방법

1. Information Protection 관리자, 보안 관리자 또는 전역 관리와 같은 관리 역할 중 하나를 사용하여 Azure Portal에 로그인했는지 확인합니다. 이러한 관리 역할에 대한 자세한 내용은 [이전 섹션](#signing-in-to-the-azure-portal)을 참조하세요.

2. 필요한 경우 **Azure Information Protection** 블레이드로 이동합니다. 예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information Protection**을 입력합니다. 결과에서 **Azure Information Protection**을 선택합니다. 
    
    사용 가능한 레이블을 보고 편집할 수 있도록 **Azure Information Protection - 레이블** 블레이드가 자동으로 열립니다. 정책에서 사용자를 추가하거나 제거하여 모든 사용자 또는 선택한 사용자가 레이블을 사용할 수 있거나 어느 사용자도 사용할 수 없도록 설정합니다.

3. 정책을 보고 편집하려면 메뉴 옵션에서 **정책**을 선택합니다. 모든 사용자가 가져오는 정책을 보고 편집하려면 **전역** 정책을 선택합니다. 선택한 사용자에 대한 사용자 지정 정책을 만들려면 **새 정책 추가**를 선택합니다.
    

### <a name="overview-of-the-policy"></a>정책 개요

이 Azure Information Protection 정책에는 구성할 수 있는 다음 요소가 포함됩니다.
    
- 관리자와 사용자가 문서 및 이메일을 분류하고 선택적으로 보호하는 데 사용할 수 있는 레이블.

- 사용자의 Office 응용 프로그램에 표시되는 Information Protection 표시줄의 제목 및 도구 설명.

- 문서 및 전자 메일을 분류하기 위한 시작점으로 기본 레이블을 설정할 수 있는 옵션.

- 사용자가 문서를 저장하고 전자 메일을 보낼 때 분류를 적용할 수 있는 옵션.

- 원래보다 민감도 수준이 낮은 레이블을 선택한 경우 이유를 제공하라는 메시지를 사용자에게 표시할 수 있는 옵션.

- 첨부 파일에 따라 메일 메시지에 자동으로 레이블을 지정할 수 있는 옵션.

- Information Protection 막대가 Office 응용 프로그램에 표시되는지 여부를 제어하는 옵션.

- [전달 안 함] 단추가 Outlook에 표시되는지 여부를 제어하는 옵션.

- 사용자가 문서에 대한 고유 권한을 지정할 수 있는 옵션.

- 사용자를 위한 사용자 지정 도움말 링크를 제공하는 옵션.

Azure Information Protection은 5개의 기본 레이블을 포함하는 [기본 정책](configure-policy-default.md)과 함께 제공됩니다. 이러한 레이블 중 두 가지는 필요할 때 하위 범주를 제공하는 하위 레이블을 포함합니다. 하위 레이블에 대한 레이블이 구성된 경우 사용자가 기본 레이블을 선택할 수 없지만 하위 레이블 중 하나를 선택해야 합니다.

Azure Information Protection 레이블은 조직에서 일반적으로 만들고 저장하는 최저 분류인 개인 데이터부터 최고 분류인 극비 데이터에 이르기까지 전체 범위의 데이터와 함께 사용할 수 있습니다. 

기본 레이블을 변경하지 않고 사용하거나, 이를 사용자 지정하거나, 삭제하고 새 레이블을 만들 수 있습니다. 다음 섹션의 링크에서 관련 옵션을 찾아 구성하는 방법을 자세히 확인할 수 있습니다.

원하는 수의 레이블을 만들 수 있습니다. 하지만 사용자가 올바른 레이블을 쉽고 보고 선택하기에 레이블이 너무 많아지기 시작하면 사용자와 관련된 레이블만 표시되도록 범위 지정 정책을 만듭니다. 보호가 적용되는 레이블의 상한선은 500입니다.

Azure Information Protection 블레이드를 변경한 경우 **Save**(저장)를 클릭하여 변경 내용을 저장하거나 **Discard**(취소)를 클릭하여 마지막으로 저장된 설정으로 되돌립니다. 정책에 변경 내용을 저장하거나 정책에 추가된 레이블의 내용을 변경하면 해당 변경 내용이 자동으로 게시됩니다. 별도의 게시 옵션이 없습니다.

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램이 시작될 때마다 변경 내용을 확인하여 해당 최신 Azure Information Protection 정책으로 변경 내용을 다운로드합니다. 클라이언트에서 정책을 새로 고치는 추가 트리거:

- 마우스 오른쪽 단추를 클릭하여 파일 또는 폴더 분류 및 보호.

- 레이블 지정 및 보호를 위한 [PowerShell cmdlets](./rms-client/client-admin-guide-powershell.md) 실행(Get-AIPFileStatus, Set-AIPFileClassification 및 Set-AIPFileLabel)

- 24시간마다.

- [Azure Information Protection 스캐너](deploy-aip-scanner.md)의 경우: 서비스가 시작할 때(1시간보다 오래된 정책) 및 작업 중 매 시간마다.


>[!NOTE]
>클라이언트가 정책을 다운로드하면 정책이 완벽하게 작동하는 데 몇 분 정도 걸립니다. 실제 시간은 정책 구성의 크기 및 복잡도, 네트워크 연결 등 여러 요소에 따라 다릅니다. 레이블의 결과 작업이 최근 변경 내용과 일치하지 않는 경우에는 최대 15분 정도 기다렸다 다시 시도하세요.

### <a name="configuring-your-organizations-policy"></a>조직의 정책 구성

다음 정보를 사용하여 Azure Information Protection 정책을 구성할 수 있습니다.

- [기본 Information Protection 정책](configure-policy-default.md)

- [정책 설정을 구성하는 방법](configure-policy-settings.md)

- [새 레이블을 만드는 방법](configure-policy-new-label.md)

- [레이블을 추가 또는 제거하는 방법](configure-policy-add-remove-label.md)
 
- [레이블을 삭제하거나 순서를 변경하는 방법](configure-policy-delete-reorder.md)

- [기존 레이블을 변경하거나 사용자 지정하는 방법](configure-policy-change-label.md)

- [보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)

- [시각적 표시를 적용하도록 레이블을 구성하는 방법](configure-policy-markings.md)

- [자동 및 권장 분류에 대한 조건을 구성하는 방법](configure-policy-classification.md)

- [범위 지정 정책을 사용하여 특정 사용자에 대한 정책을 구성하는 방법](configure-policy-scope.md)

- [템플릿을 구성 및 관리하는 방법](configure-policy-templates.md)

- [다른 언어에 대해 레이블을 구성하는 방법](configure-policy-languages.md)

## <a name="next-steps"></a>다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](infoprotect-quick-start-tutorial.md)를 참조하세요.

