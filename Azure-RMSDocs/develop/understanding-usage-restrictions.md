---
title: "사용 제한 이해 | Azure RMS"
description: "모든 RMS 사용 응용 프로그램은 사용 제한을 적용해야 합니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8862c1be4f084ee1495126b73f4e2adbdeb47acc
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2017
---
# <a name="understanding-usage-restrictions"></a>사용 제한 이해

모든 RMS 사용 응용 프로그램은 사용 제한을 적용해야 합니다. 사용 제한은 사용자가 작업(예: 문서 인쇄)을 수행하려고 하지만 해당 문서에 대한 RMS 정책에서 이 작업을 수행할 수 있는 권한(예: PRINT 권한)을 부여하지 않을 경우 발생하는 조건입니다.

[IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)함수를 사용하여 문서에 대한 사용자 권한을 쿼리할 수 있습니다.

## <a name="designing-with-usage-restrictions"></a>사용 제한을 적용하여 설계

-   표준 RMS 권한 익히기

    응용 프로그램에서 적용할 수 있는 RMS 권한의 전체 집합은 [사용 제한 참조](#usage-restriction-reference)를 참조하세요.

    사용자 상황과 관련된 응용 프로그램 정의 권한이 표준 RMS 권한보다 높게 만들어질 수도 있습니다.

-   사용 제한 적용 지점 식별

    *사용 제한 적용 지점*은 사용 제한을 적용해야 하는 응용 프로그램 제어 흐름 내의 위치입니다. [사용 제한 참조](#usage-restriction-reference) 항목에서는 일반적인 적용 지점의 몇 가지 예를 제공합니다.

    사용자 응용 프로그램을 평가하여 적용되는 사용 제한 적용 지점을 확인합니다.

    [사용 제한 참조](#usage-restriction-reference)에 설명된 모든 적용 지점이 응용 프로그램에 필요한 것은 아닙니다. 예를 들어 응용 프로그램에서 사용자가 콘텐츠를 인쇄하도록 허용하지 않는 경우 **IPC\_GENERIC\_PRINT** 권한을 확인할 필요가 없습니다.

-   각 적용 지점에서 액세스를 검사하도록 코드 업데이트

    특정 권한을 적용하는 방법에 대한 지침은 [사용 제한 참조](#usage-restriction-reference)를 참조하세요.

## <a name="usage-restriction-reference"></a>사용 제한 참조

사용 제한은 다음과 같은 상수에 의해 정의됩니다.

AD RMS 권한 열에 나열된 각 사용자 권한에는 설명, 적용 지점 및 제안된 적용 방법이 있습니다.

| AD RMS 권한/설명 | 적용 방법 |
|--------------------------|----------------|
|**IPC_GENERIC_ALL** <br><br> 사용자에게 모든 권한을 부여합니다. <br><br> **일반적인 적용 지점**: 없음 |이 권한은 시스템에서 사용되며 일반적으로 직접 검사하면 안 됩니다. <br><br> 이 예제와 같이 [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)는 이 권한을 사용하여 사용자에게 다른 권한을 부여할지 여부를 결정합니다.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`|
|**IPC_GENERIC_READ** <br><br> 문서 내용을 읽을 수 있는 권한입니다. <br><br> **일반적인 적용 지점**: 문서 로드|문서 내용을 로드하거나 표시하지 않습니다.|
|**IPC_GENERIC_WRITE** <br><br> 문서 내용을 편집할 수 있는 권한입니다. <br><br> **일반적인 적용 지점**: 문서 수정|문서 내용을 수정하는 데 사용할 수 있는 UI 컨트롤을 편집할 수 없도록 설정합니다. <br><br> 문서 변경을 트리거하는 메뉴 항목을 모두 사용하지 않도록 설정합니다. 일반적인 예로 **편집** > **잘라내기**, **편집** > **붙여넣기**, **삽입** 등이 있습니다. <br><br>문서 변경을 트리거하는 바로 가기 메뉴 항목을 모두 사용하지 않도록 설정합니다.|
|AD RMS 권한 없음 <br><br> 설명 없음 <br><br> **일반적인 적용 지점**: 저장 | **파일** > **저장** 메뉴를 사용하지 않도록 설정합니다. <br><br> **참고** 이 권한은 원본 문서의 변경을 나타내지 않으므로 **파일** > **다른 이름으로 저장**을 제어하지 않습니다.<br><br> 저장을 트리거하는 데 사용할 수 있는 바로 가기 키(예: Ctrl+S)를 모두 사용하지 않도록 설정합니다.<br><br> **팁** 사용자에게 이 권한이 없을 경우 실패하도록 핵심 **파일** > **저장** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 저장을 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다. |
|**IPC_GENERIC_EXTRACT** <br><br> 보호된 형식에서 콘텐츠를 추출하여 보호되지 않는 형식으로 저장할 수 있는 권한입니다. <br><br> **일반적인 적용 지점**: 클립보드에 복사 | **편집** > **복사** 메뉴를 사용하지 않도록 설정합니다. **편집** > **잘라내기** 메뉴를 사용하지 않도록 설정합니다. <br><br>바로 가기 메뉴에서 **복사** 및 **잘라내기**를 사용하지 않도록 설정합니다.<br><br>복사를 트리거할 수 있는 바로 가기 키(예: Ctrl+C 또는 Ctrl+X)를 모두 사용하지 않도록 설정합니다.<br><br>사용자에게 이 권한이 없을 경우 데이터 복사를 거부하도록 [**WM_CUT**](https://msdn.microsoft.com/library/ms649023)에 대한 창 메시지 처리기를 업데이트합니다. 창에서 기본 Windows 제공 메시지 처리기를 사용하는 경우 이 창을 서브클래스하고 **WM_COPY** 및 **WM_CUT**에 대한 고유의 처리기를 제공합니다. |
|AD RMS 권한 없음 <br><br> 설명 없음 <br><br> **일반적인 적용 지점**: 다른 이름으로 저장 |**다른 이름으로 저장** 대화 상자에서 RMS 보호 없이 문서가 저장되게 하는 파일 형식을 모두 사용하지 않도록 설정합니다.|
|AD RMS 권한 없음 <br><br> 설명 없음 <br><br> **일반적인 적용 지점**: Alt+PrtScn|문서 내용을 렌더링하는 창에서 [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx)를 호출합니다.|
|**IPC_GENERIC_EXPORT** <br><br> 보호된 형식에서 콘텐츠를 추출하여 다른 AD RMS 보호된 형식으로 저장할 수 있는 권한입니다. <br><br> **일반적인 적용 지점**: 다른 이름으로 저장|**다른 이름으로 저장** 대화 상자에서 다른 파일 형식으로 저장하는 기능을 사용하지 않도록 설정합니다.<br><br>**팁** 사용자가 이 파일을 다른 형식으로 저장하려고 하며 이 권한이 없을 경우 실패하도록 핵심 **파일** > **다른 이름으로 저장** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 다른 이름으로 저장을 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다.|
|**IPC_GENERIC_PRINT** <br><br> 문서 내용을 인쇄할 수 있는 권한입니다. <br><br> **일반적인 적용 지점**: 인쇄|**파일** > **인쇄** 메뉴를 사용하지 않도록 설정합니다.<br><br>인쇄를 트리거하는 데 사용할 수 있는 바로 가기 키(예: Ctrl+P)를 모두 사용하지 않도록 설정합니다.<br><br>인쇄를 트리거하는 데 사용할 수 있는 바로 가기 메뉴 항목을 사용하지 않도록 설정합니다.<br><br>**팁** 사용자에게 이 권한이 없을 경우 실패하도록 핵심 **파일** > **인쇄** 코드를 업데이트하는 것이 좋습니다. 이렇게 하면 인쇄를 트리거하는 데 사용할 수 있는 UX 메커니즘을 놓칠 경우 안전망 역할을 합니다.|
|**IPC_GENERIC_COMMENT** <br><br> 일부 응용 프로그램은 핵심 문서 내용을 업데이트하지 않고 문서에 주석을 추가하는 기능을 지원합니다.<br><br>이 권한은 이 기능에 대한 액세스 권한을 사용자에게 부여합니다. <br><br> **일반적인 적용 지점**: <br><br> 검토 > 주석 삽입 <br><br> 검토 > 주석 삭제 | 문서 설명이나 주석을 수정하는 데 사용할 수 있는 메뉴 항목을 모두 사용하지 않도록 설정합니다. 예를 들어 **검토** > **주석 삽입**, **검토** > **주석 삭제** 등이 있습니다. <br><br>문서 주석 수정을 트리거할 수 있는 바로 가기 키를 모두 사용하지 않도록 설정합니다.<br><br>**참고** 새 주석을 파일에 저장하려면 기본 구현에 **IPC_GENERIC_COMMENT** 및 **IPC_GENERIC_WRITE**가 둘 다 필요합니다. 응용 프로그램에서 **IPC_GENERIC_COMMENT** 권한이 부여되고 **IPC_GENERIC_WRITE** 권한이 부여되지 않은 경우에 대한 지원을 추가할 수도 있습니다. 이 경우 문서 수정이 주석으로만 제한되면 저장할 수 있습니다.|
|**IPC_VIEW_RIGHTS** <br><br> 설명 없음 <br><br> **일반적인 적용 지점**: 해당 없음|시스템에 의해 적용됩니다. 이 권한이 부여되지 않은 경우 시스템에서 개발자가 라이선스에서 [**사용자 권한 목록**](https://msdn.microsoft.com/library/hh535286.aspx)을 쿼리하도록 허용하지 않습니다.
|**IPC_EDIT_RIGHTS** <br><br> 일부 응용 프로그램은 사용자가 AD RMS 보호된 콘텐츠에 대한 사용자 및 권한 집합을 수정할 수 있도록 허용합니다.<br><br>이 권한은 이 기능에 대한 액세스 권한을 사용자에게 부여합니다. <br><br> **일반적인 적용 지점**: 응용 프로그램 권한 편집 UI 컨트롤|문서에 대한 RMS 정책을 편집하는 데 사용할 수 있는 UI에 사용자가 액세스할 수 없도록 설정합니다.|


## <a name="related-topics"></a>관련 항목

* [IpcAccessCheck](https://msdn.microsoft.com/library/hh535253.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]