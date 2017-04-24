---
title: "개발자 가이드 - AIP"
description: "개발자는 Azure Information Protection을 사용하여 모든 형식의 파일을 보호하고 관리할 수 있습니다."
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 16e2137dead237e59ed1d4db9e88a2a29f9595a9
ms.sourcegitcommit: bf103c02966357eccad0a4912851ceae6937c7b3
translationtype: HT
---
# <a name="azure-information-protection-developers-guide"></a>Azure Information Protection 개발자 가이드

이 가이드에서는 Azure Information Protection의 Rights Management 서비스를 확장하고 해당 서비스와 통합할 수 있는 도구를 소개합니다. 이 가이드는 권한 관리 시스템을 활용하여 광범위한 지원 플랫폼용으로 다양한 유형의 응용 프로그램을 빌드하려는 개발자를 위해 제공됩니다.

>Azure Information Protection SDK의 권한 관리 구성 요소 및 분류/레이블 지정 기능은 현재 개발이 진행 중인 상태입니다.

## <a name="service-applications"></a>서비스 응용 프로그램

서비스 응용 프로그램은 엔터프라이즈 콘텐츠 관리 시스템, 비즈니스 응용 프로그램 또는 클라우드 기반 비즈니스 솔루션에서 내보내는 정보를 보호하는 기능을 제공합니다. 서비스 응용 프로그램의 예로는 DLP(Data Loss Prevention) 및 CAS(Cloud Application Security) 응용 프로그램이 있습니다. 서비스 응용 프로그램 개발용 SDK는 두 가지 프로그래밍 모델을 통해 제공됩니다.

- [C++](https://www.microsoft.com/en-us/download/details.aspx?id=38397)
- [C# 관리되는 API](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>서비스 응용 프로그램의 예

- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)는 DLP RMS 지원 응용 프로그램이 제한된 콘텐츠를 보호 및 사용하기 위해 RMS 파일 API를 사용하여 수행해야 하는 기본 단계를 안내하는 샘플 RMS 지원 DLP 응용 프로그램입니다.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms)은 Azure 응용 프로그램에서 RMS SDK를 사용하여 Azure Blob Storage의 데이터를 보호하는 방법을 보여 주는 샘플입니다.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms)는 파일 시스템의 디렉터리를 감시하고 파일 추가, 파일 수정 등 파일이 변경될 때마다 RMS 보호 정책을 적용하는 Windows 응용 프로그램을 빌드하는 방법을 보여 주는 샘플입니다.
- [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir)는 디렉터리를 입력으로 사용하는 간단한 콘솔 응용 프로그램 샘플이며 재귀를 사용하지 않고 해당 디렉터리의 모든 파일만 보호합니다.

## <a name="powershell-guides"></a>PowerShell 가이드

대개 Azure Rights Management 관리자가 사용하는 이러한 스크립트는 서비스 응용 프로그램을 개발하고 테스트하는 데 유용합니다.

- [Azure Rights Management Cmdlet](https://msdn.microsoft.com/library/azure/dn629398.aspx)은 명령줄에서 Azure RMS를 관리할 수 있도록 합니다. 이 작업은 자동화를 가능하게 하지만 관리 오버헤드를 줄일 수 있도록 안정적이고 반복적인 프로세스를 지원하기도 합니다. 또한, 일부 Azure RMS 고급 구성 및 작업 시에는 Azure PowerShell이 필요합니다.
- [RMS Protection Cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)은 Azure Information Protection의 Azure RMS(Rights Management Services) 데이터 보호 또는 AD RMS(Active Directory Rights Management Services)와 함께 사용될 수 있으며, 이러한 Rights Management 배포에 대한 기타 PowerShell 모듈을 보완할 수 있습니다. 이러한 RMS 보호 cmdlet을 사용하여 모든 파일 형식의 파일을 대량으로 보호하거나 보호 해제합니다.

## <a name="user-applications"></a>사용자 응용 프로그램

RMS SDK 2.1 또는 RMS SDK 4.2를 통해 사용자 응용 프로그램을 빌드할 수 있습니다.
4.2 버전은 iOS/OSX, Android, Linux, Windows 등 널리 사용되는 여러 OS용의 운영 체제별 API를 기반으로 하는 REST 클라이언트입니다. 2.1 버전은 네이티브 Windows 기반 응용 프로그램을 빌드하는 데 사용됩니다.

### <a name="user-application-development-guides"></a>사용자 응용 프로그램 개발 가이드

- [응용 프로그램 배포](developing-your-application.md)
- [응용 프로그램 테스트](how-to-set-up-your-test-environment.md)
- [응용 프로그램 배포](deploying-your-application.md)

### <a name="user-application-samples"></a>사용자 응용 프로그램 샘플

- [AzureIP Test](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test)는 Azure 템플릿 또는 애드혹 정책을 사용하여 문서를 암호화할 수 있는 샘플 콘솔 응용 프로그램입니다.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test)는 각 RMS 지원 응용 프로그램이 제한된 콘텐츠를 보호 및 사용할 때 수행해야 하는 기본 단계를 안내하는 샘플 RMS 지원 응용 프로그램입니다.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms)는 콘텐츠 ID 또는 사용자 권한과 같은 RMS 보호된 파일에 대한 정보를 제공할 수 있는 도구입니다.

## <a name="development-environment-setup"></a>개발 환경 설정

다음 가이드에서는 일반적인 도구를 사용하는 응용 프로그램 개발 환경의 OS별 설정 단계를 안내합니다.

[![iOS/OSX 설정](../media/develop/ios-icon.png)](ios-sdk.md)
[![Android 설정](../media/develop/android-icon.png)](android-sdk.md)
[![Windows Phone 설정](../media/develop/windows-phone-icon.png)](windows-phone-apps.md)
[![Windows Service 설정](../media/develop/windows-icon.png)](install-the-rms-sdk.md)
[![Linux 설정](../media/develop/linux-icon.png)](linux-setup.md)


## <a name="how-tos"></a>방법

다음의 각 항목에서는 응용 프로그램 구현 측면에 대한 구체적인 지침을 제공합니다. 서비스 응용 프로그램은 RMS SDK 2.x를 사용하여 빌드합니다. 사용자 응용 프로그램은 RMS SDK 4.x를 사용하여 빌드합니다. 문서 링크에는 응용 프로그램 유형(서비스, 사용자)이 특성으로 명시되어 있습니다.

### <a name="general"></a>일반

- [문서 추적 및 액세스 권한 해지를 사용하는 방법(서비스)](tracking-content.md)
- [클라이언트를 배포하는 방법](../rms-client/client-deployment-notes.md)
- [서비스 앱을 다른 테넌트에 배포하는 방법] (how-to-deploy-app.md)
- [RMS 서버를 설치 및 구성하는 방법(서비스)](how-to-install-and-configure-an-rms-server.md)
- [문서 추적을 사용하는 방법(사용자)](how-to-use-document-tracking.md)
- [Azure Information Protection에서 대칭 키를 갱신하는 방법](how-to-renew-symmetric-key.md)

### <a name="security-and-authentication"></a>보안 및 인증

- [Azure Active Directory 로그인을 사용하여 App Service 응용 프로그램을 구성하는 방법](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
- [ADAL(Azure Active Directory 인증) 인증을 사용하는 방법](how-to-use-adal-authentication.md)
- [인증용으로 Azure RMS 구성(서비스)](adal-auth.md)
- [API 보안 모드를 설정하는 방법(서비스)](setting-the-api-security-mode-api-mode.md)
- [Azure RMS를 사용하도록 응용 프로그램 설정(서비스)](how-to-use-file-api-with-aadrm-cloud.md)
- [Azure AD를 통해 앱을 등록하고 앱이 RMS를 사용하도록 설정하는 방법(사용자)](authentication-integration.md)

### <a name="configuration-and-performance-management"></a>구성 및 성능 관리

- [명시적 소유자 권한을 추가하는 방법(서비스)](add-explicit-owner-rights.md)
- [파일 API 구성(서비스)](file-api-configuration.md)
- [기본 제공 권한을 사용하는 방법(사용자)](built-in-rights-usage-restriction-reference.md)
- [오류 및 성능 로깅을 사용하도록 설정하는 방법(사용자)](enabling-logging.md)

## <a name="videos"></a>동영상

Microsoft의 Dan Plastina가 제공하는 [Azure Information Protection 소개](https://www.microsoft.com/cloud-platform/azure-information-protection)를 확인해 보세요.

이러한 비디오는 Micorsoft 2016 Ignite 컨퍼런스에서 소개되었던 내용입니다.

- [조직 내의 전자 메일 보안](https://myignite.microsoft.com/videos/2787)
- [Adopt a comprehensive identity-driven solution for protecting and sharing data securely](https://myignite.microsoft.com/videos/2784)(데이터를 안전하게 보호 및 공유하기 위한 포괄적인 ID 기반 솔루션 채택)
- [Learn how classification, labeling, and protection delivers persistent data protection](https://myignite.microsoft.com/videos/2786)(분류, 레이블 지정 및 보호를 통해 지속적인 데이터 보호를 제공하는 방법 알아보기)

## <a name="other-resources"></a>관련 자료

- [보안 모범 사례 가이드](security-guidelines.md)
- [RMS 개발자 코너(블로그)](https://blogs.msdn.microsoft.com/rms/)
- [Azure Information Protection 질문과 대답](https://docs.microsoft.com/en-us/information-protection/get-started/faqs)

### <a name="support-articles"></a>지원 문서

- [지원되는 파일 형식](supported-file-formats.md)
- [지원되는 플랫폼](supported-platforms.md)
- [사용 제한 이해](understanding-usage-restrictions.md)

### <a name="api-reference"></a>API 참조

- [Windows API 참조](https://msdn.microsoft.com/en-us/library/hh535292.aspx)
  - [Windows SDK 오류 코드](https://msdn.microsoft.com/library/hh535248.aspx)
- [Windows Phone 및 Windows 스토어 API 참조](https://msdn.microsoft.com/library/dn891914.aspx)
- [iOS/OSX API 참조](https://msdn.microsoft.com/en-us/library/dn758306.aspx)
- [Android API 참조](https://msdn.microsoft.com/en-us/library/dn758245.aspx)
- [Linux API 참조](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>이전 버전

- [AD RMS SDK](https://msdn.microsoft.com/en-us/library/cc530379.aspx)는 RMS SDK의 첫 번째 버전입니다.
- [AD RMS 스크립팅 도구](https://msdn.microsoft.com/en-us/library/bb968797.aspx)는 AD RMS 설치용 관리 도구입니다.

### <a name="see-also"></a>참고 항목

- [개발자 관련 용어](terms.md)
- [Azure Information Protection 용어 - ITPro](../get-started/terminology.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]