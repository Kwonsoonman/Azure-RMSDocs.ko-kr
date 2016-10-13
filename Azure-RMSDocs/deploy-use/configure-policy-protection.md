---
title: "Rights Management 보호를 적용하도록 레이블을 구성하는 방법| Azure Information Protection"
description: "암호화, ID 및 권한 부여 정책을 통해 데이터 손실을 방지하는 권한 관리 서비스를 사용하여 가장 민감한 문서 및 메일을 보호할 수 있습니다. 이 보호는 권한 관리 템플릿을 사용하도록 레이블을 구성할 때 적용됩니다."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: ebb11148718f22c79bb49c82b9855f5e6f2a5b18
ms.openlocfilehash: 762ba3164c717a6c9836c4fdd383cf65ea42eac3


---

# Rights Management 보호를 적용하도록 레이블을 구성하는 방법

>*적용 대상: Azure Information Protection*

암호화, ID 및 권한 부여 정책을 통해 데이터 손실을 방지하는 권한 관리 서비스를 사용하여 가장 민감한 문서 및 메일을 보호할 수 있습니다. 이 보호는 Rights Management 템플릿을 사용하도록 레이블을 구성할 때 적용됩니다. 

이 템플릿은 Azure Rights Management를 활성화할 때 자동으로 만들어지는 기본 템플릿 또는 사용자 지정 템플릿 중 하나일 수 있습니다. Azure 권한 관리 부서별 템플릿은 지원되지만 문서 또는 메일 작성자가 구성된 템플릿 범위에 속하는 경우에만 보호를 적용합니다. 범위 내에 없는 사용자에게는 Azure Information Protection에서 레이블을 적용할 수 없음을 알리는 메시지가 표시됩니다.

## 보호 작동 방식

권한 관리를 통해 보호되는 문서 또는 메일은 사용되지 않을 때와 전송 중에 암호화되며, 권한 있는 사용자만 암호를 해독할 수 있습니다. 이 암호화는 이름이 변경된 경우에도 문서 또는 전자 메일과 함께 유지됩니다. 또한 다음 예와 같이 사용 권한 및 제한 사항을 구성할 수 있습니다.

- 조직 내부의 사용자만 회사 기밀 문서 또는 메일을 열 수 있습니다.

- 마케팅 부서의 사용자만 판촉 행사 발표 문서 또는 메일을 편집 및 인쇄할 수 있으며, 조직의 나머지 사용자는 문서 또는 메일을 읽을 수만 있습니다.

- 사용자는 내부 재구성에 대한 뉴스가 포함된 메일을 전달할 수 없습니다.

- 비즈니스 파트너에게 전송된 현재 가격 목록은 지정된 날짜 이후에 열 수 없습니다.

이러한 사용 권한과 제한을 구성하는 방법 및 Azure 권한 관리 템플릿에 대한 자세한 내용은 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

Azure Rights Management 및 작동 방식에 대한 자세한 내용은 [Azure Rights Management란?](../understand-explore/what-is-azure-rms.md)을 참조하세요.

> [!IMPORTANT]
> Azure 권한 관리 보호를 적용하도록 레이블을 구성하려면 조직에 대해 Azure 권한 관리 서비스를 활성화해야 합니다. 아직 활성화하지 않은 경우 [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요.


## Rights Management 보호를 적용하도록 레이블을 구성하려면

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창을 열고 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 

    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **Azure Information Protection** 블레이드에서 Rights Management 보호를 적용하도록 구성할 레이블을 선택합니다.

3. **Label**(레이블) 블레이드의 **Set RMS template for protecting documents and emails containing this label**(이 레이블을 포함하는 문서 및 메일을 보호하도록 RMS 템플릿 설정) 섹션에서 **Select RMS template from**(RMS 템플릿 선택)에 대해 **Azure RMS** 또는 **AD RMS(PREVIEW)**를 선택합니다.
    
    대부분의 경우에서 **Azure RMS**를 선택합니다. HYOK*("Hold Your Own Key")*라고도 하는 이 구성에 수반되는 필수 조건 및 제한을 읽고 이해한 경우에만 AD RMS를 선택하세요. 자세한 내용은 [AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한](configure-adrms-restrictions.md)을 참조하세요.
    
4. Azure RMS를 선택한 경우: **Select RMS template**(RMS 템플릿 선택) 드롭다운 상자를 클릭하고 이 레이블이 있는 문서 및 메일을 보호하는 데 사용할 [템플릿](../deploy-use/configure-custom-templates.md) 또는 권한 관리 옵션을 선택합니다.
    
    옵션에 대한 자세한 정보:
    
    - **레이블** 블레이드를 연 후 새 템플릿을 만들었나요? 이 블레이드를 닫고 2단계로 돌아가세요. 그래야 새로 만든 템플릿을 선택할 수 있도록 Azure에서 검색됩니다.
    
    - **부서별 템플릿**을 선택하거나 [온보딩 컨트롤](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우:
    
        - 구성된 템플릿 범위를 벗어나거나 적용되는 Azure 권한 관리 보호 적용에서 제외되는 사용자는 여전히 레이블을 볼 수 있지만 적용할 수는 없습니다. 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**
        
    - **보호 제거**를 선택하는 경우:
        
        - 사용자는 이 옵션이 있는 레이블을 적용하려면 권한 관리 보호를 제거할 수 있는 권한이 있어야 합니다. 이 옵션을 사용하려면 **내보내기**(Office 문서용) 또는 **모든 권한** [사용 권한](../deploy-use/configure-usage-rights.md)을 가지고 있거나 권한 관리 소유자(자동으로 모든 권한 사용 권한 부여) 또는 [Azure 권한 관리에 대한 슈퍼 사용자](../deploy-use/configure-super-users.md)여야 합니다. 기본 권한 관리 템플릿에는 사용자가 보호를 제거할 수 있는 사용 권한이 포함되어 있지 않습니다. 

            사용자가 권한 관리 보호를 제거할 권한이 없는데 **보호 제거** 옵션과 함께 이 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**

5. AD RMS를 선택한 경우: AD RMS 클러스터의 템플릿 GUID 및 라이선스 URL을 제공합니다. [추가 정보](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. **저장**을 클릭합니다.

7. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요.  



<!--HONumber=Sep16_HO4-->


