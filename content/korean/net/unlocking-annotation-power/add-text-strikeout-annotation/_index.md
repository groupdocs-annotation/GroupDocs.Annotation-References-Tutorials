---
title: 문서에 텍스트 취소선 주석 추가
linktitle: 문서에 텍스트 취소선 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 취소선 주석을 추가하는 방법을 알아보세요. 협업 및 문서 검토 프로세스를 효율적으로 향상합니다.
weight: 26
url: /ko/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 취소선 주석을 추가하는 방법을 살펴보겠습니다. 이 라이브러리는 다양한 문서 유형에 주석을 추가하고 협업 및 문서 검토 프로세스를 향상시키는 강력한 도구를 제공합니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: 라이브러리를 설치합니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: .NET 개발에 적합한 개발 환경을 설정합니다.
3. 문서: PDF 파일과 같이 주석을 달 수 있는 문서를 준비합니다.

## 네임스페이스 가져오기
먼저 GroupDocs.Annotation의 기능에 액세스하는 데 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

이제 텍스트 취소선 주석을 추가하는 과정을 여러 단계로 나누어 보겠습니다.
## 1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
여기서는 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
## 2단계: 주석자 초기화
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
입력 문서(이 경우 PDF 파일)에 대한 경로를 제공하여 Annotator 개체를 초기화합니다.
## 3단계: 취소선 주석 생성
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    }
};
```
메시지, 불투명도, 페이지 번호, 배경색, 포인트(좌표), 답글 등 원하는 속성을 사용하여 StrikeoutAnnotation 객체를 만듭니다.
## 4단계: 주석 추가
```csharp
annotator.Add(strikeout);
```
생성된 취소선 주석을 문서에 추가합니다.
## 5단계: 문서 저장
```csharp
annotator.Save(outputPath);
```
주석이 달린 문서를 지정된 출력 경로에 저장합니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 취소선 주석을 추가하는 방법을 배웠습니다. 이 강력한 라이브러리는 효율적인 문서 주석을 가능하게 하여 협업 및 문서 검토 프로세스를 향상시킵니다.
## FAQ
### GroupDocs.Annotation은 다양한 문서 형식과 호환됩니까?
예, GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 주석의 모양을 맞춤설정할 수 있나요?
물론, 요구 사항에 따라 색상, 불투명도, 글꼴 크기 등과 같은 주석 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Annotation은 공동 작업 기능을 제공합니까?
예, GroupDocs.Annotation은 사용자가 문서에 설명, 회신 및 주석을 추가할 수 있도록 하여 공동 작업을 촉진합니다.
### 무료 평가판이 제공되나요?
 예, 다음에서 무료 평가판을 이용하실 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Annotation에 대한 지원은 어디서 받을 수 있나요?
 에서 지원을 받으실 수 있습니다.[GroupDocs.Annotation 포럼](https://forum.groupdocs.com/c/annotation/10).