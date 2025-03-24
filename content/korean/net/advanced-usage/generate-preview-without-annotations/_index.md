---
title: 주석 없이 미리보기 생성
linktitle: 주석 없이 미리보기 생성
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 .NET 응용 프로그램 내에서 문서 공동 작업 및 주석을 강화합니다. 이 강력한 라이브러리를 사용하여 문서에 쉽게 주석을 달고 마크업하고 검토할 수 있습니다.
weight: 13
url: /ko/net/advanced-usage/generate-preview-without-annotations/
---

# 주석 없이 미리보기 생성

## 소개
오늘날의 디지털 시대에는 효율적인 문서 공동작업이 생산성과 성공의 열쇠입니다. 전 세계에 흩어져 있는 팀 구성원과 함께 프로젝트를 진행하든, 중요한 계약을 위해 고객과 협업하든, 문서에 원활하게 주석을 달고 검토하는 능력은 매우 중요합니다. .NET용 GroupDocs.Annotation을 사용하면 문서 공동 작업을 한 단계 더 발전시켜 .NET 응용 프로그램 내에서 직접 주석, 마크업 및 검토를 쉽게 수행할 수 있습니다.
## 전제 조건
.NET용 GroupDocs.Annotation을 사용하여 문서 주석 세계에 뛰어들기 전에 준비해야 할 몇 가지 전제 조건이 있습니다.
### 1. .NET용 GroupDocs.Annotation 설치
 무엇보다도 .NET용 GroupDocs.Annotation을 다운로드하여 설치해야 합니다. 다운로드 링크를 찾을 수 있습니다[여기](https://releases.groupdocs.com/annotation/net/). .NET 환경에서 라이브러리를 설정하려면 제공된 설치 지침을 따르십시오.
### 2. 라이센스 취득(선택)
.NET용 GroupDocs.Annotation은 무료 평가판을 제공하지만 해당 기능에 대한 전체 액세스 권한을 얻으려면 라이센스를 취득하는 것이 좋습니다. 라이센스를 구매하실 수 있습니다[여기](https://purchase.groupdocs.com/buy) 또는 임시 라이센스를 요청하세요[여기](https://purchase.groupdocs.com/temporary-license/) 테스트 목적으로.
### 3. C# 및 .NET 개발에 대한 지식
.NET용 GroupDocs.Annotation을 최대한 활용하려면 C# 및 .NET 개발에 대한 기본적인 이해가 있으면 도움이 됩니다. 이를 통해 라이브러리를 기존 애플리케이션 및 작업 흐름에 원활하게 통합할 수 있습니다.
### 4. PDF 뷰어 설치
.NET용 GroupDocs.Annotation은 PDF 문서와 함께 작동하므로 주석이 달린 문서를 미리 보려면 시스템에 PDF 뷰어를 설치해야 합니다. Adobe Acrobat Reader 또는 기타 PDF 뷰어로 충분합니다.

## 네임스페이스 가져오기
문서에 주석을 달기 전에 필요한 네임스페이스를 .NET 프로젝트로 가져와야 합니다. 이를 통해 .NET용 GroupDocs.Annotation에서 제공하는 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

이제 모든 설정이 완료되었으므로 주석 없이 문서 미리보기를 생성해 보겠습니다. 이를 수행하려면 다음 단계를 따르십시오.
## 1단계: 주석자 초기화
 먼저,`Annotator` 클래스, 주석을 달고 싶은 문서의 경로를 전달합니다.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## 2단계: 미리보기 옵션 구성
그런 다음 요구 사항에 따라 미리 보기 옵션을 구성합니다. 미리보기에 포함할 페이지 번호, 미리보기 형식(예: PNG) 및 주석 렌더링 여부를 지정할 수 있습니다.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## 3단계: 미리보기 생성
 마지막으로 다음을 사용하여 미리보기를 생성합니다.`GeneratePreview` 의 방법`Document` 클래스, 구성된 미리보기 옵션을 전달합니다.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
이러한 간단한 단계를 따르면 .NET용 GroupDocs.Annotation을 사용하여 주석 없이 문서 미리보기를 생성할 수 있습니다.

## 결론
결론적으로 .NET용 GroupDocs.Annotation은 .NET 응용 프로그램 내에서 문서 공동 작업 및 주석을 위한 강력한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 문서 주석 기능을 프로젝트에 원활하게 통합하여 협업과 생산성을 향상시킬 수 있습니다.
## FAQ
### Q: PDF 이외의 다른 문서 형식과 함께 .NET용 GroupDocs.Annotation을 사용할 수 있습니까?
예, .NET용 GroupDocs.Annotation은 DOCX, XLSX, PPTX 등을 포함한 다양한 문서 형식을 지원합니다.
### Q: .NET용 GroupDocs.Annotation은 .NET Core와 호환됩니까?
예, .NET용 GroupDocs.Annotation은 .NET Framework 및 .NET Core 환경 모두와 호환됩니다.
### Q: .NET용 GroupDocs.Annotation은 사용자 정의 가능한 주석 도구를 제공합니까?
예, .NET용 GroupDocs.Annotation은 특정 요구 사항에 맞게 사용자 정의할 수 있는 다양한 주석 도구를 제공합니다.
### Q: .NET용 GroupDocs.Annotation을 내 웹 응용 프로그램에 통합할 수 있습니까?
예, .NET용 GroupDocs.Annotation은 데스크톱 및 웹 응용 프로그램 모두에 통합되어 원활한 문서 공동 작업 기능을 제공할 수 있습니다.
### 질문: .NET용 GroupDocs.Annotation에 대한 지원을 받을 수 있는 커뮤니티 포럼이 있습니까?
 예, GroupDocs.Annotation 포럼에서 지원 및 지원을 찾을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).