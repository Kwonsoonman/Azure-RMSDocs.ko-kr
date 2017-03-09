---
title: "개요 - RMS SDK 2.1 | Azure RMS"
description: "RMS(권한 관리 서비스)는 디지털 정보가 무단으로 사용되지 않도록 보호하는 정보 보호 기술입니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: f41640a0a6c46dc7cacf69dc3784d703b971e9d0


---

# <a name="overview"></a>개요

권한 관리 서비스 SDK 2.1은 디지털 정보의 무단 사용을 방지하는 정보 보호 기술입니다. 권한 사용 응용 프로그램을 통해 콘텐츠 소유자는 콘텐츠를 열거나 수정, 인쇄, 전달하거나 다른 작업을 수행할 수 있는 사람을 정의할 수 있습니다.

AD RMS는 [서버](ad-rms-server.md) 및 [클라이언트](ad-rms-client.md) 구성 요소 둘 다로 이루어져 있습니다. Azure 또는 Windows Server에서 실행하는 서버는 여러 웹 서비스로 구성됩니다.

[클라이언트](ad-rms-client.md) 구성 요소는 클라이언트 또는 서버 운영 체제에서 실행할 수 있으며, 응용 프로그램이 콘텐츠를 암호화하고 암호 해독하고, 템플릿 및 해지 목록을 검색하고, 서버에서 라이선스 및 인증서를 획득하고, 기타 관련된 권한 관리 작업을 수행할 수 있도록 하는 기능을 포함합니다.

자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

권한 관리 서비스 SDK 2.1을 기반으로 빌드된 응용 프로그램을 적용할 수 있는 몇 가지 시나리오는 다음과 같습니다.

-   법률 회사가 중요한 메일 메시지를 인쇄하거나 전달하지 못하게 하려고 합니다.
-   컴퓨터 보조 디자인 및 제조 소프트웨어 개발자가 암호 사용을 요구하지 않고 도면 액세스 권한을 연구 부서 내의 소규모 사용자 그룹으로 제한하려고 합니다.
-   그래픽 디자인 웹 사이트의 소유자가 이미지의 저해상도 복사본에 대해서는 무료 보기를 허용하지만 고해상도 버전에 액세스할 때는 요금을 지불해야 하는 단일 라이선스를 사용하려고 합니다.
-   온라인 문서 라이브러리의 소유자가 사용자의 ID에 따라 문서를 보거나 인쇄 또는 편집할 수 있는 권한을 설정하려고 합니다.
-   회사에서 보기 및 편집 권한을 특정 사용자로 제한하는 내부 웹 사이트에 중요한 직원 정보를 게시하려고 합니다.

AD RMS 서버, AD RMS 클라이언트 및 해당 기능에 대한 자세한 내용은 [AD RMS에 대한 IT 전문가 설명서](https://TechNet.Microsoft.Com/library/cc771234.aspx)의 TechNet 콘텐츠를 참조하세요.

이 섹션의 나머지 항목에서는 RMS 아키텍처 및 구현 과정을 다룹니다.

## <a name="in-this-section"></a>섹션 내용

| 항목 | 설명 |
|-------|-------------|
|[클라이언트](ad-rms-client.md) |이 항목에서는 Rights Management Service Client 2.1의 용도와 기능에 대해 설명합니다. |
|[서버](ad-rms-server.md) | 이 항목에서는 Azure 및 Windows Server용 RMS 서버의 용도와 기능에 대해 설명합니다.|


## <a name="related-topics"></a>관련 항목

* [RMS 개념](application-types.md)
* [시작](getting-started-with-ad-rms-2-0.md)
* [IT Pro documentation for AD RMS](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)(AD RMS에 대한 IT 전문가 설명서)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


