---
title: 사용자가 Azure RMS를 사용하여 파일을 보호할 수 있도록 지원 - AIP
description: Azure Information Protection의 Azure RMS(Azure Rights Management)Rights Management 서비스를 배포 및 구성한 후 사용자, 관리자 및 지원 센터에 지침을 제공할 때 도움이 되는 정보를 제공합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b948ad9eb4c0ce839d6bdf1c2c3324d6aba8b004
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42807137"
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>사용자가 Azure Rights Management 서비스를 사용하여 파일을 보호할 수 있도록 지원

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

조직에 대해 Azure Information Protection을 배포 및 구성한 후에는 사용자, 관리자 및 지원 센터를 위해 도움말과 지침을 제공합니다.

-   **최종 사용자 정보**
    
    중요한 정보가 포함된 문서와 전자 메일을 보호하는 방법 및 시간을 사용자에게 알립니다. 가능한 경우 새로운 프로세스를 소개하지 말고, 이미 친숙한 프로세스에 추가 단계를 통합할 수 있도록 기존 워크플로에 이 정보를 제공합니다. 그와 동시에 업무와 관련된 이점과 위험을 알리고 파일과 전자 메일을 보호해야 하는 경우에 대한 지침도 제공합니다. [템플릿](configure-policy-templates.md)을 구성했다면 템플릿 이름과 설명만으로 올바른 템플릿을 선택하기 어려울 경우 선택할 템플릿에 대한 지침을 제공합니다.
    
    > [!TIP]
    > 최종 사용자를 위한 예제 비디오:
    > -   [Microsoft Azure Information Protection](https://youtu.be/ToShAUdlrPo?list=PL8nfc9haGeb6qSm1kLU8n3Zqg398764h5)
    > -   [Azure RMS Document Tracking and Revocation](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)(Azure RMS 문서 추적 및 해지)

-   **관리자 정보**
    
    일부 응용 프로그램에서는 관리자가 구성하는 정책과 설정을 사용하여 정보 보호를 자동으로 적용합니다. 이러한 응용 프로그램의 경우에는 해당 응용 프로그램과 서비스를 관리하는 기타 관리자를 위한 지침을 제공해야 할 수 있습니다. 
    
    자세한 내용은 [응용 프로그램에서 Azure Rights Management 서비스를 지원하는 방법](applications-support.md) 및 [Azure Rights Management 서비스에 대해 응용 프로그램 구성](configure-applications.md)을 참조하세요.
    
-   **지원 센터 정보**
    
    사용자에게 Azure Information Protection 클라이언트가 있는 경우 지원 센터 운영자가 Office 버전에서 보호를 지원할 수 없는지 여부 및 현재 로그인한 사용자 계정과 같은 정보에 대해 **도움말 및 피드백** 옵션을 사용하도록 요청할 수 있습니다 . 이 옵션을 사용하여 로그 파일을 수집하고 클라이언트를 다시 설정할 수도 있습니다. 자세한 내용은 관리자 가이드인 [설치 검사 및 문제 해결](./rms-client/client-admin-guide.md#installation-checks-and-troubleshooting)을 참조하세요.
    
    보호된 문서의 모든 액세스에 대한 합법적인 요청이 있을 경우 지원 센터는 Azure Rights Management [슈퍼 사용자 기능](configure-super-users.md)을 사용하여 이 액세스를 요청하는 프로세스를 진행해야 합니다. 예를 들어 직원이 조직을 떠난 후 법률 자문 부서 또는 관리자가 이러한 요청을 요구할 수 있습니다.
    
    또한 사용자가 보고할 수 있는 일반적인 문제 중 일부는 다음 범주로 구성됩니다.
    
    - **로그인 도움말**
        
        Azure Rights Management 서비스에서 사용자를 인증해야 하는데 캐시된 자격 증명을 사용할 수 없으면 사용자에게 자격 증명을 입력하라는 메시지가 표시될 수 있습니다. 일반적으로 이러한 필수 자격 증명은 Office 365 테넌트 또는 Azure Active Directory 테넌트와 연결된 사용자의 회사 또는 학교 계정과 암호입니다. Azure Rights Management 서비스는 Azure AD 계정을 인증할 수 있지만 인증에 Microsoft 계정이 사용될 경우, 일부 응용 프로그램이 보호된 콘텐츠를 열 수도 있습니다. [추가 정보](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 
        
        사용자가 Azure Rights Management 서비스를 사용하는 응용 프로그램이 있는 경우 자격 증명을 입력하라는 메시지가 표시되면 사용할 계정에 대한 지침을 사용자와 지원 센터에 제공합니다.
        
    - **콘텐츠 보호 또는 사용 문제**
        
        사용자가 사용하는 응용 프로그램에 대해 적절한 지침이 있으며 Azure Rights Management 서비스에서 지원하는 응용 프로그램 및 장치를 사용하고 있는지 확인합니다. 지원되는 응용 프로그램 및 장치에 대한 자세한 내용은 [Azure 권한 관리에 대한 요구 사항](requirements.md)을 참조하세요.
        
        Azure Active Directory를 통해 보호된 콘텐츠를 보호하거나 사용하도록 특정 사용자 또는 그룹에게 권한을 부여할 수 있는지 확인하려면 [Azure Information Protection에 대한 사용자 및 그룹 준비](prepare.md)에 포함된 유효성 검사를 사용합니다.
        
        사용자가 보호된 콘텐츠를 열 수는 있지만 필요한 권한이 없는 경우 Rights Management 템플릿에 대해 구성된 올바른 그룹에 포함되어 있지 않은 것일 수 있습니다. 또는 사용자 또는 그룹에 대해 [템플릿을 다시 구성해야](configure-policy-templates.md) 하는 문제일 수 있습니다. 
        
        사용자가 보유하는 권한이 예상과 다를 경우 [사용 권한 테이블](configure-usage-rights.md#usage-rights-and-descriptions)에서 권한 설명 및 응용 프로그램별 구현을 확인하세요.

사용자가 문서와 메일을 보호할 수 있도록 다음 섹션에서 응용 프로그램 관련 정보를 참조하세요.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에서 정보 보호 사용

Office 2010이 있는 경우 보호된 문서 및 전자 메일을 보호하고 사용하기 위해 Azure Information Protection 클라이언트(또는 이전 응용 프로그램, RMS 공유 응용 프로그램)가 필요합니다. 그러나 Azure Information Protection 클라이언트는 이 서비스를 지원하는 모든 컴퓨터 및 모바일 장치에도 권장됩니다.

Azure Information Protection 클라이언트는 사용자가 보다 쉽게 문서 및 메일을 보호하도록 할 뿐 아니라 보호한 문서를 추적할 수 있도록 합니다. 또한 이전에 권한이 부여된 사용자가 더 이상 액세스할 필요가 없는 경우 추적된 문서를 해지할 수도 있습니다.

이 Windows 컴퓨터용 클라이언트를 사용하기 위한 지침은 [Azure Information Protection 클라이언트 사용자 가이드](./rms-client/client-user-guide.md)를 참조하세요.


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Office 365, Office 2016 또는 Office 2013에서 정보 보호 기능 사용
Azure Rights Management 서비스를 사용하고 있으며 Azure Information Protection 클라이언트를 설치하지 않은 경우 Office 데스크톱 앱의 Azure Information Protection 표시줄이 표시되지 않습니다. 리본의 **보호** 단추나 파일 탐색기의 **분류 및 보호**도 표시되지 않습니다. 이러한 추가 옵션은 파일 및 전자 메일을 보다 쉽게 보호할 수 있도록 합니다. 이러한 사용자는 다음에 나오는 단계와 유사한 지침을 따라야 합니다.

> [!TIP]
> 이러한 응용 프로그램에서 정보 보호 기능을 사용하기 위한 응용 프로그램별 도움말과 지침을 찾으려면 **IRM** 및 응용 프로그램 이름과 버전을 검색합니다.

#### <a name="to-protect-a-document-in-word-2013"></a>Word 2013에서 문서를 보호하려면

1.  Microsoft Word 내에서 문서를 만듭니다.

2.  **파일** 메뉴에서 **정보**를 클릭한 후 **문서 보호**를 클릭하고 **액세스 제한**을 클릭합니다.

3. 적합한 사용 권한을 빠르게 적용할 수 있는 템플릿을 선택하거나 **액세스 제한**을 선택하고 사용 권한을 직접 선택합니다.

    > [!NOTE]
    > 이전에 컴퓨터에서 Rights Management를 사용한 적이 없으면 **액세스 제한** 옵션이 Azure Rights Management 서비스에 연결되며 Office IRM 클라이언트를 구성하기 위해 자격 증명이 요구됩니다. 그러면 템플릿 또는 사용 권한을 선택할 수 있습니다.

3.  문서를 저장합니다.

다른 사용자는 문서를 열 때 먼저 인증하게 됩니다. 해당 사용자에게 문서를 열 권한이 없으면 문서가 열리지 않으며 문서를 열 권한이 있으면 해당 사용자에 대해 지정된 제한적 [사용 권한](configure-usage-rights.md)으로 문서가 열립니다. 

예를 들어 보기 전용 사용 권한이 있는 사용자는 문서를 다른 위치로 먼저 복사하더라도 편집하거나 저장할 수 없습니다. 

사용 권한은 제한 배너를 통해 문서 맨 위에 표시됩니다. 이 배너에는 문서에 적용된 권한이 표시될 수도 있고 해당 권한을 표시할 수 있는 링크가 제공될 수도 있습니다.

#### <a name="to-protect-an-email-message-using-outlook-2013-and-exchange-online"></a>Outlook 2013 및 Exchange Online을 사용하여 전자 메일 메시지를 보호하려면

1.  Outlook 내에서 조직의 받는 사람 주소를 지정하여 메일 메시지를 작성합니다.

2.  **옵션** 탭에서 **권한**을 클릭하고 옵션을 선택합니다. 예: **전달 금지** 또는 **\<회사 이름>- 기밀** 또는 **\<회사 이름> - 기밀 보기 전용**.

3.  메시지를 보냅니다.

보호된 문서를 볼 때와 마찬가지로 받는 사람은 보호된 전자 메일 메시지를 열면 먼저 인증을 받게 됩니다. 전자 메일 메시지를 열 권한이 있으면 해당 사용자에 대해 지정된 제한적 [사용 권한](configure-usage-rights.md)으로 메시지가 열립니다. 

예를 들어 전자 메일 메시지를 **전달 금지** 옵션을 사용하여 보호한 경우 리본의 전달 단추를 사용할 수 없게 됩니다.

#### <a name="to-protect-an-email-message-using-outlook-on-the-web"></a>웹용 Outlook을 사용하여 전자 메일 메시지를 보호하려면

1.  웹용 Outlook을 사용하여 조직의 받는 사람 주소가 지정된 새 메일 메시지를 작성합니다.

2.  **…**, **사용 권한 설정**을 차례로 클릭하고 옵션을 선택합니다. 예: **전달 금지** 또는 **전체 회신 금지**. 또는 **\<회사 이름>- 기밀** 또는 **\<회사 이름> - 기밀 보기 전용**.

3.  메시지를 보냅니다.

보호된 문서를 볼 때와 마찬가지로 받는 사람은 전자 메일 메시지를 열면 먼저 인증을 받게 됩니다. 전자 메일 메시지를 열 권한이 있으면 해당 사용자에 대해 지정된 제한적 [사용 권한](configure-usage-rights.md)으로 메시지가 열립니다. 

예를 들어 **전체 회신 금지**를 선택한 경우에는 메시지 창에서 **전체 회신** 옵션을 사용할 수 없습니다.


