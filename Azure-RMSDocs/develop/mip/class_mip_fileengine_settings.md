# <a name="class-mipfileenginesettings"></a>클래스 mip::FileEngine::Settings 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& id, const std::string& clientData, const std::string& locale)  |  지정된 매개 변수를 사용하여 인스턴스를 만듭니다.
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  지정된 매개 변수를 사용하여 인스턴스를 만듭니다.
 public const std::string& GetId() const  |  엔진 ID를 반환합니다.
 public const Identity& GetIdentity() const  |  엔진 ID를 반환합니다.
 public void SetIdentity(const Identity& identity)  |  엔진 ID를 설정합니다.
 public const std::string& GetClientData() const  |  엔진 클라이언트 데이터를 반환합니다.
 public const std::string& GetLocale() const  |  엔진 로캘을 반환합니다.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& value)  |  테스트 및 실험에 사용되는 이름/값 쌍의 목록을 설정합니다.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  테스트 및 실험에 사용되는 이름/값 쌍의 목록을 가져옵니다.
 public void SetSessionId(const std::string& sessionId)  |  엔진 세션 ID를 설정합니다.
 public const std::string& GetSessionId() const  |  엔진 세션 ID를 반환합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
지정된 매개 변수를 사용하여 인스턴스를 만듭니다.
이전에 AddEngineAsync를 통해 추가된 기존 엔진을 로드하기 위해 LoadEngineAsync를 호출하는 [Settings](class_mip_fileengine_settings.md)를 만들려면 이 멤버를 사용합니다.

매개 변수:  
* **id**: AddEngineAsync에서 생성된 고유 엔진 ID로 설정합니다.


  
### <a name="settings"></a>설정
지정된 매개 변수를 사용하여 인스턴스를 만듭니다.
새 엔진을 추가하기 위해 AddEngineAsync를 호출하는 [Settings](class_mip_fileengine_settings.md)를 만들려면 이 멤버를 사용합니다.

매개 변수:  
* **identity**: identity 엔진을 추가해야 하는 사용자의 ID 정보


  
### <a name="getid"></a>GetId
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