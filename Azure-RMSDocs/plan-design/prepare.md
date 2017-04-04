---
title: "Azure Rights Management 보호 준비 - AIP"
description: "조직에서 문서 및 전자 메일을 보호할 수 있도록 Azure Rights Management 서비스를 사용할 준비가 완료되었는지 확인하세요."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4b074f9a9a3d72b4d1ab5810b69e92b4792b0711
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="preparing-for-azure-information-protection"></a>Azure Information Protection 준비

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection을 조직에 배포하기 전에 다음 사항이 준비되어 있는지 확인하세요.

-   수동으로 만들거나 AD DS(Active Directory 도메인 서비스)에서 자동으로 만들어져 동기화된 사용자 계정 및 그룹이 클라우드에 있습니다.

    온-프레미스 계정 및 그룹을 동기화할 때 모든 특성을 동기화할 필요는 없습니다. Azure Information Protection에서 사용되는 Azure Rights Management 서비스에 대해 동기화해야 하는 특성 목록은 Azure Active Directory 설명서에서 [Azure RMS 섹션](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms)을 참조하세요. 쉽게 배포하기 위해 [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis)를 사용하여 온-프레미스 디렉터리와 Azure Active Directory를 연결하는 것이 좋습니다. 하지만 동일한 결과를 달성하는 모든 디렉터리 동기화 방법을 사용할 수 있습니다.

-   Azure Information Protection에 사용할 메일 사용 가능 그룹이 클라우드에 있습니다. 그룹은 기본 제공될 수도 있고, 보호된 문서 및 전자 메일을 이용할 사용자가 포함된 그룹을 수동으로 만들 수도 있습니다.

    Exchange Online이 있는 경우 Exchange 관리 센터를 사용하여 메일 사용 가능 그룹을 만들고 사용할 수 있습니다. AD DS에서 Azure AD로 동기화하는 경우 보안 그룹 또는 배포 그룹 중 하나인 메일 사용 가능 그룹을 만들고 사용할 수 있습니다.

### <a name="group-membership-caching"></a>그룹 구성원 자격 캐싱

성능상의 이유로 Azure Rights Management 서비스에서 그룹 구성원이 캐시됩니다. 즉, 그룹 구성원 자격의 변경 내용이 적용되는 데 최대 3시간이 걸릴 수 있으며 이 시간은 변경될 수 있습니다. [사용자 지정 템플릿](../deploy-use/configure-custom-templates.md)을 구성하거나 [슈퍼 사용자 기능](../deploy-use/configure-super-users.md)에 대해 그룹을 사용하는 경우처럼 변경 적용에 따른 지연 시간 또는 Azure Rights Management 서비스 구성에서 그룹을 사용할 때 수행하는 테스트로 인한 지연 시간을 고려하세요. 

### <a name="considerations-if-email-addresses-change"></a>메일 주소를 변경하는 경우 고려할 사항

사용자 또는 그룹에 대한 사용 권한을 구성하고 표시 이름별로 선택하면 해당 개체의 메일 주소가 저장되고 사용됩니다. 나중에 메일 주소를 변경하면 선택한 사용자에게 권한이 부여되지 않습니다.

메일 주소를 변경하는 경우 기존 메일 주소를 프록시 메일 주소(별칭 또는 암호 확인용 메일이라고도 함)로 사용자 또는 그룹에 추가하여 이전에 할당된 해당 사용 권한이 유지되도록 하는 것이 좋습니다. 이렇게 할 수 없는 경우 새로 보호되는 콘텐츠에서 새 메일 주소를 사용하도록 구성에서 사용자 또는 그룹을 제거하고 업데이트된 메일 주소를 다시 저장하도록 선택해야 합니다.

사용자 지정 Rights Management 템플릿은 표시 이름별로 사용자 또는 그룹을 선택하여 사용 권한을 할당할 수 있는 한 예입니다. 사용자는 Azure Information Protection 클라이언트로 사용자 지정 권한을 구성할 때 표시 이름별로 사용자 및 그룹을 선택할 수도 있습니다.

## <a name="activate-the-rights-management-service-for-data-protection"></a>데이터 보호를 위해 Rights Management 서비스 활성화
문서 및 전자 메일 보호를 시작할 준비가 되면 이 기술을 사용할 수 있도록 Rights Management 서비스를 활성화합니다. 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


