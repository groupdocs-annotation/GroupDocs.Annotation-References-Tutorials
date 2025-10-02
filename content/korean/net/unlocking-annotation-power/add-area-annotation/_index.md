---
"description": "Groupdocs.Annotation for .NET으로 문서 협업을 강화하세요. 영역 주석을 추가하는 방법을 단계별로 알아보세요."
"linktitle": "문서에 영역 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 영역 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-area-annotation/"
type: docs
"weight": 10
---

# 문서에 영역 주석 추가

## 소개
이 튜토리얼에서는 Groupdocs.Annotation for .NET을 사용하여 문서에 영역 주석을 추가하는 과정을 안내합니다. 영역 주석은 사용자가 문서의 특정 영역을 강조 표시하여 콘텐츠의 명확성과 맥락을 제공할 수 있는 유용한 기능입니다.
## 필수 조건
시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.
1. .NET용 Groupdocs.Annotation: 필요한 라이브러리와 종속성이 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다. [웹사이트](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: .NET 개발에 적합한 개발 환경을 설정합니다.

## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 프로젝트에 가져오세요. 이 네임스페이스에는 애노테이션 작업에 필요한 클래스와 메서드가 포함되어 있습니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## 1단계: 출력 경로 초기화
주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: Annotator 초기화
인스턴스를 생성합니다 `Annotator` 문서의 경로를 매개변수로 전달하여 클래스를 만듭니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 들어갑니다
}
```
## 3단계: 영역 주석 만들기
배경색, 위치, 메시지, 불투명도 등 영역 주석의 속성을 정의합니다.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
문서에 영역 주석을 추가하려면 다음을 사용합니다. `Add` 방법 `Annotator` 사례.
```csharp
annotator.Add(area);
```
## 5단계: 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 성공 메시지 표시
문서에 성공적으로 주석이 달리고 저장되었음을 사용자에게 알립니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 튜토리얼에서는 Groupdocs.Annotation for .NET을 사용하여 문서에 영역 주석을 추가하는 방법을 알아보았습니다. 단계별 가이드를 따라 하면 유용한 주석으로 문서를 쉽게 개선하고 협업과 이해도를 높일 수 있습니다.
## 자주 묻는 질문
### 영역 주석의 모양을 사용자 정의할 수 있나요?
네, 배경색, 불투명도, 펜 스타일 등 다양한 측면을 튜토리얼에 맞게 사용자 지정할 수 있습니다.
### Groupdocs.Annotation은 다른 문서 형식과 호환됩니까?
네, Groupdocs.Annotation은 PDF, DOCX, PPTX 등 다양한 문서 형식을 지원합니다.
### 동일한 문서에 여러 개의 주석을 추가할 수 있나요?
물론입니다. 필요에 따라 동일한 문서에 다양한 유형의 주석을 여러 개 추가할 수 있습니다.
### Groupdocs.Annotation은 여러 플랫폼 간의 호환성을 제공합니까?
네, Groupdocs.Annotation은 .NET 프레임워크와 호환되므로 Windows, Linux, macOS 개발 환경에 적합합니다.
### 테스트 목적으로 사용할 수 있는 체험판이 있나요?
네, 무료 체험판을 이용하실 수 있습니다. [웹사이트](https://releases.groupdocs.com/).