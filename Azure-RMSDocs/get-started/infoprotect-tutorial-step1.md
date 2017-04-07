---
title: "빠른 시작 자습서 1단계 - AIP"
description: "Azure Information Protection를 빠르게 사용해 보기 위한 소개 자습서 1단계 - Azure Rights Management 서비스 활성화"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 8ccf0ea41e9465e10408595a3b875704baca93d2
ms.sourcegitcommit: f0402cf14506b4c61a156a2baf7e69b7b16883a1
translationtype: HT
---
# <a name="step-1-activate-the-rights-management-service"></a>1단계: Rights Management 서비스 활성화
 
>*적용 대상: Azure Information Protection*

> [!NOTE]
>테넌트에 대해 이미 Azure Rights Management 서비스를 활성화했음을 알고 있는 경우 바로 [다음 단계](infoprotect-tutorial-step2.md)로 이동할 수 있습니다. 
>
>이 서비스를 활성화했는지 확실하지 않은 경우 이 단계의 지침을 사용하여 확인하세요.

Azure Rights Management 서비스가 활성화되면 조직에서 가장 중요한 문서와 전자 메일을 보호하고, 보호된 문서가 다른 사용자와 공유할 때 사용되는 방식을 추적할 수 있습니다. 이 서비스를 활성화하는 방법으로는 Windows PowerShell을 사용하거나, 관리 포털을 사용하는 방법 등 여러 가지가 있습니다.

이 자습서에서는 Office 365 관리자용 관리 포털의 활성화 페이지로 바로 이동합니다. 이 페이지는 Office 365 클래식 포털과 Office 365 관리 센터 미리 보기의 페이지와 같습니다. 

페이지로 직접 이동하지 않고 Office 365 관리자 포털에서 이 페이지로 이동하려면 [Azure Rights Management 활성화](../deploy-use/activate-service.md)를 참조하세요. 또한 Azure Portal에 대한 액세스 권한은 있지만 Office 365 관리자 포털에 대해서는 없는 경우 다음 전체 지침을 사용하세요.

## <a name="to-activate-the-rights-management-service"></a>Rights Management 서비스를 활성화하려면

1. 새 브라우저 창을 열고 Office 365 관리자용 [Rights Management 활성화 페이지](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx)로 바로 이동합니다.
    
    로그인하라는 메시지가 나타나면 Office 365에 대한 전역 관리자 계정을 사용합니다.

2. **Rights Management** 페이지에서 **활성화**를 클릭합니다. 이 단추에 **비활성화**가 표시된 경우 서비스가 이미 활성화되어 있는 것이므로 바로 [다음 단계](infoprotect-tutorial-step2.md)로 이동할 수 있습니다. 

    ![Azure Information Protection 빠른 시작 자습서 1단계 - 서비스 활성화](../media/info-protect-activate.png)

3. **Rights Management를 활성화하시겠습니까?**라는 메시지가 나타나면 **활성화**를 클릭하여 확인합니다.

    이제 **Rights Management가 활성화된** 것을 확인하고 비활성화할 수 있습니다(페이지를 수동으로 새로 고쳐야 할 수 있음).

    이때 **고급 기능**을 클릭하지 마세요. 고급 기능을 클릭하면 사용자 지정 템플릿을 구성할 수 있는 Azure 클래식 포털로 이동되지만, 이 자습서에서는 이렇게 할 필요가 없습니다. 대신,이 페이지를 닫을 수 있습니다.

이 자습서를 완료하는 데 필요한 이 첫 번째 단계는 그 정도로 충분합니다. 프로덕션 배포의 경우 두 개의 기본 Azure 권한 관리 템플릿 외에 또는 대신 사용자 지정 템플릿을 구성하고자 할 것입니다. 그러나 이 자습서에서는 사용자 지정 템플릿이 필요하지 않으므로 2단계로 이동하면 됩니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|권한 관리 활성화 정보|[Azure 권한 관리 활성화](../deploy-use/activate-service.md)|
|기본 템플릿 및 사용자 지정 템플릿을 새로 만드는 방법 정보|[Azure Rights Management 서비스용 사용자 지정 템플릿 구성](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; 소개](infoprotect-quick-start-tutorial.md)
[2단계 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
