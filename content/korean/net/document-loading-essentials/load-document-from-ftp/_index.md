---
title: FTP에서 문서 로드
linktitle: FTP에서 문서 로드
second_title: GroupDocs.Annotation .NET API
description: 원활한 문서 주석을 위해 GroupDocs.Annotation을 사용하여 .NET 애플리케이션을 강화하세요. 단계별 튜토리얼이 포함되어 있습니다.
weight: 12
url: /ko/net/document-loading-essentials/load-document-from-ftp/
---

# FTP에서 문서 로드

## 소개
.NET용 GroupDocs.Annotation은 .NET 애플리케이션 내에서 문서 주석 기능을 쉽게 사용할 수 있도록 설계된 다목적 라이브러리입니다. PDF, Microsoft Office 문서, 이미지 또는 기타 형식을 처리하는 경우 이 라이브러리는 주석, 강조 표시, 도형 등의 주석을 추가하여 공동 작업 및 문서 관리를 향상시키는 통합 솔루션을 제공합니다.
## 전제 조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. C#에 대한 지식: 이 튜토리얼에서 제공되는 코드 예제를 이해하고 구현하려면 C# 프로그래밍 언어에 대한 숙련도가 필수적입니다.
2.  .NET용 GroupDocs.Annotation: 다음에서 .NET용 GroupDocs.Annotation을 다운로드하여 설치하십시오.[다운로드 링크](https://releases.groupdocs.com/annotation/net/). 설치 지침에 따라 라이브러리를 .NET 프로젝트에 성공적으로 통합하세요.
## 네임스페이스 가져오기
.NET 기능용 GroupDocs.Annotation을 활용하려면 필수 네임스페이스를 C# 프로젝트로 가져와야 합니다. 다음과 같이하세요:

C# 프로젝트 내에서 코드 파일 시작 부분에 필요한 네임스페이스를 포함합니다.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

이제 FTP에서 문서를 로드하고 .NET용 GroupDocs.Annotation을 사용하여 문서에 주석을 추가하는 프로세스를 살펴보겠습니다.
## 1단계: 출력 경로 정의
주석이 달린 문서가 저장될 출력 경로를 지정합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: FTP에서 문서 로드
제공된 파일 경로를 사용하여 FTP 서버에서 문서를 검색합니다.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // 여기에 주석 코드가 추가됩니다.
}
```
## 3단계: 주석 추가
영역 주석과 같은 원하는 주석을 정의하고 문서에 추가합니다.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 4단계: 주석이 달린 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## 5단계: FTP에서 파일 검색
FTP 서버에서 파일을 가져오는 메서드를 구현합니다.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## 6단계: FTP 요청 생성
파일을 다운로드하려면 FTP 요청을 생성하세요.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## 7단계: 파일 스트림 가져오기
FTP 응답에서 파일 스트림을 검색합니다.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## 결론
결론적으로, .NET용 GroupDocs.Annotation은 개발자가 문서 주석 기능을 .NET 응용 프로그램에 원활하게 통합할 수 있도록 해줍니다. 이 튜토리얼에 설명된 단계별 가이드를 따르면 FTP에서 문서를 효율적으로 로드하고 주석을 쉽게 추가하여 애플리케이션 내에서 공동 작업과 문서 관리를 향상시킬 수 있습니다.
## FAQ
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
예, .NET용 GroupDocs.Annotation은 PDF, Microsoft Office 문서, 이미지 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Annotation을 사용하여 추가된 주석의 모양을 사용자 정의할 수 있습니까?
물론 .NET용 GroupDocs.Annotation은 색상, 스타일 및 모양을 포함하여 주석 모양에 대한 광범위한 사용자 정의 옵션을 제공합니다.
### .NET용 GroupDocs.Annotation은 클라우드 저장소 서비스를 지원합니까?
예, .NET용 GroupDocs.Annotation은 널리 사용되는 클라우드 저장소 서비스와 완벽하게 통합되어 Dropbox, Google Drive, OneDrive와 같은 서비스에서 문서를 로드하고 저장할 수 있습니다.
### .NET용 GroupDocs.Annotation에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드하여 .NET용 GroupDocs.Annotation의 기능을 탐색할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation에 대한 기술 지원이나 지원을 받으려면 어떻게 해야 합니까?
 기술 지원, 문제 해결 또는 일반 문의 사항이 있는 경우 .NET용 GroupDocs.Annotation을 방문하세요.[지원 포럼](https://forum.groupdocs.com/c/annotation/10).