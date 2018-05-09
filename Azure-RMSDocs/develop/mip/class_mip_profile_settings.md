# <a name="class-mipprofilesettings"></a>클래스 mip::Profile::Settings 
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<Profile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  프로필을 구성하기 위한 인터페이스입니다.
public inline const std::string& GetPath() const  |  저장된 상태의 경로를 가져옵니다.
public inline bool GetUseInMemoryStorage() const  |  메모리 저장소에 사용 플래그를 가져옵니다.
public inline const std::shared_ptr<AuthDelegate>& GetAuthDelegate() const  |  인증 대리자를 가져옵니다.
public inline const std::shared_ptr<Profile::Observer>& GetObserver() const  |  이벤트 관찰자를 가져옵니다.
public inline const ApplicationInfo GetApplicationInfo() const  |  응용 프로그램 정보를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필을 구성하기 위한 인터페이스입니다.
  
#### <a name="parameters"></a>매개 변수
* path SDK가 프로필 상태를 저장할 디렉터리 경로입니다. 
* useInMemoryStorage 디스크에 상태를 저장해야 하는지 여부를 나타내는 플래그입니다. 
* authDelegate SDK에서 인증 토큰을 얻는 데 사용되는 인증 대리자입니다. 
* observer [Profile::Observer](#classmip_1_1_profile_1_1_observer) 인터페이스를 구현하는 클래스입니다. nullptr일 수 없습니다. 
* applicationInfo 서비스 액세스에 사용되는 응용 프로그램 식별자입니다.
  
### <a name="getpath"></a>GetPath
저장된 상태의 경로를 가져옵니다.
  
#### <a name="returns"></a>Returns
저장된 상태의 경로.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
메모리 저장소에 사용 플래그를 가져옵니다.
  
#### <a name="returns"></a>Returns
메모리에 사용이 설정된 경우 true, 그렇지 않으면 false.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
인증 대리자를 가져옵니다.
  
#### <a name="returns"></a>Returns
인증 대리자.
  
### <a name="profileobserver"></a>Profile::Observer
이벤트 관찰자를 가져옵니다.
  
#### <a name="returns"></a>Returns
이벤트 관찰자.
  
### <a name="applicationinfo"></a>ApplicationInfo
응용 프로그램 정보를 가져옵니다.
  
#### <a name="returns"></a>Returns
응용 프로그램 정보.