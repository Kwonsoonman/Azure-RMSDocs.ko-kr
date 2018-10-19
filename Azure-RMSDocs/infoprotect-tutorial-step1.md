---
title: 빠른 시작 자습서 1단계 - AIP
description: Azure Information Protection을 빠르게 사용해 보기 위한 소개 자습서의 1단계 - 보호 서비스 활성화.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: af3958d7c3bafc37772944e2cb39a9b3244eccc2
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169977"
---
# <a name="step-1-activate-protection"></a>1단계: 보호 활성화
 
>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
>보호가 테넌트에 대해 활성화되더라도 이 단계를 완료하여 활성화 상태를 확인합니다. 지침에는 2단계에 대해 준비되도록 Azure Portal에 로그인하고 Azure Information Protection 블레이드를 만드는 방법이 포함되어 있습니다.

보호가 Azure Information Protection에 대해 활성화되면 조직의 가장 중요한 문서 및 메일을 보호할 수 있습니다. 이러한 보호된 문서를 다른 사용자와 공유할 때 이들 문서의 사용 방식을 추적할 수도 있습니다. 

보호를 활성화할 수 있는 다른 방법이 있습니다. PowerShell 및 관리 포털을 사용할 수 있습니다. 그러나 이 자습서에서는 사용자에 대한 레이블을 구성하는 위치이기도 한 Azure Portal을 사용합니다. 

## <a name="to-activate-protection"></a>보호를 활성화하려면

1. 테넌트에 대한 전역 관리자 계정을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. 
    
    전역 관리자가 아닌 경우 **Information Protection 관리자** 또는 **보안 관리자**와 같은 다음 [관리 역할](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) 중 하나를 사용할 수 있습니다.

2. 허브 메뉴에서 **리소스 만들기**를 선택한 다음, Marketplace 검색 상자에 **Azure Information Protection**을 입력합니다. 
    
3. 결과 목록에서 **Azure Information Protection**을 선택합니다. **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.
    
    > [!TIP] 
    > 또는 다음에 포털에 로그인할 때 서비스 찾아보기 단계를 건너뛸 수 있도록 **대시보드에 고정**을 선택하여 대시보드에 **Azure Information Protection** 타일을 만듭니다.
    
    다시 **만들기**를 클릭합니다.

4. 서비스에 처음으로 연결할 때 자동으로 열리는 **빠른 시작** 페이지의 정보를 확인하세요. 나중에 이 페이지로 돌아올 수 있습니다. 이 자습서의 경우 **관리** > **보호 활성화**를 선택합니다. 

5. 이제 테넌트에 대해 보호가 활성화되었는지가 표시됩니다. 
    
    - 보호가 활성화된 경우 다음 확인이 표시됩니다.
        
        ![Azure RMS의 Azure Information Protection 상태](./media/info-protect-azurerms-activated.png)
        
    - 보호가 활성화되지 않은 경우 이 내용이 상태 정보에 반영된 것을 확인할 수 있으며 활성화할 옵션이 표시됩니다.
        
        ![Azure RMS의 Azure Information Protection 상태](./media/info-protect-azurerms-deactivated.png)

6. 보호가 활성화되지 않은 경우 **활성화**를 선택합니다. 

    활성화가 완료되면 정보 표시줄에 **활성화가 성공적으로 완료됨**이 표시됩니다.

이 자습서를 완료하는 데 필요한 이 첫 번째 단계는 그 정도로 충분합니다. 이제 2단계로 이동할 준비가 되었습니다.

|자세한 정보가 필요한 경우|추가 정보|
|--------------------------------|--------------------------|
|보호 활성화 정보|[Azure 권한 관리 활성화](activate-service.md)|


>[!div class="step-by-step"]
[&#171; 소개](infoprotect-quick-start-tutorial.md)
[2단계 &#187;](infoprotect-tutorial-step2.md)

