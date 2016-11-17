---
title: "개발자 가이드 | Azure RMS"
description: "개발자 도구 사용의 개요, SDK, 추가 라이브러리 및 코드 예제입니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a22e6bd0-8ce8-45b4-9a32-273126ab831e
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 84072c64f83ec97ac41d6ec030be5eabff263b4b
ms.openlocfilehash: 366652cbf38c1215f73e6996edd54829170ba4c5


---

# <a name="developers-guide"></a>개발자 가이드

## <a name="overview"></a>개요 ##
이 가이드에서는 Rights Management SDK의 제품군과, 모든 지원되는 플랫폼에 걸쳐 있는 도구 및 코드 샘플의 증가하는 집합을 간략히 설명합니다.

## <a name="software-development-kits"></a>소프트웨어 개발 키트 ##
다음 표에 나와 있는 RMS SDK의 3개 세대를 사용할 수 있습니다.

| SDK | 설명 |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Microsoft Rights Management Services를 통해 Android, iOS, Mac OS X, Windows Phone/RT 및 Linux/C++ 장치 앱이 정보 보호를 사용할 수 있도록 하는 간단한 개발 환경을 제공하는 간소화된 차세대 도구 집합입니다. |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Windows 데스크톱 응용 프로그램 개발자와 서버 기반 솔루션 공급자가 해당 제품에서 권한 관리를 사용할 수 있도록 하는 강력한 SDK 제품입니다.|
|[AD RMS SDK](https://msdn.microsoft.com/library/cc530379.aspx)|** 참고 ** - 클라이언트가 Msdrm.dll에 노출하는 기능을 활용하는 AD RMS SDK는 Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 및 Windows Vista에서 사용할 수 있습니다. 이후 버전에서는 변경되거나 제공되지 않을 수 있습니다. 클라이언트가 Msipc.dll에 노출하는 기능을 활용하는 Microsoft Rights Management Services SDK 2.1을 대신 사용합니다.|
|[AD RMS Scripting API](https://msdn.microsoft.com/en-us/library/bb968797.aspx)(AD RMS 스크립팅 API)| AD RMS 설치를 관리할 스크립트를 만드는 데 사용됩니다.|

## <a name="powershell-guidance"></a>PowerShell 지침

[Azure Rights Management Cmdlet](https://msdn.microsoft.com/library/azure/dn629398.aspx)은 명령줄에서 Azure RMS를 관리할 수 있도록 합니다. 이 작업은 자동화를 가능하게 하지만 관리 오버헤드를 줄일 수 있도록 안정적이고 반복적인 프로세스를 지원하기도 합니다. 또한, 일부 Azure RMS 고급 구성 및 작업 시에는 Azure PowerShell이 필요합니다.

[RMS Protection Cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx)은 Azure Information Protection의 Azure RMS(Rights Management Services) 데이터 보호 또는 AD RMS(Active Directory Rights Management Services)와 함께 사용될 수 있으며, 이러한 Rights Management 배포에 대한 기타 PowerShell 모듈을 보완할 수 있습니다. 이러한 RMS 보호 cmdlet을 사용하여 모든 파일 형식의 파일을 대량으로 보호하거나 보호 해제합니다.

## <a name="code-samples-and-tools"></a>코드 샘플 및 도구
이 Microsoft 제공 RMS 코드 샘플 및 개발자 지원 도구 컬렉션은 지원되는 모든 운영 체제(Android, iOS/OS X, Windows Phone 및 Windows 데스크톱)에 걸쳐 있으며, 지원되는 SDK와의 호환성을 유지하기 위해 정기적으로 업데이트됩니다.

### <a name="android"></a>Android

다음은 [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK에서 지원하는 Android에서 실행됩니다.

- GitHub의 [UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-android)은 빨리 시작하고 앱에서 표준 UI를 다시 사용할 수 있게 해줍니다.
- Java의 [Android 사용 시나리오](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx)는 RMS SDK를 익히는 데 중요한 개발 시나리오를 나타냅니다. 예를 들어 Microsoft 보호된 파일 형식, 사용자 지정 보호된 파일 형식 및 사용자 지정 UI 컨트롤 사용이 포함됩니다.

### <a name="ios-os-x"></a>iOS/OS X

다음은 [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK에서 지원하는 iOS/OS X에서 실행됩니다.

- Objective C의 [iOS/OS X 사용 시나리오](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx)는 RMS SDK를 익히는 데 중요한 개발 시나리오를 나타냅니다. 예를 들어 Microsoft 보호된 파일 형식, 사용자 지정 보호된 파일 형식 및 사용자 지정 UI 컨트롤 사용이 포함됩니다.
- GitHub의 [UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-ios)은 빨리 시작하고 앱에서 표준 UI를 다시 사용할 수 있게 해줍니다. **iOS에서만** 지원됩니다.

### <a name="windows-desktop"></a>Windows 데스크톱

다음은 [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK에서 지원하는 Windows 데스크톱에서 실행됩니다.

- [PFILE 보호된 PDF 읽기](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/)는 RMS 개발자 코너 블로그에 있는 간단한 코드 예제로, MSIPC 파일 API를 사용하여 PFILE 보호된 PDF 문서의 암호를 해독하고 엽니다.
- [IpcManagedAPI](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)는 관리되는 응용 프로그램에서 쉽게 RMS를 사용할 수 있도록 하는 RMS SDK 2.1의 .NET(C#) 표현입니다.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcNotepad)는 각 RMS 사용 응용 프로그램이 제한된 콘텐츠를 보호 및 사용할 때 수행해야 하는 기본 단계를 안내하는 샘플 RMS 사용 응용 프로그램입니다.
- [IpcDlp](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp)는 DLP RMS 사용 응용 프로그램이 제한된 콘텐츠를 보호 및 사용하기 위해 파일 API를 통해 수행해야 하는 기본 단계를 안내하는 샘플 RMS 사용 DLP(데이터 노출 방지) 응용 프로그램입니다.
- [IpcAzureApp](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcAzureApp)은 Azure 응용 프로그램에서 RMS SDK를 사용하여 Azure Blob 저장소의 데이터를 보호하는 방법을 보여 주는 샘플입니다.
- [RmsDocumentInspector](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/RmsDocumentInspector)는 콘텐츠 ID 또는 사용자 권한과 같은 RMS 보호된 파일에 대한 정보를 제공할 수 있는 도구입니다.
- [RmsFileWatcher](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/RmsFileWatcher)는 파일 시스템의 디렉터리를 감시하고 파일 추가, 파일 수정 등 파일이 변경될 때마다 RMS 보호 정책을 적용하는 Windows 응용 프로그램을 빌드하는 방법을 보여 주는 샘플입니다.

### <a name="windows-store-and-phone"></a>Windows 스토어 및 Phone

- [Windows 스토어용 UI 라이브러리](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) - Windows 스토어 응용 프로그램용 Microsoft RMS SDK v4.1에 대한 UI 라이브러리입니다. 이 라이브러리는 선택 사항이며 개발자가 Microsoft RMS SDK v4.1을 사용할 때 자체 UI를 빌드할 수도 있습니다.

- [Windows Phone용 UI 라이브러리](https://github.com/AzureAD/rms-sdk-ui-for-winphone) - Windows Phone 응용 프로그램용 Microsoft RMS SDK v4.1에 대한 UI 라이브러리입니다. 이 라이브러리는 선택 사항이며 개발자가 Microsoft RMS SDK v4.1을 사용할 때 자체 UI를 빌드할 수도 있습니다.

- [샘플 응용 프로그램](https://github.com/Azure-Samples/active-directory-dotnet-rms-windowsstore) - Windows 스토어 응용 프로그램용 Microsoft RMS SDK v4.1에 대한 샘플은 플랫폼에 대한 기본 문서 사용 예제를 제공합니다.



<!--HONumber=Nov16_HO2-->


