---
"description": "GroupDocs.Annotation을 사용하여 .NET에서 문서에 줄임표 주석을 추가하는 방법을 알아보세요. 협업과 커뮤니케이션을 손쉽게 향상시켜 보세요."
"linktitle": "문서에 타원 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 타원 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# 문서에 타원 주석 추가

## 소개
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 줄임표 주석을 추가하는 방법을 알아봅니다. 이 단계별 가이드는 각 단계를 명확하게 이해할 수 있도록 과정을 안내합니다.
## 필수 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET을 다운로드하여 설치했는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/annotation/net/).
2. IDE(통합 개발 환경): 코드를 작성하고 실행하려면 Visual Studio와 같은 IDE가 시스템에 설치되어 있어야 합니다.

## 네임스페이스 가져오기
먼저 프로젝트에 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 설정
주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: Annotator 초기화
입력 문서 경로를 제공하여 주석자를 초기화합니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3단계: 타원 주석 만들기
인스턴스를 생성합니다 `EllipseAnnotation` 클래스를 만들고 속성을 설정합니다.
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## 4단계: 주석 추가
문서에 타원 주석을 추가합니다.
```csharp
annotator.Add(ellipse);
```
## 5단계: 문서 저장
주석이 달린 문서를 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```

## 결론
축하합니다! GroupDocs.Annotation for .NET을 사용하여 문서에 타원 주석을 성공적으로 추가했습니다. 이제 이 기능을 .NET 애플리케이션에 통합하여 문서 협업 및 커뮤니케이션을 향상시킬 수 있습니다.
## 자주 묻는 질문
### 타원 주석의 모양을 사용자 지정할 수 있나요?
네, 배경색, 테두리 색상, 불투명도 등 다양한 속성을 요구 사항에 맞게 사용자 지정할 수 있습니다.
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
.NET용 GroupDocs.Annotation은 PDF, DOCX, PPTX, XLSX 등 다양한 문서 형식을 지원합니다.
### 하나의 문서에 여러 개의 주석을 추가할 수 있나요?
네, 줄임표, 사각형, 텍스트 등 여러 개의 주석을 하나의 문서에 추가할 수 있습니다.
### 테스트 목적으로 사용할 수 있는 체험판이 있나요?
네, 무료 평가판을 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/) 그 기능을 평가합니다.
### .NET용 GroupDocs.Annotation에 대한 기술 지원은 어디에서 받을 수 있나요?
GroupDocs.Annotation 커뮤니티 포럼에서 기술 지원을 받을 수 있습니다. [여기](https://forum.groupdocs.com/c/annotation/10).