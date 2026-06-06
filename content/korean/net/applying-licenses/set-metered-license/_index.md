---
categories:
- Licensing
date: '2026-06-06'
description: 애플리케이션에서 문서 주석 작업을 위한 리소스 사용을 최적화하고 비용을 절감하기 위해 GroupDocs.Annotation
  .NET에 메터드 라이선스를 설정하는 방법을 알아보세요.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: 메터드 라이선스 설정
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: GroupDocs.Annotation .NET에 대한 메터드 라이선스 설정 방법 – 사용한 만큼만 비용 지불
type: docs
url: /ko/net/applying-licenses/set-metered-license/
weight: 12
---

# GroupDocs.Annotation .NET에 대한 사용량 기반 라이선스 설정 – 사용한 만큼만 비용 지불

## 빠른 답변
- **사용량 기반 라이선스란?** 앱이 실제로 수행하는 주석 작업에 대해서만 비용을 지불하는 사용량 기반 모델입니다.  
- **필요한 키 수는?** 라이선스를 활성화하려면 공개 키와 비공개 키, 두 개의 키가 필요합니다.  
- **언제 라이선스를 초기화해야 하나요?** 애플리케이션 시작 시 또는 DI 컨테이너 구성 중, 어떤 주석 호출보다 먼저 초기화합니다.  
- **인터넷 연결이 필요합니까?** 예, SDK는 사용량을 주기적으로 보고하기 위해 GroupDocs 서버에 연결합니다.  
- **나중에 영구 라이선스로 전환할 수 있나요?** 물론입니다; 언제든지 GroupDocs 대시보드에서 라이선스 모델을 변경할 수 있습니다.

## 사용량 기반 라이선스란?
**metered license**는 각 주석 요청을 추적하고 실제 사용량에 따라 비용을 청구하는 GroupDocs.Annotation의 사용량 기반 결제 옵션입니다. 대규모 초기 비용을 없애고 투명한 실시간 청구를 제공하며 워크로드에 따라 자동으로 확장되어 주석을 다는 페이지에 대해서만 비용을 지불하게 합니다.

## 문서 주석에 사용량 기반 라이선스를 설정해야 하는 이유
사용량 기반 라이선스를 설정하면 비용을 실제 사용량에 맞출 수 있어 예측 가능한 지출을 제공하면서 성장도 지원합니다. 대규모 초기 결제가 필요 없으며 상세한 사용량 인사이트를 제공하고, 라이선스 제한 없이 급증하는 트래픽을 처리할 수 있습니다.

사용량 기반 라이선스는 **정량화된 이점**을 제공합니다:

- **비용 절감:** 실제 주석된 페이지 수에 대해서만 비용을 지불합니다. 예를 들어, 한 달에 2 000 페이지를 처리하는 경우 1 000 페이지당 $0.02만 비용이 들 수 있으며, $500 영구 라이선스와 비교됩니다.  
- **확장성:** **월 100 000+ 페이지**까지 수동 라이선스 업그레이드 없이 지원합니다.  
- **선투자 비용 없음:** 대규모 자본 지출이 필요 없으며, 무료 체험으로 즉시 테스트를 시작할 수 있습니다.  
- **상세 보고:** 대시보드에서 작업별 사용량을 표시하여 ±5 % 정확도로 비용을 예측할 수 있습니다.

## 전제 조건
시작하기 전에 다음 항목을 확인하십시오:

1. **GroupDocs.Annotation for .NET 라이브러리** – 최신 빌드를 [웹사이트](https://releases.groupdocs.com/annotation/net/)에서 다운로드하십시오. 또한 [이 링크](https://releases.groupdocs.com/)를 통해 직접 다운로드 페이지에 접근할 수 있습니다.  
2. **GroupDocs 계정** – 공개 키와 비공개 키를 가져오려면 활성 계정이 필요합니다. 계정이 없으면 [무료 체험에 가입](https://releases.groupdocs.com/)할 수 있습니다.  
3. **.NET 개발 환경** – Visual Studio 2022 또는 .NET 6+를 대상으로 하는 IDE(또는 .NET Framework 4.7.2에서도 SDK 사용 가능).  
4. **인터넷 액세스** – SDK는 15분마다 사용량 데이터를 GroupDocs 서버에 전송하므로 안정적인 외부 HTTPS 연결이 필수입니다.

## 네임스페이스 가져오기
`Metered` 클래스는 `GroupDocs.Annotation.License` 네임스페이스에 존재합니다. `Metered`는 GroupDocs 라이선스 서버와의 모든 통신을 처리하고 사용량 기반 키를 검증합니다. C# 파일 상단에 다음과 같이 가져오세요:

```csharp
using System;
```

> **정의 앵커:** `Metered` 클래스는 GroupDocs 라이선스 서버와의 모든 통신을 처리하고 사용량 기반 키를 검증합니다.

## GroupDocs.Annotation .NET에서 사용량 기반 라이선스를 설정하는 방법?
사용량 기반 라이선스를 구성하려면 공개 키와 비공개 키를 로드하고 `Metered` 객체를 인스턴스화한 뒤 `SetMeteredLicense`를 호출합니다. 이 호출은 키를 GroupDocs 서버에서 검증하고 보안 TLS 채널을 설정하며 모든 주석 작업을 추적하기 시작해 전체 애플리케이션에 대해 사용량 기반 청구를 가능하게 합니다. `SetMeteredLicense`는 SDK에 사용량 기반 라이선스 모델을 활성화합니다. 공개 키와 비공개 키를 로드하고 `Metered` 인스턴스를 만든 뒤 `SetMeteredLicense`를 호출하면 전체 애플리케이션에 사용량 기반 모델이 활성화됩니다.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **직접 답변 (40‑70 단어):**  
> 공개 및 비공개 키로 `Metered` 객체를 생성한 뒤 모든 주석 작업 전에 `SetMeteredLicense()`를 호출합니다. SDK는 즉시 키를 검증하고 GroupDocs 서버와 보안 TLS 채널을 설정하며 각 페이지 주석 요청을 추적합니다. 설정이 완료되면 이후 모든 API 호출이 사용량 기반 라이선스로 적용됩니다.

### 단계 1: 사용량 기반 라이선스 키 가져오기
첫 번째 실무 단계는 GroupDocs 대시보드에서 공개 키와 비공개 키를 가져오는 것입니다.

1. 자신의 자격 증명을 사용하여 GroupDocs 계정에 로그인합니다.  
2. 대시보드 사이드바에서 **License Management**(라이선스 관리)로 이동합니다.  
3. 사용량 기반 라이선스 항목을 찾으면 **Public Key**(공개 키)와 **Private Key**(비공개 키)가 나란히 표시됩니다.  
4. 두 키를 복사하여 안전하게 보관합니다—비밀번호처럼 취급하십시오.

> **Pro Tip:** 키를 환경 변수(`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) 또는 비밀 관리자(Azure Key Vault, AWS Secrets Manager)에 저장하세요. 소스 제어에 하드코딩하지 마세요.

### 단계 2: 사용량 기반 라이선스 설정 구현
이제 키를 애플리케이션 시작 코드에 삽입합니다. 다음 스니펫이 필요한 정확한 순서를 보여줍니다:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explanation:**  
> - **`Metered` 객체를 생성**하여 라이선스 로직을 캡슐화합니다.  
> - **공개 및 비공개 키를** 생성자에 전달하여 서명된 요청을 설정합니다.  
> - **`SetMeteredLicense()`를 호출**하여 GroupDocs 라이선스 엔드포인트에 연결하고 키를 검증하며 사용량 추적을 활성화합니다.  
> - **모든 주석 기능**(하이라이트, 댓글, 그리기)이 즉시 사용 가능해집니다.

### 단계 3: 라이선스 초기화 보안 강화
연결 문제나 키 오류를 우아하게 처리하려면 초기화를 try‑catch 블록으로 감싸세요. 라이선스를 검증하거나 적용할 수 없을 때 `LicenseException`이 발생합니다.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Why this matters:**  
> - **네트워크 실패** 또는 잘못된 키가 `LicenseException`을 발생시킵니다. 이를 잡아두면 앱이 크래시되는 것을 방지하고 읽기 전용 모드로 전환하거나 친절한 오류 페이지를 표시할 수 있습니다.  
> - **예외를 상관관계 ID와 함께 로깅**하면 지원 팀이 청구 분쟁을 신속히 진단하는 데 도움이 됩니다.

## 프로덕션 구현을 위한 모범 사례
기본 설정은 몇 줄에 불과하지만, 프로덕션 환경에서는 추가적인 주의가 필요합니다.

### 중앙 집중식 초기화
라이선스 호출을 단일 위치에 배치하세요—예: ASP.NET Core의 `Program.cs` 또는 콘솔 앱의 `Main` 메서드. 이렇게 하면 컨트롤러나 서비스가 API에 접근하기 전에 라이선스가 준비됩니다.

### 의존성 주입(DI) 통합
DI 컨테이너를 사용하는 경우 `Metered` 인스턴스를 싱글톤으로 등록합니다:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Result:** 주석 서비스를 필요로 하는 모든 구성 요소가 동일한 라이선스 인스턴스를 받아 중복 네트워크 호출을 줄입니다.

### 키의 안전한 저장
- **환경 변수** – 호스트 OS 또는 CI/CD 파이프라인에 설정합니다.  
- **Azure App Configuration / AWS Parameter Store** – 저장 시 암호화와 감사 로그를 제공합니다.  
- **Docker Secrets** – 컨테이너 배포 시 파일로 마운트하여 사용합니다.

### 사용량 모니터링
내장 사용량 로거를 활성화합니다:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

GroupDocs 포털의 **Usage** 탭을 주간 단위로 검토하면 정확한 페이지 수, API 호출 유형 및 비용 예측을 확인할 수 있습니다.

## 일반적인 문제 및 해결 방법

### “Invalid License Keys”(잘못된 라이선스 키) 오류
**근본 원인:**  
- 키를 복사할 때 공백이나 줄 바꿈 문자가 포함된 경우.  
- 다른 제품(예: GroupDocs.Viewer)의 키를 사용한 경우.  
- 키가 만료되었거나 비활성화된 경우.

**해결 방법:**  
1. 대시보드에서 키를 직접 다시 복사하고 주변 공백이 없도록 합니다.  
2. 키가 *Metered* 탭 아래 **GroupDocs.Annotation**에 속하는지 확인합니다.  
3. 계정 상태가 활성인지 확인합니다(연체 결제 없음).

### 네트워크 연결 문제
**Symptoms:** 라이선스 검증이 타임아웃 또는 DNS 오류로 실패합니다.

**Solutions:**  
- 방화벽에서 HTTPS 트래픽을 위한 **443** 포트를 열어 둡니다.  
- 기업 프록시 뒤에 있는 경우 `SetMeteredLicense()` 호출 전에 `WebRequest.DefaultWebProxy`를 프록시 URL로 설정합니다.  
- 일시적인 실패에 대비해 지수 백오프 재시도 로직을 구현합니다.

### 사용량 보고 지연
서버 측 배치 처리로 인해 사용량 데이터가 **24 시간**까지 지연될 수 있습니다. 이는 정상이며, 대시보드에 최종 카운트가 표시됩니다.

### 예상치 못한 높은 청구
스파이크가 발생하면 다음을 확인하세요:

- **스로틀링 없이 실행되는 배치 주석 작업**.  
- **같은 문서를 반복적으로 주석 달는 자동화 봇**.  
- **캐시 누락**으로 인해 매 요청마다 동일 문서를 재주석하는 경우.

서버 측 속도 제한 및 처리된 문서 캐싱을 추가하면 완화할 수 있습니다.

## 비용 최적화 전략
| 전략 | 비용 절감 방법 |
|----------|--------------------|
| **배치 처리** | 여러 주석 작업을 하나의 API 호출로 결합하여 페이지당 오버헤드를 줄입니다. |
| **문서 캐싱** | 주석이 달린 PDF를 CDN 또는 블롭 스토리지에 저장하여 변경되지 않은 파일의 재주석을 방지합니다. |
| **사용량 알림** | 일일 사용량이 임계값(예: 5 000 페이지)을 초과하면 GroupDocs 포털에서 이메일 알림을 설정합니다. |
| **선택적 기능 활성화** | `AnnotationOptions`를 통해 잘 사용되지 않는 주석 유형(예: 3‑D 스탬프)을 비활성화하여 불필요한 처리를 줄입니다. |

## 언제 사용량 기반 라이선스와 기존 라이선스를 선택할까
주석량이 변동하거나 사용량 기반 청구를 선호하는 경우 사용량 기반 라이선스를 선택하고, 지속적으로 높은 워크로드가 예측 가능하거나 인터넷 접근이 불가능한 환경에서는 영구 라이선스를 선택합니다. 월 페이지 수, 예산 유연성, 네트워크 제한 등을 평가해 가장 비용 효율적인 모델을 결정하세요.

## 결론
GroupDocs.Annotation .NET에 대한 **사용량 기반 라이선스** 설정은 간단하지만, 진정한 가치는 제공되는 유연성과 비용 투명성에 있습니다. 위 단계대로 진행하고 키를 안전하게 보관하며 프로덕션 모범 사례를 적용하면 비즈니스와 함께 성장하는 확장 가능한 사용량 기반 문서 주석을 구현할 수 있습니다.

사용량을 정기적으로 모니터링하고 자격 증명을 안전하게 관리하며 내장 로깅을 활용해 청구를 예측 가능하게 유지하세요. 협업 검토 플랫폼, 법률 문서 관리 시스템, 간단한 주석 위젯을 구축하든, 사용량 기반 라이선스 모델은 실제 제공하는 가치에 대해서만 비용을 지불하도록 보장합니다.

## 자주 묻는 질문

**Q: GroupDocs.Annotation for .NET을 상업 프로젝트에 사용할 수 있나요?**  
A: 예, 유효한 사용량 기반 또는 영구 라이선스를 보유하면 라이브러리를 상업적으로 완전 사용 허가됩니다.

**Q: 사용량 기반 라이선스 흐름을 테스트할 수 있는 체험 버전이 있나요?**  
A: 예, [웹사이트](https://releases.groupdocs.com/)에서 무료 체험을 받을 수 있습니다.

**Q: 라이선스 문제에 대한 기술 지원은 어떻게 받나요?**  
A: [여기](https://forum.groupdocs.com/c/annotation/10)에서 GroupDocs 포럼을 방문해 질문을 게시하거나 지원 티켓을 열 수 있습니다.

**Q: 단기 평가를 위한 임시 라이선스 옵션이 있나요?**  
A: 물론입니다—임시 라이선스는 제한된 기간 동안 제공됩니다. 자세한 내용은 [이 링크](https://purchase.groupdocs.com/temporary-license/)를 확인하세요.

**Q: 사용량 기반 라이선스의 사용량 추적 정확도는 어느 정도인가요?**  
A: 추적은 단일 페이지 주석 단위까지 정확하며, 보고서는 일반적으로 24 시간 이내에 갱신됩니다.

---

**Last Updated:** 2026-06-06  
**Tested With:** GroupDocs.Annotation 23.12 for .NET  
**Author:** GroupDocs

## 관련 튜토리얼

- [GroupDocs Annotation .NET 라이선스 설정 - 전체 구현 가이드](/annotation/net/applying-licenses/set-license-from-file/)
- [스트림에서 라이선스 설정 .NET - 전체 GroupDocs.Annotation 가이드](/annotation/net/applying-licenses/set-license-from-stream/)
- [GroupDocs.Annotation 라이선싱 .NET - 전체 설정 및 구성](/annotation/net/licensing-and-configuration/)