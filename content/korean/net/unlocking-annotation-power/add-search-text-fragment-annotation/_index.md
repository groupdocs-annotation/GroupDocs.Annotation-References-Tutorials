---
"description": ".NET용 GroupDocs.Annotation의 강력한 기능을 살펴보고 애플리케이션에 문서 주석 기능을 손쉽게 추가해 보세요."
"linktitle": "문서에 검색 텍스트 조각 주석 추가"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 검색 텍스트 조각 주석 추가"
"url": "/ko/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# 문서에 검색 텍스트 조각 주석 추가

## 소개
.NET 개발 분야에서 GroupDocs.Annotation은 문서에 주석을 매끄럽게 추가할 수 있는 강력한 도구로 돋보입니다. 숙련된 개발자든 .NET 세계에 막 입문한 초보자든, 이 포괄적인 튜토리얼을 통해 네임스페이스 가져오기부터 문서에 검색 텍스트 조각 주석을 추가하는 복잡한 작업까지, .NET용 GroupDocs.Annotation 사용의 핵심을 안내합니다.
## 소개
GroupDocs.Annotation for .NET은 개발자가 문서 주석 기능을 애플리케이션에 손쉽게 통합할 수 있도록 지원합니다. 직관적인 API와 강력한 기능을 통해 PDF, Microsoft Office 문서, 이미지 등 다양한 문서 형식에 주석을 추가할 수 있습니다.
## 필수 조건
.NET용 GroupDocs.Annotation을 사용하기 전에 다음 필수 구성 요소가 있는지 확인하세요.

## 네임스페이스 가져오기
먼저, .NET 프로젝트에서 GroupDocs.Annotation 클래스와 메서드에 액세스하는 데 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 출력 경로 정의
먼저 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: Annotator 초기화
다음으로 인스턴스를 초기화합니다. `Annotator` 주석을 달고 싶은 문서의 경로를 제공하여 클래스를 만듭니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3단계: 검색 텍스트 조각 주석 만들기
생성하다 `SearchTextFragment` 검색할 텍스트, 글꼴 크기, 글꼴 패밀리, 글꼴 색상, 배경색 등 원하는 속성을 가진 개체:
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
생성된 검색 텍스트 조각 주석을 문서에 추가하려면 다음을 사용합니다. `Add` 주석자의 방법:
```csharp
annotator.Add(searchText);
```
## 5단계: 주석이 달린 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 성공 메시지 표시
문서가 성공적으로 저장되었음을 사용자에게 알립니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
결론적으로, GroupDocs.Annotation for .NET은 문서에 주석을 추가하는 과정을 간소화하여 협업 및 문서 검토 프로세스를 향상시킵니다. 이 가이드에 설명된 단계를 따르면 문서 주석 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.
## 자주 묻는 질문
### GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
네, GroupDocs.Annotation은 PDF, Microsoft Office 문서, 이미지 등 다양한 문서 형식을 지원합니다.
### 주석의 모양을 사용자 지정할 수 있나요?
물론입니다! GroupDocs.Annotation은 주석에 대한 광범위한 사용자 지정 옵션을 제공하여 글꼴 크기, 색상, 스타일 등의 속성을 조정할 수 있습니다.
### GroupDocs.Annotation에 대한 무료 평가판이 있나요?
예, 구매하기 전에 GroupDocs.Annotation의 무료 평가판을 이용해 기능과 성능을 살펴보실 수 있습니다. [여기](https://releases.groupdocs.com/)..
### GroupDocs.Annotation에 대한 지원은 어디에서 찾을 수 있나요?
GroupDocs.Annotation에 대한 지원 및 도움을 받으려면 GroupDocs를 방문하세요. [법정](https://forum.groupdocs.com/c/annotation/10) 주석 관련 질의와 토론에 전념합니다.
### GroupDocs.Annotation에 대한 임시 라이선스를 얻으려면 어떻게 해야 하나요?
GroupDocs를 통해 GroupDocs.Annotation에 대한 임시 라이센스를 취득할 수 있습니다. [웹사이트](https://purchase.groupdocs.com/temporary-license/)이를 통해 제품을 전체적으로 평가할 수 있습니다.