# <a name="class-mipcontentlabel"></a>클래스 mip::ContentLabel 
콘텐츠 조각, 일반적으로 문서에 적용되는 Microsoft Information Protection 레이블의 추상화입니다.
레이블 정보 외에도 특정 적용된 레이블에 대한 속성을 포함합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::string& GetCreationTime() const  |  레이블을 만든 시간을 가져옵니다.
public AssignmentMethod GetAssignmentMethod() const  |  레이블의 할당 메서드를 가져옵니다.
public std::shared_ptr<Label> GetLabel() const  |  콘텐츠에 적용된 실제 레이블 개체를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getcreationtime"></a>GetCreationTime
레이블을 만든 시간을 가져옵니다.
  
#### <a name="returns"></a>Returns
만든 시간 gmt 문자열.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
레이블의 할당 메서드를 가져옵니다.
  
#### <a name="returns"></a>Returns
AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
**참고 항목**: mip::AssignmentMethod
  
### <a name="label"></a>Label
콘텐츠에 적용된 실제 레이블 개체를 가져옵니다.
  
#### <a name="returns"></a>Returns
콘텐츠에 적용된 레이블 개체 
**참고 항목**: [mip::Label](#classmip_1_1_label)