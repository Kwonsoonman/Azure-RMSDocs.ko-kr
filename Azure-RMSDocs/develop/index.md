---
title: "RMS 개발자 가이드 | Azure RMS"
description: "현재 세 가지 세대의 Rights Management SDK를 사용할 수 있습니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 85cd61e564b066458618c02b4ac20cddf6b7e183
ms.lasthandoff: 01/24/2017


---

# <a name="rms-developers-guide"></a>RMS 개발자 가이드

## <a name="overview"></a>개요 ##
현재 Android, iOS/OS X, Windows 장치 및 Linux용 **Microsoft Rights Management SDK 4.2**, Windows 데스크톱 클라이언트용 **Microsoft Rights Management SDK 2.1**, 대체된 **AD RMS SDK** 등 세 가지 세대의 Rights Management SDK를 사용할 수 있습니다.

## <a name="software-development-kits"></a>소프트웨어 개발 키트 ##
| SDK | 설명 |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Microsoft Rights Management Services를 통해 Android, iOS, Mac OS X, Windows Phone/RT 및 Linux/C++ 장치 앱이 정보 보호를 사용할 수 있도록 하는 간단한 개발 환경을 제공하는 간소화된 차세대 도구 집합입니다. |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Windows 데스크톱 응용 프로그램 개발자와 서버 기반 솔루션 공급자가 해당 제품에서 권한 관리를 사용할 수 있도록 하는 강력한 SDK 제품입니다.|
|[AD RMS SDK]()|** 참고 ** - 클라이언트가 Msdrm.dll에 노출하는 기능을 활용하는 AD RMS SDK는 Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 및 Windows Vista에서 사용할 수 있습니다. 이후 버전에서는 변경되거나 제공되지 않을 수 있습니다. 클라이언트가 Msipc.dll에 노출하는 기능을 활용하는 Microsoft Rights Management Services SDK 2.1을 대신 사용합니다.|
|[AD RMS Scripting API]()(AD RMS 스크립팅 API)| AD RMS 설치를 관리할 스크립트를 만드는 데 사용됩니다.|

## <a name="code-samples-and-tools"></a>코드 샘플 및 도구 ##
이 Microsoft 제공 RMS 코드 샘플 및 개발자 지원 도구 컬렉션은 지원되는 모든 운영 체제(Android, iOS/OS X, Windows Phone 및 Windows 데스크톱)에 걸쳐 있으며, 지원되는 SDK와의 호환성을 유지하기 위해 정기적으로 업데이트됩니다.

| 항목 | 운영 체제 | 지원 SDK 버전 | 설명 |
|------|------------------|------------------------|-------------|
| [PFILE 보호된 PDF 읽기](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) | Windows 데스크톱| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK | **PFILE 보호된 PDF 읽기**는 RMS 개발자 코너 블로그에 있는 간단한 코드 예제로, MSIPC 파일 API를 사용하여 PFILE 보호된 PDF 문서의 암호를 해독하고 엽니다.|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows 데스크톱 | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK | **IpcManagedAPI**는 관리되는 응용 프로그램에서 쉽게 RMS를 사용할 수 있도록 하는 RMS SDK 2.1의 .NET(C#) 표현입니다.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | Windows 데스크톱 | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK| **IPCNotepad**는 각 RMS 사용 응용 프로그램이 제한된 콘텐츠를 보호 및 사용할 때 수행해야 하는 기본 단계를 안내하는 샘플 RMS 사용 응용 프로그램입니다.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|Windows 데스크톱|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK|**IpcDlp**는 DLP RMS 사용 응용 프로그램이 제한된 콘텐츠를 보호 및 사용하기 위해 파일 API를 통해 수행해야 하는 기본 단계를 안내하는 샘플 RMS 사용 DLP(데이터 노출 방지) 응용 프로그램입니다.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows 데스크톱|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK|**IpcAzureApp**은 Azure 응용 프로그램에서 RMS SDK를 사용하여 Azure Blob 저장소의 데이터를 보호하는 방법을 보여 주는 샘플입니다.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows 데스크톱|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK|**RmsDocumentInspector**는 콘텐츠 ID 또는 사용자 권한과 같은 RMS 보호된 파일에 대한 정보를 제공할 수 있는 도구입니다.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows 데스크톱|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) 이상 버전의 2.x SDK|**RmsFileWatcher**는 파일 시스템의 디렉터리를 감시하고 파일 추가, 파일 수정 등 파일이 변경될 때마다 RMS 보호 정책을 적용하는 Windows 응용 프로그램을 빌드하는 방법을 보여 주는 샘플입니다.|
| [iOS/OS X 사용 시나리오](https://msdn.microsoft.com/library/dn758307(v=vs.85).aspx) |iOS/OS X|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK|**Objective C** 코드 예제는 RMS SDK를 익히는 데 중요한 개발 시나리오를 나타냅니다. 예를 들어 Microsoft 보호된 파일 형식, 사용자 지정 보호된 파일 형식 및 사용자 지정 UI 컨트롤 사용이 포함됩니다.|
| [UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK|GitHub의 **iOS용 UI 라이브러리 및 샘플 앱**은 빨리 시작하고 앱에서 표준 UI를 다시 사용할 수 있게 해줍니다.|
| [UI 라이브러리 및 샘플 앱](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK|GitHub의 **Android용 UI 라이브러리 및 샘플 앱**은 빨리 시작하고 앱에서 표준 UI를 다시 사용할 수 있게 해줍니다.|
| [Android 사용 시나리오](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) 이상 버전의 4.x SDK|**Java 코드 예제**는 RMS SDK를 익히는 데 중요한 개발 시나리오를 나타냅니다. 예를 들어 Microsoft 보호된 파일 형식, 사용자 지정 보호된 파일 형식 및 사용자 지정 UI 컨트롤 사용이 포함됩니다.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
