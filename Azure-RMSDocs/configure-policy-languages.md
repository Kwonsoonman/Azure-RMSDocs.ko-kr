---
title: Azure Information Protection에서 다른 언어에 대한 레이블 및 템플릿 구성
description: Azure Information Protection 정책에서 언어를 지정하고 번역을 가져오는 방식으로 Information Protection 표시줄에 표시되는 레이블과 표시되는 템플릿에 대한 다른 언어 지원을 추가할 수 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: c118abdf0f0b659b9ae330f44617901f8d11c300
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170298"
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Azure Information Protection에서 다른 언어에 대한 레이블 및 템플릿을 구성하는 방법

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection의 기본 레이블이 여러 언어를 지원하더라도 지정하는 레이블 이름 및 설명에 대한 지원을 구성해야 합니다. 이 구성을 사용하려면 다음을 수행해야 합니다.

1. 사용자가 사용하는 언어를 선택합니다. 

2. 현재 레이블 이름과 설명을 파일로 내보냅니다.

3. 파일을 편집하여 번역을 제공합니다.

4. 파일을 다시 Azure Information Protection 정책으로 가져옵니다.

다음 조건 중 하나가 적용되는 경우 다른 언어에 대한 템플릿을 구성할 수도 있습니다. 이 구성은 사용자 또는 관리자가 현재 템플릿 이름과 설명을 지역화된 해당 언어로 봐야 하는 경우 적합합니다.

- 템플릿이 Azure 클래식 포털에서나 PowerShell을 사용하여 만들어졌고 템플릿이 **미리 정의된 템플릿 선택** 보호 설정을 사용하여 레이블에 연결되지 않았습니다.

- 레이블을 지원하는 구독이 없으므로 Azure Portal에서 템플릿을 만들고 관리할 수만 있습니다.

Office 및 Windows에 대한 사용자의 언어 설정과 일치하는 언어를 선택합니다. 그러면 이러한 레이블 이름 및 설명은 Office 앱의 Azure Information Protection 표시줄과 **분류 및 보호 - Azure Information Protection** 대화 상자에 각각 표시됩니다. 선택할 언어에 대한 자세한 내용은 이 페이지에서 [Azure Information Protection 클라이언트에서 표시할 언어를 결정하는 방법](#how-the-azure-information-protection-client-determines-the-language-to- display) 섹션을 참조하세요. 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>다른 언어에 대한 레이블 및 템플릿을 구성하려면

1. 아직 그렇게 하지 않은 경우 새 브라우저 창을 열고 [Azure Portal에 로그인](configure-policy.md#signing-in-to-the-azure-portal)합니다. **Azure Information Protection** 블레이드로 이동합니다.
    
    예를 들어 허브 메뉴에서 **모든 서비스**를 클릭하고 필터 상자에 **Information**을 입력합니다. **Azure Information Protection**을 선택합니다.

2. **관리** > **언어** 메뉴 옵션에서: **Azure Information Protection - 언어** 블레이드에서 **번역할 새 언어 추가**를 선택합니다. 추가할 언어를 선택한 다음 **확인**을 선택합니다. 검색 상자에 언어 이름을 입력하거나 사용 가능한 언어 목록을 스크롤할 수 있습니다.

3. 이제 **Azure Information Protection - 언어** 블레이드에 선택한 언어가 표시됩니다.
    
    - 다른 언어를 추가하려면 **번역할 새 언어 추가**를 선택하고 이전 단계를 반복합니다. 
        
        > [!NOTE]
        > Office 및 Windows에 대한 사용자의 언어를 선택해야 합니다. 경우에 따라 컴퓨터마다 두 개의 다른 항목을 선택해야 할 수 있습니다.
        
    - 추가한 언어가 마음에 들지 않으면 목록에서 해당 항목을 선택하고 **제거**를 클릭합니다.

4. 지원하려는 모든 언어가 나열되면 **언어 이름** 옆에 있는 확인란을 선택하여 모든 항목을 선택하고(또는 개별 항목 선택) **내보내기**를 클릭하여 기존 레이블 이름 및 설명의 로컬 복사본을 파일에 저장합니다. 
    
    다운로드한 파일의 이름은 **exported localization.zip**으로 지정된 후 로컬 다운로드 폴더에 저장됩니다. Azure Portal의 상태 표시줄에서 이 파일 이름을 선택하여 액세스할 수도 있습니다.

5. **exported localization.zip**에서 파일 압축을 풀면 다운로드하기 위해 선택한 각 언어에 대해 .xml 파일이 생성됩니다. 

6. 각 .xml 파일을 편집합니다. `<LocalizedText>` 태그 내의 각 문자열에 대해 선택한 각 언어의 원하는 번역을 제공합니다. 

7. 각 .xml 파일을 편집한 경우 이러한 파일이 포함된 새 압축(zip) 폴더를 만듭니다. 압축한 폴더에는 이름을 지정할 수 이지만 확장명은 .zip이어야 합니다.

8. **Azure Information Protection - 언어** 블레이드로 돌아가서 **가져오기**를 선택합니다. 이 옵션을 사용할 수 없으면 **언어 이름**에 대한 확인란 또는 개별적으로 선택한 언어에 대한 확인란을 선택 취소합니다.
    
    가져오기가 완료되면 지역화된 이름 및 설명이 사용자에게 다운로드됩니다.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Azure Information Protection 클라이언트가 표시할 언어를 결정하는 방법

다른 언어를 지원하는 Azure Information Protection 정책을 다운로드하면 레이블 이름 및 도구 설명에 사용되는 언어는 다음 논리에 따라 결정됩니다.

**Office 앱의 Azure Information Protection 표시줄에 사용되는 레이블 및 도구 설명:**

- Office 앱용 언어와 직접적으로 일치할 경우 레이블 이름 및 설명이 해당 언어로 표시됩니다.

- Office 앱 언어와 일치하지 않을 경우 기본적으로 사용자가 지정한 언어의 레이블 이름 및 설명이 모든 사용자에게 표시됩니다. 이 언어는 일반적으로 기본 정책에 사용되는 언어인 영어입니다.

**마우스 오른쪽 단추를 클릭하고 파일이나 폴더를 보호할 때 표시되는 레이블 및 도구 설명:**

- 운영 체제의 언어와 직접적으로 일치할 경우 레이블 이름 및 설명이 해당 언어로 표시됩니다.

- 운영 체제 언어와 일치하지 않을 경우 기본적으로 사용자가 지정한 언어의 레이블 이름 및 설명이 모든 사용자에게 표시됩니다. 이 언어는 일반적으로 기본 정책에 사용되는 언어인 영어입니다.

## <a name="when-localized-label-names-are-not-used"></a>지역화된 레이블 이름이 사용되지 않을 경우

다음과 같은 시나리오에서 지역화된 레이블(및 하위 레이블) 이름은 사용되지 않습니다. 테넌트 간에 일관성을 위해 다음과 같은 경우 항상 기본 언어가 사용됩니다.

- 클라이언트 사용 현황 로그

- PowerShell(Get-AIPFileStatus의 출력)

- 문서 메타데이터 및 전자 메일 헤더


## <a name="next-steps"></a>다음 단계

레이블에 적용할 수 있는 옵션 구성 및 Azure Information Protection 정책의 기타 설정에 대해 자세히 알아보려면 [조직의 정책 구성](configure-policy.md#configuring-your-organizations-policy) 섹션의 링크를 사용하세요.



