---
title: Azure Information Protection에 대한 규정 준수 및 정보
description: 법적 정보, 규정 준수, SLA를 포함하는 Azure Information Protection 관련 지원 정보입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/12/2018
ms.topic: article
ms.service: information-protection
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fc19bade41279b399f11116b0bd692a1632f6c5a
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42803051"
---
# <a name="compliance-and-supporting-information-for-azure-information-protection"></a>Azure Information Protection에 대한 규정 준수 및 지원 정보

Azure Information Protection은 다른 서비스를 지원하는 동시에 다른 서비스가 있어야 작동합니다. Azure Information Protection 관련 정보를 찾고 있지만 Azure Information Protection 서비스를 사용하는 방법에 대해서는 알아보지 않으려는 경우 다음 리소스를 확인하세요.

## <a name="suitability-for-different-countries"></a>다양한 국가의 적합성

다양한 국가의 법률과 규정 간의 가변성, 다양한 사용 사례와 시나리오 및 다양한 비즈니스 섹터 간의 다양한 요구 사항으로 인해 Information Protection이 사용자의 국가에 적합한지 대답하는 데 도움을 줄 수 있는 법률 고문과 상의해야 합니다.

그러나 법적 관리자를 도울 수 있는 몇 가지 관련 정보는 다음을 결정합니다.

- Azure Information Protection은 AES 256 및 AES 128을 사용하여 문서를 암호화합니다. [추가 정보](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Azure Information Protection에서 사용하는 모든 암호화 키는 RSA 2048비트를 사용하는 고객 관련 루트 키로 보호됩니다. 하지만 RSA 1024는 이전 버전과 호환성을 지원합니다. [추가 정보](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- "BYOK([bring your own key](plan-implement-tenant-key.md))"를 사용하여 고객 관련 루트 키가 Microsoft에서 관리되거나 Thales HSM의 고객에 프로비전됩니다. 또한 클라우드 기반 키를 사용하여 보호되어야 함을 나타내는 요구 사항에 영향을 받는 콘텐츠의 경우 Azure Information Protection은 "HYOK([hold your own key](configure-adrms-restrictions.md))"를 사용하여 온-프레미스 키에서 제한된 기능을 지원합니다.

- Azure Information Protection 서비스는 전 세계 지역 데이터 센터에서 호스팅됩니다. Azure Information Protection 키 및 정책은 원래 배포된 지역 내에 항상 남아 있습니다.
 
- Azure Information Protection은 문서 콘텐츠를 클라이언트에서 Azure Information Protection 서비스로 전송하지 않습니다. 클라이언트 장치에서 콘텐츠 암호화 및 암호 해독 작업이 수행됩니다. 또는 이러한 작업은 서비스 기반 렌더링을 위해 콘텐츠를 렌더링하는 서비스 내에서 수행됩니다. [추가 정보](./how-does-it-work.md)

## <a name="legal-and-privacy"></a>법적 정보 및 개인 정보 보호

- Microsoft Azure 계약 정보: [Microsoft Azure 계약](http://azure.microsoft.com/support/legal/subscription-agreement/)

- Microsoft Azure 개인 정보 보호: [Microsoft Azure 개인 정보 취급 방침](http://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>보안, 규정 준수 및 감사

Azure Rights Management 서비스의 특정 인증에 대한 자세한 내용은 [Azure RMS를 통해 해결할 수 있는 문제](./azure-rms-problems-it-solves.md) 문서의 [보안, 준수 및 규정 요구 사항](./azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) 섹션을 참조하세요. 또한,

- Azure Information Protection 외부 인증: [Microsoft Azure 보안 센터](http://azure.microsoft.com/support/trust-center/)

- FIPS 140 정보: [FIPS 140 유효성 검사](https://technet.microsoft.com/library/security/cc750357.aspx)

보호 기술이 작동하는 방법에 대한 심층적인 기술 정보는 [Azure RMS는 어떤 방식으로 작동합니까?](./how-does-it-work.md)를 

## <a name="service-level-agreements"></a>서비스 수준 계약

- [Azure Information Protection에 대한 SLA](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [Azure Active Directory에 대한 SLA](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [Azure Key Vault에 대한 SLA](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>문서

- Azure Active Directory 설명서: [Azure Active Directory](/active-directory/)

- Office 365 라이브러리: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

