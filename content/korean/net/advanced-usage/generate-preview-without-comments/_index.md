---
"description": "GroupDocs.Annotation for .NET을 사용하여 문서 주석 기능을 .NET 애플리케이션에 원활하게 통합하는 방법을 알아보세요."
"linktitle": "주석 없이 미리보기 생성"
"second_title": "GroupDocs.Annotation .NET API"
"title": "주석 없이 미리보기 생성"
"url": "/ko/net/advanced-usage/generate-preview-without-comments/"
"weight": 14
---

# 주석 없이 미리보기 생성

## 소개
GroupDocs.Annotation for .NET은 개발자가 .NET 애플리케이션에 주석 기능을 원활하게 통합할 수 있도록 지원하는 강력한 도구입니다. 문서 관리 시스템, 협업 플랫폼 또는 문서 주석 기능이 필요한 다른 애플리케이션을 사용하든, GroupDocs.Annotation은 애플리케이션의 기능을 향상시키는 포괄적인 도구 세트를 제공합니다.
## 필수 조건
.NET에서 GroupDocs.Annotation을 사용하기 전에 다음 필수 구성 요소가 설정되어 있는지 확인하세요.
### 1. .NET용 GroupDocs.Annotation 설치
시작하려면 GroupDocs.Annotation for .NET을 다운로드하여 설치해야 합니다. 다운로드 링크는 다음과 같습니다. [여기](https://releases.groupdocs.com/annotation/net/)원활한 설치 과정을 위해 설명서에 제공된 설치 지침을 따르세요.
### 2. 라이센스 취득
GroupDocs.Annotation for .NET은 상업적 사용 시 라이선스가 필요합니다. 라이선스는 다음에서 구매할 수 있습니다. [여기](https://purchase.groupdocs.com/buy) 또는 임시 면허를 선택하세요 [여기](https://purchase.groupdocs.com/temporary-license/) 테스트 목적으로.
### 3. .NET Framework에 대한 지식
GroupDocs.Annotation for .NET을 효과적으로 활용하려면 .NET Framework와 C# 프로그래밍 언어에 대한 기본 지식이 필수적입니다.

## 네임스페이스 가져오기
이제 필수 구성 요소를 설정했으므로 필요한 네임스페이스를 .NET 애플리케이션으로 가져오겠습니다.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

.NET용 GroupDocs.Annotation을 사용하여 주석이 없는 미리보기를 생성하려면 다음 단계별 지침을 따르세요.
## 1단계: Annotator 초기화
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## 2단계: 미리 보기 옵션 구성
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## 3단계: 미리 보기 형식 및 페이지 번호 지정
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## 4단계: 댓글 렌더링 비활성화
```csharp
    previewOptions.RenderComments = false;
```
## 5단계: 미리보기 생성
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
이러한 단계를 따르면 .NET 애플리케이션이 주석을 렌더링하지 않고도 문서에서 지정된 페이지의 미리보기를 생성할 수 있습니다.

## 결론
GroupDocs.Annotation for .NET 덕분에 .NET 애플리케이션에 주석 기능을 통합하는 것이 그 어느 때보다 쉬워졌습니다. 이 튜토리얼에 설명된 단계를 따르면 문서 주석 기능을 애플리케이션에 원활하게 통합하여 협업 및 문서 관리를 향상시킬 수 있습니다.
## 자주 묻는 질문
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
.NET용 GroupDocs.Annotation은 PDF, DOCX, PPTX, XLSX 등 다양한 문서 형식을 지원합니다.
### .NET용 GroupDocs.Annotation을 사용하여 생성된 주석의 모양을 사용자 정의할 수 있나요?
네, .NET용 GroupDocs.Annotation은 광범위한 사용자 정의 옵션을 제공하므로 애플리케이션의 요구 사항에 맞게 주석의 모양을 조정할 수 있습니다.
### .NET용 GroupDocs.Annotation은 다중 사용자 협업을 지원합니까?
네, .NET용 GroupDocs.Annotation은 협업 주석 기능을 제공하여 여러 사용자가 동시에 문서에 주석을 달 수 있습니다.
### GroupDocs.Annotation for .NET에 대한 기술 지원을 받을 수 있나요?
예, .NET용 GroupDocs.Annotation에 대한 기술 지원은 다음을 통해 제공됩니다. [지원 포럼](https://forum.groupdocs.com/c/annotation/10).
### 구매하기 전에 GroupDocs.Annotation for .NET을 무료로 사용해 볼 수 있나요?
예, 무료 평가판을 다운로드하여 .NET용 GroupDocs.Annotation의 기능을 탐색할 수 있습니다. [여기](https://releases.groupdocs.com/).