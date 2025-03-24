---
title: 문서에 텍스트 밑줄 주석 추가
linktitle: 문서에 텍스트 밑줄 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 밑줄 주석을 추가하는 방법을 알아보세요. 손쉽게 협업과 커뮤니케이션을 강화하세요.
weight: 27
url: /ko/net/unlocking-annotation-power/add-text-underline-annotation/
---

# 문서에 텍스트 밑줄 주석 추가

## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 밑줄 주석을 추가하는 과정을 안내합니다. 텍스트 밑줄 주석은 중요한 구절이나 핵심 사항과 같은 문서의 특정 부분을 강조하는 데 유용할 수 있습니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설치되어 있는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: 다음에서 .NET용 GroupDocs.Annotation을 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: 시스템에 .NET Framework가 설치되어 있는지 확인하십시오.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 프로젝트로 가져오겠습니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

이제 예제를 여러 단계로 나누어 보겠습니다.
## 1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
이 단계에서는 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
## 2단계: 주석자 초기화
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 여기서는 인스턴스를 초기화합니다.`Annotator` 입력 문서의 경로를 제공하여 클래스를 생성합니다.
## 3단계: 밑줄 주석 만들기
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // Word 및 PDF 문서만 지원되는 작품
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
 이 단계에는`UnderlineAnnotation`글꼴 색상, 메시지, 불투명도, 페이지 번호, 배경색, 밑줄 색상, 점, 답글 등 다양한 속성을 가진 개체입니다.
## 4단계: 문서에 주석 추가
```csharp
annotator.Add(underline);
```
여기서는 문서에 밑줄 주석을 추가합니다.
## 5단계: 주석이 달린 문서 저장
```csharp
annotator.Save(outputPath);
```
마지막으로 주석이 달린 문서를 지정된 출력 경로에 저장합니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 밑줄 주석을 추가하는 방법을 배웠습니다. 이 강력한 라이브러리는 문서 공동 작업 및 커뮤니케이션을 향상시키는 다양한 주석 옵션을 제공합니다.
## FAQ
### 밑줄 주석의 모양을 사용자 정의할 수 있나요?
예, 요구 사항에 따라 색상, 불투명도, 위치 등의 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Annotation은 다른 문서 형식과 호환됩니까?
예, GroupDocs.Annotation은 Word 및 PDF를 포함한 광범위한 문서 형식을 지원합니다.
### 단일 문서에 여러 주석을 추가할 수 있나요?
물론, GroupDocs.Annotation을 사용하면 문서에 다양한 유형의 여러 주석을 추가할 수 있습니다.
### GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Annotation에 대한 지원은 어디서 받을 수 있나요?
 GroupDocs.Annotation 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).