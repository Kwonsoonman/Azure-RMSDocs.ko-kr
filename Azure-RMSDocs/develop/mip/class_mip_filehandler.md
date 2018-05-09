# <a name="class-mipfilehandler"></a>클래스 mip::FileHandler 
모든 파일 처리 함수에 대한 인터페이스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public void GetLabelAsync(const std::shared_ptr<void>& context)  |  파일에서 민감도 레이블 검색을 시작합니다.
public void GetProtectionAsync(const std::shared_ptr<void>& context)  |  파일에서 보호 정책 검색을 시작합니다.
public void SetLabel(const std::string& labelId, const LabelingOptions& labelingOptions)  |  파일에 대한 민감도 레이블을 설정합니다.
public void DeleteLabel(AssignmentMethod method, const std::string& justificationMessage)  |  파일에서 민감도 레이블을 삭제합니다.
public void SetCustomPermissions(const std::shared_ptr<PolicyDescriptor>& policyDescriptor)  |  파일에 대한 사용자 지정 권한을 설정합니다.
public void RemoveProtection()  |  파일에서 보호를 제거합니다. 파일에 레이블이 지정된 경우 레이블이 유실됩니다.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr<void>& context) | \|outputFilePath\로 지정된 파일에 변경 내용을 씁니다. |  매개 변수로 전달할 수 있습니다.
public void CommitAsync(const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& context) | \|outputStream\로 지정된 스트림에 변경 내용을 씁니다. |  매개 변수로 전달할 수 있습니다.
public std::string GetOutputFileName()  |  원래 파일 이름 및 누적된 변경 내용을 기반으로 출력 파일 이름 및 확장명을 계산합니다.
public inline virtual ~FileHandler()  |  
protected inline FileHandler()  |  
  
## <a name="members"></a>멤버
  
### <a name="getlabelasync"></a>GetLabelAsync
파일에서 민감도 레이블 검색을 시작합니다.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)는 성공 또는 실패 시 호출됩니다.
  
#### <a name="parameters"></a>매개 변수
* context 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트입니다.
  
### <a name="getprotectionasync"></a>GetProtectionAsync
파일에서 보호 정책 검색을 시작합니다.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)는 성공 또는 실패 시 호출됩니다.
  
#### <a name="parameters"></a>매개 변수
* context 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트입니다.
  
### <a name="setlabel"></a>SetLabel
파일에 대한 민감도 레이블을 설정합니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다.
레이블을 설정할 때 [JustificationRequiredError](#classmip_1_1_justification_required_error)를 throw하려면 근거 제공이 필요하고 labelingOptions 매개 변수를 통해 근거 메시지가 제공되지 않았습니다.
  
### <a name="deletelabel"></a>DeleteLabel
파일에서 민감도 레이블을 삭제합니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다. Privilegd and Auto 메서드를 사용하면 API가 기존 레이블을 재정의할 수 있습니다. 레이블을 설정할 때 [JustificationRequiredError](#classmip_1_1_justification_required_error)를 throw하려면 근거 제공이 필요하고 justificationMessage 매개 변수를 통해 근거 메시지가 제공되지 않았습니다.
  
### <a name="setcustompermissions"></a>SetCustomPermissions
파일에 대한 사용자 지정 권한을 설정합니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다.
  
### <a name="removeprotection"></a>RemoveProtection
파일에서 보호를 제거합니다. 파일에 레이블이 지정된 경우 레이블이 유실됩니다.
CommitAsync가 호출될 때까지 변경 내용이 파일에 기록되지 않습니다.
  
### <a name="commitasync"></a>CommitAsync
| outputFilePath | 매개 변수로 지정된 파일에 변경 내용을 씁니다.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)는 성공 또는 실패 시 호출됩니다.
  
### <a name="commitasync"></a>CommitAsync
| outputStream | 매개 변수로 지정된 스트림에 변경 내용을 씁니다.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer)는 성공 또는 실패 시 호출됩니다.
  
### <a name="getoutputfilename"></a>GetOutputFileName
원래 파일 이름 및 누적된 변경 내용을 기반으로 출력 파일 이름 및 확장명을 계산합니다.
  
### <a name="filehandler"></a>~FileHandler
  
### <a name="filehandler"></a>FileHandler