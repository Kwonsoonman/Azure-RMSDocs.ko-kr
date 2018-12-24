---
title: 시작 | Azure RMS
description: RMS SDK 2.1 플랫폼을 사용하면 개발자가 RMS 정보 보호를 활용하는 애플리케이션을 빌드할 수 있습니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 43e63165fcf8c19760a9f82619a02923ba55e97e
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266344"
---
# <a name="getting-started"></a>시작하기

권한 관리 서비스 SDK 2.1 플랫폼을 사용하면 개발자가 RMS 서버 또는 Azure RMS를 통해 RMS 정보 보호를 활용하는 응용 프로그램을 빌드할 수 있습니다. 이 플랫폼은 키 관리, 암호화 및 암호 해독 처리와 같은 복잡한 보안 사례를 처리하고 쉬운 응용 프로그램 개발을 위해 간소화된 API를 제공합니다.

## <a name="get-started-with-rmssdk21"></a>RMS SDK 2.1 시작

이 항목에서는 테스트 환경에서 권한 사용 응용 프로그램을 설정하고 실행하는 과정을 안내합니다. 다음 항목은 개발 환경을 설정하는 방법을 설명하며, 작업을 수행하는 순서를 제안하도록 나열되어 있습니다.

## <a name="in-this-sections"></a>이 섹션의 내용

| 항목 | 설명 |
|-------|-------------|
| [릴리스 정보](release-notes-rtm.md) | 이 항목에는 이 릴리스와 이전 릴리스의 RMS SDK 2.1에 대한 중요한 정보가 포함되어 있습니다.|
| [SDK 설치](install-the-rms-sdk.md) | 이 항목에서는 개발자 도구를 설치하는 과정을 안내합니다.|
| [Visual Studio 구성](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) | 이 항목에서는 RMS SDK 2.1을 사용하도록 Visual Studio 프로젝트를 구성하는 방법에 대한 지침을 제공합니다.|
| [응용 프로그램 배포](developing-your-application.md) | 이 항목은 RMS 사용 응용 프로그램의 핵심 측면에 대한 중요 지침을 제공하며, 고유한 응용 프로그램 개발의 기반 역할을 할 수 있습니다.|
| [응용 프로그램 테스트](how-to-set-up-your-test-environment.md) |이 항목에서는 응용 프로그램 테스트를 위해 설치하는 방법에 대한 지침을 제공합니다.|
| [프로덕션 환경에 배포](deploying-your-application.md) |이 항목에서는 권한 사용 응용 프로그램에 대한 배포 옵션을 안내합니다.|


다음 항목의 지침에 따라 RMS SDK 2.1을 사용해 보세요.

- [SDK 설치](install-the-rms-sdk.md)
- [Visual Studio 구성](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
- [응용 프로그램 배포](developing-your-application.md)
- [응용 프로그램 테스트](how-to-set-up-your-test-environment.md)
- [프로덕션 환경에 배포](deploying-your-application.md)

### <a name="why-use-rmssdk21-for-protecting-your-content"></a>콘텐츠를 보호하기 위해 RMS SDK 2.1을 사용하는 이유

새 애플리케이션과 기존 애플리케이션에 RMS 지원을 추가하려는 개발자는 RMS SDK 2.1을 사용하여 다음 작업을 보다 쉽게 수행할 수 있습니다.

-   관리 가능하고 강력한 규격 RMS 인식 응용 프로그램을 작성합니다.
-   사용자 데이터를 영구적으로 암호화합니다. 환경, 디바이스 또는 운영 체제에 관계없이 데이터가 암호화된 상태로 유지됩니다.
-   중요한 데이터의 화면 캡처 방지와 같은 다양한 사용 제한을 적용합니다.
-   엔터프라이즈 관리 보호 정책을 지원합니다.
-   새로운 인증 메커니즘 및 암호화 알고리즘이 제공되면 지원합니다.

RMS SDK 2.1에서는 다양한 중요 클라이언트 및 서버 플랫폼을 지원합니다. 자세한 내용은 [지원되는 플랫폼](supported-platforms.md)을 참조하세요.

## <a name="core-principles"></a>핵심 원칙

**단순성** - AD RMS SDK 1.0에 대한 피드백 및 사용 패턴을 분석하고 해당 데이터를 사용하여 가장 어려운 프로그래밍 작업을 간소화 또는 자동화했습니다. RMS SDK 2.1을 사용하여 작성된 RMS 응용 프로그램에서는 일반적으로 AD RMS SDK 1.0을 사용하여 작성된 RMS 응용 프로그램보다 필요한 RMS 코드 줄이 5-10배 정도 줄었습니다.
**한 번 작성** - 최신 RMS 기능을 사용하기 위해 RMS SDK 2.1 응용 프로그램에서 코드 변경이나 재컴파일을 수행할 필요가 없습니다. 새로운 RMS 기능이 RMS 서버에 추가되면 기존 응용 프로그램에서 바로 사용할 수 있습니다.
**일관성** - RMS SDK 2.1을 사용하면 다양한 RMS 구성을 일관되게 적용하는 응용 프로그램을 쉽게 작성할 수 있습니다. 응용 프로그램 개발자가 작성해야 하는 RMS 사용자 인터페이스도 훨씬 감소하므로 일관된 모양과 느낌이 장려되고 사용자 교육의 필요성이 줄어듭니다.

## <a name="related-topics"></a>관련 항목

* [RMS 개발자 가이드](developers-guide.md)