---
title: 문서에 텍스트 구불구불한 주석 추가
linktitle: 문서에 텍스트 구불구불한 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 Groupdocs.Annotation을 사용하여 문서에 구불구불한 텍스트 주석을 손쉽게 추가하는 방법을 알아보세요. 협업 및 문서 검토 프로세스를 강화합니다.
weight: 25
url: /ko/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## 소개

.NET용 Groupdocs.Annotation은 개발자가 강력한 주석 기능을 .NET 응용 프로그램에 손쉽게 통합할 수 있게 해주는 다용도 라이브러리입니다. PDF, Word 문서 또는 기타 널리 사용되는 파일 형식으로 작업하는 경우 Groupdocs.Annotation은 주석을 추가하고 문서 공동 작업을 향상시키기 위한 완벽한 솔루션을 제공합니다.

## 전제 조건

튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

## 네임스페이스 가져오기

.NET용 Groupdocs.Annotation에서 제공하는 기능에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

이제 전제 조건을 다루었으므로 텍스트 구불구불한 주석을 추가하는 프로세스를 여러 단계로 나누어 보겠습니다.

## 1단계: 출력 경로 정의

주석이 달린 문서가 저장될 경로를 정의합니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2단계: 주석자 초기화

입력 문서 경로를 제공하여 Annotator 객체를 초기화합니다.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 표시됩니다.
}
```

## 3단계: 구불구불한 주석 만들기

SquigglyAnnotation 객체를 만들고 해당 속성을 지정합니다.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## 4단계: 주석 추가

생성된 구불구불한 주석을 문서에 추가합니다.

```csharp
annotator.Add(squiggly);
```

## 5단계: 문서 저장

주석이 달린 문서를 지정된 출력 경로에 저장합니다.

```csharp
annotator.Save(outputPath);
```

## 6단계: 표시 확인

주석이 달린 문서가 성공적으로 저장되었음을 확인하는 메시지를 표시합니다.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론

결론적으로, .NET용 Groupdocs.Annotation은 개발자에게 문서 주석 기능을 .NET 응용 프로그램에 원활하게 통합하기 위한 강력한 도구 세트를 제공합니다. 이 단계별 가이드를 따르면 문서에 텍스트 구불구불한 주석을 쉽게 추가하여 공동 작업 및 문서 검토 프로세스를 향상시킬 수 있습니다.

## FAQ

### Q: Groupdocs.Annotation은 다양한 파일 형식에 대한 주석을 지원할 수 있습니까?

A: 예, Groupdocs.Annotation은 PDF, Word 문서, Excel 시트 등을 포함한 광범위한 파일 형식에 대한 주석을 지원합니다.

### Q: Groupdocs.Annotation은 데스크톱 및 웹 응용 프로그램 모두와 호환됩니까?

답: 물론이죠! Groupdocs.Annotation은 데스크톱과 웹 응용 프로그램 모두에 원활하게 통합되어 유연성과 다양성을 제공할 수 있습니다.

### Q: Groupdocs.Annotation에 사용할 수 있는 라이센스 옵션이 있습니까?

A: 예, Groupdocs.Annotation은 시험용 임시 라이센스를 포함하여 개인 또는 기업의 요구에 맞게 조정된 유연한 라이센스 옵션을 제공합니다.

### Q: Groupdocs.Annotation을 사용하여 생성된 주석을 사용자 정의할 수 있습니까?

답: 물론이죠! Groupdocs.Annotation은 주석에 대한 광범위한 사용자 정의 옵션을 제공하므로 개발자는 특정 요구 사항에 맞게 주석을 조정할 수 있습니다.

### Q: Groupdocs.Annotation은 개발자를 위한 지원 및 문서를 제공합니까?

A: 그렇죠! Groupdocs.Annotation은 개발자가 해당 기능을 효과적으로 활용하는 데 도움이 되는 포괄적인 문서와 전용 지원 포럼을 제공합니다.