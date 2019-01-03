---
title: 클래스 mip ProtectionProfile Observer
description: 클래스 mip ProtectionProfile Observer에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3678e6c1e1659f28b2f1dcc36f61295a8d29393e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446433"
---
# <a name="class-mipprotectionprofileobserver"></a>클래스 mip::ProtectionProfile::Observer 
[ProtectionProfile](class_mip_protectionprofile.md)에 관련된 알림을 받는 인터페이스입니다.
이 인터페이스는 보호 SDK를 사용하여 애플리케이션에 의해 구현되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<ProtectionProfile>& profile, const std::shared_ptr<void>& context)  |  프로필이 성공적으로 로드되었을 때 호출됩니다.
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 나열로 오류가 발생했을 때 호출됩니다.
public virtual void OnAddEngineSuccess(const std::shared_ptr<ProtectionEngine>& engine, const std::shared_ptr<void>& context)  |  새 엔진이 성공적으로 추가되었을 때 호출됩니다.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  새 엔진 추가로 오류가 발생했을 때 호출됩니다.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 삭제되었을 때 호출됩니다.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 삭제로 오류가 발생했을 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.

매개 변수:  
* **profile**: 새로 만든 [ProtectionProfile](class_mip_protectionprofile.md)에 대한 참조


* **context**: [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)에 전달된 동일한 컨텍스트


애플리케이션은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) 또는 [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)에 전달됩니다.
  
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 로드 중에 발생한 [오류](class_mip_error.md) 


* **context**: [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)에 전달된 동일한 컨텍스트


애플리케이션은 모든 유형의 컨텍스트(예: std::promise, std::function 등)를 [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)에 전달할 수 있고 이 동일 컨텍스트는 있는 그대로 [ProtectionProfile::Observer::OnLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) 또는 [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)에 전달됩니다.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
엔진 목록이 성공적으로 생성되었을 때 호출됩니다.

매개 변수:  
* **engineIds**: 사용 가능한 엔진 ID 목록 


* **context**: [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)에 전달된 동일한 컨텍스트


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
엔진 나열로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 나열 작업 실패의 원인이 된 오류 


* **context**: [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)에 전달된 동일한 컨텍스트


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
새 엔진이 성공적으로 추가되었을 때 호출됩니다.

매개 변수:  
* **engine**: 새로 만든 엔진 


* **context**: [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)에 전달된 동일한 컨텍스트


  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
새 엔진 추가로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 추가 작업 실패의 원인이 되는 오류 


* **context**: [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)에 전달된 동일한 컨텍스트


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
엔진이 성공적으로 삭제되었을 때 호출됩니다.

매개 변수:  
* **context**: [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)에 전달된 동일한 컨텍스트


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
엔진 삭제로 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 삭제 작업 실패의 원인이 되는 오류 


* **context**: [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)에 전달된 동일한 컨텍스트

