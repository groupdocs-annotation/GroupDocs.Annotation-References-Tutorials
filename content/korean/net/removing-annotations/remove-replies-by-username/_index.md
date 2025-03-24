---
title: .NET에서 사용자 이름별 회신 제거
linktitle: .NET에서 사용자 이름별 회신 제거
second_title: GroupDocs.Annotation .NET API
description: .NET용 Groupdocs.Annotation을 사용하여 문서에 원활하게 주석을 추가하는 방법을 알아보세요. 이 강력한 도구를 사용하여 공동작업과 문서 관리를 강화하세요.
weight: 17
url: /ko/net/removing-annotations/remove-replies-by-username/
---

# .NET에서 사용자 이름별 회신 제거

## 소개
Groupdocs.Annotation for .NET은 .NET 응용 프로그램 내에서 문서에 원활하게 주석을 달기 위한 강력한 도구입니다. PDF, Word 문서 또는 기타 지원되는 파일 형식으로 작업하는 경우 이 라이브러리는 주석, 강조 표시 및 설명 추가 프로세스를 단순화하고 공동 작업 및 문서 관리 기능을 향상시킵니다.
## 전제 조건
.NET용 Groupdocs.Annotation을 사용하여 문서 주석 작업을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 Groupdocs.Annotation 설치: .NET용 Groupdocs.Annotation 라이브러리를 다운로드하고 설치하는 것으로 시작합니다. 도서관에서 도서관을 구할 수 있습니다.[다운로드 링크](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework에 대한 이해: Groupdocs.Annotation의 기능을 효과적으로 활용하려면 .NET 프로그래밍에 능숙해야 합니다.
3. 주석을 달 문서: 주석을 달려는 문서를 준비합니다. PDF, Word 문서 또는 기타 지원되는 파일 형식일 수 있습니다.
4. C#에 대한 기본 지식: .NET용 Groupdocs.Annotation은 주로 C# 응용 프로그램 내에서 사용되므로 C# 프로그래밍 언어에 익숙해지세요.

## 네임스페이스 가져오기
.NET용 Groupdocs.Annotation을 사용하여 문서에 주석을 추가하려면 필요한 네임스페이스를 C# 프로젝트로 가져옵니다.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## 1단계: 출력 경로 정의
 주석이 달린 문서가 저장될 출력 경로를 지정하는 것부터 시작하세요. 당신은 사용할 수 있습니다`Path.Combine` 디렉토리 경로를 결합하는 방법:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석이 달린 문서 로드
 다음을 사용하여 회신이 포함된 주석이 포함된 문서를 로드합니다.`Annotator` 수업:
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
```
## 3단계: 주석 얻기
로드된 문서에서 주석 컬렉션을 검색합니다.
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## 4단계: 답글 삭제
작성자 이름이 지정된 사용자 이름과 일치하는 모든 답글을 제거합니다. 이 예에서는 "Tom"이 작성한 답글이 삭제됩니다.
```csharp
annotations[0].Replies.RemoveAll(x => x.User.Name == "Tom");
```
## 5단계: 변경 사항 저장
업데이트된 주석을 문서에 다시 저장하고 출력 경로를 지정합니다.
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
## 6단계: 표시 확인
마지막으로 사용자에게 문서가 성공적으로 저장되었음을 알리고 출력 파일의 경로를 제공합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## 결론
.NET용 Groupdocs.Annotation은 .NET 응용 프로그램 내에서 문서에 주석을 달기 위한 간단하고 효율적인 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 문서 주석 기능을 프로젝트에 원활하게 통합하여 협업 및 문서 관리를 향상시킬 수 있습니다.
## FAQ
### Groupdocs.Annotation은 모든 문서 형식과 호환됩니까?
Groupdocs.Annotation은 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다. 지원되는 형식의 전체 목록은 설명서를 참조하세요.
### 주석의 모양을 맞춤설정할 수 있나요?
예, Groupdocs.Annotation은 색상, 크기, 글꼴, 스타일을 포함하여 주석 모양을 사용자 정의하기 위한 광범위한 옵션을 제공합니다.
### Groupdocs.Annotation은 웹 응용 프로그램에 적합합니까?
전적으로! Groupdocs.Annotation은 ASP.NET 또는 ASP.NET Core를 사용하여 개발된 웹 애플리케이션에 원활하게 통합될 수 있습니다.
### Groupdocs.Annotation은 공동 주석을 지원합니까?
예, Groupdocs.Annotation은 여러 사용자가 동일한 문서에 주석, 강조 표시 및 주석을 동시에 추가할 수 있도록 하여 협업 주석을 용이하게 합니다.
### 테스트에 사용할 수 있는 평가판이 있습니까?
예, 웹사이트에서 Groupdocs.Annotation의 무료 평가판을 다운로드하여 기능을 살펴볼 수 있습니다.