---
title: ConsentDelegate 클래스
description: ConsentDelegate 클래스에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 841049b1e6b369eb2f6a34d9701ed34eca028af6
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446365"
---
# <a name="class-consentdelegate"></a>ConsentDelegate 클래스 
동의 관련 작업에 대한 대리자입니다.
이 대리자는 사용자에게 동의 요청 알림을 표시해야 하는 시기를 알기 위해 클라이언트 응용 프로그램에 의해 구현됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public Consent GetUserConsent(const std::string& url)  |  SDK에서 서비스 엔드포인트에 연결하는 데 사용자 동의가 필요한 경우 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="consent"></a>Consent
SDK에서 서비스 엔드포인트에 연결하는 데 사용자 동의가 필요한 경우 호출됩니다.

매개 변수:  
* **url**: SDK에서 사용자 동의가 필요한 URL



  
**반환**: 사용자의 결정이 있는 동의 열거형.
SDK에서 이 메서드로 사용자 동의를 요청하면 클라이언트 응용 프로그램이 사용자에게 URL을 표시해야 합니다. 클라이언트 응용 프로그램은 사용자 동의를 얻는 수단을 몇 가지 제공하고 사용자의 결정에 해당하는 적절한 동의 열거형을 반환해야 합니다.