---
title: 앱 배포 방법 - AIP
description: 이 문서에서는 처음에 개발된 프로세스가 아니라 서비스 애플리케이션을 다른 테넌트에 배포하는 프로세스를 설명합니다.
keywords: ''
author: kkanakas
ms.author: kartikka
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 34dc6d6f-cfe4-4848-9b11-8d90c4b38ef7
audience: developer
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: a7f31be3e7885e206d24ca4f193270b3ca1aa242
ms.sourcegitcommit: 07af86511a394274f10cf1340de4cf4bad6d1675
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473786"
---
# <a name="deploying-a-service-application-into-a-different-tenant"></a>다른 테넌트에 서비스 애플리케이션 배포

이 문서에서는 서비스 애플리케이션을 배포하는 프로세스를 설명합니다. 이 시나리오에서는 애플리케이션을 초기 개발 AD 테넌트에 등록하는 방식에서 다른 회사 프로덕션 AD 테넌트에 등록하는 방식으로 전환합니다.

> [!Note]
> 이 시나리오는 서비스 애플리케이션이 대칭 키 인증을 사용하는 경우에만 해당됩니다.

## <a name="scenario"></a>시나리오
회사 *CoolApp*은 사용자들이 Dynamics, SAP, Salesforce와 같은 비즈니스 애플리케이션에서 내보낼 때 문서를 암호화하고, 레이블을 지정하고, 보호하는 AIP(Azure Information Protection)를 사용하는 서비스 애플리케이션을 개발해 왔습니다. 이 시나리오에서 대기업 *ABC*는 *CoolApp*의 새 애플리케이션을 구입했으므로, *CoolApp* 팀은 해당 솔루션을 *ABC* 환경에 배포해야 합니다. 

![다른 테넌트에 대칭 키를 만들기 위한 샘플 흐름](../media/develop/service-app-provision.jpg)

## <a name="flow-1-coolapp-provides-a-ui-dialog-to-abc-to-implement-the-deployment"></a>흐름 1: *CoolApp*이 *ABC*에 배포를 구현하기 위한 UI 대화 상자 제공

*ABC*에서 일단 *CoolApp*의 솔루션을 구입하게 되면 *ABC*의 IT 관리자는 *CoolApp* 서비스 사용자를 만들고 *ABC*의 Azure AD 테넌트에 응용 프로그램에 등록해야 합니다. 

이 단계는 [애플리케이션 개발](developing-your-application.md)의 **서비스 사용자 만들기** 섹션에 설명되어 있습니다.

![애플리케이션 입력에 대한 IT 관리자를 위한 UI 예제](../media/develop/how-to-deploy-app-UI.png)

> [!Note]
> 테넌트에서 서비스 사용자를 만들려면 테넌트 관리자 권한이 필요합니다.

*ABC*의 IT 관리자는 *CoolApp*의 응용 프로그램을 작업 환경에서 서비스로 시작하고 응용 프로그램 ID, 테넌트 ID 및 대칭 키와 같은 *CoolApp* 응용 프로그램 작동을 위한 세부 정보를 포함합니다.

원하는 환경이 *ABC*의 IT 관리자에게 서비스 사용자 정보를 위한 UI 대화 상자를 제공하지 않는 것이면 **흐름 2**를 따라야 합니다.

## <a name="flow-2-abc-it-administrator-provides-the-key-to-the-coolapp-team"></a>흐름 2: *ABC* IT 관리자가 *CoolApp* 팀에 키 제공

*ABC*의 IT 관리자가 **그림 1**과 같이 서비스 사용자를 만들면 *ABC*는 *CoolApp* 팀에 해당 정보를 제공합니다. 그러면 *CoolApp* 팀은 *ABC*의 테넌트에서 사용할 수 있게 해당 정보를 *CoolApp* 애플리케이션에 포함합니다.
