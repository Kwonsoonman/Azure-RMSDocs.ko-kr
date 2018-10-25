---
title: 클래스 mip FileEngine Settings
description: 클래스 mip FileEngine Settings에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 656ad1cf21a2d761dfb4c857b278b7421ee2b790
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446484"
---
# <a name="class-mipfileenginesettings"></a>클래스 mip::FileEngine::Settings 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  기존 엔진을 로드하기 위한 [FileEngine::Settings](class_mip_fileengine_settings.md) 생성자입니다.
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  새 엔진을 생성하기 위한 [FileProfile::Settings](class_mip_fileprofile_settings.md) 생성자입니다.
 public const std::string& GetEngineId() const  |  엔진 ID를 반환합니다.
 public const Identity& GetIdentity() const  |  엔진 ID를 반환합니다.
 public void SetIdentity(const Identity& identity)  |  엔진 ID를 설정합니다.
 public const std::string& GetClientData() const  |  엔진 클라이언트 데이터를 반환합니다.
 public const std::string& GetLocale() const  |  엔진 로캘을 반환합니다.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  테스트 및 실험에 사용되는 이름/값 쌍의 목록을 설정합니다.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  테스트 및 실험에 사용되는 이름/값 쌍의 목록을 가져옵니다.
 public void SetSessionId(const std::string& sessionId)  |  엔진 세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  엔진 세션 ID를 반환합니다.
 public void SetProtectionCloudEndpointBaseUrl(const std::string& protectionCloudEndpointBaseUrl)  |  클라우드 경계를 지정하는 데 사용되는, 보호 클라우드 엔드포인트 기준 URL을 설정합니다.
 public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  cloudEndpointBaseUrl을 가져옵니다.
 public void SetProtectionOnlyEngine(const bool protectionOnly)  |  보호 전용 엔진 표시기를 설정합니다. 정책/레이블이 없습니다.
 public const bool IsProtectionOnlyEngine() const  |  보호 전용 엔진 표시기를 반환합니다. 정책/레이블이 없습니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
기존 엔진을 로드하기 위한 [FileEngine::Settings](class_mip_fileengine_settings.md) 생성자입니다.

매개 변수:  
* **engineId**: AddEngineAsync에서 생성된 고유한 엔진 ID로 설정합니다. 


* **clientData**: 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색할 수 있습니다. 


* **locale**: 지역화 가능한 엔진 출력이 이 로캘로 제공됩니다.


  
### <a name="settings"></a>설정
새 엔진을 생성하기 위한 [FileProfile::Settings](class_mip_fileprofile_settings.md) 생성자입니다.

매개 변수:  
* **ID**: 새 엔진과 연결된 사용자의 ID 정보입니다. 


* **clientData**: 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색할 수 있습니다. 


* **locale**: 지역화 가능한 엔진 출력이 이 로캘로 제공됩니다.


  
### <a name="getengineid"></a>GetEngineId
엔진 ID를 반환합니다.
  
### <a name="getidentity"></a>GetIdentity
엔진 ID를 반환합니다.
  
### <a name="setidentity"></a>SetIdentity
엔진 ID를 설정합니다.
  
### <a name="getclientdata"></a>GetClientData
엔진 클라이언트 데이터를 반환합니다.
  
### <a name="getlocale"></a>GetLocale
엔진 로캘을 반환합니다.
  
### <a name="setcustomsettings"></a>SetCustomSettings
테스트 및 실험에 사용되는 이름/값 쌍의 목록을 설정합니다.
  
### <a name="getcustomsettings"></a>GetCustomSettings
테스트 및 실험에 사용되는 이름/값 쌍의 목록을 가져옵니다.
  
### <a name="setsessionid"></a>SetSessionId
엔진 세션 ID를 설정합니다.
  
### <a name="getsessionid"></a>GetSessionId
엔진 세션 ID를 반환합니다.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
클라우드 경계를 지정하는 데 사용되는, 보호 클라우드 엔드포인트 기준 URL을 설정합니다.

매개 변수:  
* **protectionCloudEndpointBaseUrl**: 보호 엔드포인트와 연결된 기준 URL입니다.


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
cloudEndpointBaseUrl을 가져옵니다.

  
**반환**: 보호 엔드포인트와 연결된 기준 URL
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
보호 전용 엔진 표시기를 설정합니다. 정책/레이블이 없습니다.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
보호 전용 엔진 표시기를 반환합니다. 정책/레이블이 없습니다.