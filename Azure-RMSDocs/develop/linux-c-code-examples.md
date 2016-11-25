---
title: "Linux 코드 예제 | Azure RMS"
description: "이 항목에서는 Linux 버전의 RMS SDK에 대한 중요한 시나리오 및 코드 요소를 소개합니다."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: cb0ce6cc8f4740ffc04b36b02392bed2c5f5490c


---

# <a name="linux-code-examples"></a>Linux 코드 예제

이 항목에서는 Linux 버전의 RMS SDK에 대한 중요한 시나리오 및 코드 요소를 소개합니다.

아래 코드 조각은 샘플 응용 프로그램 *rms\_sample* 및 *rmsauth\_sample*에서 가져온 것입니다. 자세한 내용은 GitHub 리포지토리에서 [샘플](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples)을 참조하세요.

## <a name="scenario-access-protection-policy-information-from-a-protected-file"></a>시나리오: 보호된 파일에서 보호 정책 정보 액세스

**RMS 보호된 파일 열고 읽기**
**소스**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 사용자로부터 파일 이름을 받은 후 인증서를 읽고(*MainWindow::addCertificates* 참조), 클라이언트 ID 및 리디렉션 URL을 사용하여 권한 부여 콜백을 설정하고, *ConvertFromPFile*을 호출하고(다음 코드 예제 참조), 보호 정책 이름, 설명 및 콘텐츠 유효 날짜를 읽습니다.

**C++**:

    void MainWindow::ConvertFromPFILE(const string& fileIn,
        const string& clientId,
        const string& redirectUrl,
        const string& clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileOut.c_str());
     return;
      }
    
    try
    {
    // create authentication context
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    auto pfs = PFileConverter::ConvertFromPFile(
      clientEmail,
      inFile,
      outFile,
      auth,
      this->consent);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e)
    {
    AddLog("ERROR: ", e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    }
    inFile->close();
    outFile->close();
    }

**보호된 파일 스트림 만들기**
**소스**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 이 메서드는 SDK 메서드 *ProtectedFileStream::Aquire*를 통해 전달된 지원 스트림에서 보호된 파일 스트림을 만듭니다. 보호된 파일 스트림은 호출자에게 반환됩니다.

**C++**:

    shared_ptr<GetProtectedFileStreamResult>PFileConverter::ConvertFromPFile(
    const string           & userId,
    shared_ptr<istream>      inStream,
    shared_ptr<iostream>     outStream,
    IAuthenticationCallback& auth,
    IConsentCallback       & consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast<ResponseCacheFlags>(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) && (fsResult->m_status == Success) &&
      (fsResult->m_stream != nullptr)) {
    auto pfs = fsResult->m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs->Size();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    }
      return fsResult;
    }

## <a name="scenario-create-a-new-protected-file-using-a-template"></a>시나리오: 템플릿을 사용하여 새 보호된 파일 만들기

**사용자가 선택한 템플릿을 사용하여 파일 보호**
**소스**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 사용자로부터 파일 이름을 받은 후 인증서를 읽고(*MainWindow::addCertificates* 참조), 클라이언트 ID 및 리디렉션 URL을 사용하여 권한 부여 콜백을 설정합니다. 선택한 파일은 *ConvertToPFileTemplates*를 호출하여 보호됩니다(다음 코드 예제 참조).

**C++**:

    void MainWindow::ConvertToPFILEUsingTemplates(const string& fileIn,
                                              const string& clientId,
                                              const string& redirectUrl,
                                              const string& clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this->consent, this->templates);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
   catch (const rmsauth::Exception& e) { AddLog("ERROR: ", e.error().c_str()); outFile->close(); remove(fileOut.c_str()); } catch (const rmscore::exceptions::RMSException& e) { AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**템플릿에서 만든 정책을 사용하여 파일 보호**
**소스**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 사용자와 연결된 템플릿 목록을 가져온 다음 선택한 템플릿을 사용하여 파일 보호에 사용되는 정책을 만듭니다.

**C++**:

    void PFileConverter::ConvertToPFileTemplates(const string           & userId,
                                             shared_ptr<istream>      inStream,
                                             const string           & fileExt,
                                             std::shared_ptr<iostream>outStream,
                                             IAuthenticationCallback& auth,
                                             IConsentCallback& /*consent*/,
                                             ITemplatesCallback     & templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos < templates.size()) {
    auto policy = UserPolicy::CreateFromTemplateDescriptor(
      templates[pos],
      userId,
      auth,
      USER_AllowAuditedExtraction,
      signedData);
   
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    }
    }

**정책이 제공되면 파일 보호**
**소스**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 지정된 정책을 사용하여 보호된 파일 스트림을 만든 다음 해당 파일을 보호합니다.

**C++**:

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr<UserPolicy>   policy,
                                               shared_ptr<istream>      inStream,
                                               const string           & fileExt,
                                               std::shared_ptr<iostream>outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream->Size();
    
    inStream->seekg(0, ios::end);
    totalSize = inStream->tellg();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream->Flush();
    }
    


## <a name="scenario-protect-a-file-using-custom-protection"></a>시나리오: 사용자 지정 보호를 사용하여 파일 보호

**사용자 지정 보호를 사용하여 파일 보호**
**소스**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 사용자로부터 파일 이름을 받은 후 인증서를 읽고(*MainWindow::addCertificates* 참조), 사용자로부터 권한 정보를 수집하고, 클라이언트 ID 및 리디렉션 URL을 사용하여 권한 부여 콜백을 설정합니다. 선택한 파일은 *ConvertToPFilePredefinedRights*를 호출하여 보호됩니다(다음 코드 예제 참조).

**C++**:

    void MainWindow::ConvertToPFILEUsingRights(const string            & fileIn,
                                           const vector<UserRights>& userRights,
                                           const string            & clientId,
                                           const string            & redirectUrl,
                                           const string            & clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog("ERROR: ", "Please fill email and check rights");
    return;
    }
    
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFilePredefinedRights(
      clientEmail,
      inFile,
      fileExt,
      outFile,
      auth,
      this->consent,
      userRights);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e) {
    AddLog("ERROR: ", e.error().c_str());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**사용자가 선택한 권한이 제공되면 보호 정책 만들기**
**소스**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**설명**: 정책 설명자를 만들고 사용자의 권한 정보로 채운 다음 정책 설명자를 사용하여 사용자 정책을 만듭니다. 이 정책은 *ConvertToPFileUsingPolicy* 호출을 통해 선택한 파일을 보호하는 데 사용됩니다(이 항목의 이전 섹션에 있는 설명 참조).

**C++**:

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            & userId,
    shared_ptr<istream>       inStream,
    const string            & fileExt,
    shared_ptr<iostream>      outStream,
    IAuthenticationCallback & auth,
    IConsentCallback& /*consent*/,
    const vector<UserRights>& userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared<string>("https://client.test.app"));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name("Test Name");
    desc.Description("Test Description");
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## <a name="workerthread-a-supporting-method"></a>WorkerThread - 지원 메서드


*WorkerThread()* 메서드는 두 개의 이전 예제 시나리오 **보호된 파일 스트림 만들기** 및 **정책이 제공되면 파일 보호**에서 다음과 같은 방식으로 호출됩니다.

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));


**지원 메서드 WorkerThread()**

**C++**:

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector<thread> threadPool;
    
    static void WorkerThread(shared_ptr<iostream>           stdStream,
                         shared_ptr<ProtectedFileStream>pStream,
                         bool                           modeWrite) {
    vector<uint8_t> buffer(4096);
    int64_t bufferSize = static_cast<int64_t>(buffer.size());
    
    while (totalSize - readPosition > 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition <= 0) {
      threadLocker.unlock();
      return;
    }
    
    // get read/write offset
    int64_t offsetRead  = readPosition;
    int64_t offsetWrite = writePosition;
    int64_t toProcess   = min(bufferSize, totalSize - readPosition);
    readPosition  += toProcess;
    writePosition += toProcess;
    
    // no need to lock more
    threadLocker.unlock();
    
    if (modeWrite) {
      // stdStream is not thread safe!!!
      try {
        threadLocker.lock();
    
        stdStream->seekg(offsetRead);
        stdStream->read(reinterpret_cast<char *>(&buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream->WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException("Error while writing data");
        }
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    } else {
      auto read =
        pStream->ReadAsync(&buffer[0],
                           toProcess,
                           offsetRead,
                           std::launch::deferred).get();
    
      if (read == 0) {
        break;
      }
    
      try {
        // stdStream is not thread safe!!!
        threadLocker.lock();
    
        // seek to write
        stdStream->seekp(offsetWrite);
        stdStream->write(reinterpret_cast<const char *>(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    }
    }
    }


## <a name="scenario-rms-authentication"></a>시나리오: RMS 인증

다음 예제에서는 UI를 사용하거나 UI 없이 Azure 인증 oAuth2 토큰을 가져오는 두 가지 인증 방법을 보여 줍니다.
**UI를 사용하여 oAuth2 인증 토큰 가져오기**
**소스**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**1단계**: **rmsauth::FileCache** 개체의 공유 지점을 만듭니다.
설명: 캐시 경로를 설정하거나 기본값을 사용할 수 있습니다.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**2단계**: **rmsauth::AuthenticationContext** 개체를 만듭니다. 설명: Azure *기관 URI* 및 *FileCache* 개체를 지정합니다.

**C++**:

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**3단계**: **authContext** 개체의 **aquireToken** 메서드를 호출하고 다음 매개 변수를 지정합니다. 설명:

-   *요청된 리소스* - 액세스하려는 보호된 리소스입니다.
-   *클라이언트 고유 ID* - 대체로 GUID입니다.
-   *리디렉션 URI* - 인증 토큰을 가져온 후 다시 주소가 지정되는 URI입니다.
-   *인증 프롬프트 동작* - **PromptBehavior::Auto**를 설정하면 라이브러리에서 필요한 경우 캐시 및 새로 고침 토큰을 사용하려고 합니다.
-   *사용자 ID* - 프롬프트 창에 표시되는 사용자 이름입니다.

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**4단계**: 결과에서 액세스 토큰을 가져옵니다. 설명: **result-> accessToken()** 메서드를 호출합니다.

**참고** 인증 라이브러리 메서드는 **rmsauth::Exception**을 발생시킬 수 있습니다.

 
**UI를 사용하지 않고 oAuth2 인증 토큰 가져오기**
**소스**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**1단계**: **rmsauth::FileCache** 개체의 공유 지점을 만듭니다. 설명: 캐시 경로를 설정하거나 기본값을 사용할 수 있습니다.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**2단계**: **UserCredential** 개체를 만듭니다. 설명: *사용자 로그인*과 *암호*를 지정합니다.

**C++**:

    auto userCred = std::make_shared<UserCredential>("john.smith@msopentechtest01.onmicrosoft.com",
                                                 "SomePass");


**3단계**: **rmsauth::AuthenticationContext** 개체를 만듭니다. 설명: Azure *기관 URI* 및 *FileCache* 개체를 지정합니다.

**C++**:

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**4단계**: **authContext**의 **aquireToken** 메서드를 호출하고 다음 매개 변수를 지정합니다.
-   *요청된 리소스* - 액세스하려는 보호된 리소스입니다.
-   *클라이언트 고유 ID* - 대체로 GUID입니다.
-   *사용자 자격 증명* - 생성된 개체를 전달합니다.

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**5단계**: 결과에서 액세스 토큰을 가져옵니다. 설명: **result-> accessToken()** 메서드를 호출합니다.

**참고** 인증 라이브러리 메서드는 **rmsauth::Exception**을 발생시킬 수 있습니다.




<!--HONumber=Nov16_HO2-->


