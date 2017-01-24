---
title: "Rights Management로 보호된 파일 보기 및 사용 | Azure Information Protection"
description: "Azure Information Protection 클라이언트를 설치해야 하는 보호된 파일을 보고 사용하기 위한 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 364891123720daaacacbea1b382b7d101d75cd1a


---

# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Rights Management로 보호된 파일 보기 및 사용

>*적용 대상: Active Directory Rights Management 서비스, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

**[ 이 클라이언트 버전은 미리 보기 상태이며 변경될 수 있습니다. ]**

[컴퓨터에 Azure Information Protection 클라이언트가 설치되어 있는](install-client-app.md) 경우에는 보호된 파일을 열기만 하면 볼 수 있습니다. 예를 들어 전자 메일 메시지의 첨부 파일을 두 번 클릭하거나 파일 탐색기에서 파일을 두 번 클릭할 수도 있고 파일의 링크를 클릭할 수도 있습니다.

> [!NOTE]
> 보호된 파일을 볼 수 있기 전에 먼저 Rights Management 서비스는 파일을 볼 수 있는 권한이 있는지 확인하기 위해 사용자 이름 및 암호를 확인합니다. 이는 어떤 경우에 캐시될 수도 있고 자격 증명을 요청하는 메시지가 표시되지 않습니다. 다른 경우 자격 증명을 제공하라는 메시지가 표시됩니다.
>
> 조직이 Office 365 또는 Azure용으로 사용하도록 클라우드 기반 계정을 제공하지 않으며 AD RMS를 사용하지 않으면 Rights Management를 사용하여 보호되는 파일을 열 수 있도록 자격 증명을 허용하는 무료 계정을 신청할 수 있습니다.
>
> -   이 계정에 적용하려면 링크를 클릭하여 [개인용 RMS](http://go.microsoft.com/fwlink/?LinkId=309469)를 적용합니다.
>
>     등록하면 개인 메일 주소보다 회사 메일 주소를 사용합니다. 보호된 첨부 파일을 메일로 전송받았기 때문에 등록한 경우 메일 메시지를 보내는 데 사용된 동일한 메일 주소를 사용합니다.
> -   자세한 내용은 [개인용 RMS 및 Azure 권한 관리](../understand-explore/rms-for-individuals.md)를 참조하세요.

## <a name="to-view-and-use-a-protected-file"></a>보호된 파일을 보고 사용하려면

1. 보호된 파일을 엽니다. 예를 들어 파일이나 첨부 파일을 두 번 클릭하거나 파일의 링크를 클릭합니다. 앱을 선택하라는 메시지가 나타나면 **Azure Information Protection Viewer(미리 보기)**를 선택합니다. 

2. **로그인** 또는 **등록** 페이지가 표시되면 **로그인**을 클릭하고 자격 증명을 입력합니다. 보호된 파일이 첨부 파일로 전송된 경우에는 파일을 전송하는 데 사용된 것과 같은 전자 메일 주소를 지정해야 합니다.
    
    허용되는 계정이 없는 경우 이 페이지 맨 위에 있는 참고 부분의 내용을 참조하여 무료 계정을 등록하고 이 지침을 다시 수행하세요.

3. 읽기 전용 버전의 파일이 **Azure Information Protection 뷰어**에서 열립니다. 권한이 있으면 파일을 인쇄하고 편집할 수 있습니다. 

    **권한**을 클릭하면 파일에 대한 권한을 확인할 수 있습니다. **권한** 대화 상자에서는 추가 권한과 함께 새 파일 버전을 요청하려는 경우 연락할 수 있는 파일 소유자도 확인할 수 있습니다.
    
    권한 및 각 권한에 포함되는 사용 권한에 대한 자세한 내용은 [권한 수준에 포함된 권한](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels)을 참조하세요.

4. 파일을 편집하려면 **다른 이름으로 저장**을 클릭합니다. 이렇게 하면 보호되지 않은 파일을 원본 파일 이름 확장명으로 저장할 수 있습니다. 그런 다음 해당 파일 형식과 연결된 응용 프로그램을 사용하여 파일을 편집할 수 있습니다.

5. 보호된 파일을 추가로 열려는 경우 **열기** 옵션을 사용하여 뷰어에서 해당 파일을 직접 찾아볼 수 있습니다. 그러면 뷰어에서 원본 파일 대신 선택한 파일이 표시됩니다. 

> [!TIP]
> 보호된 파일이 열리지 않으면 [RMS 분석기 도구](https://www.microsoft.com/en-us/download/details.aspx?id=46437)를 다운로드하여 사용합니다. 이 도구의 지침에 따라 보호된 문서를 열지 못하게 하는 컴퓨터의 문제를 확인합니다.


## <a name="other-instructions"></a>기타 지침
사용 방법 지침은 Azure Information Protection 사용자 가이드의 다음 섹션을 참조하세요.

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


