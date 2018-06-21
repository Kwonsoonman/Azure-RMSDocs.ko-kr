# <a name="class-mipfileengine"></a>클래스 mip::FileEngine 
모든 엔진 함수에 대한 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public virtual ~FileEngine()  | _아직 문서화되지 않았습니다._
 public const Settings& GetSettings() const  |  엔진 설정을 반환합니다.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  민감도 레이블 목록을 반환합니다.
public std::shared_ptr<FileHandler> CreateFileHandler(const std::string& inputFilePath, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  지정된 파일 경로에 대한 파일 처리기를 반환합니다.
public std::shared_ptr<FileHandler> CreateFileHandler(const std::shared_ptr<Stream>& inputStream, const std::string& inputFileName, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  지정된 파일 스트림에 대한 파일 처리기를 반환합니다.
 protected FileEngine()  | _아직 문서화되지 않았습니다._
  
## <a name="members"></a>멤버
  
### <a name="fileengine"></a>~FileEngine
_아직 문서화되지 않았습니다._

  
### <a name="settings"></a>설정
엔진 설정을 반환합니다.
  
### <a name="label"></a>Label
민감도 레이블 목록을 반환합니다.
  
### <a name="filehandler"></a>FileHandler
지정된 파일 경로에 대한 파일 처리기를 반환합니다.

매개 변수:  
* **The**: 열려는 파일. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 


* **A**: [FileHandler::Observer](class_mip_filehandler_observer.md) 인터페이스를 구현하는 클래스.


  
### <a name="filehandler"></a>FileHandler
지정된 파일 스트림에 대한 파일 처리기를 반환합니다.

매개 변수:  
* **A**: 파일을 나타내는 스트림. 


* **The**: 파일의 경로. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 


* **A**: [FileHandler::Observer](class_mip_filehandler_observer.md) 인터페이스를 구현하는 클래스.


  
### <a name="fileengine"></a>FileEngine
_아직 문서화되지 않았습니다._
