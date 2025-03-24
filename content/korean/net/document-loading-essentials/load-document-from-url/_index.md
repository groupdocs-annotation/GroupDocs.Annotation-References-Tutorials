---
title: URL에서 문서 로드
linktitle: URL에서 문서 로드
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 프로그래밍 방식으로 PDF 문서에 주석을 추가하는 방법을 알아보세요. 코드 예제가 포함된 단계별 튜토리얼입니다.
weight: 15
url: /ko/net/document-loading-essentials/load-document-from-url/
---
## 소개
.NET용 GroupDocs.Annotation은 개발자가 .NET 응용 프로그램에 주석 기능을 쉽게 추가할 수 있도록 하는 기능이 풍부한 라이브러리입니다. GroupDocs.Annotation을 사용하면 프로그래밍 방식으로 PDF 문서에 주석을 달 수 있으므로 사용자는 텍스트 강조 표시, 주석 추가, 도형 그리기 등을 수행할 수 있습니다. 이 자습서에서는 URL에서 문서를 로드하고, 주석을 추가하고, GroupDocs.Annotation for .NET을 사용하여 주석이 달린 문서를 저장하는 단계를 안내합니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1. Visual Studio: 개발 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요.
2.  .NET용 GroupDocs.Annotation: 다음에서 .NET용 GroupDocs.Annotation을 다운로드하고 설치합니다.[웹사이트](https://releases.groupdocs.com/annotation/net/).
3. C# 기본 지식: C# 프로그래밍 언어에 익숙해집니다.
4. 인터넷 연결: 외부 리소스에 액세스하고 샘플 파일을 다운로드하려면 인터넷 연결이 필요합니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져옵니다.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## 1단계: URL에서 문서 로드
URL에서 PDF 문서에 주석을 추가하려면 다음 단계를 따르세요.
### 1.1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 1.2단계: URL 지정
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### 1.3단계: 문서 로드
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // 여기에 주석을 추가하세요.
    annotator.Save(outputPath);
}
```
## 2단계: 주석 추가
이제 로드된 문서에 주석을 추가해 보겠습니다. 이 예에서는 영역 주석을 추가합니다.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 3단계: 주석이 달린 문서 저장
마지막으로 주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 PDF 문서에 주석을 추가하는 방법을 배웠습니다. 단계별 가이드를 따르면 주석 기능을 .NET 애플리케이션에 원활하게 통합하여 사용자가 PDF 파일에서 효과적으로 공동 작업할 수 있습니다.

## FAQ
### .NET용 GroupDocs.Annotation은 모든 .NET 프레임워크와 호환됩니까?
예, .NET용 GroupDocs.Annotation은 .NET Framework, .NET Core 및 .NET Standard를 포함한 다양한 .NET 프레임워크와 호환됩니다.
### 주석의 모양을 맞춤설정할 수 있나요?
전적으로! .NET용 GroupDocs.Annotation은 광범위한 사용자 정의 옵션을 제공하므로 요구 사항에 따라 주석의 모양과 동작을 수정할 수 있습니다.
### .NET용 GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, 다음에서 .NET용 GroupDocs.Annotation 무료 평가판을 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 기술적인 문제가 발생하거나 .NET용 GroupDocs.Annotation에 대한 질문이 있는 경우 다음 담당자에게 도움을 요청할 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/annotation/10).
### .NET용 GroupDocs.Annotation 라이센스는 어디서 구매할 수 있나요?
 다음에서 .NET용 GroupDocs.Annotation 라이센스를 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy).