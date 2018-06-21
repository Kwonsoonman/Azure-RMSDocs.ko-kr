---
title: 개요 - RMS SDK 4.2 | Azure RMS
description: AD RMS 및 Azure RMS는 디지털 정보가 무단으로 사용되지 않도록 보호하는 정보 보호 기술입니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 9c142de580e6e77c0f1c84f12d60158f11751c15
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2018
ms.locfileid: "30258822"
---
# <a name="overview"></a>개요

Microsoft Rights Management SDK 4.2는 여러 플랫폼에서 사용할 수 있는 정보 보호 기술이며,  클라이언트 컴퓨터 및 장치에서 "권한 사용" 응용 프로그램을 통해 전송되는 정보에 대한 액세스 및 사용을 보호할 수 있도록 설계된 SDK(소프트웨어 개발자 키트) 또는 프레임워크를 제공합니다. 이러한 플랫폼용 SDK는 응용 프로그램 개발자에게 디지털 콘텐츠 보호 또는 사용, 템플릿 검색, 서버에서 정책 가져오기 및 기타 관련된 권한 관리 작업을 위한 간단한 API를 제공합니다.

현재 지원되는 플랫폼에 대한 자세한 내용은 [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)에 대한 개발자 설명서 포털을 참조하세요.

다음은 가능한 시나리오 중 일부일 뿐입니다.

-   법률 회사가 모바일 장치에서 중요한 메일 메시지를 인쇄하거나 전달하지 못하게 하려고 합니다.
-   컴퓨터 보조 디자인 및 제조 소프트웨어 개발자가 암호 사용을 요구하지 않고 도면 액세스 권한을 연구 부서 내의 소규모 사용자 그룹으로 제한하려고 합니다.
-   그래픽 디자인 모바일 앱의 소유자가 이미지의 저해상도 복사본에 대해서는 무료 보기를 허용하지만 고해상도 버전에 액세스할 때는 요금을 지불해야 하는 단일 라이선스를 사용하려고 합니다.
-   온라인 문서 라이브러리의 소유자가 모바일 장치로 문서를 다운로드할 때 사용자의 ID에 따라 문서를 보거나 인쇄 또는 편집할 수 있는 권한을 설정하려고 합니다.
-   회사에서 보기 및 편집 권한을 특정 사용자로 제한하는 내부 웹 사이트에 중요한 직원 정보를 게시하려고 합니다.

MS RMS SDK 4.2는 사용권 계약의 승인 및 동의를 통해 다운로드할 수 있으며, 타사 소프트웨어와 함께 무료로 배포되어 사용자 환경이나 Azure RMS 서비스에서 AD RMS 서버를 사용 및 배포하여 권한이 보호된 콘텐츠를 클라이언트가 액세스할 수 있게 합니다. 자세한 내용은 [시작](get-started.md)을 참조하세요.

## <a name="sdk-highlights"></a>SDK의 주요 내용


MS RMS SDK 4.2에서는 다음을 포함하여 새로운 몇 가지 멋진 기능을 제공합니다.

-   **다시 디자인된 API** – MS RMS SDK 4.2 API는 최대한 단순하게 다시 디자인되어, 개발자가 최소한의 노력으로 일관된 RMS 동작을 제공하는 간단하고 투명한 암호화 및 암호 해독 API를 이용할 수 있습니다.
-   **AD RMS 및 Azure RMS에 대한 하이브리드 지원** – 단일 RMS 사용 앱이 AD RMS 서버(AD RMS의 모바일 장치 확장 사용) 및 Azure RMS 서비스 둘 다의 콘텐츠를 사용하고 보호할 수 있습니다. MS RMS SDK 4.2에서는 IT 관리자가 구성할 수 있는 관련 끝점을 투명하게 검색합니다.
-   **사용자 고유의 인증 라이브러리 가져오기** – 앱 개발자가 MS RMS SDK 4.2에서 사용할 인증 라이브러리를 선택할 수 있습니다. [Azure AD 인증 라이브러리](https://msdn.microsoft.com/library/jj573266.aspx)든, 조직의 사용자 지정 라이브러리든 관계없이 MS RMS SDK 4.2에서 인증 스택을 분리하므로 요구에 가장 맞는 라이브러리를 선택할 수 있습니다.
-   **고유한 사용자 인터페이스 가져오기** - 이제 MS RMS SDK 4.2를 사용하여 사용자 지정 사용자 인터페이스를 구현할 수 있습니다. 콘텐츠 보호 및 템플릿 선택에서 보호된 콘텐츠를 사용하는 동안 사용 권한 표시 및 변경에 이르기까지 MS RMS SDK 4.2에서는 앱에 기본 제공 UI를 적용하지 않습니다. 하지만 원하는 경우 [GitHub 계정](https://github.com/AzureAD/)을 통해 모든 플랫폼에 Microsoft RMS UI를 사용할 수 있습니다.
-   **오프라인으로 보호된 콘텐츠 액세스** – MS RMS SDK 4.2를 사용하면 앱 사용자가 인터넷 연결이 없는 경우에도 보호된 콘텐츠에 액세스할 수 있습니다. MS RMS SDK 4.2에서는 보호된 콘텐츠의 사용 정책을 안전하게 캐시하므로 사용자가 오프라인으로 RMS 보호된 데이터에 액세스할 수 있습니다.

[시작](get-started.md) 가이드를 사용하여 보호된 정보 장치 앱 프로젝트를 시작합니다.

## <a name="related-topics"></a>관련 항목

* [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [시작](get-started.md)
* [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx)(Azure AD 인증 라이브러리)
* [GitHub 계정](https://github.com/AzureAD/)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]