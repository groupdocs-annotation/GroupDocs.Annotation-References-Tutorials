---
"date": "2025-05-06"
"description": "GroupDocs.Annotation for .NET'i kullanarak bir PDF'in yalnızca açıklamalı sayfalarını nasıl etkili bir şekilde kaydedeceğinizi öğrenin. Bu ayrıntılı kılavuzla belge yönetimini ve iş birliğini geliştirin."
"title": "GroupDocs.Annotation for .NET Kullanılarak Açıklamalı Sayfalar PDF Olarak Nasıl Kaydedilir"
"url": "/tr/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# GroupDocs.Annotation for .NET Kullanılarak Açıklamalı Sayfalar PDF Olarak Nasıl Kaydedilir

## giriiş

PDF belgelerinizden belirli açıklamalı sayfaları kaydetmekte zorluk mu çekiyorsunuz? Bu kapsamlı kılavuz, GroupDocs.Annotation for .NET kullanarak bunu nasıl verimli bir şekilde başaracağınızı gösterir. Açıklama yeteneklerinden yararlanarak, belge yönetimini kolaylaştırın ve ilgili içeriğe odaklanarak iş birliğini geliştirin.

Bu eğitimde şunları öğreneceksiniz:
- GroupDocs.Annotation ile geliştirme ortamınızı kurma
- Çeşitli türde açıklamalar ekleme
- Yalnızca açıklamalı sayfaları etkili bir şekilde kaydetme

Başlamaya hazır mısınız? Her şeyin hazır olduğundan emin olalım.

### Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- **.NET Çerçevesi** (4.6 veya üzeri sürüm) veya **.NET Çekirdek/5+**
- Visual Studio gibi bir kod düzenleyici
- C# ve .NET proje kurulumunun temel bilgisi

## .NET için GroupDocs.Annotation Kurulumu

GroupDocs.Annotation'ı kullanmaya başlamak için NuGet üzerinden yüklemeniz gerekiyor.

**NuGet Paket Yöneticisi Konsolu**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET Komut Satırı Arayüzü**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Lisans Edinimi

GroupDocs, yazılımlarını tam olarak keşfetmeniz için ücretsiz deneme sürümü sunar. Uzun süreli kullanım için bir lisans satın alın veya geçici bir lisans talep edin:
- **Ücretsiz Deneme**: Başlangıç için herhangi bir sınırlama olmaksızın özellikleri keşfedin.
- **Geçici Lisans**: Üretimde geçici olarak GroupDocs.Annotation kullanın.
- **Satın almak**Uzun vadeli ihtiyaçlarınızı ticari lisansla güvence altına alın.

Kurulum tamamlandıktan sonra kütüphaneyi aşağıdaki şekilde başlatın:

```csharp
using GroupDocs.Annotation;

// Belgeleri yüklemek ve açıklamalar eklemek için temel kurulum
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Uygulama Kılavuzu

### Açıklama Ekleme

#### Genel bakış

Açıklamalar, belgenizdeki önemli alanları vurgulamanıza yardımcı olur. Bir açıklama eklemeyi keşfedelim `AreaAnnotation` ve bir `EllipseAnnotation`.

**Adım 1: Alan Açıklaması Oluşturun**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Alan açıklamasını tanımlayın
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozisyon ve boyut
    BackgroundColor = 65535,                // Vurgulama için ARGB renk değeri
    PageNumber = 1                          // Belirli sayfa numarası
};
```

The `AreaAnnotation` Belgede dikdörtgen bir alanı vurgular. Konumunu özelleştirin (`Box`) ve arka plan rengi.

**Adım 2: Elips Açıklaması Oluşturun**

```csharp
// Elips açıklamasını tanımlayın
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozisyon ve boyut
    BackgroundColor = 123456,                // Vurgulama için ARGB renk değeri
    PageNumber = 1                           // Belirli sayfa numarası
};
```

The `EllipseAnnotation` belgeye oval bir şekil çizmeye izin verir. Konumu ve boyutları kullanarak ayarlayın `Box` mülk.

**Adım 3: Açıklamalar Ekleyin**

```csharp
// Annotator örneğine açıklamalar ekleme
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Kullanımı `Add` yöntem, birden fazla türde açıklama içerir. Bu adım, her ikisini de ekler `AreaAnnotation` Ve `EllipseAnnotation`.

### Yalnızca Açıklamalı Sayfaları Kaydetme

#### Genel bakış

Yalnızca açıklama içeren sayfaları kaydetmek için kaydetme seçeneklerinizi buna göre yapılandırın.

**Adım 4: Açıklamalı Sayfaları Kaydet**

```csharp
using GroupDocs.Annotation.Options;

// Kaydetme seçeneklerini yalnızca açıklamalı sayfaları içerecek şekilde ayarlayın
annotator.Save("path/to/output/document.pdf\