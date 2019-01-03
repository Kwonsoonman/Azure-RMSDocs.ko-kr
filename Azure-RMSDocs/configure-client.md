---
title: Azure Information Protection 클라이언트 &colon; 설치 및 구성
description: Windows 컴퓨터 및 모바일 디바이스에서 Azure Information Protection 클라이언트를 배포하기 위한 관리자용 정보입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9dfe8c6921b50faddb6ee8f24c39fe6f33e1fd4d
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173318"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection 클라이언트: 클라이언트 설치 및 구성

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Office 2010을 실행하는 컴퓨터는 Azure Rights Management 서비스 및 Azure Information Protection 서비스에서 인증을 받기 위해 Azure Information Protection 클라이언트(또는 Rights Management 공유 애플리케이션)가 필요합니다. 이 클라이언트는 Azure Rights Management 서비스 및 Azure Information Protection을 지원하는 모든 Windows 컴퓨터와 iOS 및 Android 디바이스에서도 권장됩니다. 

Azure Information Protection 클라이언트는 사용자가 Office 리본에서 직접 문서 및 전자 메일에 쉽게 레이블을 지정하고 보호할 수 있도록 Office 추가 기능을 설치하여 Office 애플리케이션과 통합됩니다. 또한 이 클라이언트는 Azure Rights Management 서비스에서 기본적으로 지원되지 않는 파일 형식에 대해 레이블 지정 및 보호를 제공하고, 보호된 문서를 보기 위한 뷰어, 사용자가 보호한 파일을 추적하고 취소할 수 있도록 문서 추적 사이트를 제공합니다.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Windows용 Azure Information Protection 클라이언트 설치 및 구성
Windows용 클라이언트의 엔터프라이즈 설치 및 구성에 대한 자세한 내용은 [ 관리자 가이드](./rms-client/client-admin-guide.md)를 참조하세요.

> [!TIP]
> 단일 컴퓨터에 대해 Azure Information Protection 클라이언트를 빠르게 설치하고 테스트하려면 [Azure Information Protection 클라이언트 사용자 가이드](./rms-client/client-user-guide.md)에서 [Azure Information Protection 클라이언트 다운로드 및 설치](./rms-client/install-client-app.md)를 참조하세요.

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>iOS 및 Android용 Azure Information Protection 클라이언트 설치 및 관리
이러한 널리 사용되는 모바일 플랫폼에 대해 Azure Information Protection 클라이언트를 설치하려면 [Microsoft Azure Information Protection 페이지](https://go.microsoft.com/fwlink/?LinkId=303970)의 링크를 사용하여 관련 앱을 다운로드할 수 있습니다. 별도의 구성이 필요 없습니다.

> [!NOTE]
> Mac 컴퓨터 및 Windows Phone의 경우 이 페이지의 링크를 클릭하면 모바일 디바이스용 RMS 공유 앱이 다운로드됩니다. 이러한 디바이스는 현재 Azure Information Protection 클라이언트를 지원하지 않습니다.

**Microsoft Intune이 있는 경우**: Azure Information Protection에 Microsoft Intune 앱 소프트웨어 개발 키트가 포함되어 있으므로 iOS 및 Android 디바이스를 Intune에서 등록하는 경우 이러한 디바이스에 대한 Azure Information Protection 뷰어를 배포하고 관리할 수 있습니다. 자세한 내용은 Intune 설명서에서 [Microsoft Intune 콘솔에서 모바일 애플리케이션 관리 정책 구성 및 배포](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)를 참조하세요. 2단계에서는 지침에 따라 정책 관리된 앱을 게시합니다.



