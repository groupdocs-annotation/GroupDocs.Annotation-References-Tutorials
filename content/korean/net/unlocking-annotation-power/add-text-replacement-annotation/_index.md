---
title: 문서에 텍스트 대체 주석 추가
linktitle: 문서에 텍스트 대체 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 .NET 문서에 텍스트 대체 주석을 손쉽게 추가하는 방법을 알아보세요. 문서 조작 능력을 강화하세요.
weight: 24
url: /ko/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 대체 주석을 추가하는 과정을 안내합니다. 이 강력한 라이브러리를 통해 개발자는 다양한 유형의 문서를 프로그래밍 방식으로 조작하고 주석을 달 수 있습니다. 이 자습서를 마치면 텍스트 대체 주석을 .NET 애플리케이션에 원활하게 통합하는 지식을 갖추게 됩니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설치되어 있는지 확인하세요.
### 1. .NET 프레임워크 설치
개발 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요. 마이크로소프트 홈페이지에서 다운로드 받으실 수 있습니다.
### 2. .NET 라이브러리용 GroupDocs.Annotation
 다음에서 .NET용 GroupDocs.Annotation 라이브러리를 다운로드하여 설치합니다.[웹사이트](https://releases.groupdocs.com/annotation/net/). 이 라이브러리는 다양한 문서 형식의 주석 작업에 필요한 도구와 기능을 제공합니다.
### 3. 개발 환경 설정
.NET 애플리케이션을 생성하고 실행하려면 Visual Studio 등 선호하는 개발 환경을 설정하세요.

## 네임스페이스 가져오기
코딩 부분을 살펴보기 전에 .NET용 GroupDocs.Annotation 작업에 필요한 필수 네임스페이스를 가져와 보겠습니다.
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## 1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
여기서는 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
## 2단계: 주석자 초기화
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 배치됩니다.
}
```
리소스의 적절한 폐기를 보장하기 위해 using 블록 내에서 입력 문서("input.pdf")를 지정하여 Annotator 개체를 초기화합니다.
## 3단계: 대체 주석 생성
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
여기서는 생성 날짜, 글꼴 색상, 메시지, 불투명도, 페이지 번호, 배경색, 포인트(좌표), 답글(댓글), 바꿀 텍스트 등 다양한 속성을 가진 replacementAnnotation 객체를 생성합니다.
## 4단계: 주석 추가
```csharp
annotator.Add(replacement);
```
생성된 대체 주석을 주석자에 추가합니다.
## 5단계: 문서 저장
```csharp
annotator.Save(outputPath);
```
마지막으로 주석이 달린 문서를 지정된 출력 경로에 저장합니다.
## 6단계: 성공 메시지 표시
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
문서가 성공적으로 저장되었음을 알리는 성공 메시지가 표시됩니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 대체 주석을 추가하는 프로세스를 다루었습니다. 단계별 가이드를 따르고 전제 조건을 이해하면 이 기능을 .NET 애플리케이션에 쉽게 통합할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Annotation을 사용하여 다양한 형식의 문서에 주석을 달 수 있나요?
예, .NET용 GroupDocs.Annotation은 PDF, DOCX, PPTX, XLSX 등과 같은 다양한 문서 형식에 주석을 달 수 있도록 지원합니다.
### .NET용 GroupDocs.Annotation은 데스크톱 및 웹 응용 프로그램 모두에 적합합니까?
예, .NET용 GroupDocs.Annotation은 데스크톱 및 웹 응용 프로그램 모두에서 사용할 수 있어 개발자에게 유연성을 제공합니다.
### .NET용 GroupDocs.Annotation을 사용하여 추가된 주석의 모양을 사용자 정의할 수 있습니까?
물론 색상, 불투명도, 글꼴 등과 같은 속성을 수정하여 주석의 모양을 사용자 정의할 수 있습니다.
### .NET용 GroupDocs.Annotation은 공동 주석 기능을 지원합니까?
예, .NET용 GroupDocs.Annotation은 공동 주석 기능을 제공하므로 여러 사용자가 동시에 문서에 주석을 달 수 있습니다.
### .NET용 GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
예, 다음 사이트에서 .NET용 GroupDocs.Annotation 무료 평가판을 이용하실 수 있습니다.[웹사이트](https://releases.groupdocs.com/).