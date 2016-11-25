---
title: "시나리오 - 회사 기밀 메일 보내기 | Azure Information Protection"
description: "이 시나리오와 지원 사용자 문서에서는 조직의 모든 사용자가 조직 외부에서 읽을 수 없는 메일 통신을 안전하게 보낼 수 있도록 Azure Rights Management 보호를 사용합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/10/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 950799e9-2289-48c7-b95a-f54a8ead520a
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: f886b72ba18f0f13ac60e08d000b231cd36d1d5f


---

# <a name="scenario-send-a-companyconfidential-email"></a>시나리오 - 회사 기밀 메일 보내기

>*적용 대상: Azure Information Protection, Office 365*

이 시나리오와 지원 사용자 문서에서는 조직의 모든 사용자가 조직 외부에서 읽을 수 없는 메일 통신을 안전하게 보낼 수 있도록 Azure Information Protection의 Azure Rights Management 서비스를 사용합니다. 예를 들어 다른 조직의 사용자나 개인 메일 계정으로 메일 메시지를 전달하는 경우입니다. 메일과 모든 첨부 파일은 Azure 권한 관리 및 사용자가 메일 클라이언트에서 선택하는 템플릿에 의해 보호됩니다.

이 시나리오를 설정하는 가장 간단한 방법은 액세스를 조직의 모든 사용자로 자동으로 제한하는 기본 제공 기본 템플릿 중 하나를 사용하는 것입니다. 그러나 필요한 경우 액세스를 사용자 하위 집합으로 제한하거나 읽기 전용, 만료 날짜 등의 다른 제한 사항이 있거나, 메일 클라이언트에서 전달 단추를 사용하지 않도록 설정하는 사용자 지정 템플릿을 만들어 보다 제한적으로 설정할 수 있습니다.

> [!IMPORTANT]
> 이 시나리오에서는 구성하는 사용자 지정 템플릿에서 바로 **전달**을 제거할 수 있고 이렇게 하면 메일 클라이언트에서 전달 단추를 사용할 수 없게 되지만 이 구성은 사용자가 다른 권한 있는 사용자와 메일을 공유하는 것을 차단하지 않습니다. 받는 사람은 메일(및 모든 첨부 파일)을 저장한 후 다른 공유 메커니즘을 사용하여 정보를 공유할 수 있습니다.
> 
> 예를 들어 Bob은 마케팅 그룹에 파일 저장 및 콘텐츠 편집 사용자 지정 권한을 적용하고 전달 권한을 포함하지 않는 사용자 지정 템플릿을 사용하여 Alice에게 메일을 보냅니다. Alice는 다른 사용자에게 메일을 전달할 수 없지만 메일 메시지와 모든 첨부 파일을 USB 드라이브 또는 파일 서버 공유에 저장할 수 있으며, 이러한 파일에 액세스할 수 있으면 마케팅 그룹의 모든 멤버가 읽고 편집할 수 있습니다. 마케팅 그룹에 속하지 않는 사용자는 콘텐츠를 열 수 없습니다.

지침을 제공하기에 적합한 상황은 다음과 같습니다.

-   조직 내의 사용자가 조직 내의 다른 사용자와 정보를 공유하려고 하지만 조직 외부에서는 해당 정보가 공유되면 안 되는 경우

-   공유할 정보가 메일 메시지 또는 첨부 파일 내에 들어 있을 수 있는 경우

-   사용자가 메일 클라이언트에서 템플릿을 수동으로 선택해야 하는 경우

## <a name="deployment-instructions"></a>배포 지침
![Azure RMS 빠른 배포를 위한 관리자 지침](../media/AzRMS_AdminBanner.png)

사용자 문서를 진행하기 전에 다음 요구 사항이 충족되었는지 확인합니다.

## <a name="requirements-for-this-scenario"></a>이 시나리오의 요구 사항
이 시나리오의 지침이 작동하려면 다음 사항을 준비해야 합니다.

|요구 사항|추가 정보가 필요한 경우 확인 가능한 위치|
|---------------|--------------------------------|
|Office 365 또는 Azure Active Directory용 계정과 그룹을 준비했는지 여부|[Azure Information Protection 준비](../plan-design/prepare.md)|
|Azure Information Protection 테넌트 키가 Microsoft에서 관리되는지 여부(사용자는 BYOK를 사용하지 않음)|[Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)|
|Azure 권한 관리가 활성화되었는지 여부|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|다음 중 하나<br /><br />- Azure 권한 관리에 Exchange Online을 사용하도록 설정되어 있는지 여부<br /><br />- Exchange 온-프레미스에 대해 RMS 커넥터가 설치되고 구성되었는지 여부|Exchange Online: [Office 365: 클라이언트 및 온라인 서비스 구성](../deploy-use/configure-office365.md)에서 **Exchange Online: IRM 구성** 섹션을 참조하세요.<br /><br />Exchange 온-프레미스의 경우: [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)|
|기본 Azure 권한 관리 템플릿인 **&lt;조직&gt; - 기밀**을 보관하지 않았습니다. 또는 더 제한적인 설정이 필요하거나 조직의 사용자 하위 집합만 보호된 메일을 읽을 수 있어야 하기 때문에 이 용도로 사용자 지정 템플릿을 구성했습니다.|[Azure Rights Management 서비스용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)<br /><br />팁: 조직의 모든 사용자에 대해 더 제한적인 사용 정책 설정이 필요한 경우 템플릿을 처음부터 만드는 대신 기본 템플릿 중 하나를 복사한 다음 편집합니다.<br /><br />이 시나리오에서는 업데이트된 템플릿이 메일 클라이언트에서 즉시 새로 고쳐지지 않습니다. 자세한 내용은 [사용자를 위한 템플릿 새로 고침](../deploy-use/refresh-templates.md) 문서를 참조하세요.|
|보호된 메일을 보내는 사용자에게 Outlook 2013, Outlook 2016 또는 Outlook Web Access가 있습니다.<br /><br />메일을 받는 사용자에게 Azure 권한 관리를 지원하는 메일 클라이언트가 있습니다.|Outlook 2010을 사용할 수 있지만 [Windows용 Rights Management 공유 응용 프로그램을 설치](../rms-client/sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)하고 사용자 지침을 적절하게 조정해야 합니다.<br /><br />Azure 권한 관리를 지원하는 메일 클라이언트 목록은 [Azure 권한 관리 데이터 보호를 지원하는 응용 프로그램](../get-started/requirements-applications.md)의 표에 있는 **Email**열을 참조하세요.|

## <a name="user-documentation-instructions"></a>사용자 문서 지침
다음 템플릿을 사용하여 최종 사용자 통신에 사용자 지침을 복사해서 붙여넣고 사용자 환경에 맞게 다음과 같이 수정합니다.

1.  모든 *&lt;조직 이름&gt;* 인스턴스를 사용자 조직의 이름으로 바꿉니다.

2.  모든 *&lt;조직 이름 - 기밀&gt;* 인스턴스를 기본 또는 사용자 지정 템플릿의 이름으로 바꿉니다.

3.  사용자 조직 템플릿 이름이 표시되도록 스크린샷을 바꿉니다.

4.  *&lt;연락처 세부 정보&gt;*를 웹 사이트 링크, 메일 주소, 전화 번호 등 사용자가 지원 센터에 연락을 할 수 있는 방법에 대한 지침으로 바꿉니다.

5.  **그 외에 수정할 수 있는 사항은 다음과 같습니다.**

    -   지침을 하나의 메일 클라이언트로만 제한할 수 있는 경우 간단한 설명을 위해 이렇게 하는 것이 좋으며 다른 지침 집합을 삭제합니다.

    -   제안된 기본 템플릿 대신 사용자 지정 템플릿을 사용하는 경우 단어를 적절하게 수정합니다.

        -   제목을 보다 구체적으로 지정합니다.

        -   1단계에서 선택할 사용자 또는 그룹을 지정합니다.

        -   2단계에서 사용자 지정 템플릿의 이름을 지정합니다.

        -   최종 단락을 수정하여 받는 사람에게 적용되는 제한 사항을 설명합니다.

6.  이 지침 집합을 원하는 대로 수정한 다음 해당 사용자에게 보냅니다.

7.  일부 클라이언트는 Rights Management를 지원하지 않으므로 보호된 메일 메시지를 받는 사람에게 지침과 권장 사항을 제공해야 할 수도 있습니다. 이 정보는 조직에서 사용 중인 장치 및 메일 응용 프로그램과 사용자 기본 설정을 기반으로 합니다. 예를 들어 iOS 사용자에게 기본 iOS 메일 클라이언트 대신 iPad 및 iPhone용 Outlook에서 보호된 메일을 읽도록 권장합니다.

    메일 클라이언트에 대한 자세한 내용은 [Azure 권한 관리 요구 사항](https://technet.microsoft.com/library/dn655136.aspx)에 있는 [클라이언트 장치 기능](https://technet.microsoft.com/library/dn655136.aspx) 표의 **메일** 열을 참조하세요.

예제 문서에서는 사용자 지정 후 이러한 지침이 사용자에게 표시되는 방식을 보여 줍니다.

![Azure RMS 빠른 배포를 위한 템플릿 사용자용 설명 문서](../media/AzRMS_UsersBanner.png)

### <a name="how-to-send-emails-that-contain-companyconfidential-information-using-outlook"></a>Outlook을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법

1.  Outlook 내에서 새 메일 메시지를 만들고 포함하려는 첨부 파일을 추가한 다음 *&lt;조직 이름&gt;*에서 사용자 또는 그룹을 선택합니다.

2.  **옵션** 탭에서 **사용 권한**을 클릭하고 **&lt;조직 이름 - 기밀&gt;**을 선택합니다.

    ![Outlook을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법 스크린샷](../media/AzRMS_OutlookTemplate.PNG)

3.  메시지를 보냅니다.

### <a name="how-to-send-emails-that-contain-companyconfidential-information-using-outlook-web-app"></a>Outlook Web App을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법

1.  Outlook Web App 내에서 새 메일 메시지를 만들고 포함하려는 첨부 파일을 추가한 다음 주소록에서 *&lt;조직 이름&gt;* 사용자 또는 그룹을 선택합니다.

2.  **...**를 클릭하고 **사용 권한 설정**을 클릭한 다음 **&lt;조직 이름 - 기밀&gt;**을 선택합니다.

    ![Outlook Web App을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법 스크린샷](../media/AzRMS_OWATemplate.png)

3.  메시지를 보냅니다.

**받는 사람**, **참조** 또는 **숨은 참조** 줄에 있는 사용자가 이 메일을 받을 때 메시지를 읽기 전에 인증하여 *&lt;조직 이름&gt;*의 사용자임을 확인하라는 메시지가 표시될 수도 있습니다. 사용자가 이미 인증된 경우에는 메시지가 표시되지 않습니다.

메일을 받은 사람은 다른 사용자에게 전달할 수 있지만 *&lt;조직 이름&gt;* 내의 사용자만 메일을 읽을 수 있습니다. Office 문서를 첨부하는 경우 해당 첨부 파일이 다른 위치에 다른 이름으로 저장된 경우에도 동일한 보호가 적용됩니다. 그러나 성공적으로 인증된 사용자는 메일 또는 첨부 파일에서 복사하여 붙여넣거나 인쇄할 수 있습니다. 이러한 작업을 방지하는 더 제한적인 보호가 필요한 경우 지원 센터에 문의하세요.

**도움이 필요한가요?**

-   지원 센터에 연락하려면 다음 정보를 참조하세요.

    -   *&lt;연락처 세부 정보&gt;*

### <a name="example-customized-user-documentation"></a>예제 사용자 지정 사용자 문서
![Azure RMS 빠른 배포를 위한 예제 사용자용 설명 문서](../media/AzRMS_ExampleBanner.png)

#### <a name="how-to-send-emails-that-contain-companyconfidential-information-using-outlook"></a>Outlook을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법

1.  Outlook 내에서 새 메일 메시지를 만들고 포함하려는 첨부 파일을 추가한 다음 주소록에서 VanArsdel 사용자 또는 그룹을 선택합니다.

2.  **옵션** 탭에서 **사용 권한**을 클릭하고 **VanArsdel, Ltd - 기밀**을 선택합니다.

    ![Outlook을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법 스크린샷](../media/AzRMS_OutlookTemplate.PNG)

3.  메시지를 보냅니다.

#### <a name="how-to-send-emails-that-contain-companyconfidential-information-using-outlook-web-app"></a>Outlook Web App을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법

1.  Outlook Web App 내에서 새 메일 메시지를 만들고 포함하려는 첨부 파일을 추가한 다음 주소록에서 VanArsdel 사용자 또는 그룹을 선택합니다.

2.  **...**을 클릭하고 **사용 권한 설정**을 클릭한 다음 **VanArsdel, Ltd - 기밀**을 선택합니다.

    ![Outlook Web App을 사용하여 회사 기밀 정보가 포함된 메일을 보내는 방법 스크린샷](../media/AzRMS_OWATemplate.png)

3.  메시지를 보냅니다.

**받는 사람**, **참조** 또는 **숨은 참조** 줄에 있는 사용자가 이 메일을 받을 때 메시지를 읽기 전에 인증하여 VanArsdel, Ltd의 사용자임을 확인하라는 메시지가 표시될 수도 있습니다. 사용자가 이미 인증된 경우에는 메시지가 표시되지 않습니다.

메일을 받은 사람은 다른 사용자에게 전달할 수 있지만 VanArsdel 내의 사용자만 메일을 읽을 수 있습니다. Office 문서를 첨부하는 경우 해당 첨부 파일이 다른 위치에 다른 이름으로 저장된 경우에도 동일한 보호가 적용됩니다. 그러나 성공적으로 인증된 사용자는 메일 또는 첨부 파일에서 복사하여 붙여넣거나 인쇄할 수 있습니다. 이러한 작업을 방지하는 더 제한적인 보호가 필요한 경우 지원 센터에 문의하세요.

**도움이 필요한가요?**

-   지원 센터에 연락하려면 다음 정보를 참조하세요.

    -   메일: helpdesk@vanarsdelltd.com




<!--HONumber=Nov16_HO2-->


