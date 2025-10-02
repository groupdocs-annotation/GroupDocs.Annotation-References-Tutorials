---
"description": "GroupDocs.Annotation for .NET을 사용하여 PDF에 점 주석을 추가하는 방법을 알아보세요. 원활한 통합을 위한 단계별 가이드입니다."
"linktitle": "문서에 포인트 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 포인트 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# 문서에 포인트 주석 추가

## 소개
GroupDocs.Annotation for .NET은 개발자가 다양한 유형의 주석을 프로그래밍 방식으로 문서에 추가할 수 있는 강력한 도구입니다. 이 튜토리얼에서는 C#을 사용하여 문서에 Point Annotation을 추가하는 방법을 중점적으로 살펴보겠습니다.
## 필수 조건
시작하기에 앞서 다음 사항이 있는지 확인하세요.
1. C# 프로그래밍 언어에 대한 기본적인 이해.
2. 시스템에 Visual Studio가 설치되어 있어야 합니다.
3. .NET 라이브러리용 GroupDocs.Annotation이 설치되었습니다. 다음에서 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/annotation/net/).

## 필요한 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
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
## 2단계: Annotator 초기화
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
여기서 우리는 초기화합니다 `Annotator` 입력 문서("input.pdf")가 있는 개체입니다.
## 3단계: 포인트 주석 만들기
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
이 단계에서는 다음을 생성합니다. `PointAnnotation` 객체를 만들고 위치, 메시지, 페이지 번호, 답변 등의 속성을 지정합니다.
## 4단계: 주석 추가
```csharp
annotator.Add(point);
```
여기서는 생성된 포인트 주석을 문서에 추가합니다.
## 5단계: 문서 저장
```csharp
annotator.Save(outputPath);
```
마지막으로, 주석이 달린 문서를 지정된 출력 경로에 저장합니다.

## 결론
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 Point Annotation을 추가하는 방법을 알아보았습니다. 이 강력한 라이브러리를 사용하면 주석 기능을 통합하여 문서 관리 애플리케이션을 더욱 강화할 수 있습니다.
## 자주 묻는 질문
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
네, GroupDocs.Annotation for .NET은 PDF, Microsoft Word, Excel, PowerPoint 등 다양한 문서 형식을 지원합니다.
### 주석의 모양을 사용자 지정할 수 있나요?
물론입니다! GroupDocs.Annotation for .NET은 애플리케이션의 필요에 맞게 주석의 모양을 사용자 지정할 수 있는 다양한 옵션을 제공합니다.
### GroupDocs.Annotation for .NET에 대한 무료 평가판이 있나요?
네, 무료 체험판을 이용하실 수 있습니다. [여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation과 관련된 문제나 문의사항에 대한 지원을 받으려면 어떻게 해야 하나요?
GroupDocs.Annotation 포럼에서 지원을 받을 수 있습니다. [여기](https://forum.groupdocs.com/c/annotation/10).
### 테스트 목적으로 임시 면허를 얻을 수 있나요?
네, 임시면허를 취득할 수 있습니다. [여기](https://purchase.groupdocs.com/temporary-license/).