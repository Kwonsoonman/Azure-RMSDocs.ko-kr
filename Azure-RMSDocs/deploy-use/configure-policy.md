---
title: "Azure Information Protection 정책 구성"
description: "분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 2510c14fc10411783838516f45fdfd06fd73350d
ms.lasthandoff: 02/24/2017


---

# <a name="configuring-azure-information-protection-policy"></a>Azure Information Protection 정책 구성

>*적용 대상: Azure Information Protection*

분류, 레이블 지정 및 보호를 구성하려면 Azure Information Protection 정책을 구성해야 합니다. 이 정책은 [Azure Information Protection 클라이언트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)를 설치한 컴퓨터에 다운로드됩니다.

Azure Information Protection 정책을 구성하려면

1. 새 브라우저 창에서 전역 관리자로 [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **Azure Information Protection** 블레이드로 이동합니다. 예를 들어 허브 메뉴에서 **추가 서비스**를 클릭하고 필터 상자에 **Information Protection**을 입력합니다. 결과에서 **Azure Information Protection**을 선택합니다. 

    그러면 **Azure Information Protection** 블레이드가 표시됩니다. 여기서 모든 사용자에게 적용되는 **전역** 정책을 열 수 있습니다. 또한 필요에 따라 범위가 지정된 정책을 추가하고 편집할 수 있습니다. **전역** Azure Information Protection 정책에는 구성할 수 있는 다음 요소가 포함됩니다.

    - 문서 및 전자 메일을 분류할 수 있는 레이블.

    - 사용자의 Office 응용 프로그램에 표시되는 Information Protection 표시줄의 제목 및 도구 설명.

    - 사용자가 문서를 저장하고 전자 메일을 보낼 때 분류를 적용할 수 있는 옵션.

    - 문서 및 전자 메일을 분류하기 위한 시작점으로 기본 레이블을 설정할 수 있는 옵션.

    - 원래보다 민감도 수준이 낮은 레이블을 선택한 경우 이유를 제공하라는 메시지를 사용자에게 표시할 수 있는 옵션.

    - 사용자를 위한 사용자 지정 도움말 링크를 제공하는 옵션.

Azure Information Protection은 **Personal**(개인), **Public**(공개), **Internal**(내부), **Confidential**(기밀) 및 **Secret**(비밀) 레이블을 포함하는 [기본 정책](configure-policy-default.md)과 함께 제공됩니다. 기본 레이블을 변경하지 않고 사용하거나, 이를 사용자 지정하거나, 삭제하고 새 레이블을 만들 수 있습니다.

Azure Information Protection 블레이드를 변경한 경우 **Save**(저장)를 클릭하여 변경 내용을 저장하거나 **Discard**(취소)를 클릭하여 마지막으로 저장된 설정으로 되돌립니다. 

원하는 변경 작업을 마쳤으면 **Publish**(게시)를 클릭합니다. 

Azure Information Protection 클라이언트는 지원되는 Office 응용 프로그램이 시작될 때마다 변경 내용을 확인하여 해당 Azure Information Protection 정책으로 변경 내용을 다운로드합니다.

## <a name="configuring-your-organizations-policy"></a>조직의 정책 구성

다음 정보를 사용하여 Azure Information Protection 정책을 구성할 수 있습니다.

- [기본 Information Protection 정책](configure-policy-default.md)

- [정책 설정을 구성하는 방법](configure-policy-settings.md)

- [새 레이블을 만드는 방법](configure-policy-new-label.md)

- [레이블을 삭제하거나 순서를 변경하는 방법](configure-policy-delete-reorder.md)

- [기존 레이블을 변경하거나 사용자 지정하는 방법](configure-policy-change-label.md)

- [보호를 적용하도록 레이블을 구성하는 방법](configure-policy-protection.md)

- [시각적 표시를 적용하도록 레이블을 구성하는 방법](configure-policy-markings.md)

- [자동 및 권장 분류에 대한 조건을 구성하는 방법](configure-policy-classification.md)

- [범위 지정 정책을 사용하여 특정 사용자에 대한 정책을 구성하는 방법](configure-policy-scope.md)

## <a name="next-steps"></a>다음 단계

기본 정책을 사용자 지정하는 방법에 대한 예제를 보려면 Office 응용 프로그램에서 결과 동작을 확인하고 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

