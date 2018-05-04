# <a name="class-mippolicyenginesettings"></a>클래스 mip::PolicyEngine::Settings 
엔진을 시작하려면 적절한 매개 변수를 사용하여 이 클래스 인스턴스를 제공해야 합니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline  Settings public inline  Settings public inline const std::string & GetId | 엔진 ID를 가져옵니다. public inline void SetId | Set the engine id. public inline const Identity & GetIdentity | ID 개체를 가져옵니다.
public inline void SetIdentity | ID 개체를 설정합니다.
public inline const std::string & GetClientData | 설정에 설정된 클라이언트 데이터를 가져옵니다.
public inline void SetClientData | 클라이언트 데이터 문자열을 설정합니다.
public inline const std::string & GetLocale | 설정에 설정된 로캘을 가져옵니다.
public inline void SetCustomSettings | 기능 제어 및 테스트에 사용되는 사용자 지정 설정을 설정합니다.
public inline const std::vector< std::pair< std::string, std::string > > & GetCustomSettings | 기능 제어 및 테스트에 사용되는 사용자 지정 설정을 설정합니다.
public inline void SetSessionId | 클라이언트 정의 원격 분석에 사용되는 세션 ID를 설정합니다.
public inline const std::string & GetSessionId | 고유 식별자인 세션 ID를 가져옵니다.
## <a name="members"></a>멤버
### <a name="settings"></a>설정
지정된 매개 변수로 인스턴스를 생성합니다. 기존 엔진을 로드하기 위해 LoadEngineAsync를 호출하는 [Settings](#classmip_1_1_policy_engine_1_1_settings)를 만들려면 이 멤버를 사용합니다.
#### <a name="parameters"></a>매개 변수
* id AddEngineAsync에서 생성되거나 자체 생성된 고유 엔진 ID입니다. 기존 엔진을 로드할 경우 ID를 다시 사용하고, 이외의 경우에는 새 엔진이 만들어집니다. 
* clientData 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색될 수 있습니다. 
* locale 엔진 지역화 가능한 출력이 이 로캘로 제공되고, 기본값은 “en-US”입니다.
### <a name="settings"></a>설정
새 엔진을 추가하기 위해 AddEngineAsync를 호출하는 [Settings](#classmip_1_1_policy_engine_1_1_settings)를 만들려면 이 멤버를 사용합니다.
#### <a name="parameters"></a>매개 변수
* identity 엔진을 추가해야 하는 사용자의 고유 식별자입니다. 
* clientData 언로드될 때 엔진과 함께 저장되는 사용자 지정 가능한 클라이언트 데이터로, 로드된 엔진에서 검색될 수 있습니다. 
* locale 엔진 지역화 가능한 출력이 이 로캘로 제공되고, 기본값은 “en-US”입니다.
### <a name="getid"></a>GetId
엔진 ID를 가져옵니다.
#### <a name="returns"></a>Returns
엔진을 식별하는 고유 문자열.
### <a name="setid"></a>SetId
엔진 ID를 설정합니다.
#### <a name="parameters"></a>매개 변수
* id 엔진 ID입니다.
### <a name="getidentity"></a>GetIdentity
ID 개체를 가져옵니다.
#### <a name="returns"></a>Returns
Settings 개체의 ID에 대한 참조. 
**참고 항목**: mip::Identity
### <a name="setidentity"></a>SetIdentity
ID 개체를 설정합니다.
#### <a name="parameters"></a>매개 변수
* identity 사용자의 고유 ID입니다. 
**참고 항목**: mip::Identity
### <a name="getclientdata"></a>GetClientData
설정에 설정된 클라이언트 데이터를 가져옵니다.
#### <a name="returns"></a>Returns
클라이언트가 지정한 데이터 문자열.
### <a name="setclientdata"></a>SetClientData
클라이언트 데이터 문자열을 설정합니다.
#### <a name="parameters"></a>매개 변수
* clientData 사용자가 지정한 데이터입니다.
### <a name="getlocale"></a>GetLocale
설정에 설정된 로캘을 가져옵니다.
#### <a name="returns"></a>Returns
로캘.
### <a name="setcustomsettings"></a>SetCustomSettings
기능 제어 및 테스트에 사용되는 사용자 지정 설정을 설정합니다.
#### <a name="parameters"></a>매개 변수
* customSettings 이름/값 쌍의 목록입니다.
### <a name="getcustomsettings"></a>GetCustomSettings
기능 제어 및 테스트에 사용되는 사용자 지정 설정을 설정합니다.
#### <a name="parameters"></a>매개 변수
* 이름/값 쌍의 목록입니다.
### <a name="setsessionid"></a>SetSessionId
클라이언트 정의된 원격 분석에 사용되는 세션 ID를 설정합니다.
#### <a name="parameters"></a>매개 변수
* sessionId 원격 분석 이벤트를 연결하는 고유 문자열입니다.
### <a name="getsessionid"></a>GetSessionId
고유 식별자인 세션 ID를 가져옵니다.
#### <a name="returns"></a>Returns
세션 ID.