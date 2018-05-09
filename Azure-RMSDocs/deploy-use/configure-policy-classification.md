---
title: Azure Information Protection 레이블에 대한 조건 구성
description: 레이블에 대한 조건을 구성할 때 문서 또는 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 053d8dfd51d8c79cdc733f4395226c12ab6e2102
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

레이블에 대한 조건을 구성할 때 문서 또는 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다. 

이러한 조건을 구성할 때 **신용 카드 번호** 또는 **SSN(사회 보장 번호)** 과 같은 미리 정의된 패턴을 사용할 수 있습니다. 또는 자동 분류에 대한 조건으로 사용자 지정 문자열 또는 패턴을 정의할 수 있습니다. 이러한 조건은 문서와 메일의 본문 텍스트 및 머리글과 바닥글에 적용됩니다. 조건에 대한 자세한 내용은 [다음 절차](#to-configure-recommended-or-automatic-classification-for-a-label)의 5단계를 참조하세요.

최상의 사용자 환경과 비즈니스 연속성 보장을 위해 자동 분류보다 사용자 권장 분류로 시작하는 것이 좋습니다. 이 구성을 통해 사용자가 분류 및 연결된 보호를 수락하거나, 이러한 제안이 해당 문서 또는 메일 메시지에 적합하지 않은 경우 재정의할 수 있습니다.

레이블을 권장 작업으로 적용하도록 조건을 구성할 때 표시되는 예제 메시지 및 사용자 지정 정책 팁은 다음과 같습니다.

![Azure Information Protection 보호 및 권장 사항](../media/info-protect-recommend-calloutsv2.png)

이 예제에서는 사용자가 **Change now**(지금 변경)를 클릭하여 권장 레이블을 적용하거나, **Dismiss**(해제)를 선택하여 권장 사항을 재정의할 수 있습니다. 사용자가 권장 사항을 무시하도록 선택하고 다음에 문서가 열릴 때 조건이 계속 적용되는 경우 레이블 권장 사항이 다시 표시됩니다. 

> [!IMPORTANT]
>자동 분류 및 사용자 정의 권한에 대한 레이블을 구성하지 않습니다. 사용자 정의 권한 옵션은 사용자가 권한을 부여받아야 하는 사용자를 지정하도록 하는 [보호 설정](configure-policy-protection.md)입니다.
>
>자동 분류 및 사용자 지정 권한에 대한 레이블을 구성하는 경우 조건에 대한 콘텐츠를 검사하고 사용자 정의 권한 설정을 적용하지 않습니다. 권장 분류 및 사용자 정의 권한을 사용할 수 있습니다.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>자동 또는 권장 레이블을 적용하는 방법

- Word, Excel 및 PowerPoint의 경우 문서가 저장될 때 자동 분류가 적용되고, Outlook의 경우 메일이 전송될 때 자동 분류가 적용됩니다. 
    
    이전에 수동으로 레이블이 지정되거나 더 높은 분류에서 이전에 자동으로 레이블이 지정된 문서 및 전자 메일에 자동 분류를 사용할 수 없습니다. 

- 권장 분류는 문서가 저장될 때 Word, Excel 및 PowerPoint에 적용됩니다. Outlook에 권장 분류를 사용할 수 없습니다.
    
    이전에 더 높은 분류로 레이블이 지정된 문서에는 권장 분류를 사용할 수 없습니다. 

Azure Information Protection 클라이언트에서 사용자가 지정한 조건 규칙에 대한 문서를 정기적으로 검사하도록 이 동작을 변경할 수 있습니다. 이 구성에는 현재 미리 보기로 제공되는 [고급 클라이언트 설정](../rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background)이 필요합니다.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>둘 이상의 레이블에 적용할 때 여러 조건을 평가하는 방법

1. 레이블은 정책에서 지정한 해당 위치에 따라 평가 순서가 결정됩니다. 첫 번째에 위치한 레이블이 최하위 위치(민감도가 가장 낮음)이고 마지막에 위치한 레이블이 최상위 위치(민감도가 가장 높음)입니다.

2. 민감도가 가장 높은 레이블이 적용됩니다.
 
3. 마지막 하위 레이블이 적용됩니다.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>레이블에 대한 권장 또는 자동 분류를 구성하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **분류** > **레이블** 메뉴 옵션에서: **Azure Information Protection - 레이블** 블레이드에서 구성할 레이블을 선택합니다.

3. **레이블** 블레이드의 **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션에서 **Add a new condition**(새 조건 추가)을 클릭합니다.

4. **조건** 블레이드에서 미리 정의된 조건을 사용하려면 **정보 유형**을 선택하고, 사용자 고유의 조건을 지정하려면 **사용자 지정**을 선택합니다.
    - **정보 유형**의 경우: 사용 가능한 조건 목록에서 선택한 다음 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 선택합니다.
        
        정보 유형에서는 Office 365 DLP(데이터 손실 방지) 민감도 정보 유형 및 패턴 감지를 사용합니다. 여러 일반적인 중요한 정보 유형 중에서 선택할 수 있으며, 이 중 일부는 특정 지역과만 관련됩니다. 자세한 내용은 Office 설명서의 [중요한 정보 유형이 찾는 내용](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)을 참조하세요.
        
        Azure Portal에서 선택할 수 있는 정보 유형의 목록은 새 Office DLP 추가 기능을 포함하도록 정기적으로 업데이트됩니다. 그러나 목록은 Office 365 Security & Compliance 센터에 규칙 패키지로 정의 및 업로드한 사용자 지정 중요한 정보 유형은 제외합니다. 
        
        Azure Information Protection에서 선택한 정보 유형을 평가할 때 Office DLP 신뢰도 설정을 사용하지 않고 가장 낮은 신뢰도에 따라 일치시킵니다.
    
    - **Custom**(사용자 지정)의 경우: 따옴표와 특수 문자를 포함하여 일치시킬 이름 및 구를 지정합니다. 그런 다음 정규식으로 일치시킬지 여부, 대/소문자를 구분할지 여부, 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 지정합니다.
        
        정규식은 Office 365 정규식(regex) 패턴을 사용합니다. 자세한 내용은 Office 설명서의 [정규식 기반 일치 정의](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2)를 참조하세요. 또한 부스트에서 [Perl 정규식 구문](http://www.boost.org/doc/libs/1_66_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html)을 참조하는 것이 유용할 수 있습니다.
        
5. **최소 발생 수**와 **Count occurrence with unique value only(고유 값만 있는 발생 수)** 로 변경해야 하는지 여부를 결정한 다음 **저장**을 선택합니다. 
    
    발생 옵션의 예: 주민등록번호에 대한 정보 유형을 선택하고, 최소 발생 수를 2로 설정하고, 문서에 동일한 주민등록번호가 두 번 나열됩니다. **Count occurrence with unique value only(고유 값만 있는 발생 수)** 를 **설정**으로 설정하면 조건이 충족되지 않습니다. 이 옵션을 **끄기**로 설정하면 조건을 충족합니다.

6. **레이블** 블레이드에서 다음을 구성한 후 **저장**을 클릭합니다.
    
    - 자동 또는 권장 분류를 선택합니다. **Select how this label is applied: automatically or recommended to user**(이 레이블이 적용되는 방식 선택: 자동 또는 사용자에게 권장)에서 **Automatic**(자동) 또는 **Recommended**(권장)를 선택합니다.
    
    - 사용자 프롬프트 또는 정책 팁에 대한 텍스트를 지정합니다. 기본 텍스트를 유지하거나 사용자 고유의 문자열을 지정할 수 있습니다.

**저장**을 클릭하면 변경 내용이 사용자 및 서비스에 자동으로 제공됩니다. 더 이상 별도의 게시 옵션이 없습니다.

## <a name="next-steps"></a>다음 단계

[Azure Information Protection 스캐너](deploy-aip-scanner.md)를 배포하는 것이 좋습니다. 그러면 자동 분류 규칙을 사용하여 네트워크 공유 및 온-프레미스 파일 저장소에서 파일을 검색, 분류 및 보호할 수 있습니다.  

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

