---
# required metadata

title: 관리자와 사용자에게 표시되는 내용 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 013e0eb4-49a7-4e81-9e4d-f56c0ceb017f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Azure RMS 작동 중: 관리자와 사용자에게 표시되는 결과
이 문서에서는 관리자와 사용자에게 표시되는 내용과 Azure 권한 관리(Azure RMS)를 사용하여 중요한 정보나 기밀 정보를 보호할 수 있는 방법에 대한 몇 가지 일반적인 예를 보여 줍니다.

> [!NOTE]
> Azure RMS로 데이터를 보호하는 이러한 모든 예에서, 적용된 보호가 콘텐츠 소유자가 속하지 않은 그룹에게도 권한을 부여하거나 적용된 보호에 만료 일자가 포함된 경우에도 해당 소유자는 계속 데이터(파일 또는 전자 메일)에 대한 모든 권한을 가집니다.
> 
> 마찬가지로 IT 부서는 사용자가 지정한 권한 있는 사용자나 서비스에 대한 위임된 액세스 권한을 부여하는 Rights Management의 슈퍼 사용자 기능을 사용하여 제한 없이 항상 보호된 데이터에 액세스할 수 있습니다. 또한 IT 부서는 보호된 데이터의 사용 현황(예: 데이터에 액세스하는 사용자와 액세스하는 시간)을 추적하고 모니터링할 수 있습니다.

RMS 실행을 보여 주는 다른 스크린샷과 비디오는 [Microsoft Rights Management 서비스 포털](http://www.microsoft.com/rms) 및 [Microsoft Rights Management(RMS) 팀 블로그](http://blogs.technet.com/b/rms)를 확인하세요.

## 권한 관리 활성화 및 구성
Windows PowerShell을 사용하여 Azure RMS를 활성화하고 구성할 수도 있지만 관리 포털에서 하는 것이 가장 간편합니다. 서비스가 활성화되면 바로 관리자와 사용자가 파일에 정보 보호를 빠르고 쉽게 적용하는 데 선택할 수 있는 두 개의 기본 템플릿이 제공됩니다. 하지만 추가 옵션 및 설정이 포함된 사용자 지정 템플릿을 직접 만들 수도 있습니다.

![](../media/AzRMS_StoryboardActivate_small1.png)


**1단계에서 관리자에게 표시되는 내용:** Office 365 관리 센터(첫 번째 그림) 또는 Azure 클래식 포털(두 번째 그림)을 사용하여 RMS를 활성화할 수 있습니다.<br /><br />한 번 클릭으로 활성화하고 다시 클릭하여 확인하면 조직에서 관리자와 사용자에 대한 정보 보호가 사용됩니다.

---

![](../media/AzRMS_TemplatesPortal_small.png)

**2단계에서 관리자에게 표시되는 내용:** 활성화되면 조직에서 두 개의 권한 정책 템플릿을 자동으로 사용할 수 있습니다. 한 템플릿은 읽기 전용 템플릿(**기밀 보기 전용**)이고 다른 템플릿은 읽기 및 수정 권한이 있는 템플릿(**기밀**)입니다.

이러한 템플릿이 파일이나 전자 메일에 적용되면 조직의 사용자에 대한 액세스를 제한합니다. 이는 회사 데이터가 조직 외부인에게 누출되는 것을 방지하는 매우 빠르고 쉬운 방법입니다.

> [!TIP]
> 이러한 기본 템플릿은 조직 이름이 접두사로 자동 추가되므로 쉽게 알아볼 수 있습니다. 이 예제에서는 **VanArsdel, Ltd**입니다.

사용자에게 이러한 템플릿을 표시하지 않거나 자체 템플릿을 만들려는 경우 Azure 클래식 포털에서 이 작업을 수행할 수 있습니다. 이 그림에서처럼 마법사가 사용자 지정 템플릿 만들기 프로세스를 안내합니다.

---

![](../media/AzRMS_TemplatesSettings3.png)

**3단계에서 관리자에게 표시되는 내용:** 오프라인 액세스, 만료 설정 및 템플릿을 즉시 게시할지 여부(권한 관리를 지원하는 응용 프로그램에 표시)는 자체 템플릿을 만들 경우 사용 가능한 구성 설정 중 일부에 포함됩니다.

---

![](../media/AzRMS_TemplatesPortal_ExplorerWord3.png)

**4단계에서 사용자에게 표시되는 내용:** 이러한 템플릿을 게시하면 이제 사용자가 파일 탐색기, Microsoft Word 등의 응용 프로그램에서 템플릿을 선택할 수 있습니다.

- 사용자가 기본 템플릿인 **VanArsdel, Ltd – 기밀**을 선택할 수 있습니다. 그러면 나중에 이 문서가 조직 외부인에게 전자 메일로 전송되거나 공용 위치에 저장된 경우에도 VanArsdel 조직의 직원만 해당 문서를 열고 사용할 수 있습니다.

- 사용자가 관리자가 만든 사용자 지정 템플릿인 **영업 및 마케팅 – 읽기 및 인쇄 전용**을 선택할 수 있습니다. 그러면 조직 외부인으로부터 파일을 보호하면서 판매 및 마케팅 부서의 직원에게로 액세스가 제한됩니다. 또한 이러한 직원들도 문서에 대한 전체 권한이 없으며 읽기와 인쇄만 가능합니다. 예를 들어 문서를 수정하거나 복사할 수 없습니다.

---

**이 시나리오에 대한 추가 정보:**

- 단계별 지침은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md) 및 [Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)을 참조하세요.

- 사용자가 중요한 회사 파일을 보호할 수 있도록 지원하려면 [사용자가 Azure 권한 관리를 사용하여 파일을 보호할 수 있도록 지원](../deploy-use/help-users.md)을 참조하세요.

다음으로, 관리자가 템플릿을 적용하여 파일 및 전자 메일에 대한 정보 보호를 자동으로 구성할 수 있는 방법에 대한 몇 가지 예를 살펴봅시다.

## Windows Server 및 파일 분류 인프라가 실행되는 파일 서버에서 파일을 자동으로 보호

이 예에서는 Azure RMS를 사용하여 Windows Server 2012 이상을 실행하고 파일 분류 인프라를 사용하도록 구성된 파일 서버에서 파일을 자동으로 보호할 수 있는 방법을 보여 줍니다.

파일에 분류 값을 적용할 수 있는 여러 가지 방법이 있습니다. 예를 들어 파일 콘텐츠를 검사하고 그에 따라 기밀성 및 개인 식별 정보 같은 기본 제공 분류를 적용할 수 있습니다. 하지만 이 예에서 관리자는 **마케팅 판촉** 폴더에 저장된 모든 사용자 문서에 자동으로 적용되는 사용자 지정 **마케팅** 분류를 만듭니다. 이 폴더가 마케팅 그룹의 구성원으로 액세스를 제한하는 NTFS 권한으로 보호된 경우에도 관리자는 해당 그룹의 일부 사용자가 파일을 이동하거나 전자 메일로 보내면 이러한 권한이 손실될 수 있음을 알고 있습니다. 그러면 권한 없는 사용자가 파일 정보에 액세스할 수 있습니다.

![](../media/AzRMS_FCI_ConnectorSmall.png)

**1단계에서 관리자에게 표시되는 내용:** 관리자가 온-프레미스 서버와 Azure RMS 간에 릴레이 역할을 하는 Rights Management(RMS) 커넥터를 설치하고 구성합니다.

---

![](../media/AzRMS_ExampleFCI_ConfigurationSmall.png)

**2단계에서 관리자에게 표시되는 내용:** 파일 서버에서 관리자가 **Marketing Promotions** 폴더의 모든 사용자 파일이 **마케팅**으로 자동 분류되고 RMS 암호화로 보호되도록 분류 규칙과 작업을 구성합니다.

첫 번째 예제에서 만든 사용자 지정 RMS 템플릿을 선택하고 판매 및 마케팅 부서의 구성원으로 액세스를 제한합니다. 즉, **판매 및 마케팅 - 읽기 및 인쇄 전용**을 부여합니다.

따라서 해당 폴더의 모든 문서가 자동으로 마케팅 분류로 구성되며 판매 및 마케팅 RMS 템플릿으로 보호됩니다.

---

![](../media/AzRMS_FCI_EmailSmall.png)

**3단계에서 사용자에게 표시되는 내용:** RMS를 통해 중요한 정보나 기밀 정보에 액세스할 수 없는 사용자에게 데이터가 누출되는 것을 방지하는 방법:

- 마케팅 부서의 Janet이 마케팅 판촉 폴더의 기밀 보고서를 전자 메일로 보냅니다. 이 보고서에는 새 제품 기능과 광고 계획이 담겨 있으며 현재 출장 중인 동료가 요청한 보고서입니다. 하지만 Janet이 실수로 이 보고서를 잘못된 사람에게 전자 메일로 보냅니다. Janet은 실수로 다른 회사의 비슷한 이름을 가진 받는 사람을 선택했다는 것을 모릅니다.<br><br>
받는 사람은 판매 및 마케팅 그룹의 구성원이 아니므로 기밀 보고서를 읽을 수 없습니다.

---

**이 시나리오에 대한 추가 정보:**

- 단계별 지침은 [Azure 권한 관리 커넥터 배포](../deploy-use/deploy-rms-connector.md)를 참조하세요.

## Exchange Online 및 데이터 손실 방지 정책으로 전자 메일을 자동으로 보호

이전 예제는 중요 정보 또는 기밀 정보가 포함된 파일을 자동으로 보호할 수 있는 방법을 보여 줍니다. 그런데 정보가 파일 형식이 아니라 메일 메시지 형식인 경우에는 어떻게 하나요? 이 경우에는 사용자에게 정책 팁을 사용하여 정보 보호를 적용하라는 메시지를 표시하거나 전송 규칙을 사용하여 정보 보호를 자동으로 적용하는 등 Exchange Online DLP(데이터 손실 방지) 정책을 통해 해결할 수 있습니다.

이 예에서 관리자는 조직이 개인 식별 정보 데이터 보호를 위해 미국 규정을 준수하는 데 도움이 되는 정책을 구성하지만 다른 준수 규정이나 사용자가 정의한 사용자 지정 규칙에 대한 규칙을 구성할 수도 있습니다.

![](../media/AzRMS_DLPExample1.png)

**1단계에서 관리자에게 표시되는 내용:** Exchange 관리 센터에서 이름이 **미국 PII(개인 식별이 가능한 정보) 데이터**라는 Exchange 템플릿은 관리자가 새 DLP 정책을 만들고 구성하는 데 사용됩니다. 이 템플릿은 전자 메일 메시지에서 사회 보장 번호 및 운전 면허 번호 같은 정보를 찾습니다.

이 정보가 포함된 상태로 조직 외부에 전송된 전자 메일 메시지에 회사 직원으로만 액세스를 제한하는 RMS 템플릿을 사용하여 권한 보호가 자동으로 적용되도록 규칙이 구성됩니다.

여기서 규칙은 첫 번째 예의 기본 템플릿인 **VanArsdel, Ltd – 기밀**중 하나를 사용하도록 구성됩니다. 하지만 템플릿을 선택하여 사용자가 만든 사용자 지정 템플릿을 포함하는 방법과 Exchange에 해당되는 **전달 금지** 옵션도 확인할 수 있습니다.

---

![](../media/AzRMS_DLPUnprotectedEmail_small.png)

**2단계에서 사용자에게 표시되는 내용:** 고용 관리자가 최근에 고용된 직원의 사회 보장 번호가 포함된 메일 메시지를 작성한 후 이 전자 메일 메시지를 인사 부서의 Sherrie에게 보냅니다.

---

![](../media/AzRMS_DLPProtectedEmail_small.png)

**3단계에서 사용자에게 표시되는 내용:** 이 메일 메시지가 조직 외부 사용자에게 전송되거나 전달되면 DLP 규칙에 따라 권한 보호가 자동으로 적용됩니다.

전자 메일이 조직 인프라를 떠날 때 암호화되므로 메시지가 전송되는 동안이나 받는 사람의 받은 편지함에 있는 동안 전자 메일 메시지의 사회 보장 번호를 읽을 수 없습니다. 받는 사람이 VanArsdel 직원이 아니면 해당 메시지를 읽을 수 없게 됩니다.

---

**이 시나리오에 대한 추가 정보:**

-   Azure RMS가 Exchange Online과 함께 작동하는 방식에 대한 자세한 내용은 [응용 프로그램에서 Azure 권한 관리를 지원하는 방법](applications-support.md)에서 [Exchange Online 및 Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) 섹션을 참조하세요.

-   Azure RMS에 대해 Exchange Online을 구성하는 단계별 지침은 [Azure 권한 관리에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)에서 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

## SharePoint Online 및 보호된 라이브러리로 파일을 자동으로 보호

여기서는 SharePoint Online 및 보호된 라이브러리를 사용할 때 문서를 손쉽게 보호할 수 있는 방법을 보여 줍니다.

이 예에서 Contoso의 SharePoint 관리자는 편집 및 버전 제어를 위해 중앙에서 문서를 저장하고 체크 아웃하는 데 사용하는 부서별 라이브러리를 만들었습니다. 예를 들어 판매, 마케팅, 인사 부서 등에 대한 라이브러리가 있습니다. 보호된 이 라이브러리 중 한 곳에 새 문서가 업로드되거나 만들어지면 권한 정책 템플릿을 선택하지 않고도 해당 문서가 라이브러리의 보호를 상속하여 자동으로 보호되고 SharePoint 라이브러리 외부로 이동한 경우에도 보호가 유지됩니다.

![](../media/AzRMS_StoryboardSPO_small1.png)

**1단계에서 관리자에게 표시되는 내용:** 관리자가 SharePoint 사이트에 대해 정보 권한 관리를 사용하도록 설정합니다.

---

![](../media/AzRMS_StoryboardSPO_small2.png)

**2단계에서 관리자에게 표시되는 내용:** 그런 다음 라이브러리에 대해 권한 관리를 사용하도록 설정합니다. 추가 옵션이 있지만 간단한 이 설정으로 필요한 모든 항목이 거의 포함됩니다.

이제 문서가 이 라이브러리에서 다운로드되면 Rights Management에 의해 자동으로 보호되고 라이브러리에 대해 구성된 보호 기능을 상속합니다.

---

![](../media/AzRMS_StoryboardSPO_small3.png)

**3단계에서 사용자에게 표시되는 내용:** 영업 부서의 사용자가 라이브러리에서 이 영업 보고서를 체크 아웃하면 맨 위의 정보 배너에 제한된 액세스로 보호된 문서라고 명확하게 표시됩니다.

사용자가 문서 이름을 바꾸거나 문서를 다른 위치에 저장하거나 전자 메일로 공유하는 경우에도 보호가 유지됩니다. 파일 이름, 저장 위치 또는 전자 메일로 공유되는지 여부에 관계 없이 판매 부서의 구성원만 이 문서를 읽을 수 있습니다.

---

**이 시나리오에 대한 추가 정보:**

-   Azure RMS가 SharePoint와 함께 작동하는 방식에 대한 자세한 내용은 [응용 프로그램에서 Azure 권한 관리를 지원하는 방법](applications-support.md)에서 [SharePoint Online 및 SharePoint Server](office-apps-services-support.md#sharepoint-online-and-sharepoint-server) 섹션을 참조하세요.

-   Azure RMS에 대해 SharePoint를 구성하는 단계별 지침은 [Azure 권한 관리에 대해 응용 프로그램 구성](../deploy-use/configure-applications.md)에서 [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)섹션을 참조하세요.

## 사용자가 모바일 사용자와 안전하게 첨부 파일 공유

이전 예에서는 관리자가 중요 데이터 및 기밀 데이터에 자동으로 정보 보호를 적용할 수 있는 방법에 대해 살펴 보았습니다. 하지만 어떤 경우에는 사용자가 이 보호를 직접 적용해야 할 수 있습니다. 사용자가 다른 조직의 파트너와 공동으로 작업하거나, 템플릿에 정의되지 않은 사용자 지정 권한이나 설정이 필요하거나, 이전 예에서 다루지 않은 애드혹 환경을 예로 들 수 있습니다. 이러한 환경에서 사용자는 RMS 템플릿을 직접 적용하고 사용자 지정 권한을 구성할 수 있습니다.

이 예제에서는 사용자가 공동으로 작업하는 다른 회사의 사용자와 문서를 손쉽게 공유하면서도 문서를 계속 보호할 수 있고 수신자가 많이 사용되는 모바일 장치에서도 문서를 읽을 수 있도록 하는 방법을 보여 줍니다. 이 시나리오는 조직의 Windows 컴퓨터에 자동으로 배포할 수 있는 권한 관리 공유 응용 프로그램을 사용합니다. 또는 사용자가 응용 프로그램을 직접 설치할 수 있습니다.

이 예에서 Contoso의 Alice는 Fabrikam의 Bob에게 기밀 Word 문서를 전자 메일로 보냅니다. Bob은 자신의 iPad에서 문서를 읽으며 iPhone, Android 태블릿 또는 휴대폰, Mac 컴퓨터 또는 Windows 휴대폰이나 컴퓨터에서도 손쉽게 읽을 수 있습니다.

![](../media/AzRMS_StoryboardEmail_small1.png)

**1단계에서 사용자에게 표시되는 내용:** Windows PC에서 Alice는 표준 메일 메시지를 만들고 문서를 첨부합니다.

리본에서 **보호된 항목 공유** 를 클릭하면 RMS 공유 응용 프로그램의 **보호된 항목 공유** 대화 상자가 로드됩니다.

Alice는 Bob이 해당 문서를 보고 편집만 할 수 있도록 제한하고 문서를 복사하거나 인쇄하지는 못하도록 설정하려고 하므로 **검토자 - 보기 및 편집**을 선택합니다. 또한 Alice는 누군가 문서를 열 때 전자 메일을 받고자 하며, 나중에 필요한 경우 문서를 해지하고 해지가 즉시 적용됨을 확인할 수 있습니다.

---

![](../media/AzRMS_StoryboardEmail_small2.png)

**2단계에서 사용자에게 표시되는 내용:** Bob이 자신의 iPad에서 메일을 봅니다.

Alice의 메시지와 첨부 파일 외에도 iPad에서 RMS 공유 앱을 등록하고 설치하는 지침이 표시됩니다.

---

![](../media/AzRMS_StoryboardEmail_small3.png)

**3단계에서 사용자에게 표시되는 내용:** Bob이 이제 첨부 파일을 열 수 있습니다. 우선 원하는 받는 사람인지를 확인하기 위해 로그인하라는 메시지가 표시됩니다.

Bob이 문서를 볼 때 정보를 보고 편집할 수는 있지만 복사하거나 인쇄할 수 없음을 알리는 제한된 액세스 정보도 표시됩니다.

---

![](../media/AzRMS_StoryboardEmail_small4.png)

**4단계에서 사용자에게 표시되는 내용:** Alice는 자신이 보낸 문서를 Bob이 열었다는 사실과 Bob이 문서에 액세스한 시간을 알리는 메일 메시지를 받습니다.

Bob이 첨부 파일과 함께 이 전자 메일을 전달하거나 다른 사람이 액세스할 수 있는 위치에 저장하거나 네트워크에서 문서를 가로채는 경우 다른 사람이 해당 문서를 읽을 수 없게 됩니다.

---

**이 시나리오에 대한 추가 정보:**

- 자세한 내용은 [Rights Management 공유 응용 프로그램 사용자 가이드](../rms-client/sharing-app-user-guide.md)에서 [메일을 통해 공유하는 파일 보호](../rms-client/sharing-app-protect-by-email.md) 및 [보호된 파일 보기 및 사용](../rms-client/sharing-app-view-use-files.md)을 참조하세요.

- [Azure 권한 관리에 대한 빠른 시작 자습서](../get-started/quick-start-tutorial.md)에는 이 시나리오에 대한 단계별 지침이 포함되어 있습니다.

## 다음 단계

이제 Azure RMS가 수행할 수 있는 작업의 몇 가지 예를 살펴 보았으며 이를 수행하는 방법에 관심을 가질 수 있습니다. Azure RMS 작동 방식에 대한 기술적인 정보는 [Azure RMS 작동 방식](how-does-it-work.md)을 참조하세요.

<!--HONumber=Apr16_HO3-->

