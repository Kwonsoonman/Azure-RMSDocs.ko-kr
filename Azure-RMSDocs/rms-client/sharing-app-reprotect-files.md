---
title: RMS로 보호된 파일에 대한 권한 변경 - AIP
description: 파일이 Rights Management로 보호된 경우 파일을 다시 보호한 다음 해당 파일에 대한 액세스 권한이 있어야 하는 모든 사용자와 해당 사용자에게 부여할 사용 권한을 지정하여 사용 권한을 변경할 수 있습니다.
keywords: ''
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 5ac121b3-d7a0-40e4-8fe7-90bf4cf796f1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5f031bf584b9feffc185c384b9a54780c844407b
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808397"
---
# <a name="change-permissions-on-files-that-have-been-protected-by-rights-management"></a>Rights Management로 보호된 파일에 대한 사용 권한 변경

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

파일이 Rights Management로 보호된 경우 파일을 다시 보호한 다음 해당 파일에 대한 액세스 권한이 있어야 하는 모든 사용자와 해당 사용자에게 부여할 사용 권한을 지정하여 사용 권한을 변경할 수 있습니다.

> [!IMPORTANT]
> 이 변경은 증분 변경이 아니라 완전한 대체입니다. 원하는 전체 사용 권한 집합으로 파일을 다시 효과적으로 보호합니다.
> 
>  예를 들어 마케팅 부서의 직원만 파일을 열 수 있는 방식으로 파일이 보호되는 경우 영업 부서의 직원도 파일을 열 수 있게 하려면 영업 부서와 마케팅 부서에서 파일을 열 수 있도록 파일을 다시 보호해야 합니다.
>
> 마찬가지로 사용 권한을 추가하거나 제거하려는 경우 추가하거나 제거할 해당 사용 권한만 지정할 수는 없으며, 지정된 사용자에게 부여할 모든 사용 권한을 지정해야 합니다.

다시 보호하려는 파일의 소유자(예: 공유 응용 프로그램을 사용하여 원래 파일을 보호한 사람)인 경우 자동으로 파일을 다시 보호하는 권한을 가지게 됩니다. 소유자가 아닌 경우 현재 보호된 파일에 있는 사용 권한에 따라 파일을 다시 보호할 권한이 있을 수도 있고 없을 수도 있습니다. 파일을 다시 보호하기 위해 [모든 권한 사용 권리](../configure-usage-rights.md#usage-rights-and-descriptions)가 필요합니다.

예를 들어 다른 사용자가 Rights Management 공유 응용 프로그램을 사용하여 파일을 보호한 경우 해당 사용자가, 사용자가 속하는 그룹을 지정하고 사용자 지정 권한으로 **공동 소유자**를 지정하면 사용자는 파일을 다시 보호할 수 있습니다. 그러나 해당 사용자가, 사용자가 속하는 이름이나 그룹을 지정하지 않았거나 **검토자 - 보기 및 편집**이나 사용자가 사용 권한을 제거할 수 없는 템플릿을 선택한 경우 사용자는 파일을 다시 보호할 수 없습니다. 확인하는 가장 쉬운 방법은 파일을 다시 보호해 보는 것입니다.

파일이 더 이상 보호되지 않도록 모든 사용 권한을 완전히 제거하려면 [파일에서 보호 제거](sharing-app-remove-protection.md)를 참조하세요.

## <a name="to-re-protect-a-file-in-place"></a>바로 파일을 다시 보호하려면

1.  파일 탐색기에서 보호할 파일을 선택합니다. 마우스 오른쪽 단추를 클릭하고 **RMS로 보호**를 선택한 다음 **바로 보호**를 선택합니다. 예를 들면 다음과 같습니다.

    ![바로 보호 메뉴 옵션](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > **RMS로 보호** 옵션이 표시되지 않는다면 RMS 공유 응용 프로그램이 컴퓨터에 설치되지 않았거나, 설치를 완료하기 위해 컴퓨터를 다시 시작해야 하는 경우입니다. RMS 공유 응용 프로그램을 설치하는 방법에 대한 자세한 내용은 [Rights Management 공유 응용 프로그램 다운로드 및 설치](install-sharing-app.md)를 참조하세요.

2.  다음 중 하나를 수행합니다.

    -   정책 템플릿 선택: 일반적으로 조직 내 사람들에게 액세스 및 사용을 제한하는 사전 정의된 권한입니다. 예를 들어 조직 이름이 "Contoso, Ltd"이면 **Contoso, Ltd - 기밀 보기 전용**이라고 표시될 수 있습니다. 이 컴퓨터에서 처음으로 파일을 보호하는 경우 먼저 **회사 정의 보호**를 선택하여 탬플릿을 다운로드해야 합니다.

        다음에 **바로 보호** 옵션을 클릭하면 선택 가능한 템플릿이 최대 10개까지 표시됩니다. 사용할 수 있는 템플릿이 10개가 넘는데도 원하는 템플릿이 표시되지 않으면 **회사 정의 보호**를 클릭하여 모든 템플릿을 다운로드하고 표시합니다.

        정책 템플릿을 선택하면 여러 파일과 폴더를 보호할 수 있습니다. 폴더를 선택하면 폴더의 모든 파일이 보호 대상으로 자동 선택되지만 해당 폴더에 만든 새 파일은 자동으로 보호되지 않습니다.

    -   **사용자 지정 권한**선택: 템플릿이 필요한 보호 수준을 제공하지 않거나 직접 보호 옵션을 명시적으로 설정하려는 경우 이 옵션을 선택합니다. [보호 대화 상자 추가](sharing-app-dialog-box.md)에서 이 파일에 대한 옵션을 지정하고 **적용**을 클릭합니다.

3. 파일을 다시 보호하는 권한이 없는 경우 **콘텐츠를 보호할 수 없음** 메시지와 담당자(문서 소유자)가 사용자의 사용 권한을 변경할 수 있도록 담당자의 메일 주소가 함께 표시됩니다.

    파일을 다시 보호하는 권한이 있는 경우 파일이 보호되고 있음을 설명하는 대화 상자가 잠시 표시될 수 있으며, 포커스가 파일 탐색기로 돌아갑니다. 이제 선택한 파일이 변경 내용으로 보호됩니다. 

> [!NOTE]
> 파일을 다시 보호할 수 있기 전에 먼저 Rights Management Services에서 사용자에게 이 파일에 대해 이 작업을 수행할 권한이 있는지 확인하기 위해 사용자 이름 및 암호를 확인합니다. 이는 어떤 경우에 캐시될 수도 있고 자격 증명을 요청하는 메시지가 표시되지 않습니다. 다른 경우 자격 증명을 제공하라는 메시지가 표시됩니다.
>
> 조직에서 Azure Information Protection 또는 AD RMS를 사용하지 않으면 RMS로 보호된 파일을 사용할 수 있도록 사용자의 자격 증명을 허용하는 무료 계정을 신청할 수 있습니다.
>
> -   이 계정에 적용하려면 링크를 클릭하여 [개인용 RMS](http://go.microsoft.com/fwlink/?LinkId=309469)를 적용합니다.
>
>     등록하면 개인 메일 주소보다 회사 메일 주소를 사용합니다. 보호된 첨부 파일을 메일로 전송받았기 때문에 등록한 경우 메일 메시지를 보내는 데 사용된 동일한 메일 주소를 사용합니다.
> -   자세한 내용은 [개인용 RMS 및 Azure 권한 관리](../rms-for-individuals.md)를 참조하세요.

## <a name="to-re-protect-a-file-that-you-have-emailed"></a>메일로 보낸 파일을 다시 보호하려면

메일로 보낸 파일에 대한 사용 권한을 변경하려면:

- **더 많은 사용자가 파일을 읽을 수 있도록 하려면**: [메일을 통해 공유하는 파일 보호](sharing-app-protect-by-email.md)의 지침에 따라 해당 사용자에게 파일을 메일로 보냅니다.

- **파일에 대한 사용 권한을 변경하려면**: [메일을 통해 공유하는 파일 보호](sharing-app-protect-by-email.md)의 지침에 따라 다시 파일을 메일로 보냅니다. 

    원래 메일로 보낸 파일에 대한 이전 사용 권한을 제거할 수는 없으므로, 파일을 새 버전으로 바꾸기만 하고 받는 사람이 해당 버전의 문서를 더 이상 열 수 없도록 이전에 메일로 보낸 파일의 취소를 고려합니다. 취소는 사용 권한을 더 제한적으로 만들어야 하는 경우(예: 파일에 액세스하면 안 되거나 더 이상 파일을 편집할 수 있어서는 안 되는 사용자 제거)에 적절합니다.

    메일로 보낸 파일을 취소하려면 [문서 추적 및 취소](sharing-app-track-revoke.md)를 참조하세요.


## <a name="examples-and-other-instructions"></a>예제 및 기타 지침
예를 들어 Rights Management 공유 응용 프로그램 및 방법 지침을 사용하는 방법에 대한 예는 Rights Management 공유 응용 프로그램 사용자 가이드에서 다음 섹션을 참조하세요.

-   [RMS 공유 응용 프로그램 사용 예제](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [원하는 옵션을 선택하](sharing-app-user-guide.md#what-do-you-want-to-do)세요.

## <a name="see-also"></a>참고 항목
[Rights Management 공유 응용 프로그램 사용자 가이드](sharing-app-user-guide.md)
