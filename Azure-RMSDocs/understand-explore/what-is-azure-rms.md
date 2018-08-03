---
title: Azure 권한 관리란? - AIP
description: Azure RMS(Azure Rights Management)는 Azure Information Protection에서 사용하는 보호 기술입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: aeeebcd7-6646-4405-addf-ee1cc74df5df
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 967bea2a8cefcff618432cfa90fe8627b2c4c6a1
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39369686"
---
# <a name="what-is-azure-rights-management"></a>Azure 권한 관리란?

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Azure Rights Management(줄여서 Azure RMS라고도 함)는 [Azure Information Protection](what-is-information-protection.md)에서 사용하는 보호 기술입니다.

이 클라우드 기반 보호 서비스는 암호화, ID 및 권한 부여 정책을 사용하여 파일과 메일을 보호하며 휴대폰, 태블릿, PC 등의 여러 장치에서 작동합니다. 데이터가 조직 경계를 벗어나더라도 데이터가 계속 보호되므로 조직 내부와 외부에서 모두 정보를 보호할 수 있습니다.

직원이 파트너 회사에 문서를 메일로 보내거나 클라우드 드라이브에 문서를 저장하는 경우를 예로 들어 보겠습니다. Azure RMS에서 제공하는 영구적인 보호 기능을 통해 회사 데이터의 보안을 유지할 수 있을 뿐만 아니라 규정 준수, 법률상의 검색 요구 사항 또는 단순히 효율적인 정보 관리 방식에 따라 이러한 보호 기능을 법적으로 반드시 사용해야 할 수도 있습니다.

그러나 매우 중요한 점은 권한 있는 사람과 서비스(예: 검색 및 인덱싱)가 보호된 데이터를 계속 읽고 검사할 수 있다는 점입니다. 이 기능은 피어 투 피어 암호화를 사용하는 다른 정보 보호 솔루션으로는 쉽게 구현할 수 없습니다. 이 기능을 “데이터 추론”이라고도 일컫는 것을 들어 보셨을 것입니다. 이 기능은 조직 데이터에 대한 제어 기능을 유지 관리하는 데 필수적인 요소입니다.

아래 그림에는 이 서비스가 온-프레미스 서버 및 서비스뿐만 아니라 Office 365를 위해 보호 솔루션을 제공하는 방식이 표시되어 있습니다. Windows, Mac OS, iOS, Android 및 Windows Phone을 실행하는 널리 사용되는 최종 사용자 장치가 보호를 지원하는 것도 확인할 수 있습니다.


![Azure RMS의 작동 방식](../media/AzRMS_elements.png)

Azure Information Protection에 대한 구독뿐만 아니라 Office 365 구독과 함께 이 보호 기능을 사용할 수 있습니다. [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) 사이트에서 사용 가능한 구독 및 지원되는 기능에 대한 자세한 내용을 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection의 이 데이터 보호 서비스에 대한 자세한 정보:

- [응용 프로그램에서 Azure Rights Management 서비스를 지원하는 방법](applications-support.md)

- [Azure RMS를 통해 해결할 수 있는 문제](azure-rms-problems-it-solves.md)

- [Azure RMS는 어떤 방식으로 작동하나요? 기본적인 이해](how-does-it-work.md)

Azure Information Protection 레이블을 사용하여 직접 사용해 보고 문서를 보호하려는 경우 [Azure Information Protection 빠른 시작 자습서](../get-started/infoprotect-quick-start-tutorial.md)를 참조하세요. 이 자습서에는 중요한 데이터가 검색되었을 때 문서 보호 확인에 대한 내용이 포함됩니다. 또한 메일로 공유하는 문서 보호(사용 현황을 파악할 수 있도록 추적할 수 있고, 필요한 경우 액세스를 취소할 수 있음)에 대한 내용도 포함됩니다.

그러나 관리자 및 사용자가 문서 및 전자 메일 보호를 시작할 수 있도록 조직에 대해 Azure Information Protection 배포를 시작할 준비가 되면 [Azure Information Protection 배포 로드맵](../plan-design/deployment-roadmap.md)에서 배포 단계 및 방법 지침 링크를 확인할 수 있습니다.

> [!TIP]
> 추가 정보와 도움말을 확인하려면 [Azure Information Protection에 대한 정보 및 지원](../get-started/information-support.md)의 리소스와 링크를 사용하세요.
