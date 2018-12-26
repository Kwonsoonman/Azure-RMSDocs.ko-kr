---
title: 빠른 시작 - C++ MIP SDK를 사용하여 파일에서 민감도 레이블 설정 및 가져오기
description: Microsoft Information Protection C++ SDK를 사용하여 파일에서 민감도 레이블을 설정 및 가져오는 방법을 보여 주는 빠른 시작입니다.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 651fc73c00f18d06ad1a824337a096331bc7e897
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251746"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>빠른 시작: 민감도 레이블 설정 및 가져오기(C++)

이 빠른 시작은 더 많은 MIP 파일 API를 사용하는 방법을 보여 줍니다. 이전 빠른 시작에서 제공된 민감도 레이블 중 하나를 사용하여 파일 처리기를 통해 파일에서 레이블을 설정/가져옵니다. 파일 처리기 클래스는 레이블을 설정/가져오거나 보호를 위해 지원되는 파일 형식에 대해 다양한 작업을 표시합니다.

## <a name="prerequisites"></a>전제 조건

다음 필수 구성 요소를 아직 완료하지 않은 경우 먼저 완료합니다.

- 시작 Visual Studio 솔루션을 빌드하는 전체 [빠른 시작: 민감도 레이블 나열(C++)](quick-file-list-labels-cpp.md)을 먼저 완료하여 조직의 민감도 레이블을 나열합니다. “민감도 레이블 설정 및 가져오기” 빠른 시작은 이전 빠른 시작을 토대로 구축되었습니다.
- 선택 사항: [MIP SDK의 파일 처리기](concept-handler-file-cpp.md) 개념을 검토합니다.

## <a name="implement-an-observer-class-to-monitor-the-file-handler-object"></a>파일 처리기 개체를 모니터링하기 위한 Observer 클래스 구현

애플리케이션 초기화 빠른 시작에서 구현한 Observer(파일 프로필 및 엔진 관련)와 비슷한 Observer 클래스를 파일 처리기 개체에 대해 구현합니다.

SDK의 `mip::FileHandler::Observer` 클래스를 확장하여 Observer 클래스에 대한 기본 구현을 만듭니다. Observer는 인스턴스화된 후 나중에 파일 처리기 작업을 모니터링하는 데 사용됩니다.

1. 이전에 “빠른 시작: 민감도 레이블 나열(C++)” 문서에서 작업했던 Visual Studio 솔루션을 엽니다.

2. 헤더/.h 및 구현/.cpp 파일을 둘 다 생성하는 새 클래스를 프로젝트에 추가합니다.

   - **솔루션 탐색기**에서 프로젝트 노드를 다시 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 후 **클래스**를 선택합니다.
   - **클래스 추가** 대화 상자에서 다음을 수행합니다.
     - **클래스 이름** 필드에 "filehandler_observer"를 입력합니다. **.h 파일** 및 **.cpp 파일** 필드가 입력한 이름을 기준으로 자동으로 채워집니다.
     - 완료되면 **확인** 단추를 클릭합니다.

3. 클래스에 대해 .h 및 .cpp 파일을 생성하면 두 파일이 편집기 그룹 탭에서 열립니다. 이제 각 파일을 업데이트하여 새 Observer 클래스를 구현합니다.

   - 생성된 `filehandler_observer` 클래스를 선택/삭제하여 “filehandler_observer.h”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 기존 전처리기 지시문 뒤에 다음 소스를 복사한 후 붙여넣습니다.

     ```cpp
     #include <memory>
     #include "mip/file/file_engine.h"
     #include "mip/file/file_handler.h"

     class FileHandlerObserver final : public mip::FileHandler::Observer {
     public:
        FileHandlerObserver() { }
        // Observer implementation
        void OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) override;
        void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
        void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) override;
        void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;       
     };
     ```

   - 생성된 `filehandler_observer` 클래스 구현을 선택/삭제하여 “filehandler_observer.cpp”를 업데이트합니다. 이전 단계에서 생성한 전처리기 지시문(#pragma, #include)을 제거하지 **마세요**. 기존 전처리기 지시문 뒤에 다음 소스를 복사한 후 붙여넣습니다.

     ```cpp
     void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_value(fileHandler);
     }

     void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_exception(error);
     }

     void FileHandlerObserver::OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_value(committed);
     }

     void FileHandlerObserver::OnCommitFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_exception(error);
     }
     ```

4. 경우에 따라 F6 키(**솔루션 빌드**)를 통해 솔루션의 테스트 컴파일/연결을 실행하여 성공적으로 빌드되는지 확인합니다.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>민감도 레이블을 설정 및 가져오기 위한 논리 추가

파일 엔진 개체를 사용하여 파일에서 민감도 레이블 설정 및 가져오기 위한 논리를 추가합니다. 

1. **솔루션 탐색기**를 사용하여 프로젝트에서 `main()` 메서드의 구현이 포함된 .cpp 파일을 엽니다. 파일 이름은 프로젝트를 만드는 동안 지정한 프로젝트 이름과 같습니다. 

2. 다음 `#include` 및 `using` 지시문을 파일 맨 위, 기존 지시문 아래에 추가합니다.

   ```cpp
   #include "filehandler_observer.h" 
   #include "mip/file/file_handler.h" 

   using mip::FileHandler;
   ```
3. `main()` 본문이 끝나가는 위치에서 `system("pause");` 아래, `return 0;` 위에(이전 빠른 시작을 중지한 위치) 다음 코드를 삽입합니다.

   ```cpp
   // Set up async FileHandler for input file operations
   string filePathIn = "<input-file-path>";
   std::shared_ptr<FileHandler> handler;
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathIn, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid input file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Set a label on input file
   try
   {
        string labelId = "<label-id>";
        cout << "\nApplying Label ID " << labelId << " to " << filePathIn << endl;
        mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
        handler->SetLabel(labelId, labelingOptions);
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Commit changes, save as a different/output file
   string filePathOut = "<output-file-path>";
   try
   {
        cout << "Committing changes" << endl;
        auto commitPromise = std::make_shared<std::promise<bool>>();
        auto commitFuture = commitPromise->get_future();
        handler->CommitAsync(filePathOut, commitPromise);
        if (commitFuture.get()) {
            cout << "\nLabel committed to file: " << filePathOut << endl;
        }
        else {
            cout << "Failed to label: " + filePathOut << endl;
            return 1;
        }
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid commit file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");

   // Set up async FileHandler for output file operations
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathOut, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid output file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Get the label from output file
   try
   {
        cout << "\nGetting the label committed to file: " << filePathOut << endl;
        auto label = handler->GetLabel();
        cout << "Name: " + label->GetLabel()->GetName() << endl;
        cout << "Id: " + label->GetLabel()->GetId() << endl;
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");
   ```

4. 방금 붙여넣은 소스 코드의 자리 표시자 값을 다음 값으로 바꿉니다.

   | 자리 표시자 | 값 |
   |:----------- |:----- |
   | \<input-file-path\> | 입력 파일을 테스트할 전체 경로(예: `c:\\Test\\Test.docx`)입니다. |
   | \<label-id\> | 이전 빠른 시작의 출력 콘솔에서 복사한 민감도 레이블 ID(예: `f42a3342-8706-4288-bd31-ebb85995028z`)입니다. |
   | \<output-file-path\> | 입력 파일의 레이블 지정 사본이 되는 출력 파일의 전체 경로(예: `c:\\Test\\Test_labeled.docx`)입니다. |

## <a name="build-and-test-the-application"></a>애플리케이션 빌드 및 테스트

클라이언트 애플리케이션을 빌드하고 테스트합니다. 

1. F6 키(**솔루션 빌드**)를 사용하여 클라이언트 애플리케이션을 빌드합니다. 빌드 오류가 없으면 F5 키(**디버깅 시작**)를 사용하여 애플리케이션을 실행합니다.

2. 프로젝트가 성공적으로 빌드 및 실행되면 애플리케이션은 SDK가 `AcquireOAuth2Token()` 메서드를 호출할 때마다 액세스 토큰을 묻는 메시지를 표시합니다. 이전에 "민감도 레이블 나열" 빠른 시작에서 수행한 것처럼 제공된 값을 사용하여 매번 토큰을 가져오기 위한 PowerShell 스크립트를 실행합니다. 요청된 인증 및 리소스가 동일한 경우 `AcquireOAuth2Token()`이 이전에 생성된 토큰을 사용하려고 하면 다음을 수행할 수 있습니다.

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Sensitivity labels for your organization:
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
   Press any key to continue . . .

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/94f69844-8d34-4794-bde4-3ac89ad2b664/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

출력 파일을 열고 문서의 정보 보호 설정을 눈으로 확인하여 레이블이 적용되었는지 확인할 수 있습니다.

> [!NOTE]
> Office 문서에 레이블을 지정했으나 액세스 토큰을 획득한 Azure AD(Active Directory) 테넌트의 계정을 사용하여 로그인하지 않은 경우(민감도 레이블이 구성됨) 레이블이 지정된 문서를 열기 위해 먼저 로그인해야 할 수 있습니다. 



