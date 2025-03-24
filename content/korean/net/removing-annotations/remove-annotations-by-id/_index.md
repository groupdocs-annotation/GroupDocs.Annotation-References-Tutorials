---
title: ID별로 주석 제거
linktitle: ID별로 주석 제거
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 ID별로 주석을 제거하는 방법을 알아보세요. 문서 작업 흐름을 효율적으로 간소화하세요.
weight: 11
url: /ko/net/removing-annotations/remove-annotations-by-id/
---

# ID별로 주석 제거

## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 ID별로 주석을 제거하는 과정을 안내합니다. 주석은 문서를 복잡하게 만들 수 있으며 선택적으로 주석을 제거하면 작업 흐름을 간소화할 수 있습니다. 각 단계를 명확하게 이해할 수 있도록 단계별로 안내해 드립니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: .NET용 GroupDocs.Annotation 라이브러리를 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. 주석이 달린 문서에 대한 액세스: GroupDocs.Annotation으로 주석이 달린 문서를 갖습니다. 없는 경우 이전 튜토리얼에 따라 문서에 주석을 달 수 있습니다.
3. C#에 대한 기본 지식: 코드 예제를 이해하려면 C# 프로그래밍 언어에 대한 지식이 필요합니다.

## 네임스페이스 가져오기
코딩을 시작하기 전에 필요한 네임스페이스를 가져오겠습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## 1단계: 출력 경로 정의
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
주석이 제거된 문서가 저장될 출력 경로를 정의합니다.
## 2단계: 주석자 초기화
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 여기서는`Annotator` 주석이 달린 PDF 문서의 경로가 있는 개체입니다.
## 3단계: 주석 제거
```csharp
annotator.Remove(0);
```
 ID를 지정하여 주석을 제거합니다. 이 예에서는 ID가 포함된 주석을 제거합니다.`0` . 교체할 수 있습니다`0` 제거하려는 주석의 ID를 사용하세요.
## 4단계: 문서 저장
```csharp
annotator.Save(outputPath);
```
주석을 제거한 후 수정된 문서를 앞에서 지정한 출력 경로에 저장합니다.
## 5단계: 성공 메시지 표시
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
마지막으로 수정된 문서가 저장된 경로와 함께 성공 메시지를 표시합니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 ID별로 주석을 제거하는 방법을 배웠습니다. 이 기능은 주석을 선택적으로 제거하여 주석이 달린 문서를 보다 효율적으로 관리하는 데 도움이 됩니다.
## FAQ
### 여러 주석을 한 번에 제거할 수 있나요?
 예.`Remove` 방법.
### 주석 제거를 취소할 수 있는 방법이 있나요?
아니요. 주석을 삭제한 후에는 취소할 수 없습니다. 주석을 제거하기 전에 문서를 백업하세요.
### PDF가 아닌 문서에서 주석을 제거할 수 있나요?
예, GroupDocs.Annotation은 DOCX, XLSX, PPTX 등을 포함한 다양한 문서 형식을 지원합니다.
### 제거할 수 있는 주석 수에 제한이 있나요?
아니요. ID를 올바르게 지정하기만 하면 문서에서 주석을 얼마든지 제거할 수 있습니다.
### 문제가 발생하면 기술 지원을 받을 수 있나요?
 예, GroupDocs.Annotation 포럼에서 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).