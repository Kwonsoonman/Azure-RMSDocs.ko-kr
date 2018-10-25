---
title: 클래스 mip ProtectionEngine Observer
description: 클래스 mip ProtectionEngine Observer에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5c5b5e807a80c8db3cbdb69ea5d09da1e79aec6e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446586"
---
# <a name="class-mipprotectionengineobserver"></a>class mip::ProtectionEngine::Observer 
[ProtectionEngine](class_mip_protectionengine.md)과 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 응용 프로그램에 의해 구현되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnGetTemplatesSuccess(const std::shared_ptr<std::vector<std::string>>& templateIds, const std::shared_ptr<void>& context)  |  템플릿이 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetTemplatesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  템플릿 검색 시 오류가 발생될 때 호출됩니다.
public virtual void OnGetRightsForLabelIdSuccess(const std::shared_ptr<std::vector<std::string>>& rights, const std::shared_ptr<void>& context)  |  권한이 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetRightsForLabelIdFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  레이블 ID에 대한 사용자의 권한을 검색할 때 호출됩니다.
public virtual void OnGetGrantingLabelIdsSuccess(const std::shared_ptr<std::vector<std::string>>& lableIds, const std::shared_ptr<void>& context)  |  레이블 ID가 성공적으로 검색될 때 호출됩니다.
public virtual void OnGetGrantingLabelIdsFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  사용자의 레이블 ID를 검색할 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
템플릿이 성공적으로 검색될 때 호출됩니다.

매개 변수:  
* **templateIds**: 검색된 템플릿 목록에 대한 참조입니다. 


* **context**: [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) 또는 [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)에 전달됩니다.
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
템플릿 검색 시 오류가 발생될 때 호출됩니다.

매개 변수:  
* **error**: 템플릿 검색 중에 발생한 [오류](class_mip_error.md) 


* **context**: [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) 또는 [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)에 전달됩니다.
  
### <a name="ongetrightsforlabelidsuccess"></a>OnGetRightsForLabelIdSuccess
권한이 성공적으로 검색될 때 호출됩니다.

매개 변수:  
* **rights**: 검색된 권한 목록에 대한 참조 


* **context**: [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)에 전달된 것과 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) 또는 [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)에 전달됩니다.
  
### <a name="ongetrightsforlabelidfailure"></a>OnGetRightsForLabelIdFailure
레이블 ID에 대한 사용자의 권한을 검색할 때 호출됩니다.

매개 변수:  
* **error**: 권한 검색 중에 발생한 [오류](class_mip_error.md) 


* **context**: [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)에 전달된 것과 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) 또는 [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)에 전달됩니다.
  
### <a name="ongetgrantinglabelidssuccess"></a>OnGetGrantingLabelIdsSuccess
레이블 ID가 성공적으로 검색될 때 호출됩니다.

매개 변수:  
* **lableIds**: 검색된 레이블 ID 목록에 대한 참조 


* **context**: [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) 또는 [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)에 전달됩니다.
  
### <a name="ongetgrantinglabelidsfailure"></a>OnGetGrantingLabelIdsFailure
사용자의 레이블 ID를 검색할 때 호출됩니다.

매개 변수:  
* **error**: 레이블 ID 검색 중에 발생한 [오류](class_mip_error.md) 


* **context**: [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)에 전달된 동일한 컨텍스트


응용 프로그램은 모든 유형의 컨텍스트(예: std::promise, std::function)를 [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)에 전달할 수 있고 동일한 컨텍스트가 있는 그대로 [ProtectionEngine::Observer::OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) 또는 [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)에 전달됩니다.