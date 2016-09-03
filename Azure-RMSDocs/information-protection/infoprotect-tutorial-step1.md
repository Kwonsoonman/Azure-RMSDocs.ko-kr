---
title: "Azure Information Protection 빠른 시작 자습서 1단계 | Azure 권한 관리"
description: "약 10분 만에 완료할 수 있는 4단계를 통해 조직에서 Microsoft Azure Information Protection 사용을 빠르게 시작하는 방법을 확인할 수 있는 소개 자습서의 1단계입니다."
author: cabailey
manager: mbaldwin
ms.date: 07/291/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: b608ee307bf7388ab7c7ed70cc1286db5df176c8


---

# 1단계: Rights Management 서비스 활성화
 
>*적용 대상: Azure Information Protection 미리 보기*

**[ 이 정보는 임시로 제공되며 변경될 수 있습니다. ]**

> [!NOTE]
>Azure 권한 관리로 데이터를 분류만 하고 보호하지는 않으려는 경우나 테넌트에 대해 이미 Azure 권한 관리를 활성화한 경우 바로 [다음 단계](infoprotect-tutorial-step2.md)로 이동하세요. 

Azure 권한 관리를 활성화한 경우 가장 중요한 문서와 파일을 분류한 후 보호할 수 있습니다. Azure 권한 관리를 활성화하려면 Office 365 관리 센터 또는 Azure 클래식 포털을 사용하면 됩니다.

-   Azure 권한 관리가 포함된 Office 365 구독이 있거나, Azure 권한 관리가 제외된 Office 365 구독을 사용하지만 Azure RMS Premium 구독이 있는 경우: **Office 365 관리 센터를 사용**합니다.

-   Office 365 구독이 없는 경우: **Azure 클래식 포털을 사용**합니다.

### Office 365 클래식 관리 센터에서 Rights Management를 활성화하려면

> [!NOTE]
> Office 365 클래식 관리 센터보다는 **Office 365 관리 센터 미리 보기**를 사용하는 경우, [Office 365 관리 센터 미리 보기에서 Azure 권한 관리를 활성화하는 방법](../deploy-use/activate-office365-preview.md)의 지침을 사용하거나, 클래식 버전으로 전환하여 다음 지침을 사용하세요. 전환하려면 로그인 후 **홈** 페이지의 **Go to the old admin center(기존 관리 센터로 이동)**를 클릭합니다.

1.  [Office 365 포털](https://portal.office.com/)로 이동하고 Office 365 전역 관리자 계정으로 로그인합니다.

2.  Office 365 관리 센터가 자동으로 표시되지 않으면 왼쪽 위에서 앱 시작 관리자 아이콘을 선택하고 **관리자**를 선택합니다. **관리자** 타일은 Office 365 관리자에게만 나타납니다.

  > [!TIP]
  > 관리 센터 도움말은 [Office 365 관리 센터 정보 - 관리자 도움말](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)을 참조하세요.

3.  왼쪽 창에서 **서비스 설정**을 확장합니다.

4.  **권한 관리**를 클릭합니다.

5.  **권한 관리** 페이지에서 **관리**를 클릭합니다.

6.  **Rights Management** 페이지에서 **활성화**를 클릭합니다.

7.  **권한 관리를 활성화하시겠나요?**라는 메시지가 나타나면 **활성화**를 클릭합니다.

이제 **Rights Management가 활성화된** 것을 확인하고 비활성화할 수 있습니다(페이지를 수동으로 새로 고쳐야 할 수 있음).

이때 **고급 기능**을 클릭하지 마세요. 고급 기능을 클릭하면 사용자 지정 템플릿을 구성할 수 있는 Azure 클래식 포털로 이동되지만, 이 자습서에서는 이렇게 할 필요가 없습니다. 대신 Office 365 관리 센터를 닫을 수 있습니다.

### Azure 클래식 포털에서 Rights Management를 활성화하려면

1.  [Azure 클래식 포털](http://go.microsoft.com/fwlink/p/?LinkID=275081)로 이동하고 Azure Active Directory 전역 관리자 계정으로 로그인합니다.

2.  왼쪽 창에서 **ACTIVE DIRECTORY**를 클릭합니다.

3.  **Active Directory** 페이지에서 **Rights Management**를 클릭합니다.

4.  [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]에 대해 관리할 디렉터리를 선택하고 **활성화**를 클릭한 다음 작업을 확인합니다.

이제 **Rights Management 상태** 가 **활성** 으로 표시되고 **활성화** 옵션이 **비활성화**로 바뀝니다.

포털에서 Rights Management에 대한 다른 옵션을 구성할 수 있지만, 이 자습서에서는 필요하지 않으므로 Azure 클래식 포털을 닫을 수 있습니다.

이 첫 번째 단계는 그 정도로 충분합니다. 나중에 이 자습서에서는 기밀로 분류된 문서와 메일을 보호하기 위해 기본 Azure 권한 관리 템플릿 중 하나를 선택할 수 있도록 Azure 권한 관리 서비스를 활성화합니다.

프로덕션 배포의 경우 두 개의 기본 Azure 권한 관리 템플릿 외에 또는 대신 사용자 지정 템플릿을 구성하고자 할 것입니다. 그러나 이 자습서에서는 사용자 지정 템플릿이 필요하지 않으므로 2단계로 이동하면 됩니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|권한 관리 활성화 정보|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|기본 템플릿 및 사용자 지정 템플릿을 새로 만드는 방법 정보|[Azure 권한 관리용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; 소개](infoprotect-quick-start-tutorial.md)
[2단계 &#187;](infoprotect-tutorial-step2.md)



<!--HONumber=Aug16_HO4-->


