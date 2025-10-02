---
"description": "GroupDocs.Annotation for .NET을 사용하여 문서에 거리 주석을 추가하는 방법을 알아보세요. 협업과 커뮤니케이션을 손쉽게 향상시켜 보세요."
"linktitle": "문서에 거리 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 거리 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# 문서에 거리 주석 추가

## 소개
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 거리 주석을 추가하는 방법을 알아봅니다. 다음 단계에 따라 작업을 완료하세요.
## 필수 조건

계속 진행하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

- .NET 라이브러리용 GroupDocs.Annotation: .NET 라이브러리용 GroupDocs.Annotation을 다운로드하여 설치하세요. [이 링크](https://releases.groupdocs.com/annotation/net/).
- 주석을 달 문서: 거리 주석을 추가할 문서(예: PDF)를 준비합니다.
- 개발 환경: Visual Studio나 원하는 다른 IDE로 개발 환경을 설정하세요.

## 네임스페이스 가져오기

시작하기 전에 코드에 필요한 네임스페이스를 포함해야 합니다. 이러한 네임스페이스는 필요한 클래스와 메서드에 액세스하는 데 필수적입니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 1단계: Annotator 초기화

초기화로 시작하세요 `Annotator` 주석을 달고 싶은 문서의 경로가 있는 객체입니다.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 들어갑니다
}
```

## 2단계: 거리 주석 만들기

이제 생성하세요 `DistanceAnnotation` 객체를 만들고 상자 크기, 메시지, 불투명도, 펜 색상 등의 속성을 구성합니다.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## 3단계: 주석 추가

생성된 거리 주석을 문서에 추가하려면 다음을 사용합니다. `Add` 주석자 객체의 메서드.

```csharp
annotator.Add(distance);
```

## 4단계: 문서 저장

주석이 달린 문서를 시스템의 원하는 위치에 저장합니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 5단계: 확인 표시

마지막으로, 주석이 달린 문서가 성공적으로 저장되었음을 확인하는 메시지를 표시합니다.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론

GroupDocs.Annotation for .NET을 사용하여 문서에 거리 주석을 추가하는 것은 간단한 과정입니다. 이 튜토리얼에 설명된 단계를 따르면 유용한 주석으로 문서를 더욱 풍부하게 만들고, 협업과 소통을 더욱 원활하게 할 수 있습니다.

## 자주 묻는 질문

### 질문: 거리 주석의 모양을 사용자 지정할 수 있나요?

답변: 네, 색상, 불투명도, 선 스타일 등 다양한 속성을 요구 사항에 맞게 사용자 정의할 수 있습니다.

### 질문: GroupDocs.Annotation은 다양한 유형의 문서에 대한 주석을 지원합니까?

답변: 네, GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등 다양한 문서 형식에 대한 주석을 지원합니다.

### 질문: GroupDocs.Annotation에 대한 무료 평가판이 있나요?

A: 예, GroupDocs.Annotation의 무료 평가판에 액세스할 수 있습니다. [이 링크](https://releases.groupdocs.com/).

### 질문: .NET용 GroupDocs.Annotation에 대한 설명서는 어디에서 찾을 수 있나요?

A: 자세한 내용은 사용 가능한 문서를 참조하시면 됩니다. [여기](https://tutorials.groupdocs.com/annotation/net/).

### 질문: GroupDocs.Annotation에 대한 지원이나 도움을 받으려면 어떻게 해야 하나요?

A: GroupDocs.Annotation 커뮤니티 포럼에서 지원과 도움을 요청할 수 있습니다. [여기](https://forum.groupdocs.com/c/annotation/10).