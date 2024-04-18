---
title: 텍스트 위에 이미지 주석 넣기
linktitle: 텍스트 위에 이미지 주석 넣기
second_title: GroupDocs.Annotation .NET API
description: 효율적인 문서 관리 및 공동 작업을 위해 GroupDocs.Annotation을 사용하여 .NET에서 텍스트 위에 이미지 주석을 추가하는 방법을 알아보세요.
type: docs
weight: 21
url: /ko/net/advanced-usage/put-image-annotation-over-text/
---
## 소개
.NET 개발 분야에서 GroupDocs.Annotation은 문서에 주석을 추가하여 공동 작업과 문서 관리를 더욱 효율적으로 만드는 강력한 솔루션을 제공합니다. 일반적인 요구 사항 중 하나는 텍스트 위에 이미지 주석을 추가하는 것인데, 이는 .NET용 GroupDocs.Annotation을 사용하여 원활하게 수행할 수 있습니다.
## 전제 조건
.NET용 GroupDocs.Annotation을 사용하여 텍스트 위에 이미지 주석을 추가하는 프로세스를 시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Annotation: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET IDE와 같은 적합한 개발 환경을 설정합니다.
3. 문서 및 이미지 파일: 주석에 사용할 문서 파일(PDF, DOCX 등)과 이미지 파일을 준비합니다.
4. C#에 대한 기본 이해: 이 자습서에서 제공되는 코드 조각을 구현하려면 C# 프로그래밍 언어에 대한 지식이 필요합니다.

## 네임스페이스 가져오기
주석 프로세스를 진행하기 전에 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1단계: 출력 경로 정의
먼저 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 2단계: 주석자 초기화
 초기화`Annotator` 입력 문서 경로를 제공하여 객체:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 표시됩니다.
}
```
## 3단계: 이미지 주석 생성
 만들기`ImageAnnotation` 상자 크기, 불투명도, 페이지 번호, 이미지 경로 및 Z-색인과 같은 원하는 속성을 가진 개체:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## 4단계: 주석 추가
 다음을 사용하여 문서에 이미지 주석을 추가합니다.`Add` 의 방법`Annotator` 물체:
```csharp
annotator.Add(image);
```
## 5단계: 주석이 달린 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 성공 메시지 표시
주석이 달린 문서의 경로와 함께 성공 메시지를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
결론적으로, GroupDocs.Annotation을 사용하여 .NET 응용 프로그램의 텍스트 위에 이미지 주석을 추가하는 것은 간단한 프로세스입니다. 이 튜토리얼에서 제공되는 단계별 가이드를 따르면 문서에 효율적으로 주석을 달고 .NET 프로젝트에서 공동 작업 및 문서 관리 기능을 향상시킬 수 있습니다.
## FAQ
### PDF 이외의 문서에 주석을 달 수 있나요?
예, GroupDocs.Annotation은 DOCX, XLSX, PPTX 등과 같은 다양한 문서 형식을 지원합니다.
### GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Annotation에 대한 지원을 받으려면 어떻게 해야 합니까?
 GroupDocs.Annotation 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).
### 테스트 목적으로 임시 라이센스가 필요합니까?
 예, 다음에서 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/) 테스트 목적으로.
### 주석의 모양을 맞춤설정할 수 있나요?
예, GroupDocs.Annotation은 색상, 불투명도, 글꼴 크기 등과 같은 주석 모양을 사용자 정의할 수 있는 다양한 옵션을 제공합니다.