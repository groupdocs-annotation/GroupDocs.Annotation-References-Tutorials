---
"description": "Groupdocs.Annotation for .NET을 사용하여 PDF 문서를 손쉽게 회전하는 방법을 알아보세요. 문서 관리 효율성을 높여보세요."
"linktitle": "PDF 문서 회전"
"second_title": "GroupDocs.Annotation .NET API"
"title": "PDF 문서 회전"
"url": "/ko/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# PDF 문서 회전

## 소개
PDF 문서를 회전하는 것은 다르게 보거나 처리해야 하는 파일을 다룰 때 매우 중요한 작업이 될 수 있습니다. 이 튜토리얼에서는 Groupdocs.Annotation for .NET을 사용하여 PDF 문서를 단계별로 회전하는 방법을 살펴보겠습니다.
## 필수 조건
튜토리얼을 시작하기 전에 다음 필수 조건이 충족되었는지 확인하세요.
1. Groupdocs.Annotation for .NET 라이브러리: Groupdocs.Annotation for .NET 라이브러리를 다운로드하여 설치했는지 확인하세요. 다음에서 다운로드할 수 있습니다. [여기](https://releases.groupdocs.com/annotation/net/).
2. C# 프로그래밍에 대한 기본 지식: 이 튜토리얼에서는 사용자가 C# 프로그래밍 언어에 대한 기본적인 이해와 .NET 라이브러리를 사용하는 방법을 알고 있다고 가정합니다.

## 네임스페이스 가져오기
먼저, Groupdocs.Annotation 라이브러리가 제공하는 기능에 액세스하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 1단계: PDF 문서 로드
회전하려는 PDF 문서를 로드하여 시작하세요. `Annotator` 수업.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 2단계: 회전 설정 및 페이지 처리
회전 각도와 회전할 페이지를 지정하세요. 이 예시에서는 첫 번째 페이지를 시계 방향으로 90도 회전해 보겠습니다.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## 3단계: 회전된 문서 저장
지정된 변경 사항을 적용하여 회전된 PDF 문서를 저장합니다.
```csharp
annotator.Save("result.pdf");
```
## 4단계: 확인 표시
문서가 성공적으로 회전되었음을 사용자에게 알립니다.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## 결론
PDF 문서 회전은 기본적인 작업이며, Groupdocs.Annotation for .NET을 사용하면 간단하고 효율적으로 작업할 수 있습니다. 이 튜토리얼에 설명된 단계를 따르면 필요에 따라 PDF 파일을 쉽게 회전할 수 있습니다.
## 자주 묻는 질문
### Groupdocs.Annotation for .NET을 사용하여 PDF 문서의 여러 페이지를 회전할 수 있나요?
예, 조정하여 여러 페이지를 회전하도록 지정할 수 있습니다. `ProcessPages` 이에 따라 재산을 소유합니다.
### Groupdocs.Annotation for .NET은 모든 버전의 .NET 프레임워크와 호환됩니까?
.NET용 Groupdocs.Annotation은 다양한 .NET 프레임워크 버전을 지원하여 대부분 개발 환경에서 호환성을 보장합니다.
### .NET용 Groupdocs.Annotation은 PDF 문서를 여러 방향으로 회전하는 옵션을 제공합니까?
네, 사용자의 요구 사항에 따라 PDF 문서를 시계 방향, 시계 반대 방향 또는 사용자 지정 각도로 회전할 수 있습니다.
### Groupdocs.Annotation for .NET을 기존 문서 관리 시스템에 통합할 수 있나요?
물론입니다. Groupdocs.Annotation for .NET은 원활한 통합 옵션을 제공하여 손쉽게 문서 관리 기능을 향상시킬 수 있습니다.
### Groupdocs.Annotation for .NET의 평가판이 있나요?
네, 무료 체험판을 받으실 수 있습니다. [여기](https://releases.groupdocs.com/).