---
title: 문서에 점 주석 추가
linktitle: 문서에 점 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 PDF에 점 주석을 추가하는 방법을 알아보세요. 원활한 통합을 위한 단계별 가이드입니다.
weight: 17
url: /ko/net/unlocking-annotation-power/add-point-annotation/
---
## 소개
.NET용 GroupDocs.Annotation은 개발자가 프로그래밍 방식으로 문서에 다양한 유형의 주석을 추가할 수 있는 강력한 도구입니다. 이 튜토리얼에서는 C#을 사용하여 문서에 점 주석을 추가하는 방법에 중점을 둘 것입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1. C# 프로그래밍 언어에 대한 기본 이해.
2. 시스템에 Visual Studio가 설치되어 있습니다.
3.  .NET 라이브러리용 GroupDocs.Annotation이 설치되었습니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).

## 필요한 네임스페이스 가져오기
시작하려면 필수 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
이 단계에서는 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
## 2단계: 주석자 초기화
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 여기서는`Annotator` 입력 문서("input.pdf")가 있는 개체입니다.
## 3단계: 점 주석 생성
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 이 단계에서는`PointAnnotation` 위치, 메시지, 페이지 번호, 회신 등의 속성을 지정합니다.
## 4단계: 주석 추가
```csharp
annotator.Add(point);
```
여기서는 생성된 점 주석을 문서에 추가합니다.
## 5단계: 문서 저장
```csharp
annotator.Save(outputPath);
```
마지막으로 주석이 달린 문서를 지정된 출력 경로에 저장합니다.

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 점 주석을 추가하는 방법을 배웠습니다. 이 강력한 라이브러리를 사용하면 주석 기능을 통합하여 문서 관리 애플리케이션을 향상시킬 수 있습니다.
## FAQ
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
예, .NET용 GroupDocs.Annotation은 PDF, Microsoft Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 주석의 모양을 맞춤설정할 수 있나요?
전적으로! .NET용 GroupDocs.Annotation은 응용 프로그램의 요구 사항에 맞게 주석 모양을 사용자 정의할 수 있는 광범위한 옵션을 제공합니다.
### .NET용 GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 이용하실 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation과 관련된 문제나 쿼리에 대한 지원을 받으려면 어떻게 해야 합니까?
 GroupDocs.Annotation 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).
### 테스트 목적으로 임시 라이센스를 얻을 수 있나요?
 예, 다음에서 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).