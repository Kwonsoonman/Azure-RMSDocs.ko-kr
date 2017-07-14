---
title: "보호를 위해 Azure Information Protection 레이블 구성"
description: "Rights Management 보호를 사용하도록 레이블을 구성하면 가장 중요한 문서 및 메일을 보호할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: f5c4e2f7513832a884820ec0c57c7da2dec5f04e
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2017
---
# Rights Management 보호에 대해 레이블을 구성하는 방법
<a id="how-to-configure-a-label-for-rights-management-protection" class="xliff"></a>

>*적용 대상: Azure Information Protection*

암호화, ID 및 권한 부여 정책을 통해 데이터 손실을 방지하는 권한 관리 서비스를 사용하여 가장 민감한 문서 및 메일을 보호할 수 있습니다. 이 보호는 문서 및 메일에 Rights Management 템플릿을 사용하거나 Outlook 메일 메시지에 대해 **Do not forward**(전달 금지) 옵션을 사용하도록 레이블을 구성할 때 적용됩니다. 

템플릿은 Azure Rights Management를 활성화할 때 자동으로 만들어지는 기본 템플릿 또는 사용자 지정 템플릿 중 하나일 수 있습니다. Azure 권한 관리 부서별 템플릿은 지원되지만 문서 또는 메일 작성자가 구성된 템플릿 범위에 속하는 경우에만 보호를 적용합니다. 범위 내에 없는 사용자에게는 Azure Information Protection에서 레이블을 적용할 수 없음을 알리는 메시지가 표시됩니다.

## 보호 작동 방식
<a id="how-the-protection-works" class="xliff"></a>

권한 관리를 통해 보호되는 문서 또는 메일은 사용되지 않을 때와 전송 중에 암호화되며, 권한 있는 사용자만 암호를 해독할 수 있습니다. 이 암호화는 이름이 변경된 경우에도 문서 또는 메일과 함께 유지됩니다. 또한 다음 예와 같이 사용 권한 및 제한 사항을 구성할 수 있습니다.

- 조직 내부의 사용자만 회사 기밀 문서 또는 메일을 열 수 있습니다.

- 마케팅 부서의 사용자만 판촉 행사 발표 문서 또는 메일을 편집 및 인쇄할 수 있으며, 조직의 나머지 사용자는 문서 또는 메일을 읽을 수만 있습니다.

- 사용자는 내부 재구성에 대한 뉴스가 포함된 메일을 전달하거나 메일에서 정보를 복사할 수 없습니다.

- 비즈니스 파트너에게 전송된 현재 가격 목록은 지정된 날짜 이후에 열 수 없습니다.

Azure Rights Management 템플릿 및 Azure 클래식 포털에서 이러한 템플릿을 구성하는 방법에 대한 자세한 내용은 [Azure Rights Management Service용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

Azure Rights Management 및 작동 방식에 대한 자세한 내용은 [Azure Rights Management란?](../understand-explore/what-is-azure-rms.md)을 참조하세요.

> [!IMPORTANT]
> Azure 권한 관리 보호를 적용하도록 레이블을 구성하려면 조직에 대해 Azure 권한 관리 서비스를 활성화해야 합니다. 아직 활성화하지 않은 경우 [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요.

Exchange에서 IRM(정보 권한 관리)을 구성하지 않고도 사용자가 Outlook에서 레이블을 적용하여 메일을 보호할 수 있습니다. 그러나 Exchange에서 IRM을 구성할 때까지 Exchange를 통한 Azure 권한 관리 보호 사용의 전체 기능을 활용할 수 없습니다. 예를 들어 사용자는 휴대폰에서나 웹용 Outlook에서 보호된 메일을 볼 수 없고, 보호된 메일을 검색을 위해 인덱싱할 수 없고, Exchange Online DLP에서 권한 관리 보호를 구성할 수 없습니다. 이러한 추가 시나리오를 지원하도록 Exchange를 구성하려면 다음 리소스를 참조하세요.

- Exchange Online의 경우 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

- Exchange 온-프레미스의 경우 [RMS 커넥터를 배포하고 Exchange 서버를 구성](../deploy-use/deploy-rms-connector.md)해야 합니다. 


## Rights Management 보호에 대해 레이블을 구성하려면
<a id="to-configure-a-label-for-rights-management-protection" class="xliff"></a>

1. 아직 그렇게 하지 않은 경우에는, 새 브라우저 창을 열고 보안 관리자나 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 

    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 레이블을 모든 사용자에게 적용하려는 경우 **Azure Information Protection** 블레이드에서 **Global**을 선택합니다. 그러나 구성하려는 레이블이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 대신 해당 범위 지정 정책을 선택합니다.

3. **정책** 블레이드에서 구성하려는 레이블을 선택합니다. 그러면 **레이블** 블레이드가 열립니다. 

4. **Label**(레이블) 블레이드에서 **Set permissions for documents and emails containing this label**(이 레이블을 포함하는 문서 및 메일에 대한 사용 권한 설정)로 이동하고 다음 옵션 중 하나를 선택합니다.
    
    - **Not configured**(구성되지 않음): 레이블이 현재 보호를 적용하도록 구성되어 있는데 선택한 레이블에 더 이상 보호를 적용하지 않으려면 이 옵션을 선택합니다. 11단계로 이동합니다.
    
    - **Protect**(보호): 보호를 적용하려면 이 옵션을 선택한 다음 5단계로 이동합니다.
    
    - **보호 제거**: 문서 또는 메일에 대해 구성된 보호를 제거하려면 이 옵션을 선택합니다. 11단계로 이동합니다.
        
        사용자는 이 옵션이 있는 레이블을 적용하려면 Rights Management 보호를 제거할 수 있는 권한이 있어야 합니다. 이 옵션을 사용하려면 사용자가 **내보내기** 또는 **모든 권한** [사용 권한](../deploy-use/configure-usage-rights.md)을 가지고 있거나 Rights Management 소유자(자동으로 모든 권한 사용 권한 부여) 또는 [Azure Rights Management의 슈퍼 사용자](../deploy-use/configure-super-users.md)여야 합니다. 기본 Azure Rights Management 템플릿에는 사용자가 보호를 제거할 수 있는 사용 권한이 포함되어 있지 않습니다. 
        
        사용자가 Rights Management 보호를 제거할 권한이 없는데 이 **보호 제거** 옵션을 사용하여 구성된 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 이 작업을 수행할 권한이 없습니다). If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**

5. **보호**를 선택한 경우 **보호**를 선택하여 **보호** 블레이드를 엽니다.
    
    ![Azure Information Protection 레이블에 대한 보호 구성](../media/info-protect-protection-bar.png)

6. **보호** 블레이드에서 **Azure RMS** 또는 **HYOK(AD RMS)**를 선택합니다. 
    
    대부분의 경우 사용 권한 설정에 대해 **Azure RMS**를 선택합니다. 이 "*HYOK(Hold Your Own Key)*" 구성에 수반되는 필수 조건 및 제한을 읽고 이해한 경우에만 **HYOK(AD RMS)**를 선택하세요. 자세한 내용은 [AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한](configure-adrms-restrictions.md)을 참조하세요. HYOK(AD RMS)에 대한 구성을 계속하려면 10단계로 이동합니다.
    
7. 다음 옵션 중 하나를 선택합니다.
    
    - **전달 안 함**: 메일에 대해 이 Outlook 옵션을 설정합니다.
    
    - **미리 정의된 템플릿 선택**: 기본 템플릿 또는 구성한 사용자 지정 템플릿을 중 하나를 사용합니다.
    
    - **권한 설정(미리 보기)**: 이 포털에서 새로운 보호 설정을 정의합니다.

8. **Azure RMS**에 대해 **Select a predefined template**(미리 정의된 템플릿 선택)을 선택한 경우 드롭다운 상자를 클릭하고 이 레이블이 있는 문서 및 메일을 보호하는 데 사용할 [템플릿](../deploy-use/configure-custom-templates.md)을 선택합니다.
    
    **부서별 템플릿**을 선택하거나 [온보딩 컨트롤](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우:
    
    - 구성된 템플릿 범위를 벗어나거나 적용되는 Azure 권한 관리 보호 적용에서 제외되는 사용자는 여전히 레이블을 볼 수 있지만 적용할 수는 없습니다. 레이블을 선택하는 경우 다음 메시지가 표시됩니다. **Azure Information Protection cannot apply this label. If this problem persists, contact your administrator.(Azure Information Protection에서 이 레이블을 적용할 수 없습니다. 문제가 지속되면 관리자에게 문의하세요.)**
    
        범위 지정 정책을 구성하더라도 모든 템플릿은 항상 표시됩니다. 마케팅 그룹용 범위 지정 정책을 구성하는 경우를 예로 들어 보겠습니다. 이 경우 마케팅 그룹으로 범위가 지정된 Azure RMS 템플릿만 선택할 수 있는 것이 아니라 선택한 사용자가 사용할 수 없는 부서별 템플릿도 선택할 수 있습니다. 구성을 쉽게 수행하고 문제 해결 작업을 최소화하려면 범위 지정 정책의 레이블과 일치하도록 부서별 템플릿 이름을 지정하는 것이 좋습니다. 
            
9. **Azure RMS**에 대해 **권한 설정(미리 보기)**을 선택한 경우 이 옵션은 Azure 클래식 포털에서 구성할 수 있는 [사용자 지정 템플릿](configure-custom-templates.md)에 대한 구성 옵션 대부분을 포함합니다. 또한 도메인 이름을 지정할 때 조직에서 모든 사용자를 쉽게 추가하고, 개별 사용자나 그룹 또는 다른 조직에 있는 모든 사용자의 외부 메일 주소를 지정할 수 있습니다. 
    
    이 미리 보기 구성에 대한 자세한 내용은 블로그 게시물 [Azure Information Protection 통합 관리, 이제 미리 보기로 제공](https://blogs.technet.microsoft.com/enterprisemobility/2017/04/26/azure-information-protection-unified-administration-now-in-preview/)을 참조하세요. 
    
    선택할 수 있는 사용 권한에 대한 자세한 내용은 [Azure Rights Management에 대한 사용 권한 구성](configure-usage-rights.md)을 참조하세요.
    
    **권한 설정(미리 보기)** 옵션에 포함된 다음 설정을 변경하고 싶은지 확인하세요. 사용 권한과 마찬가지로 이러한 설정은 [Rights Management 발급자 또는 Rights Management 소유자](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)나 사용자가 할당한 [슈퍼 사용자](configure-super-users.md)에게는 적용되지 않습니다.
    
    |설정|추가 정보|권장 설정
    |-----------|--------------------|--------------------|
    |**콘텐츠 만료**|선택한 사용자에 대해 템플릿으로 보호되는 문서 또는 메일이 열리지 않아야 하는 경우 해당 템플릿에 대해 날짜 또는 일수를 설정합니다. 콘텐츠에 보호 기능이 적용되는 시점부터 시작해서 특정 일수를 정하거나 날짜를 지정할 수 있습니다.<br /><br />날짜를 지정하면 현재 표준 시간대에서 자정까지 유효합니다.|콘텐츠에 특정 시간 제한이 요구되지 않을 경우 **콘텐츠는 만료되지 않습니다**.|
    |**오프라인 액세스 허용**|이 설정을 사용하여 사용자의 보안 요구 사항(취소 이후의 액세스 포함)에 따라 선택한 사용자가 인터넷에 연결되어 있지 않을 때 보호된 콘텐츠를 열 수 있는 기능을 적절히 조정하세요.<br /><br />인터넷이 연결되지 않은 경우에는 해당 콘텐츠를 사용할 수 없도록 지정하거나 지정된 일수 동안에만 해당 콘텐츠를 사용할 수 있게 하는 경우, 임계치에 다다르면 사용자는 다시 인증받아야 하며 이러한 사용자의 액세스가 기록됩니다. 이런 경우가 발생하고 자격 증명이 캐시되지 않은 경우 문서나 메일을 열려고 하면 우선 로그인하라는 메시지가 표시됩니다.<br /><br />재인증과 더불어 정책 및 사용자 그룹 멤버 자격이 재평가됩니다. 이는 사용자가 콘텐츠에 마지막으로 액세스한 이후에 정책 또는 그룹 멤버 자격이 변경되었다면 같은 문서나 메일에 대해 다른 액세스 결과를 겪을 수도 있다는 의미입니다. 즉, 문서가 [해지](../rms-client/client-track-revoke.md)된 경우에는 액세스 권한이 없을 수도 있습니다.|콘텐츠의 중요도에 따라 다릅니다.<br /><br />- **인터넷 연결 없이 콘텐츠를 사용할 수 있는 일수** = **7** - 권한이 없는 사용자와 공유하는 경우 비즈니스에 피해를 줄 수 있는 중요한 업무 데이터 이러한 권장 지침을 따르면 유연성과 보안을 균형 있게 조정할 수 있습니다. 계약, 보안 보고서, 예측 요약 및 판매 계정 데이터를 예로 들 수 있습니다.<br /><br />- **안 함**: 권한이 없는 사람들과 공유할 경우 비즈니스에 피해를 야기하는 매우 중요한 비즈니스 데이터에 사용합니다. 이 권장 사항은 유연성보다는 보안을 우선적으로 고려하며, 문서가 해지되면 권한 있는 모든 사용자가 즉시 해당 문서를 열 수 없게 됩니다. 직원 및 고객 정보, 암호, 소스 코드 및 미리 공개된 재무 보고서 등을 예로 들 수 있습니다.|
    
    이 설정 그룹은 Azure Rights Management 서비스에 대해 사용자 지정 템플릿을 만듭니다. 이러한 템플릿은 Azure Rights Management와 통합되는 응용 프로그램 및 서비스에서 사용될 수 있습니다. 컴퓨터 및 서비스가 이러한 템플릿을 다운로드하고 새로 고치는 방법에 대한 자세한 내용은 [사용자 및 서비스를 위한 템플릿 새로 고침](refresh-templates.md)을 참조하세요.

10. **HYOK(AD RMS)**에 대해 **Select template**(템플릿 선택)을 선택한 경우 AD RMS 클러스터의 템플릿 GUID 및 라이선스 URL을 제공합니다. [추가 정보](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

11. **확인**을 클릭하여 **보호** 블레이드를 닫고 **전달 금지** 선택 항목 또는 **레이블** 블레이드의 **보호** 옵션에 대해 선택한 템플릿 표시를 확인합니다.

12. **레이블** 블레이드에서 **저장**을 클릭합니다.

13. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## 다음 단계
<a id="next-steps" class="xliff"></a>

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]