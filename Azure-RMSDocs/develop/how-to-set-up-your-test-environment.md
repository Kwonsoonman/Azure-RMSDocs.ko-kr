---
title: 응용 프로그램 테스트 | Azure RMS
description: 테스트를 위해 응용 프로그램을 설치하는 방법에 대한 지침입니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 054121899523056e9d61a673c01f70022e77d13c
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44149637"
---
# <a name="testing-your-application"></a>응용 프로그램 테스트

여기에서 응용 프로그램 테스트를 준비하는 방법을 배웁니다.

## <a name="instructions"></a>지침

Azure RMS 또는 Windows Server에서 실행 중인 RMS 서버로 테스트할 수 있습니다.  Azure RMS를 사용하여 테스트를 시작하고 RMS 서버로 테스트합니다(배포에 필요한 경우).

- Azure RMS에서 테스트하는 방법에 대해서는 [방법: ADAL 인증 사용](how-to-use-adal-authentication.md) 항목을 참조하세요.
- RMS 서버에서 테스트하는 방법에 대해서는 [방법: RMS 서버 설치 및 구성](how-to-install-and-configure-an-rms-server.md) 항목을 참조하세요.
- 개발자 런타임을 설치하려면 다음을 수행합니다.

   응용 프로그램을 테스트할 컴퓨터에 Rights Management Service Client 2.1이 설치되어 있어야 합니다.
   - 개발 컴퓨터 이외의 컴퓨터에서 응용 프로그램을 테스트하려면 [AD RMS 클라이언트 다운로드 페이지](http://www.microsoft.com/en-us/download/details.aspx?id=38396)에서 해당 컴퓨터에 RMS Client 2.1을 설치합니다.
   - 개발 컴퓨터에는 이전에 설치된 Rights Management Services SDK 2.1이 있어야 합니다.

   RMS SDK 2.1 설치에 대한 도움말은 [SDK 설치](install-the-rms-sdk.md)를 참조하세요.

## <a name="remarks"></a>설명

이 지침은 포괄적이지 않습니다. RMS Client 2.1을 구성하는 방법을 알아보려면 [RMS Client 2.1 배포 참고 사항](https://technet.microsoft.com/library/jj159267(WS.10).aspx)을 참조하세요.

## <a name="related-topics"></a>관련 항목

* [RMS 서버 설치 및 구성 방법](how-to-install-and-configure-an-rms-server.md)
* [방법: ADAL 인증 사용](how-to-use-adal-authentication.md)
* [SDK 설치](install-the-rms-sdk.md)
* [RMS Client 2.1 배포 참고 사항](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

