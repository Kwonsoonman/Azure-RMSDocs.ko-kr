---
title: 클래스 mip ProtectionHandler Observer
description: 클래스 mip ProtectionHandler Observer에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 7fed286dec42f16d7dfa8e375ec739264bd365ba
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446184"
---
# <a name="class-mipprotectionhandlerobserver"></a>class mip::ProtectionHandler::Observer 
[ProtectionHandler](class_mip_protectionhandler.md)와 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 애플리케이션에 의해 구현되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnCreateProtectionHandlerSuccess(const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& context)  |  [ProtectionHandler](class_mip_protectionhandler.md)가 성공적으로 생성될 때 호출됩니다.
public virtual void OnCreateProtectionHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  [ProtectionHandler](class_mip_protectionhandler.md) 생성이 실패하면 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="oncreateprotectionhandlersuccess"></a>OnCreateProtectionHandlerSuccess
[ProtectionHandler](class_mip_protectionhandler.md)가 성공적으로 생성될 때 호출됩니다.

매개 변수:  
* **protectionHandler**: 새로 생성된 [ProtectionHandler](class_mip_protectionhandler.md)


* **context**: [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) 또는 [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)에 전달된 동일한 컨텍스트


애플리케이션은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) 또는 [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess 또는 ProtectionEngine::Observer::OnCreateProtectionHandlerFailure에 전달됩니다.
  
### <a name="oncreateprotectionhandlerfailure"></a>OnCreateProtectionHandlerFailure
[ProtectionHandler](class_mip_protectionhandler.md) 생성이 실패하면 호출됩니다.

매개 변수:  
* **오류**: 작성 중 발생한 오류 


* **context**: [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) 또는 [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)에 전달된 동일한 컨텍스트


애플리케이션은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) 또는 [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess 또는 ProtectionEngine::Observer::OnCreateProtectionHandlerFailure에 전달됩니다.