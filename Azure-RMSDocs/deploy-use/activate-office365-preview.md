---
title: "Office 365 관리 센터 미리 보기에서 Azure RMS 활성화 - AIP"
description: "Office 365 관리 센터의 신규 미리 보기 버전(Office 365 관리 센터 미리 보기) 액세스 권한이 있는 경우의 Azure Rights Management 서비스의 활성화 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a2b3e1a2-59a0-4191-bf4c-4485ae7a70a9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b39c39756ec5f6e6554b87a15186f998eda977b3
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-activate-azure-rights-management-from-the-office-365-admin-center-preview"></a>Office 365 관리 센터 미리 보기에서 Azure 권한 관리를 활성화하는 방법

>*적용 대상: Azure Information Protection, Office 365*


새 미리 보기 버전의 Office 365 관리 센터(**Office 365 관리 센터 미리 보기**)를 사용하는 경우에만 다음 지침을 따르세요.

이 버전의 관리 센터는 미리 보기로 제공되고 Azure Rights Management를 Azure Information Protection으로 브랜드를 변경하는 중이므로 이 버전의 관리 센터에 대한 지침은 클래식 버전의 관리 센터에 대한 지침을 사용하는 것보다 안정적이지 않습니다. 이 버전의 관리 센터를 사용할 때 고객에게 서로 다른 옵션이 표시될 수 있습니다.

1. Rights Management가 포함된 Office 365 계획에 등록한 후 Office 365 배포의 전역 관리자인 [회사 또는 학교 계정으로 Office 365에 로그인](https://portal.office.com/)합니다.

2. Office 365 관리 센터가 자동으로 표시되지 않으면 왼쪽 위에서 앱 시작 관리자 아이콘을 선택하고 **관리자**를 선택합니다. **관리자** 타일은 Office 365 관리자에게만 나타납니다.

    > [!TIP]
    > 관리 센터 도움말은 [Office 365 관리 센터 정보 - 관리자 도움말](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)을 참조하세요.

3. **권한 관리** 페이지로 이동하거나 검색 기능을 사용합니다.

    미리 보기 버전을 처음 사용하고 관련 구성 옵션을 확인하면 도움이 되는 경우 이 페이지로 이동하는 것이 좋고 미리 보기 버전에 대해 잘 알고 있고 곧바로 Azure 권한 관리를 활성화려는 경우에는 검색 기능을 사용합니다. 탐색 지침이 표시된 내용과 일치하지 않는 경우 관리 센터의 미리 버전 사용 중에 검색 옵션을 사용해야 할 수도 있습니다.

    - 탐색: **설정** > **서비스 및 추가 기능** > **Microsoft Azure Information Protection** > **Manage Microsoft Azure Information Protection settings**(Microsoft Azure Information Protection 설정 관리)

    - 검색: **홈** 페이지의 검색 상자에 **Information Protection**을 입력하고 검색 결과에서 **Microsoft Azure Information Protection**을 클릭한 다음 **Manage Microsoft Azure Information Protection settings**(Microsoft Azure Information Protection 설정 관리)를 클릭합니다. 검색 결과가 반환되지 않는 경우 **Rights Management**를 입력한 다음 검색 결과에서 **Microsoft Azure rights management settings**(Microsoft Azure Rights Management 설정)를 클릭합니다.

        > [!NOTE]
        >이 옵션으로 이동하는 경우 사용 중인 디스플레이에 따라 이 옵션을 보려면 스크롤해야 할 수 있습니다. 그러나 해당 옵션이 페이지에 나타나지 않고 검색 결과로 표시되지 않으면 서비스 계획에 Azure Information Protection의 Azure Rights Management Service가 포함되지 않은 것일 수 있습니다.
        >
        >Azure Rights Management Service를 활성화하려면 [Azure Information Protection Premium plan](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing)(Azure Information Protection Premium 계획) 또는 [Rights Management가 포함된 Office 365 계획](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)이 있어야 합니다. 이 문제에 대한 도움이 필요한 경우 [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS)으로 전자 메일 메시지를 보내 주세요.

4. **Rights Management** 페이지에서 **활성화**를 클릭합니다.

5. **Rights Management를 활성화하시겠습니까?**라는 메시지가 나타나면 **활성화**를 클릭합니다.

이제 **Rights Management가 활성화되었음** 이 표시되고 비활성화 옵션이 나타납니다.


## <a name="next-steps"></a>다음 단계
[Azure 권한 관리 활성화](activate-service.md)로 돌아갑니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
