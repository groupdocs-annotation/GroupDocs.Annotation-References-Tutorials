---
title: 문서에 거리 주석 추가
linktitle: 문서에 거리 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 거리 주석을 추가하는 방법을 알아보세요. 손쉽게 협업과 커뮤니케이션을 강화하세요.
weight: 12
url: /ko/net/unlocking-annotation-power/add-distance-annotation/
---

# 문서에 거리 주석 추가

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 거리 주석을 추가하는 방법을 배웁니다. 작업을 완료하려면 다음 단계를 따르세요.
## 전제 조건

계속하기 전에 다음 전제조건이 충족되었는지 확인하십시오.

-  .NET 라이브러리용 GroupDocs.Annotation: 다음 위치에서 .NET 라이브러리용 GroupDocs.Annotation을 다운로드하고 설치합니다.[이 링크](https://releases.groupdocs.com/annotation/net/).
- 주석을 달 문서: 거리 주석을 추가할 문서(예: PDF)를 준비합니다.
- 개발 환경: Visual Studio 또는 원하는 다른 IDE를 사용하여 개발 환경을 설정합니다.

## 네임스페이스 가져오기

시작하기 전에 코드에 필요한 네임스페이스를 포함했는지 확인하세요. 이러한 네임스페이스는 필수 클래스와 메서드에 액세스하는 데 필수적입니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 1단계: 주석자 초기화

 초기화부터 시작하세요.`Annotator` 주석을 달고 싶은 문서의 경로를 개체에 추가하세요.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 표시됩니다.
}
```

## 2단계: 거리 주석 생성

 이제`DistanceAnnotation` 상자 크기, 메시지, 불투명도, 펜 색상 등과 같은 개체의 속성을 구성합니다.

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

 생성된 거리 주석을 다음을 사용하여 문서에 추가합니다.`Add` 주석자 개체의 메서드입니다.

```csharp
annotator.Add(distance);
```

## 4단계: 문서 저장

주석이 달린 문서를 시스템의 원하는 위치에 저장합니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 5단계: 표시 확인

마지막으로 주석이 달린 문서가 성공적으로 저장되었음을 확인하는 메시지를 표시합니다.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론

.NET용 GroupDocs.Annotation을 사용하여 문서에 거리 주석을 추가하는 과정은 간단합니다. 이 튜토리얼에 설명된 단계를 따르면 귀중한 주석을 추가하여 문서를 개선하고 더 나은 협업과 커뮤니케이션을 촉진할 수 있습니다.

## FAQ

### Q: 거리 주석의 모양을 사용자 정의할 수 있습니까?

A: 예, 색상, 불투명도, 선 스타일 등과 같은 다양한 속성을 요구 사항에 맞게 사용자 정의할 수 있습니다.

### Q: GroupDocs.Annotation은 다양한 유형의 문서에 대한 주석을 지원합니까?

A: 예, GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식에 대한 주석을 지원합니다.

### Q: GroupDocs.Annotation에 대한 무료 평가판이 있습니까?

 A: 예, 다음에서 GroupDocs.Annotation 무료 평가판에 액세스할 수 있습니다.[이 링크](https://releases.groupdocs.com/).

### Q: .NET용 GroupDocs.Annotation 설명서는 어디에서 찾을 수 있습니까?

 A: 사용 가능한 자세한 문서를 참조할 수 있습니다.[여기](https://tutorials.groupdocs.com/annotation/net/).

### 질문: GroupDocs.Annotation에 대한 지원을 받으려면 어떻게 해야 합니까?

 A: GroupDocs.Annotation 커뮤니티 포럼에서 지원을 구할 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).