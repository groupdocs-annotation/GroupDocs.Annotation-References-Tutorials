---
title: 문서에 텍스트 교정 주석 추가
linktitle: 문서에 텍스트 교정 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 PDF 문서에 텍스트 편집 주석을 추가하는 방법을 알아보세요. 민감한 정보를 손쉽게 보호하세요.
weight: 23
url: /ko/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# 문서에 텍스트 교정 주석 추가

## 소개
문서에 텍스트 편집 주석을 추가하는 것은 중요한 정보를 안전하게 관리하는 데 있어 중요한 단계가 될 수 있습니다. .NET용 GroupDocs.Annotation은 이를 원활하게 달성할 수 있는 강력한 솔루션을 제공합니다. 이 튜토리얼에서는 문서에 텍스트 수정 주석을 추가하는 과정을 단계별로 안내합니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: .NET용 GroupDocs.Annotation 라이브러리를 설치했는지 확인하세요. 다음에서 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: Visual Studio와 같은 .NET 호환 IDE를 사용하여 개발 환경을 설정합니다.

## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 프로젝트로 가져오겠습니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 정의
주석이 달린 문서를 저장할 출력 경로를 정의합니다. 액세스 가능하고 쓰기 가능한지 확인하세요.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석자 초기화
 입력 문서 경로로 주석자를 초기화합니다. 바꾸다`"input.pdf"` 문서의 경로와 함께.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 표시됩니다.
}
```
## 3단계: 텍스트 교정 주석 생성
 만들기`TextRedactionAnnotation`다음과 같은 필수 속성을 가진 객체`PageNumber`, `FontColor` , 그리고`Points`. 요구 사항에 따라 주석을 사용자 정의합니다.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## 4단계: 주석 추가 및 저장
생성된 Annotation을 Annotator를 이용하여 문서에 추가하고 지정된 출력 경로에 Annotation된 문서를 저장합니다.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 5단계: 출력 확인
마지막으로 문서가 지정된 출력 경로에 성공적으로 저장되었는지 확인합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 텍스트 교정 주석을 추가하는 과정을 살펴보았습니다. 이러한 단계를 통해 이제 문서 내의 민감한 정보를 안전하게 관리할 수 있습니다.
## FAQ
### 텍스트 수정 주석의 모양을 사용자 정의할 수 있나요?
예. 글꼴 색상, 채우기 색상, 불투명도 등 다양한 속성을 요구 사항에 맞게 사용자 정의할 수 있습니다.
### 구매하기 전에 체험판을 사용할 수 있나요?
 예, 다음에서 무료 평가판에 액세스할 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 GroupDocs.Annotation 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).
### 테스트 목적으로 임시 라이센스가 필요합니까?
 네, 임시 면허는 다음 기관에서 받으실 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/temporary-license/)시험용.
### 단일 문서에 여러 주석을 추가할 수 있나요?
물론, GroupDocs.Annotation을 사용하면 다양한 유형의 주석과 여러 인스턴스를 단일 문서에 추가할 수 있습니다.