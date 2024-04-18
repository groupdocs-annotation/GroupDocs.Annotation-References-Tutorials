---
title: PDF 문서 회전
linktitle: PDF 문서 회전
second_title: GroupDocs.Annotation .NET API
description: .NET용 Groupdocs.Annotation을 사용하여 PDF 문서를 쉽게 회전하는 방법을 알아보세요. 문서 관리 효율성을 향상시킵니다.
type: docs
weight: 22
url: /ko/net/advanced-usage/rotating-pdf-documents/
---
## 소개
PDF 문서 회전은 다르게 보거나 처리해야 하는 파일을 처리할 때 중요한 작업이 될 수 있습니다. 이 튜토리얼에서는 .NET용 Groupdocs.Annotation을 사용하여 PDF 문서를 단계별로 회전하는 방법을 살펴보겠습니다.
## 전제 조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 Groupdocs.Annotation: .NET 라이브러리용 Groupdocs.Annotation을 다운로드하고 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. C# 프로그래밍에 대한 기본 지식: 이 자습서에서는 사용자가 C# 프로그래밍 언어와 .NET 라이브러리 작업 방법에 대한 기본 지식을 가지고 있다고 가정합니다.

## 네임스페이스 가져오기
먼저 Groupdocs.Annotation 라이브러리에서 제공하는 기능에 액세스하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 1단계: PDF 문서 로드
 다음을 사용하여 회전하려는 PDF 문서를 로드하는 것으로 시작하십시오.`Annotator` 수업.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 2단계: 회전 및 프로세스 페이지 설정
회전 각도와 회전하려는 페이지를 지정합니다. 이 예에서는 첫 번째 페이지를 시계 방향으로 90도 회전합니다.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## 3단계: 회전된 문서 저장
지정된 변경 사항을 적용하여 회전된 PDF 문서를 저장합니다.
```csharp
annotator.Save("result.pdf");
```
## 4단계: 표시 확인
사용자에게 문서가 성공적으로 회전되었음을 알립니다.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## 결론
PDF 문서 회전은 기본적인 작업이며 .NET용 Groupdocs.Annotation을 사용하면 이 작업이 간단하고 효율적입니다. 이 튜토리얼에 설명된 단계를 따르면 요구 사항에 따라 PDF 파일을 쉽게 회전할 수 있습니다.
## FAQ
### .NET용 Groupdocs.Annotation을 사용하여 PDF 문서에서 여러 페이지를 회전할 수 있습니까?
 예, 회전할 여러 페이지를 지정할 수 있습니다.`ProcessPages` 그에 따라 재산.
### .NET용 Groupdocs.Annotation은 모든 버전의 .NET Framework와 호환됩니까?
.NET용 Groupdocs.Annotation은 광범위한 .NET 프레임워크 버전을 지원하여 대부분의 개발 환경에 대한 호환성을 보장합니다.
### .NET용 Groupdocs.Annotation은 PDF 문서를 다른 방향으로 회전할 수 있는 옵션을 제공합니까?
예, PDF 문서를 시계 방향, 시계 반대 방향 또는 요구 사항에 따라 사용자 정의 각도로 회전할 수 있습니다.
### .NET용 Groupdocs.Annotation을 기존 문서 관리 시스템에 통합할 수 있습니까?
물론 .NET용 Groupdocs.Annotation은 원활한 통합 옵션을 제공하므로 문서 관리 기능을 쉽게 향상시킬 수 있습니다.
### .NET용 Groupdocs.Annotation에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 받을 수 있습니다.[여기](https://releases.groupdocs.com/).