---
title: "시나리오 - 파일 서버 공유에 있는 파일 보호 | Azure Information Protection"
description: "이 시나리오 및 지원 사용자 문서에서는 복사하여 IT 부서가 제어하지 않는 저장소에 저장되었거나 다른 사용자에게 메일로 전송된 경우에도 Azure Rights Management 보호를 통해 파일 서버에서 보호하려는 모든 파일을 대량으로 보호하여 조직의 직원만 액세스할 수 있도록 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 283c7db3-5730-439e-a215-40a1088ed506
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: f5a95beb3cd42921351181b412a5b08dd6fa3b9b


---

# <a name="scenario---protect-files-on-a-file-server-share"></a>시나리오 - 파일 서버 공유에 있는 파일 보호

>*적용 대상: Azure Information Protection, Office 365*

이 시나리오 및 지원 사용자 문서에서는 복사하여 IT 부서가 제어하지 않는 저장소에 저장되었거나 다른 사용자에게 메일로 전송된 경우에도 Azure Information Protection의 Azure Rights Management 기술을 통해 파일 서버에서 보호하려는 모든 파일을 대량으로 보호하여 조직의 직원만 액세스할 수 있도록 합니다.

이러한 지침은 모든 사용 권한을 가진 모든 직원으로 액세스를 제한하는 기본 템플릿 중 하나를 사용합니다. 그러나 필요한 경우 기본 템플릿을 사용하는 대신 사용자 지정 템플릿을 구성하여 액세스 및 사용 권한을 더욱 제한할 수 있습니다.

지침을 제공하기에 적합한 상황은 다음과 같습니다.

-   Office 파일뿐 아니라 모든 파일 형식을 보호해야 하는 경우 Azure RMS를 통해 기본적으로 보호할 수 없는 파일이 일반적으로 보호되는 경우

-   지정된 경로에 있는 모든 파일(하위 폴더 포함)이 보호되는 경우

-   일정에 따라 모든 파일에 보호 기능을 다시 적용하여 권한 정책 템플릿 변경 내용이 보호된 파일에 적용되도록 하는 경우

## <a name="deployment-instructions"></a>배포 지침
![Azure RMS 빠른 배포를 위한 관리자 지침](../media/AzRMS_AdminBanner.png)

사용자 문서를 진행하기 전에 다음 요구 사항이 충족되었는지 확인한 다음 지원 절차에 대한 지침을 따르세요.

## <a name="requirements-for-this-scenario"></a>이 시나리오의 요구 사항
이 시나리오의 지침이 작동하려면 다음 사항을 준비해야 합니다.

|요구 사항|추가 정보가 필요한 경우 확인 가능한 위치|
|---------------|--------------------------------|
|Azure 권한 관리가 활성화되었는지 여부|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|온-프레미스 Active Directory 사용자 계정을 Azure Active Directory 또는 Office 365와 동기화해야 합니다(각각의 메일 주소를 포함). 이렇게 하려면 모든 사용자가 파일을 FCI 및 Azure 권한 관리로 보호한 후에 해당 파일에 액세스해야 할 수도 있습니다.|[Azure Information Protection 준비](../plan-design/prepare.md)|
|다음 중 하나<br /><br />- 모든 사용자에 대해 기본 템플릿을 사용하려는 경우: 기본 &lt;조직 이름&gt; - 기밀을 보관하지 않았는지 여부<br /><br />- 특정 사용자에 대해 사용자 지정 템플릿을 사용하려는 경우: 이 사용자 지정 템플릿을 만들고 게시했는지 여부|[Azure Rights Management 서비스용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)|
|Windows를 실행하는 사용자의 컴퓨터에 Rights Management 공유 응용 프로그램이 배포되었는지 여부|[Microsoft Rights Management 공유 응용 프로그램 자동 배포](../rms-client/sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)|
|RMS 보호 도구를 다운로드하고 Azure RMS에 대한 필수 조건을 구성했는지 여부|도구 다운로드 지침과 필수 조건: [RMS 보호 Cmdlet](https://msdn.microsoft.com/library/mt433195.aspx)<br /><br />Azure RMS에 대해 서비스 보안 주체 계정과 같은 추가 필수 조건을 구성하려는 경우: [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)|

### <a name="configuring-a-file-server-to-protect-all-files-by-using-azure-rms-and-file-server-resource-manager-with-file-classification-infrastructure"></a>파일 분류 인프라와 함께 Azure RMS 및 파일 서버 리소스 관리자를 사용하여 모든 파일을 보호하도록 파일 서버 구성

1.  Windows PowerShell 세션을 시작합니다. 이 세션은 관리자 권한으로 실행할 필요가 없습니다.

2.  Azure RMS에 인증합니다.

    ```
    Set-RMSServerAuthentication
    ```
    메시지가 표시되면 RMS 보호 cmdlet의 필수 조건으로 만든 서비스 보안 주체 계정의 값을 제공합니다.

3.  다음을 실행하여 파일을 보호하는 데 사용할 템플릿 ID를 식별합니다.

    ```
    Get-RMSTemplate
    ```
    모든 사용 권한을 가진 모든 직원으로 액세스를 제한하는 기본 템플릿을 사용하려면 템플릿 이름 **&lt;조직 이름&gt; - 기밀**을 찾습니다. 예를 들어 **VanArsdel, Ltd - 기밀**입니다.

4.  [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](../rms-client/configure-fci.md)에서 단계별 지침을 따르세요.

    이러한 지침에는 파일 서버 리소스 관리자에서 사용자 지정 실행 파일로 실행하도록 지정하는 Windows PowerShell 스크립트가 포함됩니다. Azure 권한 관리를 통해 파일이 보호되는지 확인하는 방법도 포함됩니다.

## <a name="user-documentation-instructions"></a>사용자 문서 지침
Office 파일만 보호하는 경우 보호된 파일에 대한 지침을 사용자에게 제공할 필요가 없을 수도 있습니다. 권한 있는 사용자가 이러한 문서를 열면 정상적으로 Office에서 열리며, 유일한 차이점은 사용자에게 인증하라는 메시지가 표시될 수 있다는 것입니다. 문서가 보호되고 있음을 알리는 알림 표시줄이 문서 맨 위에 표시됩니다.

보호된 파일이 **.ppdf** 파일 이름 확장명을 사용하거나 보호된 텍스트 또는 이미지 파일(예: **.ptxt** 또는 **.pjpg** 파일 이름 확장명 사용)인 경우 해당 파일은 이제 읽기 전용이며 편집할 수 없습니다. 사용자는 이러한 파일 형식에 대해 자동으로 로드되는 RMS 공유 응용 프로그램 뷰어를 사용하여 파일을 볼 수 있습니다. 파일 자체가 읽기 전용이기 때문에 해당 파일은 Azure RMS를 통해 기본적으로 보호되며 사용 권한을 제외하고 적용된 템플릿의 모든 정책 설정을 적용합니다. 이러한 파일 형식을 보호할 것을 알고 있지 않다면 이 시나리오에 대한 사용자 지침이 필요할 가능성은 없지만 사용자에게 해당 파일을 편집할 수 없는 이유를 설명해야 할 수도 있다고 지원 센터에 경고합니다.

보호된 파일이 **.pfile** 파일 이름 확장명을 사용하는 경우 사용자가 해당 파일을 볼 수 있지만 편집하고 변경 내용을 저장하려면 원래 파일 이름(.pfile 파일 이름 확장명 제거)으로 저장해야 합니다. 이러한 파일은 일반적으로 Azure RMS를 통해 보호되며 적용된 템플릿의 사용 권한을 적용할 수 없으므로 파일을 새 이름으로 저장하면 보호 기능이 손실됩니다. 이 시나리오에서는 사용자 지침이 필요합니다.

최종 사용자가 일반적으로 보호된 파일을 편집하는 방법을 알 수 있도록 다음 템플릿을 사용하여 최종 사용자 지침을 복사하여 붙여넣습니다. 사용자 환경에 맞게 다음과 같이 수정합니다.

-   *&lt;파일 형식&gt;* 및 *&lt;파일 서버 공유&gt;*를 일반적으로 보호될 파일 형식 및 파일 서버 공유 이름으로 바꿉니다.

-   *&lt;조직 이름&gt;*을 기본 Azure 권한 관리 템플릿에 표시되는 사용자 조직의 이름으로 바꿉니다.

-   *&lt;조직 이름&gt;*을 사용자 조직의 이름으로 바꿉니다.

-   *&lt;파일을 저장하고 .pfile 파일 이름 확장명을 제거하는 방법에 대한 지침&gt;*을 이 파일 형식에 대한 응용 프로그램별 지침으로 바꿉니다.

-   연락처 세부 정보를 웹 사이트 링크, 메일 주소, 전화 번호 등 사용자가 지원 센터에 연락을 할 수 있는 방법에 대한 지침으로 바꿉니다.

-   이 지침 집합을 원하는 대로 수정한 다음 해당 사용자에게 보냅니다.

예제 문서에서는 사용자 지정 후 이러한 지침이 사용자에게 표시되는 방식을 보여 줍니다.

![Azure RMS 빠른 배포를 위한 템플릿 사용자용 설명 문서](../media/AzRMS_UsersBanner.png)

### <a name="how-to-edit-lttype-of-filegt-from-the-ltfile-server-sharegt"></a>&lt;파일 서버 공유&gt;에서 &lt;파일 형식&gt;을 편집하는 방법

1.  파일을 두 번 클릭하여 엽니다. 자격 증명을 입력하라는 메시지가 표시될 수 있습니다.

2.  Microsoft Rights Management 공유 응용 프로그램에서 **보호된 파일** 대화 상자가 나타나며, **&lt;조직 이름&gt; - 기밀**의 사용 권한을 준수하라는 메시지가 표시됩니다. 이는 &lt;조직 이름&gt;의 직원이 아닌 다른 사용자와 이 문서를 공유하면 안 된다는 것입니다.

3.  **열기**를 클릭합니다.

4.  파일을 편집하려면 먼저 파일을 저장하고 .pfile 파일 이름 확장명을 제거합니다.

    -   &lt;파일을 저장하고 .pfile 파일 이름 확장명을 제거하는 방법에 대한 지침&gt;

5.  이제 파일을 정상적으로 편집하고 저장할 수 있습니다.

정기적으로 파일이 다시 보호되어 .pfile 파일 이름 확장명을 다시 추가하므로 이러한 단계를 반복해야 합니다.

**도움이 필요한가요?**

-   추가 정보를 확인하려면 다음 항목을 참조하세요.

    -   [보호된 파일 보기 및 사용](../rms-client/sharing-app-view-use-files.md)

-   지원 센터에 연락하려면 다음 정보를 참조하세요.

    -   *&lt;연락처 세부 정보&gt;*

### <a name="example-customized-user-documentation"></a>예제 사용자 지정 사용자 문서
![Azure RMS 빠른 배포를 위한 예제 사용자용 설명 문서](../media/AzRMS_ExampleBanner.png)

#### <a name="how-to-edit-cad-drawings-from-the-projectnextgen-share"></a>ProjectNextGen 공유에서 CAD 드로잉을 편집하는 방법

1.  파일을 두 번 클릭하여 엽니다. 자격 증명을 입력하라는 메시지가 표시될 수 있습니다.

2.  Microsoft Rights Management 공유 응용 프로그램에서 **보호된 파일** 대화 상자가 나타나며, **VanArsdel, Ltd - 기밀**의 사용 권한을 준수하라는 메시지가 표시됩니다. 이는 VanArsdel, Ltd의 직원이 아닌 다른 사용자와 이 문서를 공유하면 안 된다는 것입니다.

3.  **열기**를 클릭합니다.

4.  파일을 편집하려면 먼저 파일을 저장하고 .pfile 파일 이름 확장명을 제거합니다.

    -   **파일** &gt; **다른 이름으로 저장**

    -   파일 이름의 끝에서 **.pfile**을 삭제하고 **확인**을 클릭합니다.

5.  이제 파일을 정상적으로 편집하고 저장할 수 있습니다.

정기적으로 파일이 다시 보호되어 .pfile 파일 이름 확장명을 다시 추가하므로 이러한 단계를 반복해야 합니다.

**도움이 필요한가요?**

-   추가 정보를 확인하려면 다음 항목을 참조하세요.

    -   [보호된 파일 보기 및 사용](../rms-client/sharing-app-view-use-files.md)

-   지원 센터에 연락하려면 다음 정보를 참조하세요. helpdesk@vanarsdelltd.com

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


