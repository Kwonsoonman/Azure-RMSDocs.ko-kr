---
title: "Azure Information Protection SDK 2.1 개발자 지침 | Microsoft Docs"
description: "AIP SDK 2.1 개발 방법에 대한 도움말 항목 컬렉션"
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3b56c14d4ec1faf940e8b7d350d2680625cac795
ms.openlocfilehash: 268d474e11f70961263b1cbbcc5eca926e880416
ms.lasthandoff: 02/28/2017


---

# <a name="developer-guidance"></a>개발자 지침

이 섹션에서는 이 SDK를 사용하여 개발하는 방법에 대한 일반 정보뿐만 아니라 몇 가지 중요한 개발 시나리오에 대한 구체적인 지침을 다룹니다. 이 섹션의 시나리오는 이 릴리스의 권한 관리 서비스 SDK 2.1에만 해당하며, 후속 릴리스에서 변경될 수 있습니다.
- [방법: ADAL 인증 사용](how-to-use-adal-authentication.md) -Azure ADAL(Active Directory 인증 라이브러리)을 사용하여 Azure RMS에서 앱을 인증합니다.
- [방법: 명시적 소유자 권한 추가](add-explicit-owner-rights.md) - 라이선스를 처음부터 만드는 경우([IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)) 응용 프로그램에서 "소유자" 권한을 명시적으로 추가해야 합니다.
- [방법: 권한 사용 응용 프로그램 디버그](debugging-applications-that-use-ad-rms.md) - 이 항목에서는 응용 프로그램을 디버그하고 Windows 이벤트 로그를 사용하는 방법을 보여 줍니다.
- [방법: 고객의 테넌트에 앱 배포](how-to-deploy-app.md) - 개발 Azure AD 테넌트에서 프로덕션 Azure AD 테넌트로 앱을 배포하는 단계를 간략하게 설명합니다.
- [방법: 문서 추적 및 해지 사용](tracking-content.md) - 이 항목에서는 콘텐츠의 문서 추적과 메타데이터 업데이트에 대한 예제 코드를 구현하고, 앱에 대한 **사용 추적** 단추를 만들기 위한 기본 지침을 다룹니다.
- [방법: 메일 알림 사용](how-to-enable-email-notification.md) - 메일 알림을 사용하면 누군가가 보호된 콘텐츠에 액세스할 경우 보호된 콘텐츠 소유자가 알림을 받을 수 있습니다.
- [방법: 서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md) - 이 항목에서는 Azure 권한 관리를 사용하도록 서비스 응용 프로그램을 설정하는 단계를 간략하게 설명합니다.
- [방법: RMS 서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md) - 이 항목에서는 권한 사용 응용 프로그램 테스트에 사용할 RMS 서버 또는 Azure RMS에 연결하는 단계를 설명합니다.
- [방법: API 보안 모드 설정](setting-the-api-security-mode-api-mode.md) - [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) 함수를 사용하여 파일 API 응용 프로그램이 실행되는 보안 모드를 선택할 수 있습니다.
- [방법: 암호화 설정 작업](working-with-encryption.md) - 이 항목에서는 암호화 패키지에 대해 설명하고 사용과 관련된 몇 가지 코드 조각을 보여 줍니다.
- [응용 프로그램 종류](application-types.md) - 이 항목에서는 권한 사용 응용 프로그램으로 만들도록 선택할 수 있는 응용 프로그램 종류에 대해 설명합니다.
- [파일 API 구성](file-api-configuration.md) - 레지스트리 설정을 통해 파일 API의 동작을 구성할 수 있습니다.
- [보안 지침](security-guidelines.md) - 응용 프로그램 개발자가 AIP 에코 시스템 내에서 제 역할을 하도록 하기 위한 예비 교육과 지침을 제공합니다.
- [지원되는 파일 형식](supported-file-formats.md) - 파일 API는 원시 형식과 Pfile 형식을 지원합니다.
- [지원되는 플랫폼](supported-platforms.md) - 이 항목에서는 RMS SDK 2.1 지원 클라이언트 및 서버 플랫폼을 식별합니다.
- [사용 제한 이해](understanding-usage-restrictions.md) - 모든 RMS 사용 응용 프로그램에는 이 항목에 나열된 상수로 정의되는 사용 제한을 적용해야 합니다.

 
## <a name="related-topics"></a>관련 항목
* [개요](ad-rms-overview.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
