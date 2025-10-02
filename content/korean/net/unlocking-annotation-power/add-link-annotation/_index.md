---
"description": "Groupdocs.Annotation for .NET을 사용하여 문서에 링크 주석을 추가하는 방법을 알아보세요. 협업과 상호 작용성을 손쉽게 향상시키세요."
"linktitle": "문서에 링크 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 링크 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-link-annotation/"
type: docs
"weight": 16
---

# 문서에 링크 주석 추가

## 소개
Groupdocs.Annotation for .NET은 개발자가 포괄적인 주석 기능을 .NET 애플리케이션에 손쉽게 통합할 수 있도록 지원하는 강력한 라이브러리입니다. 주요 기능 중 하나는 문서에 링크 주석을 추가하여 협업과 상호 작용을 향상시키는 기능입니다.
## 필수 조건
링크 주석을 추가하는 과정을 시작하기에 앞서, 다음과 같은 전제 조건이 충족되었는지 확인하세요.
- C# 프로그래밍 언어에 대한 기본적인 이해.
- .NET 라이브러리에 Groupdocs.Annotation을 설치했습니다.
- 주석을 달고 싶은 문서에 접근합니다.

## 네임스페이스 가져오기
먼저, .NET 기능에 Groupdocs.Annotation을 활용하는 데 필요한 네임스페이스를 가져와야 합니다. 이를 통해 애플리케이션에서 문서에 주석을 추가하는 데 필요한 클래스와 메서드에 액세스할 수 있습니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 설정
주석이 달린 문서를 저장할 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: Annotator 초기화
인스턴스를 생성합니다 `Annotator` 주석을 달고 싶은 문서의 경로를 제공하여 클래스를 만듭니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 들어갑니다
}
```
## 3단계: 링크 주석 만들기
정의하다 `LinkAnnotation` 객체를 만들고 메시지, 불투명도, 페이지 번호, 배경색, 포인트, 회신, URL 등의 속성을 지정합니다.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## 4단계: 주석 추가
생성된 링크 주석을 문서에 추가하려면 다음을 사용합니다. `Add` 주석자 인스턴스의 메서드입니다.
```csharp
annotator.Add(link);
```
## 5단계: 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 성공 메시지 표시
주석이 달린 문서가 성공적으로 저장되었음을 사용자에게 알립니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
결론적으로, 위 단계를 따르면 Groupdocs.Annotation for .NET을 사용하여 문서에 링크 주석을 원활하게 추가할 수 있습니다. 이를 통해 문서 협업이 향상되고 사용자에게 대화형 기능이 제공됩니다.
## 자주 묻는 질문
### Groupdocs.Annotation for .NET은 모든 유형의 문서와 호환됩니까?
.NET용 Groupdocs.Annotation은 PDF, Word, Excel 등 다양한 문서 형식을 지원합니다.
### 주석의 모양을 사용자 지정할 수 있나요?
네, 색상, 불투명도, 크기 등 주석의 다양한 속성을 요구 사항에 맞게 사용자 정의할 수 있습니다.
### .NET용 Groupdocs.Annotation은 실시간 협업 기능을 제공합니까?
네, .NET용 Groupdocs.Annotation은 여러 사용자가 동시에 문서에 주석을 달 수 있는 실시간 협업 기능을 제공합니다.
### Groupdocs 제품에 대한 기술 지원을 받을 수 있나요?
예, Groupdocs 제품에 대한 기술 지원은 포럼과 지원을 통해 제공됩니다. [여기](https://forum.groupdocs.com/c/annotation/10).
### 구매하기 전에 Groupdocs.Annotation for .NET을 사용해 볼 수 있나요?
예, 구매하기 전에 .NET용 Groupdocs.Annotation의 무료 평가판을 활용하여 기능을 살펴볼 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).