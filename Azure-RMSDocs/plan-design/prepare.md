---
title: "Azure Rights Management 보호 준비 | Azure Information Protection"
description: "조직에서 문서 및 전자 메일을 보호할 수 있도록 Azure Rights Management 서비스를 사용할 준비가 완료되었는지 확인하세요."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 46db6ef6f65a06c42909252cf99884cc5eaaefe4
ms.openlocfilehash: 5a3df821c70b8cd308f8fb8cc94ee0cff069a3d9


---

# Azure Information Protection 준비

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection을 조직에 배포하기 전에 다음 사항이 준비되어 있는지 확인하세요.

-   수동으로 만들거나 AD DS(Active Directory 도메인 서비스)에서 자동으로 만들어져 동기화된 사용자 계정 및 그룹이 클라우드에 있습니다.

    온-프레미스 계정 및 그룹을 동기화할 때 모든 특성을 동기화할 필요는 없습니다. Azure Information Protection에서 사용되는 Azure Rights Management 서비스에 대해 동기화해야 하는 특성 목록은 Azure Active Directory 설명서에서 [Azure RMS 섹션](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms)을 참조하세요. 쉽게 배포하기 위해 [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis)를 사용하여 온-프레미스 디렉터리와 Azure Active Directory를 연결하는 것이 좋습니다. 하지만 동일한 결과를 달성하는 모든 디렉터리 동기화 방법을 사용할 수 있습니다.

-   Azure Information Protection에 사용할 메일 사용 가능 그룹이 클라우드에 있습니다. 그룹은 기본 제공될 수도 있고, 보호된 문서 및 전자 메일을 이용할 사용자가 포함된 그룹을 수동으로 만들 수도 있습니다.

    Exchange Online이 있는 경우 Exchange 관리 센터를 사용하여 메일 사용 가능 그룹을 만들고 사용할 수 있습니다. AD DS에서 Azure AD로 동기화하는 경우 보안 그룹 또는 배포 그룹 중 하나인 메일 사용 가능 그룹을 만들고 사용할 수 있습니다.

## 데이터 보호를 위해 Rights Management 서비스 활성화
문서 및 전자 메일 보호를 시작할 준비가 되면 이 기술을 사용할 수 있도록 Rights Management 서비스를 활성화합니다. 자세한 내용은 [Azure 권한 관리 활성화](../deploy-use/activate-service.md)를 참조하세요.






<!--HONumber=Sep16_HO4-->


