---
title: '방법: 암호화 설정 작업 | Azure RMS'
description: Azure RMS 암호화 패키지 및 사용과 관련된 코드 조각을 설명합니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 049a923c27bf1201d3b800c92bacf5f210d565a5
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806838"
---
# <a name="how-to-work-with-encryption-settings"></a>방법: 암호화 설정 작업

이 항목에서는 암호화 패키지에 대해 설명하고 사용과 관련된 몇 가지 코드 조각을 보여 줍니다.

## <a name="support-for-aes-256-the-new-default"></a>새 기본값, AES 256 지원

RMS SDK 2.1 2015년 3월 업데이트 이상에 대해 빌드한다고 가정할 경우 *AES 256* 기반 암호화가 새 기본값이기 때문에 추가 코드 없이 사용할 수 있습니다. *AES 256*의 보안 강화 혜택을 활용하려면 응용 프로그램을 이 릴리스로 업데이트하는 것이 좋습니다.

> [!IMPORTANT]
> *AES 256* 보호된 파일 사용은 [2014년 10월 릴리스](release-notes-rtm.md)부터 지원되었습니다. 2014년 10월 이전 버전의 SDK로 빌드한 응용 프로그램을 실행하는 경우 이 업데이트를 사용하면 응용 프로그램이 중단됩니다. 빌드하는 응용 프로그램의 고객이 업데이트된 SDK를 사용 중이거나 최신 버전의 응용 프로그램으로 즉시 업데이트할 의향이 있는지 확인합니다.

 
## <a name="api-encryption-support"></a>API 암호화 지원

[2015년 3월 업데이트](release-notes-rtm.md) 이상에서는 API 및 관련된 암호화 패키지에 다음 세 가지 플래그가 통합되었습니다.

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB(사용되지 않는 알고리즘이라고도 함)

암호화 패키지 플래그([Preferred encryption](https://msdn.microsoft.com/library/dn974065.aspx)(기본 암호화) 참조)를 라이선스 속성 플래그 *IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE*와 함께 사용할 수 있습니다.

다음은 새 라이선스 속성을 사용하는 방법을 보여 주는 몇 가지 간단한 코드 조각입니다.

## <a name="deprecated-algorithms"></a>사용되지 않는 알고리즘

*IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS* 플래그는 더 이상 API에 노출되지 않습니다. 즉, 이후 응용 프로그램에서 이 플래그를 참조할 경우 더 이상 컴파일되지 않지만 API 코드에서 비공개로 플래그가 적용되므로 이 플래그를 사용하여 이미 빌드된 응용 프로그램은 계속 작동합니다.

플래그를 변경하기만 하면 사용되지 않는 이전 암호화 알고리즘 플래그를 여전히 활용할 수 있습니다. 예제는 다음 코드 조각을 참조하세요.

## <a name="protect-files-with-aes-256-cbc4k"></a>AES 256 CBC4K를 사용하여 파일 보호

*AES 256* CBC4K가 기본값이므로 코드를 변경할 필요가 없습니다.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## <a name="protect-files-with-aes-128-cbc4k"></a>AES-128 CBC4K를 사용하여 파일 보호

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## <a name="protect-files-with-aes-128-ecb-deprecated-algorithms"></a>AES-128 ECB(사용되지 않는 알고리즘)를 사용하여 파일 보호

또한 이 샘플에서는 *사용되지 않는 알고리즘*을 지원하는 새로운 방법을 보여 줍니다.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);

