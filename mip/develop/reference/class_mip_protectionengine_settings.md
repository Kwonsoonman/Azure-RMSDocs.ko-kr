---
title: 클래스 mip ProtectionEngine Settings
description: 클래스 mip ProtectionEngine Settings에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f61e86a87ecfea21bc9d02f4e55f3fbe663e9b80
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446705"
---
# <a name="class-mipprotectionenginesettings"></a>class mip::ProtectionEngine::Settings 
만드는 동안 그리고 수명 기간 내내 [ProtectionEngine](class_mip_protectionengine.md)에서 사용되는 [설정](class_mip_protectionengine_settings.md)입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  새 엔진을 생성하기 위한 [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 생성자입니다.
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  기존 엔진을 로드하기 위한 [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 생성자입니다.
 public const std::string& GetEngineId() const  |  엔진 ID를 가져옵니다.
 public void SetEngineId(const std::string& engineId)  |  엔진 ID를 설정합니다.
 public const Identity& GetIdentity() const  |  엔진과 연결된 사용자 ID를 가져옵니다.
 public void SetIdentity(const Identity& identity)  |  엔진과 연결된 사용자 ID를 설정합니다.
 public const std::string& GetClientData() const  |  클라이언트에서 지정한 사용자 지정 데이터를 가져옵니다.
 public void SetClientData(const std::string& clientData)  |  클라이언트에서 지정한 사용자 지정 데이터를 설정합니다.
 public const std::string& GetLocale() const  |  엔진 데이터를 작성할 로캘을 가져옵니다.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  테스트 및 실험에 사용되는 이름/값 쌍을 설정합니다.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  테스트 및 실험에 사용되는 이름/값 쌍을 가져옵니다.
 public void SetSessionId(const std::string& sessionId)  |  로깅/원격 분석의 상관 관계를 지정하는 데 사용되는 엔진 세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  엔진 세션 ID를 가져옵니다.
 public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  선택적으로 클라우드 엔드포인트 기준 URL을 설정합니다.
 public const std::string& GetCloudEndpointBaseUrl() const  |  모든 서비스 요청에 사용되는 클라우드 기준 URL(지정된 경우)을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
새 엔진을 생성하기 위한 [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 생성자입니다.

매개 변수:  
* **identity**: [ProtectionEngine](class_mip_protectionengine.md)과 연결될 ID


* **clientData**: 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색될 수 있습니다. 


* **locale**: 엔진 출력이 이 로캘로 제공됩니다.


  
### <a name="settings"></a>설정
기존 엔진을 로드하기 위한 [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 생성자입니다.

매개 변수:  
* **engineId**: 로드될 엔진의 고유 식별자 


* **clientData**: 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색될 수 있습니다. 


* **locale**: 엔진 출력이 이 로캘로 제공됩니다.


  
### <a name="getengineid"></a>GetEngineId
엔진 ID를 가져옵니다.

  
**반환**: 엔진 ID
  
### <a name="setengineid"></a>SetEngineId
엔진 ID를 설정합니다.

매개 변수:  
* **engineId**: 엔진 ID입니다.


  
### <a name="getidentity"></a>GetIdentity
엔진과 연결된 사용자 ID를 가져옵니다.

  
**반환**: 엔진과 연결된 사용자 ID
  
### <a name="setidentity"></a>SetIdentity
엔진과 연결된 사용자 ID를 설정합니다.

매개 변수:  
* **identity**: 엔진과 연결된 사용자 ID


  
### <a name="getclientdata"></a>GetClientData
클라이언트에서 지정한 사용자 지정 데이터를 가져옵니다.

  
**반환**: 클라이언트에서 지정한 사용자 지정 데이터
  
### <a name="setclientdata"></a>SetClientData
클라이언트에서 지정한 사용자 지정 데이터를 설정합니다.

매개 변수:  
* **Custom**: 클라이언트에서 지정한 데이터입니다.


  
### <a name="getlocale"></a>GetLocale
엔진 데이터를 작성할 로캘을 가져옵니다.

  
**반환**: 엔진 데이터를 작성할 로캘
  
### <a name="setcustomsettings"></a>SetCustomSettings
테스트 및 실험에 사용되는 이름/값 쌍을 설정합니다.

매개 변수:  
* **customSettings**: 테스트 및 실험에 사용되는 이름/값 쌍


  
### <a name="getcustomsettings"></a>GetCustomSettings
테스트 및 실험에 사용되는 이름/값 쌍을 가져옵니다.

  
**반환**: 테스트 및 실험에 사용되는 이름/값 쌍
  
### <a name="setsessionid"></a>SetSessionId
로깅/원격 분석의 상관 관계를 지정하는 데 사용되는 엔진 세션 ID를 설정합니다.

매개 변수:  
* **sessionId**: 로깅/원격 분석의 상관 관계에 사용되는 엔진 세션 ID


  
### <a name="getsessionid"></a>GetSessionId
엔진 세션 ID를 가져옵니다.

  
**반환**: 엔진 세션 ID
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
선택적으로 클라우드 엔드포인트 기준 URL을 설정합니다.

매개 변수:  
* **cloudEndpointBaseUrl**: 모든 서비스 요청에서 사용되는 기준 URL(예: “https://api.aadrm.com”)


지정되지 않은 경우 기준 URL은 엔진 ID 도메인의 DNS 조회를 통해 결정됩니다.
  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
모든 서비스 요청에 사용되는 클라우드 기준 URL(지정된 경우)을 가져옵니다.

  
**반환**: 기준 URL