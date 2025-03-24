---
title: 문서에 워터마크 주석 추가
linktitle: 문서에 워터마크 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 워터마크 주석을 쉽게 추가하는 방법을 알아보세요. 문서의 명확성과 보안을 강화합니다.
weight: 28
url: /ko/net/unlocking-annotation-power/add-watermark-annotation/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 워터마크 주석을 추가하는 과정을 안내합니다. 워터마크 주석은 문서의 상태를 표시하거나 기밀로 표시하거나 기타 관련 정보를 추가하는 데 유용합니다.

## 전제 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  .NET용 GroupDocs.Annotation: 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: 시스템에 Visual Studio가 설치되어 있는지 확인하세요.
3. C#에 대한 기본 지식: 코드 예제를 이해하고 구현하려면 C# 프로그래밍 언어에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

코딩을 시작하기 전에 필요한 네임스페이스를 가져오겠습니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

이제 워터마크 주석을 추가하는 과정을 여러 단계로 나누어 보겠습니다.

## 1단계: 출력 경로 정의

 먼저 주석이 달린 문서가 저장될 출력 경로를 정의해야 합니다. 우리는`Path` 수업`System.IO` 출력 디렉터리 경로를 파일 이름과 결합하는 네임스페이스입니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2단계: 주석자 초기화

다음으로 입력 문서의 경로를 제공하여 어노테이터를 초기화하겠습니다. 이를 통해 문서에 주석을 추가할 수 있습니다.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 표시됩니다.
}
```

## 3단계: 워터마크 주석 생성

이제 각도, 위치, 텍스트, 글꼴 색상, 불투명도 등 원하는 속성을 가진 워터마크 주석 개체를 만들어 보겠습니다.

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

 이제 다음을 사용하여 문서에 워터마크 주석을 추가하겠습니다.`Add` 주석자 개체의 메서드입니다.

```csharp
annotator.Add(watermark);
```

## 5단계: 문서 저장

마지막으로 주석이 달린 문서를 지정된 출력 경로에 저장합니다.

```csharp
annotator.Save(outputPath);
```

## 결론

이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 워터마크 주석을 추가하는 방법을 배웠습니다. 워터마크 주석은 문서에 관련 정보를 표시하거나 상태를 표시하는 데 유용한 도구입니다.

## FAQ

### 질문: 워터마크 주석의 모양을 사용자 정의할 수 있습니까?

A: 예, 텍스트, 글꼴 크기, 색상, 불투명도, 위치 등과 같은 다양한 속성을 사용자 정의하여 요구 사항에 따라 워터마크를 맞춤화할 수 있습니다.

### Q: .NET용 GroupDocs.Annotation은 다른 문서 형식과 호환됩니까?

A: 예, GroupDocs.Annotation은 PDF, Microsoft Word, Excel, PowerPoint 및 이미지 형식을 포함한 광범위한 문서 형식을 지원합니다.

### Q: 단일 문서에 여러 주석을 추가할 수 있나요?

A: 물론 GroupDocs.Annotation을 사용하면 단일 문서에 다양한 유형의 여러 주석을 추가할 수 있으므로 포괄적인 문서 마크업이 가능합니다.

### Q: GroupDocs.Annotation은 공동 주석을 지원합니까?

A: 예, GroupDocs.Annotation은 사용자가 설명, 회신 및 주석을 추가할 수 있도록 하여 팀 구성원 간의 효과적인 공동 작업을 촉진함으로써 공동 주석 작업을 촉진합니다.

### Q: .NET용 GroupDocs.Annotation에 사용할 수 있는 평가판이 있습니까?

 A: 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).