---
"description": "GroupDocs.Annotation for .NET을 사용하여 문서에 워터마크 주석을 손쉽게 추가하는 방법을 알아보세요. 문서의 명확성과 보안을 강화하세요."
"linktitle": "문서에 워터마크 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 워터마크 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# 문서에 워터마크 주석 추가

## 소개
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 워터마크 주석을 추가하는 과정을 살펴보겠습니다. 워터마크 주석은 문서의 상태를 표시하거나, 기밀로 표시하거나, 기타 관련 정보를 추가하는 데 유용합니다.

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

1. .NET용 GroupDocs.Annotation: 여기에서 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: 시스템에 Visual Studio가 설치되어 있는지 확인하세요.
3. C#에 대한 기본 지식: 코드 예제를 이해하고 구현하려면 C# 프로그래밍 언어에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

코딩을 시작하기 전에 필요한 네임스페이스를 가져와 보겠습니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

이제 워터마크 주석을 추가하는 과정을 여러 단계로 나누어 살펴보겠습니다.

## 1단계: 출력 경로 정의

먼저, 주석이 달린 문서가 저장될 출력 경로를 정의해야 합니다. `Path` 에서 수업 `System.IO` 출력 디렉토리 경로를 파일 이름과 결합하는 네임스페이스입니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2단계: Annotator 초기화

다음으로, 입력 문서의 경로를 제공하여 주석 작성자를 초기화합니다. 이를 통해 문서에 주석을 추가할 수 있습니다.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 들어갑니다
}
```

## 3단계: 워터마크 주석 만들기

이제 각도, 위치, 텍스트, 글꼴 색상, 불투명도 등 원하는 속성을 사용하여 워터마크 주석 객체를 만들어 보겠습니다.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## 4단계: 워터마크 주석 추가

이제 다음을 사용하여 문서에 워터마크 주석을 추가합니다. `Add` 주석자 객체의 메서드.

```csharp
annotator.Add(watermark);
```

## 5단계: 문서 저장

마지막으로, 주석이 달린 문서를 지정된 출력 경로에 저장합니다.

```csharp
annotator.Save(outputPath);
```

## 결론

이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 워터마크 주석을 추가하는 방법을 알아보았습니다. 워터마크 주석은 문서에 관련 정보를 표시하거나 문서의 상태를 나타내는 데 유용한 도구입니다.

## 자주 묻는 질문

### 질문: 워터마크 주석의 모양을 사용자 지정할 수 있나요?

답변: 네, 텍스트, 글꼴 크기, 색상, 불투명도, 위치 등 다양한 속성을 사용자 지정하여 요구 사항에 맞게 워터마크를 맞춤 설정할 수 있습니다.

### 질문: .NET용 GroupDocs.Annotation은 다양한 문서 형식과 호환됩니까?

답변: 네, GroupDocs.Annotation은 PDF, Microsoft Word, Excel, PowerPoint, 이미지 형식을 포함한 다양한 문서 형식을 지원합니다.

### 질문: 하나의 문서에 여러 개의 주석을 추가할 수 있나요?

답변: 물론입니다. GroupDocs.Annotation을 사용하면 다양한 유형의 주석을 하나의 문서에 추가하여 포괄적인 문서 마크업이 가능합니다.

### 질문: GroupDocs.Annotation은 협업 주석 기능을 지원합니까?

답변: 네, GroupDocs.Annotation을 사용하면 사용자가 댓글, 답변, 주석을 추가할 수 있어 공동 주석 작업이 용이해지고, 팀원 간의 효과적인 협업이 촉진됩니다.

### 질문: GroupDocs.Annotation for .NET의 평가판이 있나요?

A: 네, 무료 체험판을 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/).