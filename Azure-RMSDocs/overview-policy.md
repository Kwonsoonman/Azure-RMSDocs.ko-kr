---
title: Azure Information Protection 정책 개요
description: Azure Inforamtion Protection 정책의 레이블 및 설정을 이해합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e66a2c117523eb01089881b8210f12ed2f657ed4
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304896"
---
# <a name="overview-of-the-azure-information-protection-policy"></a>Azure Information Protection 정책 개요

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

이 Azure Information Protection 정책에는 구성할 수 있는 다음 요소가 포함됩니다.
    
- 관리자와 사용자가 문서 및 이메일을 분류하고 선택적으로 보호하는 데 사용할 수 있는 레이블.

- 사용자의 Office 애플리케이션에 표시되는 Information Protection 표시줄의 제목 및 도구 설명.

- 문서 및 전자 메일을 분류하기 위한 시작점으로 기본 레이블을 설정할 수 있는 옵션.

- 사용자가 문서를 저장하고 전자 메일을 보낼 때 분류를 적용할 수 있는 옵션.

- 원래보다 민감도 수준이 낮은 레이블을 선택한 경우 이유를 제공하라는 메시지를 사용자에게 표시할 수 있는 옵션.

- 첨부 파일에 따라 메일 메시지에 자동으로 레이블을 지정할 수 있는 옵션.

- Information Protection 막대가 Office 애플리케이션에 표시되는지 여부를 제어하는 옵션.

- [전달 안 함] 단추가 Outlook에 표시되는지 여부를 제어하는 옵션.

- 사용자가 문서에 대한 고유 권한을 지정할 수 있는 옵션.

- 사용자를 위한 사용자 지정 도움말 링크를 제공하는 옵션.

Azure Information Protection은 5개의 기본 레이블을 포함하는 [기본 정책](configure-policy-default.md)과 함께 제공됩니다. 이러한 레이블 중 두 가지는 필요할 때 하위 범주를 제공하는 하위 레이블을 포함합니다. 하위 레이블에 대한 레이블이 구성된 경우 사용자가 기본 레이블을 선택할 수 없지만 하위 레이블 중 하나를 선택해야 합니다.

Azure Information Protection 레이블은 조직에서 일반적으로 만들고 저장하는 최저 분류인 개인 데이터부터 최고 분류인 극비 데이터에 이르기까지 전체 범위의 데이터와 함께 사용할 수 있습니다. 

기본 레이블을 변경하지 않고 사용하거나, 이를 사용자 지정하거나, 삭제하고 새 레이블을 만들 수 있습니다. 전체 지침에 대해서는 [Azure Information Protection 정책 구성](configure-policy.md)을 참조하세요.


## <a name="next-steps"></a>다음 단계

Azure Information Protection 정책을 사용자 지정하고 결과 동작을 확인하는 방법에 대한 예제를 보려면 다음 자습서를 시도해 보세요.

- [Azure Information Protection 정책 편집 및 새 레이블 만들기](infoprotect-quick-start-tutorial.md)

- [함께 작동하는 Azure Information Protection 정책 설정 구성](infoprotect-settings-tutorial.md)
