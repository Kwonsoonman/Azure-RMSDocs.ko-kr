# <a name="class-mipfileprofile"></a>클래스 mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다.
일반적인 응용 프로그램은 하나의 [프로필](class_mip_profile.md)만 필요하지만 필요한 경우 여러 프로필을 만들 수 있습니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public virtual ~FileProfile()  | _아직 문서화되지 않았습니다._
 public const Settings& GetSettings() const  |  프로필 설정을 반환합니다.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  엔진 나열 작업을 시작합니다.
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 파일 엔진 언로드를 시작합니다.
public void AddEngineAsync(const FileEngine::Settings& settings, const std::shared_ptr<void>& context)  |  프로필에 대한 새 파일 엔진 추가를 시작합니다.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 파일 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 완전히 삭제됩니다.
 protected FileProfile()  | _아직 문서화되지 않았습니다._
  
## <a name="members"></a>멤버
  
### <a name="fileprofile"></a>~FileProfile
_아직 문서화되지 않았습니다._

  
### <a name="settings"></a>설정
프로필 설정을 반환합니다.
  
### <a name="listenginesasync"></a>ListEnginesAsync
엔진 나열 작업을 시작합니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
지정된 ID를 사용하여 파일 엔진 언로드를 시작합니다. [FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="addengineasync"></a>AddEngineAsync
프로필에 대한 새 파일 엔진 추가를 시작합니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
지정된 ID를 사용하여 파일 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 완전히 삭제됩니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="fileprofile"></a>FileProfile
_아직 문서화되지 않았습니다._
