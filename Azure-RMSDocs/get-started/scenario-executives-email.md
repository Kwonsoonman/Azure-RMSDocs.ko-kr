---
title: "시나리오 - 임원이 권한이 제한된 정보를 안전하게 교환 | Azure Information Protection"
description: "이 시나리오 및 지원 사용자 문서에서는 Azure Rights Management 보호를 사용하여 임원이 메일과 첨부 파일을 서로 안전하게 교환할 수 있고 임원이 특별한 작업을 수행하지 않아도 정책에 따라 액세스가 임원으로 자동으로 제한되도록 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: c8c460549df34a746b21f57aa890a52571bf2061


---

# <a name="scenario-executives-securely-exchange-privileged-information"></a>시나리오 - 임원이 권한이 제한된 정보를 안전하게 교환

>*적용 대상: Azure Information Protection, Office 365*

이 시나리오 및 지원 사용자 문서에서는 Azure Information Protection의 Azure Rights Management 기술을 사용하여 임원이 메일과 첨부 파일을 서로 안전하게 교환할 수 있고 임원이 특별한 작업을 수행하지 않아도 정책에 따라 액세스가 임원으로 자동으로 제한되도록 합니다. 메일과 모든 첨부 파일은 Azure 권한 관리에 의해 자동으로 보호됩니다.

필요한 경우 임원이 다른 임원에게 보호되지 않는 메일을 보내야 하면(예: 다른 사용자에게 전달하기 전에 검토하기 위해) 지정할 수 있도록 메일 메시지 제목에 약어 DNP("보호 안 함")와 같은 규칙 예외를 추가할 수 있습니다.

지침을 제공하기에 적합한 상황은 다음과 같습니다.

-   임원이 다른 사용자와 공유해서는 안 되는 기밀 정보를 서로 공유하는 경우

-   임원이 해당 메일을 보낼 때 개인 메일 주소가 아니라 회사 메일 주소로 보내는 것 이외에는 다른 작업을 수행할 필요가 없는 경우

-   임원이 다른 임원에게 보호되지 않는 메일 메시지를 보내야 하면 직접 규칙을 재정의할 수 있는 경우

## <a name="deployment-instructions"></a>배포 지침
![Azure RMS 빠른 배포를 위한 관리자 지침](../media/AzRMS_AdminBanner.png)

사용자 문서를 진행하기 전에 다음 요구 사항이 충족되었는지 확인한 다음 지원 절차에 대한 지침을 따르세요.

## <a name="requirements-for-this-scenario"></a>이 시나리오의 요구 사항
이 시나리오의 지침이 작동하려면 다음 사항을 준비해야 합니다.

|요구 사항|추가 정보가 필요한 경우 확인 가능한 위치|
|---------------|--------------------------------|
|Office 365 또는 Azure Active Directory용 계정과 그룹을 준비했는지 여부<br /><br />- **Executives**라는 메일 사용이 가능한 그룹이 있고 모든 임원이 이 그룹의 구성원인지 여부<br /><br />- **RMS administrators**라는 메일 사용이 가능한 그룹이며, Azure RMS를 구성하는 모든 관리자가 이 그룹의 구성원임|[Azure Information Protection 준비](../plan-design/prepare.md)|
|Azure Information Protection 테넌트 키가 Microsoft에서 관리되는지 여부(사용자는 BYOK를 사용하지 않음)|[Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)|
|Azure 권한 관리가 활성화되었는지 여부|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|다음 구성 중 하나:<br /><br />- Azure 권한 관리에 Exchange Online을 사용하도록 설정되어 있는지 여부<br /><br />- Exchange 온-프레미스에 대해 RMS 커넥터가 설치되고 구성되었는지 여부|Exchange Online의 경우: [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration) 정보를 참조하세요.<br /><br />Exchange 온-프레미스의 경우: [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)|
|다음에 설명하는 대로 사용자 지정 템플릿을 구성했는지 여부|[Azure Rights Management 서비스용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)|
|이 문서의 뒷부분에서 설명하는 대로 IRM에 대한 전송 보호 규칙을 구성했는지 여부|Exchange Online의 경우: [Mail flow or transport rules](https://technet.microsoft.com/library/jj919238(v=exchg.150).aspx)(메일 흐름 또는 전송 규칙)<br /><br />Exchange 2013의 경우: [전송 보호 규칙 만들기](https://technet.microsoft.com/en-us/library/dd302432(v=exchg.150))<br /><br />Exchange 2010의 경우: [전송 보호 규칙 만들기](https://technet.microsoft.com/library/dd302432(v=exchg.141))|

### <a name="to-configure-the-custom-template-for-executives"></a>임원용 사용자 지정 템플릿을 구성하려면

1.  Azure 클래식 포털에서 다음 값과 설정이 포함된 Azure 권한 관리용 사용자 지정 템플릿을 새로 만듭니다.

    -   이름: **임원**

    -   권한: 메일 사용이 가능한 **Executives** 그룹에 **공동 소유자** 권한 부여

    -   범위: 메일 사용이 가능한 **Executives** 그룹 및 메일 사용이 가능한 **RMS administrators** 그룹을 선택합니다.

2.  새 템플릿을 게시합니다.

3.  Exchange Online에만 해당: Exchange Online용 Windows PowerShell 명령을 사용하여 템플릿을 새로 고칩니다.

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates -RMSOnline
    ```

### <a name="to-configure-the-transport-rule-for-irm"></a>IRM에 대한 전송 규칙을 구성하려면

-   다음 설정으로 전송 규칙을 만드는 절차 정보는 표에 참조된 Exchange 설명서를 참조하세요.

    -   이름: **임원 메일에 Executives 템플릿 적용**

    -   **Executives** 그룹을 규칙의 보낸 사람과 받는 사람으로 지정하고 추가 조건을 지정합니다.

    -   작업에 대해 **다음을 포함하는 메시지에 권한 보호 적용**을 선택한 다음 구성한 **Executives** 템플릿을 선택합니다.

    -   **DNP**("보호 안 함"의 약어) 예외나 제목에 포함되어 이 예외를 식별할 선택한 단어를 추가합니다.

    -   **적용**에 대한 규칙이 구성되었는지 확인합니다.

## <a name="user-documentation-instructions"></a>사용자 문서 지침
메일 제목에 **DNP** 또는 선택한 예외 단어나 구를 지정하는 방법에 대한 지침을 제공하려는 경우가 아니면 임원과 주고받는 메일을 보호하기 위해 임원이 특별한 작업을 수행할 필요가 없기 때문에 이 시나리오에서 사용자에게 제공할 절차 지침은 없습니다. 메일 메시지와 모든 첨부 파일은 임원 그룹의 구성원만 액세스할 수 있도록 자동으로 보호됩니다.

그러나 이러한 메일이 자동으로 보호되고 이로 이해 해당 메일의 사용이 어떻게 제한될 수 있는지를 임원과 지원 센터에 알려야 할 수도 있습니다. 예를 들어 메일이나 첨부 파일이 나중에 다른 사용자에게 전달된 경우 다른 사람들이 해당 메일이나 첨부 파일을 읽을 수 없습니다. DNP(또는 이와 동등한 단어) 예외를 구성한 경우 Exchange 관리자의 작업 없이도 임원이 직접 규칙을 재정의할 수 있도록 지원 센터에 이 구성을 알려야 합니다.

다음 템플릿을 사용하여 최종 사용자 통신에 알림을 복사해서 붙여넣고 사용자 환경에 맞게 다음과 같이 수정합니다.

1.  *&lt;조직 이름&gt;* 인스턴스를 사용자 조직의 이름으로 바꿉니다.

2.  예외에 대해 DNP와 다른 문자열을 선택한 경우 해당 값과 설명을 적절하게 바꿉니다.

3.  *&lt;메일 도메인&gt;*을 사용자 조직의 메일 도메인 이름으로 바꿉니다.

4.  *&lt;연락처 세부 정보&gt;*를 웹 사이트 링크, 메일 주소, 전화 번호 등 사용자가 지원 센터에 연락을 할 수 있는 방법에 대한 지침으로 바꿉니다.

5.  알림을 원하는 대로 수정한 다음 해당 사용자에게 보냅니다.

예제 문서에서는 사용자 지정 후 이 알림이 사용자에게 표시되는 방식을 보여 줍니다.

![Azure RMS 빠른 배포를 위한 템플릿 사용자용 설명 문서](../media/AzRMS_UsersBanner.png)

### <a name="it-announcement-ltorganization-namegt-executive-emails-are-now-automatically-protected"></a>IT 알림: &lt;조직 이름&gt; 임원 메일이 이제 자동으로 보호됨
지금부터 회사의 다른 &lt;조직 이름&gt; 임원에게 메일을 보낼 때마다 메일의 내용과 모든 첨부 파일이 자동으로 보호되어 회사의 다른 임원만 해당 메일과 첨부 파일에 액세스하여 정보를 읽고 인쇄하고 복사하는 등의 작업을 수행할 수 있습니다. 이 제한은 메일 메시지를 다른 사용자에게 전달하거나 첨부 파일을 저장하는 경우에도 적용됩니다. 이러한 보호 기능은 기밀 정보와 중요한 정보의 데이터 손실을 방지하는 데 도움이 됩니다.

&lt;조직 이름&gt; 임원이 아닌 다른 사용자가 해당 메일에 보내는 정보를 읽고 편집할 수 있게 하려면 다른 사용자에게 별도로 메일을 보내야 합니다. 또는 자동 보호를 재정의하기 위해 메일 메시지 제목에 **DNP**(보호 안 함의 약어) 문자를 입력합니다.

다른 &lt;조직 이름&gt; 임원에게 회사 기밀 정보를 보내는 경우 개인 메일 주소가 아니라 회사 메일 주소(*name*@&lt;emaildomain&gt;)로 보내야 합니다.

**도움이 필요한가요?**

-   지원 센터에 문의하세요. &lt;연락처 세부 정보&gt;

### <a name="example-user-documentation"></a>예제 사용자 문서
![Azure RMS 빠른 배포를 위한 예제 사용자용 설명 문서](../media/AzRMS_ExampleBanner.png)

#### <a name="it-announcement-vanarsdel-executive-emails-are-now-automatically-protected"></a>IT 알림: VanArsdel 임원 메일이 이제 자동으로 보호됨
지금부터 회사의 다른 VanArsdel 임원에게 메일을 보낼 때마다 메일의 내용과 모든 첨부 파일이 자동으로 보호되어 회사의 다른 임원만 해당 메일과 첨부 파일에 액세스하여 정보를 읽고 인쇄하고 복사하는 등의 작업을 수행할 수 있습니다. 이 제한은 메일 메시지를 다른 사용자에게 전달하거나 첨부 파일을 저장하는 경우에도 적용됩니다. 이러한 보호 기능은 기밀 정보와 중요한 정보의 데이터 손실을 방지하는 데 도움이 됩니다.

VanArsdel 임원이 아닌 다른 사용자가 해당 메일에 보내는 정보를 읽고 편집할 수 있게 하려면 다른 사용자에게 별도로 메일을 보내야 합니다. 또는 자동 보호를 재정의하기 위해 메일 메시지 제목에 **DNP**(보호 안 함의 약어) 문자를 입력합니다.

다른 VanArsdel 임원에게 회사 기밀 정보를 보내는 경우 개인 메일 주소가 아니라 회사 메일 주소(*name*@vanarsdelltd.com))로 보내야 합니다.

**도움이 필요한가요?**

-   지원 센터에 연락하려면 다음 정보를 참조하세요. helpdesk@vanarsdelltd.com




<!--HONumber=Nov16_HO2-->


