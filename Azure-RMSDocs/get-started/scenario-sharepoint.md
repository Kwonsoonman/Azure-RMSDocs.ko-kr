---
title: "시나리오 - SharePoint에 저장된 문서에 대한 제어 유지 | Azure Information Protection"
description: "이 시나리오 및 지원 사용자 문서에서는 Azure Rights Management 보호를 사용하여 SharePoint에 저장된 Office 문서가 보호된 라이브러리를 통해 계속 제어되도록 합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 371e566a166dad74b55266db23e034f926942a26


---

# <a name="scenario-retain-control-of-documents-stored-in-sharepoint"></a>시나리오 - SharePoint에 저장된 문서에 대한 제어 유지

>*적용 대상: Azure Information Protection, Office 365*

이 시나리오 및 지원 사용자 문서에서는 Azure Information Protection의 Azure Rights Management 기술을 사용하여 SharePoint에 저장된 Office 문서가 보호된 라이브러리를 통해 계속 제어되도록 합니다. 예를 들어 사용자의 우발적이거나 의도적인 누출로부터 문서가 자동으로 보호되며, 문서가 다운로드되거나 동기화된 후에도 콘텐츠에 대한 액세스를 차단할 수 있습니다. 보호하려는 파일은 설계 문서 또는 계획에 대한 내부 공동 작업에 사용하거나 다른 결과물로 제공하기 위한 것일 수 있습니다. SharePoint용 보호된 라이브러리를 구성할 때 해당 라이브러리에 저장된 Office 파일은 Azure 권한 관리에 의해 보호됩니다.

지침을 제공하기에 적합한 상황은 다음과 같습니다.

-   직원들이 SharePoint 라이브러리에 있는 Office 문서를 사용하여 공유하고 공동 작업을 수행하는 경우

-   직원들이 관리자가 라이브러리 수준에서 설정하는 사용 권한을 설정하거나 변경할 필요가 없는 경우

-   직원들이 조직 외부 사용자와 이러한 문서를 공유할 필요가 없는 경우

## <a name="deployment-instructions"></a>배포 지침
![Azure RMS 빠른 배포를 위한 관리자 지침](../media/AzRMS_AdminBanner.png)

사용자 문서를 진행하기 전에 다음 요구 사항과 지원 절차가 충족되었는지 확인합니다.

## <a name="requirements-for-this-scenario"></a>이 시나리오의 요구 사항
이 시나리오가 작동하려면 다음 사항을 준비해야 합니다.

|요구 사항|추가 정보가 필요한 경우 확인 가능한 위치|
|---------------|--------------------------------|
|Office 365 또는 Azure Active Directory용 계정과 그룹을 준비했는지 여부|[Azure Information Protection 준비](../plan-design/prepare.md)|
|Azure 권한 관리가 활성화되었는지 여부|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|SharePoint Server를 사용할 경우: RMS 커넥터를 배포하고 SharePoint에 대해 구성|[Azure Rights Management 커넥터 배포](../deploy-use/deploy-rms-connector.md)|
|보호할 SharePoint 사이트에 대한 사용 권한 구성|[목록, 라이브러리, 폴더, 문서 또는 목록 항목에 대한 사용 권한 관리](https://support.office.com/en-ca/article/Manage-permissions-for-a-list-library-folder-document-or-list-item-9d13e7df-a770-4646-91ab-e3c117fcef45)<br /><br />[목록이나 라이브러리에 정보 권한 관리 적용](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|
|IRM 및 보호된 라이브러리에 대해 SharePoint 구성|[SharePoint 관리 센터의 IRM(정보 권한 관리) 설정](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[목록이나 라이브러리에 정보 권한 관리 적용](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

### <a name="to-configure-the-sharepoint-library-for-irm-settings"></a>IRM 설정에 대해 SharePoint 라이브러리를 구성하려면

1.  IRM 서비스를 사용하도록 SharePoint를 구성한 후 Azure RMS로 보호할 SharePoint 라이브러리로 이동합니다. 사이트의 **설정** &gt; **IRM(정보 권한 관리)** 페이지에서 **다운로드 시 라이브러리에 대한 사용 권한 제한**을 선택하고 관리자를 위한 정책 제목과 사용자를 위한 정책 설명을 지정한 후 **옵션 표시**를 클릭합니다.

2.  다음을 선택합니다.

    -   **IRM을 지원하지 않는 문서의 업로드 허용 안 함**

    -   선택 사항: **그룹 보호 허용. 기본 그룹**을 선택하고 이 라이브러리에 저장된 문서에 대해 공동 작업을 해야 하지만 SharePoint 외부에 있을 수 있는 추가 그룹의 이름을 지정합니다. 예를 들어 Sales 그룹에 사이트에 대한 편집 권한이 있으며, 이 그룹의 구성원이 문서를 다운로드하고 디스크에 저장한 다음 Sales 그룹에 속하지 않는 동료에게 메일로 보냅니다. 동료가 여기서 지정한 그룹에 속하는 경우 사이트에 대해 구성된 것과 동일한 사용 권한을 자동으로 상속하며 문서를 편집할 수 있습니다.

        이 옵션을 사용하지 않으면 SharePoint 라이브러리에 액세스할 수 있는 사용자만 이러한 문서에 대해 공동 작업을 할 수 있으며 SharePoint에서 직접 문서를 다운로드해야 합니다. 이 제한은 대부분의 경우에 적합합니다.

## <a name="user-documentation-instructions"></a>사용자 문서 지침
보호된 라이브러리에는 사용자의 특별한 작업이 필요하지 않기 때문에 이 시나리오의 경우 사용자에게 제공할 절차 지침이 없습니다. SharePoint 관리자가 사이트에 대해 설정하는 사용 권한에 따라 문서가 자동으로 보호되거나 다운로드됩니다. 그러나 예상 결과를 알 수 있도록 이 변경 내용을 사용자에게 알리고, 어떤 라이브러리가 보호되며 이로 인해 문서 사용이 어떻게 제한될 수 있는지를 지원 센터에 알립니다. 예를 들어 현재의 제한 때문에 모바일 장치에서 해당 문서를 볼 수 있지만 편집할 수는 없습니다. 그룹 보호를 구성한 경우 SharePoint 외부 문서에 액세스하고 편집할 수 있는 그룹을 사용자에게 알립니다.

다음 템플릿을 사용하여 최종 사용자 통신에 알림을 복사해서 붙여넣고 사용자 환경에 맞게 다음과 같이 수정합니다.

1.  각 *&lt;SharePoint 라이브러리 이름&gt;* 인스턴스를 Azure 권한 관리에 대해 구성한 SharePoint 라이브러리의 이름과 링크로 바꿉니다. 이 통신이 둘 이상의 보호된 라이브러리에 사용되는 경우 지침을 적절하게 변경합니다.

2.  **그룹 보호 허용. 기본 그룹** 옵션을 구성한 경우 *&lt;그룹 이름&gt;*을 구성한 그룹 이름으로 바꾸고 &lt;이 그룹에 파일에 대한 공동 작업 액세스 권한이 있지만 SharePoint 라이브러리를 사용하여 공동 작업할 수 없는 이유&gt;에 대한 이유를 입력합니다. 이 옵션을 구성하지 않은 경우에는 이 문장을 삭제합니다.

3.  *&lt;연락처 세부 정보&gt;*를 웹 사이트 링크, 메일 주소, 전화 번호 등 사용자가 지원 센터에 연락을 할 수 있는 방법에 대한 지침으로 바꿉니다.

4.  알림을 원하는 대로 수정한 다음 해당 사용자에게 보냅니다.

예제 문서에서는 사용자 지정 후 이 알림이 사용자에게 표시되는 방식을 보여 줍니다.

![Azure RMS 빠른 배포를 위한 템플릿 사용자용 설명 문서](../media/AzRMS_UsersBanner.png)

### <a name="it-announcement-changes-to-the-ltname-of-sharepoint-librarygt-site"></a>IT 알림: &lt;SharePoint 라이브러리 이름&gt; 사이트에 대한 변경 내용
SharePoint 사이트인 **&lt;SharePoint 라이브러리 이름&gt;**이 이제 안전한 공동 작업에 사용할 수 있도록 구성되었습니다. 이제는 이러한 문서를 로컬로 저장하거나 다른 사람에게 메일로 보낸 경우에도 &lt;그룹 이름&gt;의 구성원만 이 사이트에서 해당 문서를 열 수 있습니다. 단, &lt;이 그룹에 파일에 대한 공동 작업 액세스 권한이 있지만 SharePoint 라이브러리를 사용하여 공동 작업할 수 없는 이유&gt;로 인해 문서를 다운로드한 후 &lt;그룹 이름&gt;의 구성원과 공유할 수 있다는 점은 예외입니다. 파일을 편집할 때 이러한 보호 기능이 있으며 액세스할 수 있는 사람을 알 수 있도록 문서 위쪽에 노란색 정보 배너가 표시됩니다.

이러한 변경 사항은 회사 기밀 데이터를 공개하지 않아야 하는 사람으로부터 안전하게 보호하는 데 도움이 됩니다. 모바일 장치를 사용하여 이러한 보호된 문서에 액세스하면 볼 수 있지만 데스크톱 장치를 사용하여 편집해야 합니다.

안전한 공동 작업을 지원하지 않는 경우 &lt;SharePoint 사이트 이름&gt; 사이트에 문서를 업로드할 수 없습니다.

**도움이 필요한가요?**

-   지원 센터에 문의하세요. &lt;연락처 세부 정보&gt;

### <a name="example-user-documentation"></a>예제 사용자 문서
![Azure RMS 빠른 배포를 위한 예제 사용자용 설명 문서](../media/AzRMS_ExampleBanner.png)

#### <a name="it-announcement-changes-to-the-sales-forecasts-and-reports-site"></a>IT 알림: 판매 예측 및 보고서 사이트에 대한 변경 사항
SharePoint 사이트인 **판매 예측 및 보고서**가 이제 안전한 공동 작업에 사용할 수 있도록 구성되었습니다. 이제는 이러한 문서를 로컬로 저장하거나 다른 사람에게 전자 메일로 보낸 경우에도 판매 및 마케팅 팀의 구성원만 이 사이트에서 해당 문서를 열 수 있습니다. 단, 문서를 다운로드한 후 재무 팀의 구성원과 공유할 수 있으므로 월별 예측 수치를 추출할 수 있다는 차이가 있습니다. 파일을 편집할 때 이러한 보호 기능이 있으며 액세스할 수 있는 사람을 알 수 있도록 문서 위쪽에 노란색 정보 배너가 표시됩니다.

이러한 변경 사항은 회사 기밀 데이터를 공개하지 않아야 하는 사람으로부터 안전하게 보호하는 데 도움이 됩니다. 모바일 장치를 사용하여 이러한 보호된 문서에 액세스하면 볼 수 있지만 데스크톱 장치를 사용하여 편집해야 합니다.

안전한 공동 작업을 지원하지 않는 경우 판매 예측 및 보고서 사이트에 문서를 업로드할 수 없습니다.

**도움이 필요한가요?**

-   지원 센터에 연락하려면 다음 정보를 참조하세요. helpdesk@vanarsdelltd.com




<!--HONumber=Nov16_HO2-->


