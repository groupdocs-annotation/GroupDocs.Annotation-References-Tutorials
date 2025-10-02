---
"description": "Groupdocs.Annotation for .NET을 사용하여 문서에 텍스트 주석을 손쉽게 추가하는 방법을 알아보세요. 협업 및 문서 검토 프로세스를 개선하세요."
"linktitle": "문서에 텍스트 물결 모양 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 텍스트 물결 모양 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# 문서에 텍스트 물결 모양 주석 추가

## 소개

Groupdocs.Annotation for .NET은 개발자가 강력한 주석 기능을 .NET 애플리케이션에 손쉽게 통합할 수 있도록 지원하는 다재다능한 라이브러리입니다. PDF, Word 문서 또는 기타 널리 사용되는 파일 형식 등 어떤 파일 형식을 사용하든 Groupdocs.Annotation은 주석을 추가하고 문서 협업을 향상시키는 완벽한 솔루션을 제공합니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

## 네임스페이스 가져오기

.NET용 Groupdocs.Annotation이 제공하는 기능에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

이제 전제 조건을 충족했으므로 텍스트 물결 모양 주석을 추가하는 과정을 여러 단계로 나누어 보겠습니다.

## 1단계: 출력 경로 정의

주석이 달린 문서가 저장될 경로를 정의합니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2단계: Annotator 초기화

입력 문서 경로를 제공하여 Annotator 객체를 초기화합니다.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 있습니다
}
```

## 3단계: 구불구불한 주석 만들기

SquigglyAnnotation 객체를 만들고 속성을 지정합니다.

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

## 6단계: 확인 표시

주석이 달린 문서가 성공적으로 저장되었음을 확인하는 메시지를 표시합니다.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론

결론적으로, Groupdocs.Annotation for .NET은 개발자에게 문서 주석 기능을 .NET 애플리케이션에 원활하게 통합할 수 있는 강력한 도구 세트를 제공합니다. 이 단계별 가이드를 따라 하면 텍스트 주석을 문서에 손쉽게 추가하여 협업 및 문서 검토 프로세스를 향상시킬 수 있습니다.

## 자주 묻는 질문

### 질문: Groupdocs.Annotation은 다양한 파일 형식에 대한 주석을 지원할 수 있나요?

답변: 네, Groupdocs.Annotation은 PDF, Word 문서, Excel 시트 등 다양한 파일 형식에 대한 주석을 지원합니다.

### 질문: Groupdocs.Annotation은 데스크톱과 웹 애플리케이션 모두와 호환됩니까?

A: 물론입니다! Groupdocs.Annotation은 데스크톱과 웹 애플리케이션 모두에 완벽하게 통합되어 유연성과 다양성을 제공합니다.

### 질문: Groupdocs.Annotation에 사용할 수 있는 라이선스 옵션이 있나요?

답변: 네, Groupdocs.Annotation은 개인이나 기업의 요구에 맞춰 유연한 라이선스 옵션을 제공하며, 여기에는 체험 목적의 임시 라이선스도 포함됩니다.

### 질문: Groupdocs.Annotation을 사용하여 만든 주석을 사용자 정의할 수 있나요?

A: 물론입니다! Groupdocs.Annotation은 주석에 대한 광범위한 사용자 정의 옵션을 제공하여 개발자가 특정 요구 사항에 맞게 주석을 맞춤 설정할 수 있도록 합니다.

### 질문: Groupdocs.Annotation은 개발자에게 지원과 문서화를 제공합니까?

A: 물론입니다! Groupdocs.Annotation은 개발자가 기능을 효과적으로 활용할 수 있도록 포괄적인 설명서와 전담 지원 포럼을 제공합니다.