---
title: "Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법 | Azure Rights Management"
description: "레이블에 대한 조건을 구성할 때 문서 또는 전자 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다."
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 0e6baca43c7a4f2e91f45222f5f6f233b3eeb438


---

# Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법

>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

레이블에 대한 조건을 구성할 때 문서 또는 전자 메일에 레이블을 자동으로 할당할 수 있습니다. 또는 사용자에게 권장하는 레이블을 선택하라는 메시지를 표시할 수 있습니다. 

- Word, Excel 및 PowerPoint의 경우 파일이 저장될 때 자동 분류가 적용되고, Outlook의 경우 전자 메일이 전송될 때 자동 분류가 적용됩니다. 이전에 수동으로 레이블을 지정한 파일에는 자동 분류를 사용할 수 없습니다.
 
- 권장 분류는 파일이 저장될 때 Word, Excel 및 PowerPoint에 적용됩니다.

조건을 구성할 때 "신용 카드 번호" 또는 "주민등록번호"와 같은 미리 정의된 패턴을 사용할 수 있습니다. 또는 자동 분류에 대한 조건으로 사용자 지정 문자열 또는 패턴을 정의할 수 있습니다. 조건에 대한 자세한 내용은 [기본 제공 조건에 대한 정보](#information-about-the-built-in-conditions) 섹션을 참조하세요.

둘 이상의 레이블에 적용할 때 여러 조건을 평가하는 방법:

1. 레이블은 정책에서 지정한 해당 위치에 따라 평가 순서가 결정됩니다. 첫 번째에 위치한 레이블이 최하위 위치(민감도가 가장 낮음)이고 마지막에 위치한 레이블이 최상위 위치(민감도가 가장 높음)입니다.

2. 민감도가 가장 높은 레이블이 적용됩니다.
 
3. 마지막 하위 레이블이 적용됩니다.

> [!TIP]
>최상의 사용자 환경과 비즈니스 연속성 보장을 위해 자동 분류보다 사용자 권장 분류로 시작하는 것이 좋습니다. 이 구성을 사용하면 사용자가 레이블 지정 또는 보호 작업을 수락하거나, 이 작업이 자신의 문서 또는 전자 메일 메시지에 적합하지 않은 경우 이러한 제안을 재정의할 수 있습니다.

레이블을 권장 작업으로 적용하도록 조건을 구성할 때 표시되는 예제 메시지 및 사용자 지정 정책 팁은 다음과 같습니다.

![Azure Information Protection 보호 및 권장 사항](../media/info-protect-recommend-callouts.png)

이 예제에서는 사용자가 **Change now**(지금 변경)를 클릭하여 권장 레이블을 적용하거나, 표시줄을 닫아 권장 사항을 재정의할 수 있습니다.

## 레이블에 대한 권장 또는 자동 분류를 구성하려면

1. 아직 로그인하지 않은 경우 [Azure 포털](https://portal.azure.com)에 로그인한 다음 **Azure Information Protection** 블레이드로 이동합니다. 
    
    예를 들어 허브 메뉴에서 **찾아보기**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **Azure Information Protection** 블레이드에서 자동 또는 권장 분류에 대해 구성할 레이블을 선택합니다.

3. **레이블** 블레이드의 **Configure conditions for automatically applying this label**(이 레이블을 자동으로 적용하기 위한 조건 구성) 섹션에서 **Add a new condition**(새 조건 추가)을 클릭합니다.

4. **Condition**(조건) 블레이드에서 미리 정의된 조건을 사용하려면 **Built-in**(기본 제공)을 선택하고, 사용자 고유의 조건을 지정하려면 **Custom**(사용자 지정)을 선택한 다음 **Save**(저장)를 클릭합니다.

    - **Built-in**(기본 제공)의 경우: 사용 가능한 조건 목록에서 선택한 다음 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 선택합니다.
        
        이러한 조건의 검색 규칙 및 몇 가지 예제에 대한 자세한 내용은 [기본 제공 조건에 대한 정보](#information-about-the-built-in-conditions) 섹션을 참조하세요.

    - **Custom**(사용자 지정)의 경우: 따옴표와 특수 문자를 포함하여 일치시킬 이름 및 구를 지정합니다. 그런 다음 정규식으로 일치시킬지 여부, 대/소문자를 구분할지 여부, 최소 발생 횟수 및 해당 발생에 발생 횟수에 포함할 고유 값이 있어야 하는지 여부를 지정합니다.
        
    **발생 옵션의 예**: 기본 제공 주민등록번호 옵션을 선택하고 최소 발생 횟수를 2로 설정하면 문서에 동일한 주민등록번호가 두 번 나열됩니다. **Count occurrences with unique values only**(고유 값이 있는 발생만 계산)를 **On**(켜기)으로 설정한 경우에는 조건을 충족하지 않으며 이 옵션을 **Off**(끄기)로 설정한 경우에는 조건을 충족합니다.

5. **Label**(레이블) 블레이드에서 다음을 구성하고 **Save**(저장)를 클릭합니다.

    - 자동 또는 권장 분류를 선택합니다. **Select how this label is applied: automatically or recommended to user**(이 레이블이 적용되는 방식 선택: 자동 또는 사용자에게 권장)에서 **Automatic**(자동) 또는 **Recommended**(권장)를 선택합니다.

    - 사용자 프롬프트 또는 정책 팁에 대한 텍스트를 지정합니다. 기본 텍스트를 유지하거나 사용자 고유의 문자열을 지정할 수 있습니다.

6. 변경 내용을 사용자에게 제공하려면 **Azure Information Protection** 블레이드에서 **Publish**(게시)를 클릭합니다.

## 기본 제공 조건에 대한 정보

미리 보기 기간 동안 다음 조건을 선택할 수 있습니다.

- [SWIFT 코드](#swift-code )

- [신용 카드 번호](#credit-card-number )

- [ABA 라우팅 번호](#aba-routing-number )

- [주민등록번호](#usa-social-security-number-ssn)

- [IBAN(국제 은행 계좌 번호)](#international-banking-account-number-iban)


### SWIFT 코드

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


### 신용 카드 번호

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

### ABA 라우팅 번호

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

### 주민등록번호

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

### IBAN(국제 은행 계좌 번호)

콘텐츠에 다음이 포함된 경우 이 정보 유형을 일치시킵니다.  

1. 다음 구: **IBAN** 

2. IBAN 번호: 국가 코드(문자 2자), 확인 번호(숫자 2자), bban 번호(숫자 최대 30자) 순.


테스트를 위한 예제:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## 다음 단계

Azure Information Protection 정책 구성에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organization-s-policy) 섹션의 링크를 사용하세요.  






<!--HONumber=Aug16_HO4-->


