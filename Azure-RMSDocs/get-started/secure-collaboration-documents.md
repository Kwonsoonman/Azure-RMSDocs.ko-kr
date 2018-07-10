---
title: Azure Information Protection을 사용하여 문서 공동 작업 보호
description: Azure Information Protection에 의해 보호되는 문서에서 공동 작업을 위한 종단 간 워크플로입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4a642960e81a7d1a5cb6f8433e4098bed06a663d
ms.sourcegitcommit: dc98226f339339c10fd01535a1adf7e30a817a41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36300026"
---
# <a name="secure-document-collaboration-by-using-azure-information-protection"></a>Azure Information Protection을 사용하여 문서 공동 작업 보호

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection을 사용하면 권한 부여된 사용자의 공동 작업에 대한 효율성 저하 없이 문서를 보호할 수 있습니다. 한 사용자가 만든 다음 보고 편집하도록 다른 사용자와 공유하는 대부분의 문서는 Word, Excel 및 PowerPoint의 Office 문서입니다. 이러한 문서는 기본 보호를 지원하며, 이는 권한 부여 및 암호화의 보호 기능 외에도 더 세부적인 제어를 위해 제한된 권한을 지원한다는 것을 의미합니다. 

이러한 권한을 사용 권한이라고 하며 보기, 편집, 인쇄와 같은 권한을 포함합니다. 문서가 보호될 때 개별 사용 권한을 정의하거나, 권한 수준이라는 사용 권한 그룹을 정의할 수 있습니다. 권한 수준을 통해 일반적으로 함께 사용되는 사용 권한(예: 검토자 및 공동 작성자)을 더 쉽게 선택할 수 있습니다. 사용 권한 및 권한 수준에 대한 자세한 내용은 [Azure Rights Management에 대한 사용 권한 구성](../deploy-use/configure-usage-rights.md)을 참조하세요.

이러한 권한을 구성할 때 사용자의 역할을 지정할 수 있습니다.

- **Azure Active Directory를 사용하는 자체 조직 또는 다른 조직의 사용자**: Azure AD 사용자 계정, Azure AD 그룹 또는 해당 조직의 모든 사용자를 지정할 수 있습니다. 

- **Azure Active Directory 계정이 없는 사용자**: Microsoft 계정에 사용할 메일 주소를 지정합니다. 이 계정은 이미 있을 수도 있고 사용자가 보호된 문서를 열 때 만들 수도 있습니다. 
    
    Microsoft 계정으로 문서를 열려면 사용자가 Office 2016 간편 실행을 사용해야 합니다. 다른 Office 버전은 Microsoft 계정으로 Office 보호 문서를 여는 기능을 아직 지원하지 않습니다.

- **인증된 사용자의 경우**: 이 옵션은 사용자를 인증할 수 있는 경우 보호된 문서에 액세스하는 사용자를 제어하지 않아도 되는 경우에 적합합니다. 이 인증은 Azure AD, Microsoft 계정 사용 또는 콘텐츠가 Office 365 메시지 암호화의 새 기능으로 보호되는 경우 페더레이션 소셜 공급자나 일회용 암호를 통해 수행될 수 있습니다. 

관리자는 권한과 권한 부여된 사용자를 적용하도록 Azure Information Protection 레이블을 구성할 수 있습니다. 이 구성을 사용하면 세부 정보를 지정할 필요 없이 레이블을 적용하면 되므로 사용자와 다른 관리자가 올바른 보호 설정을 매우 쉽게 적용할 수 있습니다. 다음 섹션에서는 내부 및 외부 사용자와 보안 공동 작업을 지원하는 문서를 보호하는 예제 연습을 제공합니다.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>내부 및 외부 공동 작업을 지원하기 위해 보호를 적용하는 레이블의 예제 구성

이 예제에서는 조직의 사용자가 Office 365 또는 Azure AD가 있는 다른 조직의 모든 사용자, Office 365 또는 Azure AD가 있는 다른 조직의 그룹 및 Azure AD에 계정이 없고 대신 Gmail 메일 주소를 사용하는 사용자와 문서에 대한 공동 작업을 할 수 있도록 보호를 적용하는 기존 레이블을 구성하는 작업을 연습합니다.

이 시나리오에서는 특정 사용자에 대한 액세스 권한을 제한하므로 인증된 사용자에 대한 설정은 포함되지 않습니다. 이 설정으로 레이블을 구성하는 방법에 대한 예는 [예제 5: 콘텐츠를 암호화하지만 액세스할 수 있는 사용자는 제한하지 않는 레이블](../deploy-use/configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)을 참조하세요.  

1. 전역 정책 또는 범위 지정 정책에서 기존에 있는 레이블을 선택합니다. **보호** 블레이드에서 **Azure(클라우드 키)** 가 선택되었는지 확인합니다.
    
2. **사용 권한 설정**을 선택했는지 확인하고 **사용 권한 추가**를 선택합니다.

3. **권한 추가** 블레이드에서: 
    
    - 내부 그룹: **디렉터리 찾아보기**를 선택하여 메일을 사용해야 하는 그룹을 선택합니다.
    
    - 첫 번째 외부 조직의 모든 사용자: **세부 정보 입력**을 선택하고 조직의 테넌트에 도메인 이름을 입력합니다. 예를 들면 fabrikam.com입니다.
    
    - 두 번째 외부 조직의 그룹: 계속 **세부 정보 입력** 탭에서 조직의 테넌트에 그룹의 메일 주소를 입력합니다. 정의합니다(예: sales@contoso.com).
    
    - Azure AD 계정이 없는 사용자: 계속 **세부 정보 입력** 탭에서 사용자의 메일 주소를 입력합니다. 정의합니다(예: bengi.turan@gmail.com). 

4. 이러한 모든 사용자에게 동일한 권한을 부여하려면: **사전 설정에서 사용 권한 선택**에서 **공동 소유자**, **공동 작성자**, **검토자** 또는 **사용자 지정**을 선택하여 권한을 부여하려는 권한을 선택합니다.
    
    예를 들어, 구성된 권한은 다음과 같이 표시됩니다.
        
    ![보안 공동 작업을 위한 권한 구성](../media/collaboration-permissions.png)

5. **사용 권한 추가** 블레이드에서 **확인**을 클릭합니다.

6. **보호** 블레이드에서 **확인**을 클릭합니다.

7. **레이블** 블레이드에서 **저장**을 선택합니다. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>보안 공동 작업을 지원하는 레이블 적용

이제 이 레이블이 구성되었으므로 다양한 방법으로 다음을 포함하는 문서에 적용할 수 있습니다.

|다양한 레이블 적용 방법|추가 정보|
|---------------|----------|
|해당 문서가 Office 응용 프로그램에서 만들어진 경우 사용자가 레이블을 수동으로 선택합니다.|사용자는 Office 리본의 **보호** 단추 또는 Azure Information Protection 막대에서 레이블을 선택합니다.|
|새 문서가 저장될 때 레이블을 선택하라는 메시지가 표시됩니다.|**All documents and emails must have a label(모든 문서와 메일에 레이블이 있어야 함)** 이라는 Azure Information Protection [정책 설정](../deploy-use/configure-policy-settings.md)을 구성했습니다.|
|사용자는 메일로 문서를 공유하고 Outlook에서 레이블을 수동으로 선택합니다.|사용자는 Office 리본의 **보호** 단추 또는 Azure Information Protection 막대에서 레이블을 선택하고, 첨부된 문서는 동일한 설정으로 자동으로 보호됩니다.|
|관리자는 PowerShell을 사용하여 문서에 레이블을 적용합니다.|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) cmdlet을 사용하여 폴더의 특정 문서 또는 모든 문서에 레이블을 적용합니다.|
|이제 Azure Information Protection 스캐너 또는 PowerShell을 사용하여 적용할 수 있는 자동 분류를 적용하도록 레이블을 추가로 구성했습니다.|[Azure Information Protection에 대한 자동 및 권장 분류 조건을 구성하는 방법](../deploy-use/configure-policy-classification.md)을 참조하세요.|

이 연습을 완료하려면 Office 응용 프로그램에서 문서를 만들 때 레이블을 수동으로 적용합니다. 

1. 클라이언트 컴퓨터에서 Office 응용 프로그램이 이미 열려 있는 경우 먼저 닫았다가 다시 열어 새로 구성된 레이블을 포함하는 최신 정책 변경 내용을 가져옵니다. 

2. 레이블을 문서에 적용하고 저장합니다.

보호된 문서를 메일에 첨부하여 공유하고 문서를 편집하도록 권한을 부여한 사용자에게 보냅니다.

## <a name="opening-and-editing-the-protected-document"></a>보호된 문서 열기 및 수정

권한을 부여한 사용자가 편집할 문서를 열면 문서가 열리고 해당 권한이 제한됨을 알리는 정보 배너가 표시됩니다. 예를 들면 다음과 같습니다.

![Azure Information Protection 권한 예제 정보 배너](../media/example-restricted-access-banner.png)

**권한 보기** 단추를 선택하면 사용자가 보유한 권한이 표시됩니다. 다음 예제에서 사용자는 문서를 보고 편집할 수 있습니다.

![Azure Information Protection 권한 예제 대화 상자](../media/example-permisisons-popup.png)

참고: Azure Information Protection을 사용하는 외부 사용자가 문서를 열면 레이블의 시각적 표시가 남아 있더라도 Office 응용 프로그램에서 문서에 대한 분류 레이블을 표시하지 않습니다. 대신 외부 사용자가 해당 조직의 분류 체계에 맞춰 자신의 레이블을 적용할 수 있습니다. 그런 다음, 이러한 외부 사용자가 편집된 문서를 사용자에게 다시 보내면 사용자가 문서를 다시 열 때 Office에서 원래 분류 레이블을 표시합니다.

보호된 문서가 열리기 전에 다음 인증 흐름 중 하나가 발생합니다.

- Azure AD 계정이 있는 사용자의 경우 Azure AD 자격 증명을 사용하여 Azure AD에서 인증을 받고 문서가 열립니다. 

- Azure AD 계정이 없는 사용자의 경우 문서를 열 권한이 있는 계정으로 Office에 로그인하지 않으면 **계정** 페이지가 표시됩니다. 
    
   **계정** 페이지에서 **계정 추가**를 선택합니다.
   
    ![보호된 문서를 열기 위해 Microsoft 계정 추가](../media/add-account-msa.png)

   **로그인** 페이지에서 **계정을 만드세요!** 를 선택하고 프롬프트에 따라 권한을 부여하는 데 사용한 메일 주소로 새 Microsoft 계정을 만듭니다.
    
    ![보호된 문서를 열기 위해 Microsoft 계정 만들기](../media/create-account-msa.png)
    
    새 Microsoft 계정이 생성되면 로컬 계정이 이 새로운 Microsoft 계정으로 전환되고 사용자가 문서를 열 수 있습니다.


### <a name="supported-scenarios-for-opening-protected-documents"></a>보호된 문서를 열기 위해 지원되는 시나리오

다음 표에서는 보호된 문서를 보고 편집할 수 있도록 지원하는 여러 인증 방법을 요약합니다.

또한 다음 시나리오에서는 문서 보기를 지원합니다.

- Windows용은 물론 iOS 및 Android용 Azure Information Protection 뷰어는 Microsoft 계정을 사용하여 파일을 열 수 있습니다. 

- 소셜 공급자와 일회용 암호가 Exchange Online 인증 및 Office 365 메시지 암호화의 새로운 기능에 사용되는 경우, 브라우저에서 보호된 첨부 파일을 열 수 있습니다. 

|문서 보기 및 편집을 위한 플랫폼: <br />Word, Excel, PowerPoint|인증 방법:<br />Azure AD|인증 방법:<br />Microsoft 계정|
|---------------|----------|-----------|-----------|
|Windows|예 [[1]](#footnote-1)|예 [[2]](#footnote-2)|
|iOS|예 [[1]](#footnote-1)|아니요|
|Android|예 [[1]](#footnote-1)|아니요|
|MacOS|예 [[1]](#footnote-1)|아니요|

###### <a name="footnote-1"></a>각주 1
사용자 계정, 메일 사용 그룹, 모든 구성원을 지원합니다. 사용자 계정 및 메일 사용 그룹에는 게스트 계정이 포함될 수 있습니다. 모든 구성원에서 게스트 계정은 제외됩니다.

###### <a name="footnote-2"></a>각주 2
현재 Office 2016 간편 실행에서만 지원됩니다.




## <a name="next-steps"></a>다음 단계

일반적인 시나리오에 대한 보호를 적용하려면 레이블에 대한 기타 [예제 구성](../deploy-use/configure-policy-protection.md#example-configurations)을 참조하세요. 이 문서에는 보호 설정에 대한 자세한 내용이 포함되어 있습니다.

레이블에 대해 구성할 수 있는 다른 옵션 및 설정에 대한 자세한 내용은 [Azure Information Protection 정책 구성](../deploy-use/configure-policy.md)을 참조하세요. 

또한 이 문서에 구성된 레이블은 동일한 이름으로 보호 템플릿을 만듭니다. Azure Information Protection의 보호 템플릿과 통합되는 응용 프로그램 및 서비스가 있는 경우, 이 템플릿을 적용할 수 있습니다. 예를 들면 DLP 솔루션 및 메일 흐름 규칙입니다. 웹용 Outlook은 Azure Information Protection 전역 정책의 보호 템플릿을 자동으로 표시합니다. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


