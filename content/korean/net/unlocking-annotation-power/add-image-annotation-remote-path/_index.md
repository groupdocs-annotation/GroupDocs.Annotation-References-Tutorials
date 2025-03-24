---
title: 문서에 이미지 주석 추가(원격 경로)
linktitle: 문서에 이미지 주석 추가(원격 경로)
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보세요. 강력한 주석 기능으로 문서 관리를 강화하세요.
weight: 15
url: /ko/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 이미지 주석을 추가하는 과정을 안내합니다. 이 라이브러리는 프로그래밍 방식으로 다양한 유형의 문서에 주석을 달 수 있는 강력한 도구를 제공합니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: .NET 개발을 위한 작업 개발 환경이 설정되어 있는지 확인하세요.
3.  문서: 주석을 달고 싶은 문서를 준비합니다. 이 튜토리얼에서는 다음과 같은 PDF 문서가 있다고 가정합니다.`input.pdf`.
4. 주석용 이미지: 주석에 사용할 이미지를 선택합니다. 이미지 URL 또는 로컬 경로가 준비되어 있는지 확인하세요.

## 네임스페이스 가져오기
코딩을 시작하기 전에 필요한 네임스페이스를 가져오겠습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1단계: 출력 경로 설정
먼저 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석자 초기화
 인스턴스를 생성합니다.`Annotator` 클래스를 입력하고 입력 문서를 지정합니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드가 여기에 표시됩니다.
}
```
## 3단계: 이미지 주석 추가
이제 문서에 이미지 주석을 추가해 보겠습니다. 위치, 불투명도, 페이지 번호 및 이미지 경로와 같은 이미지 주석의 속성을 지정합니다.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // 주석 위치 지정
    CreatedOn = DateTime.Now, // 생성 날짜 설정
    Opacity = 0.7, // 불투명도 설정(0~1)
    PageNumber = 0, // 페이지 번호를 지정하세요
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 이미지의 URL 제공
};
annotator.Add(image); // 이미지 주석 추가
```
## 4단계: 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 5단계: 출력 경로 표시
사용자에게 성공적인 문서 저장 작업을 알리고 출력 경로를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 이미지 주석을 추가하는 방법을 배웠습니다. 다음 단계를 수행하면 강력한 주석 기능으로 문서 관리 애플리케이션을 향상시킬 수 있습니다.
## FAQ
### GroupDocs.Annotation을 PDF 이외의 다른 문서 형식과 함께 사용할 수 있습니까?
예, GroupDocs.Annotation은 Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다.
### GroupDocs.Annotation은 .NET Core와 호환되나요?
예, GroupDocs.Annotation은 .NET Framework 및 .NET Core 모두와 호환됩니다.
### 주석의 모양을 맞춤설정할 수 있나요?
예, 색상, 불투명도, 크기 등 주석의 모양을 맞춤설정할 수 있습니다.
### GroupDocs.Annotation은 공동 주석 기능을 지원합니까?
예, GroupDocs.Annotation은 문서에 대한 실시간 공동 작업을 위한 공동 주석 기능을 제공합니다.
### 테스트에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 GroupDocs.Annotation 무료 평가판을 받을 수 있습니다.[여기](https://releases.groupdocs.com/).