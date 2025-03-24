---
title: 측정 라이센스 설정
linktitle: 측정 라이센스 설정
second_title: GroupDocs.Annotation .NET API
description: .NET 응용 프로그램의 리소스 사용 및 문서 주석 기능을 위해 GroupDocs.Annotation .NET용 계량 라이센스를 설정하는 방법을 알아보세요.
weight: 12
url: /ko/net/applying-licenses/set-metered-license/
---
## 소개
.NET용 GroupDocs.Annotation은 개발자가 .NET 응용 프로그램에 문서 주석 기능을 쉽게 추가할 수 있도록 지원하는 강력한 라이브러리입니다. 문서 관리 시스템, 공동 작업 플랫폼 또는 문서 검토 및 마크업과 관련된 응용 프로그램을 구축하는 경우 .NET용 GroupDocs.Annotation은 프로세스를 간소화하는 포괄적인 도구 세트를 제공합니다.
이 자습서에서는 GroupDocs.Annotation .NET에 대한 계량 라이센스를 설정하는 과정을 자세히 살펴보겠습니다. 계량형 라이선스를 사용하면 소비한 리소스에 대해서만 비용을 지불할 수 있으므로 모든 규모의 프로젝트에 비용 효율적인 솔루션이 됩니다. 아래 설명된 단계를 따르면 리소스 사용을 최적화하고 예산 제어를 유지하면서 GroupDocs.Annotation을 .NET 응용 프로그램에 원활하게 통합할 수 있습니다.
## 전제 조건
튜토리얼을 시작하기 전에 다음 전제조건이 충족되었는지 확인하십시오.
1.  .NET 라이브러리용 GroupDocs.Annotation: 다음에서 라이브러리를 다운로드하세요.[웹사이트](https://releases.groupdocs.com/annotation/net/).
2. GroupDocs 계정에 대한 액세스: 계량 라이센스 설정에 필요한 공개 및 개인 키를 얻으려면 GroupDocs 계정이 필요합니다. 아직 계정이 없다면 무료 평가판에 등록할 수 있습니다.[여기](https://releases.groupdocs.com/).
3. C# 및 .NET Framework에 대한 기본 이해: C# 프로그래밍 언어 및 .NET Framework에 익숙하면 이 자습서에 설명된 단계를 구현하는 데 도움이 됩니다.

## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다. 이러한 네임스페이스는 GroupDocs.Annotation 기능과 상호 작용하는 데 필수적입니다.
```csharp
using System;
```
## 1단계: 공개 및 개인 키 얻기
계량 라이센스를 설정하기 전에 GroupDocs 계정 대시보드에서 공개 및 개인 키를 얻어야 합니다.
1. GroupDocs 계정에 로그인합니다.
2. 라이선스 관리 섹션으로 이동합니다.
3. GroupDocs에서 제공한 공개 및 개인 키를 복사합니다.
## 2단계: 측정 라이센스 설정
공개 키와 개인 키를 얻은 후에는 .NET 애플리케이션에서 계량 라이센스를 설정할 수 있습니다.
```csharp
string publicKey = "*****"; // *****를 공개 키로 바꾸세요.
string privateKey = "*****"; // *****를 개인 키로 바꾸세요.
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 결론
결론적으로 GroupDocs.Annotation .NET에 대한 계량형 라이센스를 설정하는 것은 문서 주석 프로젝트의 효율적인 리소스 활용과 비용 효율성을 보장하는 간단한 프로세스입니다. 이 자습서에 설명된 단계를 수행하면 GroupDocs.Annotation을 .NET 응용 프로그램에 원활하게 통합하고 문서 공동 작업 및 검토 기능을 향상시킬 수 있습니다.
## FAQ
### 상업용 프로젝트에서 .NET용 GroupDocs.Annotation을 사용할 수 있습니까?
예, .NET용 GroupDocs.Annotation은 상업용 및 비상업용 프로젝트 모두에서 사용할 수 있습니다. 그러나 프로젝트 요구 사항에 따라 적절한 라이선스를 취득해야 합니다.
### .NET용 GroupDocs.Annotation에 사용할 수 있는 평가판이 있습니까?
 예, 다음 사이트를 방문하여 .NET용 GroupDocs.Annotation 무료 평가판을 이용하실 수 있습니다.[이 링크](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 GroupDocs 포럼을 방문하여 기술 지원을 요청할 수 있습니다.[여기](https://forum.groupdocs.com/c/annotation/10).
### 사용할 수 있는 임시 라이센스 옵션이 있습니까?
 예, 단기 사용 또는 평가 목적으로 GroupDocs에서 임시 라이센스를 얻을 수 있습니다. 방문하다[이 링크](https://purchase.groupdocs.com/temporary-license/) 자세한 내용은.
### 내 프로젝트 요구 사항에 따라 주석 기능을 사용자 정의할 수 있나요?
예, .NET용 GroupDocs.Annotation은 광범위한 사용자 정의 옵션을 제공하므로 특정 프로젝트 요구 사항에 맞게 주석 기능을 맞춤화할 수 있습니다.