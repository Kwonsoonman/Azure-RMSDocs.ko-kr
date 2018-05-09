# <a name="class-mipfileengine"></a>클래스 mip::FileEngine 
모든 엔진 함수에 대한 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public inline virtual ~FileEngine()  |  
public const Settings& GetSettings() const  |  엔진 설정을 반환합니다.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  민감도 레이블 목록을 반환합니다.
public std::shared_ptr<FileHandler> CreateFileHandler(const std::string& inputFilePath, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  지정된 파일 경로에 대한 파일 처리기를 반환합니다.
public std::shared_ptr<FileHandler> CreateFileHandler(const std::shared_ptr<Stream>& inputStream, const std::string& inputFileName, const std::shared_ptr<FileHandler::Observer>& fileHandlerObserver)  |  지정된 파일 스트림에 대한 파일 처리기를 반환합니다.
protected inline FileEngine()  |  
  
## <a name="members"></a>멤버
  
### <a name="fileengine"></a>~FileEngine
  
### <a name="settings"></a>설정
엔진 설정을 반환합니다.
  
### <a name="label"></a>Label
민감도 레이블 목록을 반환합니다.
  
### <a name="filehandler"></a>FileHandler
지정된 파일 경로에 대한 파일 처리기를 반환합니다.
  
#### <a name="parameters"></a>매개 변수
* 열려는 파일입니다. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 
* [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) 인터페이스를 구현하는 클래스입니다.
  
### <a name="filehandler"></a>FileHandler
지정된 파일 스트림에 대한 파일 처리기를 반환합니다.
  
#### <a name="parameters"></a>매개 변수
* 파일을 나타내는 스트림입니다. 
* 파일의 경로입니다. 경로에는 파일 이름과 파일 이름 확장명(있는 경우)이 포함되어야 합니다. 
* [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) 인터페이스를 구현하는 클래스입니다.
  
### <a name="fileengine"></a>FileEngine