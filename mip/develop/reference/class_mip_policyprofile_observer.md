---
title: 클래스 mip PolicyProfile Observer
description: 클래스 class mip PolicyProfile Observer에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5de2156f4906c14e4ebc1418df8acb092c089d7d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446905"
---
# <a name="class-mippolicyprofileobserver"></a>클래스 mip::PolicyProfile::Observer 
클라이언트가 프로필 관련 이벤트에 대한 알림을 가져올 수 있는 [Observer](class_mip_policyprofile_observer.md) 인터페이스입니다.
모든 오류는 [mip::Error](class_mip_error.md)에서 상속됩니다. 클라이언트는 관찰자를 호출하는 스레드에서 엔진을 다시 호출하면 안 됩니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public virtual void OnLoadSuccess(const std::shared_ptr<PolicyProfile>& profile, const std::shared_ptr<void>& context)  |  프로필이 성공적으로 로드되었을 때 호출됩니다.
public virtual void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  프로필 로드로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnListEnginesSuccess(const std::vector<std::string>& engineIds, const std::shared_ptr<void>& context)  |  엔진 목록이 성공적으로 생성되었을 때 호출됩니다.
public virtual void OnListEnginesFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 나열로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnUnloadEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 언로드되었을 때 호출됩니다.
public virtual void OnUnloadEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnAddEngineSuccess(const std::shared_ptr<PolicyEngine>& engine, const std::shared_ptr<void>& context)  |  새 엔진이 성공적으로 추가되었을 때 호출됩니다.
public virtual void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.
public virtual void OnDeleteEngineSuccess(const std::shared_ptr<void>& context)  |  엔진이 성공적으로 삭제되었을 때 호출됩니다.
public virtual void OnDeleteEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context)  |  엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.
 public virtual void OnPolicyChanged(const std::string& engineId)  |  지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.
  
## <a name="members"></a>멤버
  
### <a name="onloadsuccess"></a>OnLoadSuccess
프로필이 성공적으로 로드되었을 때 호출됩니다.

매개 변수:  
* **profile**: 작업을 시작하는 데 사용되는 현재 프로필 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onloadfailure"></a>OnLoadFailure
프로필 로드로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 로드 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
엔진 목록이 성공적으로 생성되었을 때 호출됩니다.

매개 변수:  
* **engineIds**: 사용 가능한 엔진 ID 목록 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
엔진 나열로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 나열 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
엔진이 성공적으로 언로드되었을 때 호출됩니다.

매개 변수:  
* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
엔진 언로드로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 언로드 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
새 엔진이 성공적으로 추가되었을 때 호출됩니다.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
새 엔진 추가로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 추가 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
엔진이 성공적으로 삭제되었을 때 호출됩니다.

매개 변수:  
* **context**: 작업에 전달되는 컨텍스트


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
엔진 삭제로 인해 오류가 발생했을 때 호출됩니다.

매개 변수:  
* **error**: 엔진 삭제 작업 실패의 원인이 되는 오류 


* **context**: 작업에 전달되는 컨텍스트


  
### <a name="onpolicychanged"></a>OnPolicyChanged
지정된 ID를 가진 엔진에 대한 정책이 변경되었을 때 호출됩니다.

매개 변수:  
* **engineId**: 엔진. 


새 정책을 로드하려면 지정된 엔진 ID를 사용하여 AddEngineAsync를 다시 호출해야 합니다.