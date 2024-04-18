---
title: 문서에 검색 텍스트 조각 주석 추가
linktitle: 문서에 검색 텍스트 조각 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation의 강력한 기능을 살펴보고 응용 프로그램에 문서 주석 기능을 손쉽게 추가하세요.
type: docs
weight: 20
url: /ko/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## 소개
.NET 개발 영역에서 GroupDocs.Annotation은 문서에 원활하게 주석을 달기 위한 강력한 도구로 돋보입니다. 숙련된 개발자이거나 .NET의 세계에 입문한 사람이든 관계없이 이 포괄적인 튜토리얼은 네임스페이스 가져오기부터 검색 텍스트 조각 주석을 서류.
## 소개
.NET용 GroupDocs.Annotation을 사용하면 개발자가 문서 주석 기능을 자신의 응용 프로그램에 쉽게 통합할 수 있습니다. 직관적인 API와 강력한 기능을 통해 개발자는 PDF, Microsoft Office 문서, 이미지 등을 포함한 다양한 문서 형식에 주석을 달 수 있습니다.
## 전제 조건
.NET용 GroupDocs.Annotation을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

## 네임스페이스 가져오기
먼저, .NET 프로젝트의 GroupDocs.Annotation 클래스 및 메서드에 액세스하는 데 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 정의
주석이 달린 문서가 저장될 출력 경로를 정의하는 것부터 시작하세요.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석자 초기화
 다음으로 인스턴스를 초기화합니다.`Annotator` 주석을 달고 싶은 문서의 경로를 제공하여 클래스를 지정하세요.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3단계: 검색 텍스트 조각 주석 생성
 만들기`SearchTextFragment` 검색할 텍스트, 글꼴 크기, 글꼴 모음, 글꼴 색상, 배경색 등 원하는 속성이 있는 개체:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## 4단계: 주석 추가
 생성된 검색 텍스트 조각 주석을 다음을 사용하여 문서에 추가합니다.`Add` 주석자의 방법:
```csharp
annotator.Add(searchText);
```
## 5단계: 주석이 달린 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 성공 메시지 표시
사용자에게 문서가 성공적으로 저장되었음을 알립니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
결론적으로 .NET용 GroupDocs.Annotation은 문서에 주석을 추가하는 프로세스를 단순화하고 공동 작업 및 문서 검토 프로세스를 향상시킵니다. 이 가이드에 설명된 단계를 따르면 문서 주석 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.
## FAQ
### GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
예, GroupDocs.Annotation은 PDF, Microsoft Office 문서, 이미지 등을 포함한 광범위한 문서 형식을 지원합니다.
### 주석의 모양을 맞춤설정할 수 있나요?
전적으로! GroupDocs.Annotation은 주석에 대한 광범위한 사용자 정의 옵션을 제공하므로 글꼴 크기, 색상, 스타일과 같은 속성을 조정할 수 있습니다.
### GroupDocs.Annotation에 대한 무료 평가판이 있습니까?
 예, GroupDocs.Annotation의 무료 평가판에 액세스하여 구매하기 전에 기능을 살펴보실 수 있습니다.[여기](https://releases.groupdocs.com/)..
### GroupDocs.Annotation에 대한 지원은 어디서 찾을 수 있나요?
 GroupDocs.Annotation에 대한 지원 및 지원을 받으려면 GroupDocs를 방문하세요.[법정](https://forum.groupdocs.com/c/annotation/10) 주석 관련 쿼리 및 토론 전용입니다.
### GroupDocs.Annotation에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 GroupDocs를 통해 GroupDocs.Annotation에 대한 임시 라이센스를 얻을 수 있습니다.[웹사이트](https://purchase.groupdocs.com/temporary-license/), 제품을 완전히 평가할 수 있습니다.