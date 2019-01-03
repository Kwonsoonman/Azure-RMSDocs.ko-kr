---
title: FCI를 사용하는 파일 서버에서 AIP의 Azure RMS를 지원하는 방법
description: Office 문서를 자동으로 보호하기 위해 RMS 커넥터를 배포할 때 Azure RMS에서 Windows Server 파일 분류 인프라를 사용하는 방법을 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 45469e6e59139f10bd565730a5fb9fafbdaf13d0
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304852"
---
# <a name="how-file-servers-that-run-windows-server-and-use-file-classification-infrastructure-fci-support-azure-rights-management"></a>Windows Server를 실행하고 FCI(파일 분류 인프라)를 사용하는 파일 서버에서 Azure Rights Management를 지원하는 방식

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


파일 분류 인프라를 사용하도록 Windows Server를 구성하면 이 파일 서버 리소스 관리자 기능이 로컬 파일을 검색하여 중요한 데이터가 포함되어 있는지를 확인할 수 있습니다. 이 기준을 충족하는 파일에는 관리자가 정의하는 분류 속성이 태그로 지정됩니다. 그러면 파일 분류 인프라가 분류에 따라 자동 작업을 수행할 수 있습니다. 이러한 작업 중 하나가 Azure 권한 관리를 사용하고 권한 관리 커넥터(RMS 커넥터라고도 알려짐)를 배포하여 정보 보호를 적용하는 것입니다. 그런 다음 Office 파일은 Azure RMS를 통해 자동으로 보호됩니다.

모든 파일 형식을 보호하려면 RMS 커넥터를 사용하는 대신, [Azure Information Protection 모듈](./rms-client/client-admin-guide-powershell.md)의 cmdlet을 사용하여 Windows PowerShell 스크립트를 실행합니다.

분류 정책은 완전하게 구성 가능하며 확장성이 뛰어나므로 권한이 있는/없는 사용자의 데이터 유출 가능성을 방지할 수 있습니다. 또한 네트워크 관리자에게 파일 액세스 권한을 요구하지 않는 정책을 구성할 수 있으므로 해당 관리자가 데이터를 유출할 위험도 줄일 수 있습니다.

Office 파일용 RMS 커넥터를 배포하고 구성하는 방법에 대한 지침은 [Azure 권한 관리 커넥터 배포](deploy-rms-connector.md)를 참조하세요.

모든 파일 형식에 대해 Windows PowerShell 스크립트를 사용하는 방법에 대한 지침은 [Windows Server FCI(파일 분류 인프라)를 사용하는 RMS 보호](./rms-client/configure-fci.md)를 참조하세요.



## <a name="next-steps"></a>다음 단계
이제 애플리케이션과 서비스가 Azure RMS를 지원하는 방식을 이해하게 되었으므로 온-프레미스 버전의 Rights Management인 AD RMS(Active Directory Rights Management Services)와 Azure RMS를 비교할 수 있습니다. 기능, 요구 사항 및 보안 제어를 비교한 내용을 보려면 [Azure 권한 관리와 AD RMS 비교](compare-on-premise.md)를 참조하세요.


