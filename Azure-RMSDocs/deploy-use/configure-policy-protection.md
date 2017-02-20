---
title: "Rights Management 보호를 적용하도록 레이블을 구성하는 방법| Azure Information Protection"
description: "암호화, ID 및 권한 부여 정책을 통해 데이터 손실을 방지하는 권한 관리 서비스를 사용하여 가장 민감한 문서 및 메일을 보호할 수 있습니다. 이 보호는 권한 관리 템플릿을 사용하도록 레이블을 구성할 때 적용됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: f71b5d98d03453ee49ea177fcb894c28f0f2688f
ms.openlocfilehash: 9224cdbd5c7e1aa1453328150b903db386af2322


---

# <a name="how-to-configure-a-label-to-apply-rights-management-protection"></a>Rights Management 보호를 적용하도록 레이블을 구성하는 방법

>*적용 대상: Azure Information Protection*

암호화, ID 및 권한 부여 정책을 통해 데이터 손실을 방지하는 권한 관리 서비스를 사용하여 가장 민감한 문서 및 메일을 보호할 수 있습니다. 이 보호는 Rights Management 템플릿을 사용하도록 레이블을 구성할 때 적용됩니다. 

이 템플릿은 Azure Rights Management를 활성화할 때 자동으로 만들어지는 기본 템플릿 또는 사용자 지정 템플릿 중 하나일 수 있습니다. Azure 권한 관리 부서별 템플릿은 지원되지만 문서 또는 메일 작성자가 구성된 템플릿 범위에 속하는 경우에만 보호를 적용합니다. 범위 내에 없는 사용자에게는 Azure Information Protection에서 레이블을 적용할 수 없음을 알리는 메시지가 표시됩니다.

## <a name="how-the-protection-works"></a>보호 작동 방식

권한 관리를 통해 보호되는 문서 또는 메일은 사용되지 않을 때와 전송 중에 암호화되며, 권한 있는 사용자만 암호를 해독할 수 있습니다. 이 암호화는 이름이 변경된 경우에도 문서 또는 메일과 함께 유지됩니다. 또한 다음 예와 같이 사용 권한 및 제한 사항을 구성할 수 있습니다.

- 조직 내부의 사용자만 회사 기밀 문서 또는 메일을 열 수 있습니다.

- 마케팅 부서의 사용자만 판촉 행사 발표 문서 또는 메일을 편집 및 인쇄할 수 있으며, 조직의 나머지 사용자는 문서 또는 메일을 읽을 수만 있습니다.

- 사용자는 내부 재구성에 대한 뉴스가 포함된 메일을 전달할 수 없습니다.

- 비즈니스 파트너에게 전송된 현재 가격 목록은 지정된 날짜 이후에 열 수 없습니다.

이러한 사용 권한과 제한을 구성하는 방법 및 Azure Rights Management 템플릿에 대한 자세한 내용은 [Azure Rights Management Service용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

Azure Rights Management 및 작동 방식에 대한 자세한 내용은 [Azure Rights Management란?](../understand-explore/what-is-azure-rms.md)을 참조하세요.

> [!IMPORTANT]
> Azure 권한 관리 보호를 적용하도록 레이블을 구성하려면 조직에 대해 Azure 권한 관리 서비스를 활성화해야 합니다. 아직 활성화하지 않은 경우 [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요.

Exchange에서 IRM(정보 권한 관리)을 구성하지 않고도 사용자가 Outlook에서 레이블을 적용하여 메일을 보호할 수 있습니다. 그러나 Exchange에서 IRM을 구성할 때까지 Exchange를 통한 Azure 권한 관리 보호 사용의 전체 기능을 활용할 수 없습니다. 예를 들어 사용자는 휴대폰에서나 Outlook Web Access에서 보호된 메일을 볼 수 없고, 보호된 메일을 검색을 위해 인덱싱할 수 없고, Exchange Online DLP에서 권한 관리 보호를 구성할 수 없습니다. 이러한 추가 시나리오를 지원하도록 Exchange를 구성하려면 다음 리소스를 참조하세요.

- Exchange Online의 경우 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

- Exchange 온-프레미스의 경우 [RMS 커넥터를 배포하고 Exchange 서버를 구성](../deploy-use/deploy-rms-connector.md)해야 합니다. 


## <a name="to-configure-a-label-for-rights-management-protection"></a>Rights Management 보호에 대해 레이블을 구성하려면

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창을 열고 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 

    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 레이블을 모든 사용자에게 적용하려는 경우 **Azure Information Protection** 블레이드에서 **Global**을 선택합니다. 그러나 구성하려는 레이블이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 대신 해당 범위 지정 정책을 선택합니다.

3. **정책** 블레이드에서 구성하려는 레이블을 선택합니다. 그러면 **레이블** 블레이드가 열립니다. 

4. **레이블** 블레이드에서 **Set permissions for documents and emails containing this label**(이 레이블을 포함하는 문서 및 메일에 대한 사용 권한 설정)을 찾습니다. 
    
    **보호**를 선택하여 보호를 적용하거나 **보호 제거**를 선택하여 메일 또는 문서에 적용되는 보호를 제거합니다.

    - **보호**를 선택한 경우 5단계로 이동합니다.
    - **보호 제거**를 선택한 경우 11단계로 이동합니다.

5. **보호**를 선택하는 경우 **보호** 막대를 클릭하여 **사용 권한** 블레이드를 엽니다.
    
    ![Azure Information Protection 레이블에 대한 보호 구성](../media/info-protect-protection-bar.png)

6. **사용 권한** 블레이드에서 **Azure RMS** 또는 **HYOK(AD RMS)**를 선택합니다. 
    
    대부분의 경우 사용 권한 설정에 대해 **Azure RMS**를 선택합니다. 이 "*HYOK(Hold Your Own Key)*" 구성에 수반되는 필수 조건 및 제한을 읽고 이해한 경우에만 **HYOK(AD RMS)**를 선택하세요. 자세한 내용은 [AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한](configure-adrms-restrictions.md)을 참조하세요.
    
7. 메일에 대해 이 Outlook 옵션을 설정하려면 **Do not forward**(전달 금지)를 선택하거나 **Select template**(템플릿 선택)을 선택합니다. 
    
8. **Azure RMS**에 대해 **Select template**(템플릿 선택)을 선택한 경우 드롭다운 상자를 클릭하고 이 레이블이 있는 문서 및 메일을 보호하는 데 사용할 [템플릿](../deploy-use/configure-custom-templates.md)을 선택합니다.
    
    **부서별 템플릿**을 선택하거나 [온보딩 컨트롤](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우:
    
    - 구성된 템플릿 범위를 벗어나거나 적용되는 Azure 권한 관리 보호 적용에서 제외되는 사용자는 여전히 레이블을 볼 수 있지만 적용할 수는 없습니다. 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**
    
        범위 지정 정책을 구성하더라도 모든 템플릿은 항상 표시됩니다. 마케팅 그룹용 범위 지정 정책을 구성하는 경우를 예로 들어 보겠습니다. 이 경우 마케팅 그룹으로 범위가 지정된 Azure RMS 템플릿만 선택할 수 있는 것이 아니라 선택한 사용자가 사용할 수 없는 부서별 템플릿도 선택할 수 있습니다. 구성을 쉽게 수행하고 문제 해결 작업을 최소화하려면 범위 지정 정책의 레이블과 일치하도록 부서별 템플릿 이름을 지정하는 것이 좋습니다. 
            
9. **HYOK(AD RMS)**에 대해 **Select template**(템플릿 선택)을 선택한 경우 AD RMS 클러스터의 템플릿 GUID 및 라이선스 URL을 제공합니다. [추가 정보](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

10. **완료**를 클릭하여 **사용 권한** 블레이드를 닫고 **Do not forward**(전달 금지) 선택 항목 또는 **레이블** 블레이드의 **보호** 막대에서 선택한 템플릿 표시를 확인합니다.

11. **보호 제거**를 선택하는 경우:
    
    사용자는 이 옵션이 있는 레이블을 적용하려면 권한 관리 보호를 제거할 수 있는 권한이 있어야 합니다. 이 옵션을 사용하려면 **내보내기**(Office 문서용) 또는 **모든 권한** [사용 권한](../deploy-use/configure-usage-rights.md)을 가지고 있거나 권한 관리 소유자(자동으로 모든 권한 사용 권한 부여) 또는 [Azure 권한 관리에 대한 슈퍼 사용자](../deploy-use/configure-super-users.md)여야 합니다. 기본 권한 관리 템플릿에는 사용자가 보호를 제거할 수 있는 사용 권한이 포함되어 있지 않습니다. 
    
    사용자가 권한 관리 보호를 제거할 권한이 없는데 **보호 제거** 옵션과 함께 이 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**

6. **레이블** 블레이드에서 **저장**을 클릭합니다.

7. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO3-->


