---
title: .NET에서 저장 옵션을 사용하여 주석 제거
linktitle: .NET에서 저장 옵션을 사용하여 주석 제거
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation을 사용하여 PDF 및 .NET의 기타 문서에서 주석을 제거하는 방법을 알아보세요. 코드 예제가 포함된 단계별 가이드입니다.
weight: 14
url: /ko/net/removing-annotations/remove-annotations-using-save-options/
---
## 소개

.NET용 GroupDocs.Annotation은 개발자가 .NET 응용 프로그램에 주석 기능을 쉽게 추가할 수 있는 강력한 도구입니다. 문서 관리 시스템, 공동 작업 플랫폼 또는 문서 처리와 관련된 기타 응용 프로그램에서 작업하는 경우 GroupDocs.Annotation은 PDF 및 기타 문서 형식에 원활하게 주석을 달 수 있는 포괄적인 기능 세트를 제공합니다.

## 전제 조건

.NET용 GroupDocs.Annotation을 사용하여 문서에 주석을 추가하는 방법을 알아보기 전에 다음 전제 조건이 충족되었는지 확인하세요.

### 1. .NET용 GroupDocs.Annotation 설치

 .NET용 GroupDocs.Annotation을 다운로드하고 설치하여 시작하세요. 최신 버전은 다음 사이트에서 다운로드할 수 있습니다.[download page](https://releases.groupdocs.com/annotation/net/).

## 네임스페이스 가져오기

.NET 프로젝트에서 GroupDocs.Annotation 사용을 시작하려면 필요한 네임스페이스를 가져와야 합니다. 일반적으로 사용하게 될 네임스페이스는 다음과 같습니다.

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


이제 .NET의 저장 옵션 기능을 사용하여 문서에서 주석을 제거하는 과정을 살펴보겠습니다.

## 1단계: 출력 경로 정의

먼저 주석이 제거된 문서가 저장될 출력 경로를 정의합니다. 당신은 사용할 수 있습니다`Path.Combine` 디렉터리 경로와 출력 파일 이름을 결합하는 방법입니다.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2단계: 주석자 초기화

 다음으로 인스턴스를 초기화합니다.`Annotator` 주석이 포함된 문서에 대한 경로를 제공하여 클래스를 생성합니다.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // 주석 제거 코드가 여기에 표시됩니다.
}
```

## 3단계: 주석을 제거하여 문서 저장

 이제`Save` 의 방법`Annotator` 수업과 함께`SaveOptions` 주석이 제거된 문서를 저장하려면 에서`SaveOptions` , 설정`AnnotationTypes` 재산`AnnotationType.None` 모든 주석을 제거합니다.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## 4단계: 성공 메시지 표시

마지막으로 주석이 제거된 상태로 문서가 성공적으로 저장되었음을 나타내는 성공 메시지를 표시합니다.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론

결론적으로, .NET용 GroupDocs.Annotation은 문서에서 주석을 제거하는 프로세스를 단순화합니다. 위에 설명된 단계별 가이드를 따르면 개발자는 주석 제거 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ

### Q: GroupDocs.Annotation은 PDF 이외의 다른 문서 형식에서 주석을 제거할 수 있습니까?

답변: GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등 다양한 문서 형식을 지원하므로 광범위한 문서에서 주석을 제거할 수 있습니다.

### Q: GroupDocs.Annotation은 기존 .NET 프로젝트에 쉽게 통합됩니까?

A: 예, GroupDocs.Annotation은 간단한 API와 포괄적인 문서를 제공하므로 개발자가 주석 기능을 .NET 응용 프로그램에 쉽게 통합할 수 있습니다.

### Q: GroupDocs.Annotation은 선택적 주석 제거를 지원합니까?

A: 예, GroupDocs.Annotation을 사용하면 개발자가 제거할 주석 유형을 지정할 수 있으므로 문서 내에서 주석을 유연하게 관리할 수 있습니다.

### 질문: 구매하기 전에 GroupDocs.Annotation을 무료로 사용해 볼 수 있습니까?

 A: 예, 다음에서 GroupDocs.Annotation의 무료 평가판을 다운로드할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/) 구매 결정을 내리기 전에 기능을 살펴보세요.

### Q: GroupDocs.Annotation에 대한 지원은 어디서 받을 수 있습니까?

 답변: 기술 지원 및 커뮤니티 지원을 받으려면[GroupDocs.Annotation 포럼](https://forum.groupdocs.com/c/annotation/10).