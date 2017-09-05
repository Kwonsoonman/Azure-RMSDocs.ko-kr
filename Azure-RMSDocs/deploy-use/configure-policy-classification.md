---
title: "Azure Information Protection 레이블에 대한 조건 구성"
description: "레이블에 대한 조건을 구성할 때 문서 또는 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: ef84f3ceb8f732dd475b4db8eae489e715d4b7da
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법

>*적용 대상: Azure Information Protection*

레이블에 대한 조건을 구성할 때 문서 또는 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다. 

- Word, Excel 및 PowerPoint의 경우 파일이 저장될 때 자동 분류가 적용되고, Outlook의 경우 메일이 전송될 때 자동 분류가 적용됩니다. 이전에 수동으로 레이블을 지정한 파일에는 자동 분류를 사용할 수 없습니다.
 
- 권장 분류는 파일이 저장될 때 Word, Excel 및 PowerPoint에 적용됩니다.

조건을 구성할 때 **신용 카드 번호** 또는 **주민등록번호**와 같은 미리 정의된 패턴을 사용할 수 있습니다. 또는 자동 분류에 대한 조건으로 사용자 지정 문자열 또는 패턴을 정의할 수 있습니다. 이러한 조건은 문서와 메일의 본문 텍스트 및 머리글과 바닥글에 적용됩니다. 조건에 대한 자세한 내용은 [정보 유형에 대한 세부 정보](#details-about-the-information-types) 섹션을 참조하세요.

둘 이상의 레이블에 적용할 때 여러 조건을 평가하는 방법:

1. 레이블은 정책에서 지정한 해당 위치에 따라 평가 순서가 결정됩니다. 첫 번째에 위치한 레이블이 최하위 위치(민감도가 가장 낮음)이고 마지막에 위치한 레이블이 최상위 위치(민감도가 가장 높음)입니다.

2. 민감도가 가장 높은 레이블이 적용됩니다.
 
3. 마지막 하위 레이블이 적용됩니다.

> [!TIP]
>최상의 사용자 환경과 비즈니스 연속성 보장을 위해 자동 분류보다 사용자 권장 분류로 시작하는 것이 좋습니다. 이 구성을 사용하면 사용자가 레이블 지정 또는 보호 작업을 수락하거나, 이 작업이 자신의 문서 또는 메일 메시지에 적합하지 않은 경우 이러한 제안을 재정의할 수 있습니다.

레이블을 권장 작업으로 적용하도록 조건을 구성할 때 표시되는 예제 메시지 및 사용자 지정 정책 팁은 다음과 같습니다.

![Azure Information Protection 보호 및 권장 사항](../media/info-protect-recommend-calloutsv2.png)

이 예제에서는 사용자가 **Change now**(지금 변경)를 클릭하여 권장 레이블을 적용하거나, **Dismiss**(해제)를 선택하여 권장 사항을 재정의할 수 있습니다.

## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>레이블에 대한 권장 또는 자동 분류를 구성하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 보안 관리자 또는 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다. **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. 구성하려는 레이블을 모든 사용자에게 적용하려는 경우 **Azure Information Protection - 전역 정책** 블레이드에 그대로 있습니다.
    
    구성하려는 레이블이 선택한 사용자에게만 적용되도록 [범위 지정 정책](configure-policy-scope.md)에 포함되는 경우 **정책** 메뉴 선택에서 **범위 지정 정책**을 선택합니다. 그런 다음 **Azure Information Protection - 범위 지정 정책** 블레이드에서 범위 지정 정책을 선택합니다.

3. **Azure Information Protection - 전역 정책** 블레이드 또는 **정책:\<이름>** 블레이드에서 구성할 레이블을 선택합니다. 

4. **레이블** 블레이드의 **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션에서 **Add a new condition**(새 조건 추가)을 클릭합니다.

5. **조건** 블레이드에서 미리 정의된 조건을 사용하려면 **정보 유형**을 선택하고, 사용자 고유의 조건을 지정하려면 **사용자 지정**을 선택한 다음 **저장**을 클릭합니다.
    - **정보 유형**의 경우: 사용 가능한 조건 목록에서 선택한 다음 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 선택합니다.
        
        전체 조건 목록을 사용하려면 Azure Information Protection 클라이언트의 현재 미리 보기 버전을 사용해야 합니다. 클라이언트의 현재 일반 공급 버전이 있는 경우 **SWIFT 코드**, **신용 카드 번호**, **ABA 라우팅 번호**, **주민등록번호** 및 **IBAN(국제 은행 계좌 번호)**의 다섯 가지 조건만 지원됩니다. [추가 정보](#details-about-the-information-types)
    
    - **Custom**(사용자 지정)의 경우: 따옴표와 특수 문자를 포함하여 일치시킬 이름 및 구를 지정합니다. 그런 다음 정규식으로 일치시킬지 여부, 대/소문자를 구분할지 여부, 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 지정합니다.
        
        Azure Information Protection 클라이언트의 현재 미리 보기 버전이 있는 경우 정규식은 Office 365 regex 패턴을 사용합니다. 자세한 내용은 Office 설명서의 [정규식 기반 일치 정의](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2)를 참조하세요. 
        
    **발생 옵션의 예**: 기본 제공 주민등록번호 옵션을 선택하고 최소 발생 횟수를 2로 설정하면 문서에 같은 주민등록번호가 두 번 나열됩니다. **고유 값이 포함된 발생 수만 계산**을 **켜기**로 설정한 경우에는 조건을 충족하지 않습니다. 이 옵션을 **끄기**로 설정하면 조건을 충족합니다.

6. **Label**(레이블) 블레이드에서 다음을 구성하고 **Save**(저장)를 클릭합니다.
    
    - 자동 또는 권장 분류를 선택합니다. **Select how this label is applied: automatically or recommended to user**(이 레이블이 적용되는 방식 선택: 자동 또는 사용자에게 권장)에서 **Automatic**(자동) 또는 **Recommended**(권장)를 선택합니다.
    
    - 사용자 프롬프트 또는 정책 팁에 대한 텍스트를 지정합니다. 기본 텍스트를 유지하거나 사용자 고유의 문자열을 지정할 수 있습니다.

7. 변경 내용을 사용자에게 제공하려면 초기 **Azure Information Protection** 블레이드에서 **게시**를 클릭합니다.

## <a name="details-about-the-information-types"></a>정보 유형에 대한 세부 정보

Azure Information Protection 클라이언트의 현재 미리 보기 버전이 있는 경우 전체 정보 유형 목록이 지원되며 Office 365 DLP(데이터 손실 방지) 민감도 정보 유형 및 패턴 감지를 사용합니다. 여러 일반적인 중요한 정보 유형 중에서 선택할 수 있으며, 이 중 일부는 특정 지역과만 관련됩니다. 자세한 내용은 Office 설명서의 [중요한 정보 유형이 찾는 내용](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)을 참조하세요. Azure Information Protection에서 이러한 정보 유형을 평가할 때 Office DLP 신뢰도 설정을 사용하지 않고 가장 낮은 신뢰도에 따라 일치시킵니다.  

클라이언트의 현재 일반 공급 버전이 있는 경우 다음 정보 유형만 지원됩니다.

- [SWIFT 코드](#swift-code )

- [신용 카드 번호](#credit-card-number )

- [ABA 라우팅 번호](#aba-routing-number )

- [미국 SSN(사회 보장 번호)](#usa-social-security-number-ssn)

- [IBAN(국제 은행 계좌 번호)](#international-banking-account-number-iban)

클라이언트의 일반 공급 버전에 대한 이러한 각 정보 유형의 자세한 내용은 다음 섹션을 참조하세요.

### <a name="swift-code"></a>SWIFT 코드

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

1. 다음 구 중 하나: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. 서식이 지정된 패턴의 Swift 코드:  

    a. 문자 4자(은행 코드)  

    b. 문자 2자(국가 코드)  

    c. 문자 또는 숫자 2자(위치 코드)  

    d. 선택적 문자 또는 숫자 3자(지점 코드)  


테스트를 위한 예제:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### <a name="credit-card-number"></a>신용 카드 번호

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

- [Luhn 검사](https://wikipedia.org/wiki/Luhn_algorithm)를 통과한 유효한 신용 카드 번호(서식이 지정되거나 지정되지 않은 패턴). 이 정보 유형은 Visa, MasterCard, Discover Card, American Express, Diners 등 전 세계의 모든 주요 카드 브랜드에서 카드를 검색합니다.

    - **서식 있음**:
    
        - 16자리 숫자: (dddd-dddd-dddd-dddd)  
        
    - **서식 없음**:
    
        - (dddddddddddddddd)  


테스트를 위한 예제:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### <a name="aba-routing-number"></a>ABA 라우팅 번호

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

1. 다음 구 중 하나 이상: **aba**, **rtn**, **라우팅 번호** 

2. 서식이 지정되거나 지정되지 않은 패턴일 수 있는 9자리 숫자를 포함하는 ABA 라우팅 번호: 

    - **서식 있음**: 
        
        a. 0, 1, 2, 3, 6, 7 또는 8로 시작하는 4자리 숫자 
        
        b. 하이픈 
        
        c. 4자리 숫자 
        
        d. 하이픈 
        
        e. 숫자 
        
        예: 3456-9876-1 ABA 
        
    - **서식 없음**: 
        
        0, 1, 2, 3, 6, 7 또는 8로 시작하는 연속된 9자리 숫자 
        
        예: 345698761 RTN 
 

테스트를 위한 예제:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### <a name="usa-social-security-number-ssn"></a>주민등록번호

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

1. 다음 구 중 하나 이상: **ssn**, **주민등록번호**, **ssid**, **ss#** 

2. 주민등록번호: 서식이 지정되거나 지정되지 않은 패턴일 수 있는 9자리 숫자:

    - **서식 있음**: 
    
        - 다음과 같은 형식의 9자리 숫자: ddd-dd-dddd 또는 ddd dd dddd 
        
    - **서식 없음**: 
    
        - 다음과 같은 형식의 9자리 숫자: ddddddddd 


테스트를 위한 예제:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### <a name="international-banking-account-number-iban"></a>IBAN(국제 은행 계좌 번호)

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

1. 다음 구: **IBAN** 

2. IBAN 번호: 국가 코드(문자 2자), 확인 번호(숫자 2자), bban 번호(숫자 최대 30자) 순.


테스트를 위한 예제:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


