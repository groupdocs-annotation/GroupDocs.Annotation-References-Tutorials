---
title: 문서에 텍스트 강조 주석 추가
linktitle: 문서에 텍스트 강조 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 강조 주석을 추가하는 방법을 알아보세요. 이 포괄적인 기능을 통해 협업과 생산성을 향상하세요.
weight: 22
url: /ko/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# 문서에 텍스트 강조 주석 추가

## 소개
문서 관리 및 공동 작업 영역에서 .NET용 GroupDocs.Annotation은 개발자가 텍스트 강조 주석을 응용 프로그램에 원활하게 통합할 수 있도록 지원하는 강력한 솔루션으로 등장합니다. 이 튜토리얼은 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 강조 주석을 추가하는 방법에 대한 포괄적인 가이드 역할을 합니다. 단계별 지침과 자세한 설명을 통해 이 강력한 라이브러리의 기능을 활용하는 데 능숙해질 것입니다.
## 전제 조건
텍스트 강조 주석 구현을 자세히 알아보기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. 환경 설정: .NET 개발에 적합한 개발 환경을 구성합니다.
2.  .NET용 GroupDocs.Annotation 설치: 제공된 파일에서 .NET용 GroupDocs.Annotation을 다운로드하여 설치합니다.[다운로드 링크](https://releases.groupdocs.com/annotation/net/).
3. C#에 대한 지식: C# 프로그래밍 언어에 대한 기본적인 이해.
4. 주석을 달 문서: 주석을 달려는 문서(예: PDF)를 준비합니다.

## 네임스페이스 가져오기
시작하려면 C# 코드에 필요한 네임스페이스를 가져와서 .NET용 GroupDocs.Annotation의 기능을 활용하세요.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#이제 텍스트 강조 주석을 추가하는 과정을 여러 단계로 나누어 보겠습니다.
## 1단계: 출력 경로 정의
주석이 달린 문서가 저장될 출력 경로를 지정합니다:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석자 초기화
 인스턴스를 생성합니다.`Annotator` 클래스, 문서 파일 이름을 매개변수로 전달:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 3단계: 하이라이트 주석 생성
 인스턴스화`HighlightAnnotation` 개체를 만들고 해당 속성을 구성합니다.
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
생성된 하이라이트 주석을 문서에 추가합니다.
```csharp
annotator.Add(highlight);
```
## 5단계: 주석이 달린 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```

## 결론
결론적으로 .NET용 GroupDocs.Annotation은 텍스트 강조 주석을 문서에 통합하는 효율적인 접근 방식을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 개발자는 애플리케이션 내에서 문서 공동 작업과 생산성을 원활하게 향상시킬 수 있습니다.
## FAQ
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
.NET용 GroupDocs.Annotation은 PDF, Word, Excel 등을 포함한 다양한 문서 형식을 지원합니다. 전체 목록은 설명서를 참조하세요.
### 특정 요구사항에 따라 주석을 맞춤설정할 수 있나요?
예, 개발자는 주석의 속성과 모양을 완전히 제어할 수 있으므로 다양한 요구 사항을 충족할 수 있는 사용자 정의가 가능합니다.
### .NET용 GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, 제공된 무료 평가판에 액세스하여 .NET용 GroupDocs.Annotation의 기능을 탐색할 수 있습니다.[링크](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation과 관련된 문제나 쿼리에 대한 지원을 받으려면 어떻게 해야 합니까?
 지원 및 도움이 필요하면 GroupDocs.Annotation 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/annotation/10).
### .NET용 GroupDocs.Annotation에 어떤 라이센스 옵션을 사용할 수 있습니까?
 .NET용 GroupDocs.Annotation은 테스트 목적을 위한 임시 라이센스와 프로덕션 환경을 위한 상용 라이센스를 포함하여 다양한 라이센스 옵션을 제공합니다. 구매 페이지 방문[여기](https://purchase.groupdocs.com/buy) 상세 사항은.