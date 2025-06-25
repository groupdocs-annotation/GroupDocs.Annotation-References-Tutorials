---
"description": "GroupDocs.Annotation for .NET'i kullanarak belgelerinize filigran açıklamalarını zahmetsizce nasıl ekleyeceğinizi öğrenin. Belge netliğini ve güvenliğini artırın."
"linktitle": "Belgeye Filigran Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Filigran Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Belgeye Filigran Açıklaması Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye filigran açıklaması ekleme sürecini ele alacağız. Filigran açıklamaları, bir belgenin durumunu belirtmek, onu gizli olarak işaretlemek veya diğer ilgili bilgileri eklemek için kullanışlıdır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. GroupDocs.Annotation for .NET: Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Sisteminizde Visual Studio'nun yüklü olduğundan emin olun.
3. Temel C# Bilgisi: Kod örneklerini anlamak ve uygulamak için C# programlama diline aşina olmak gerekir.

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce gerekli namespace'leri import edelim:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Şimdi, filigran açıklaması ekleme sürecini birden fazla adıma bölelim:

## Adım 1: Çıktı Yolunu Tanımlayın

İlk olarak, açıklamalı belgenin kaydedileceği çıktı yolunu tanımlamamız gerekir. `Path` sınıftan `System.IO` Çıktı dizin yolunu dosya adıyla birleştirmek için namespace.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Adım 2: Annotator'ı Başlatın

Sonra, giriş belgesinin yolunu sağlayarak açıklayıcıyı başlatacağız. Bu, belgeye açıklamalar eklememize olanak tanıyacaktır.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelecek
}
```

## Adım 3: Filigran Açıklaması Oluşturun

Şimdi açı, konum, metin, yazı rengi, opaklık vb. gibi istediğimiz özelliklere sahip bir filigran açıklama nesnesi oluşturalım.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```

## Adım 4: Filigran Açıklaması Ekle

Şimdi, filigran açıklamasını belgeye şu şekilde ekleyeceğiz: `Add` açıklayıcı nesnenin yöntemi.

```csharp
annotator.Add(watermark);
```

## Adım 5: Belgeyi Kaydedin

Son olarak, açıklamalı belgeyi belirtilen çıktı yoluna kaydedeceğiz.

```csharp
annotator.Save(outputPath);
```

## Çözüm

Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye filigran ek açıklamasının nasıl ekleneceğini öğrendik. Filigran ek açıklamaları, belgeleri ilgili bilgilerle işaretlemek veya durumlarını belirtmek için değerli bir araçtır.

## SSS

### S: Filigran açıklamasının görünümünü özelleştirebilir miyim?

C: Evet, filigranı ihtiyaçlarınıza göre uyarlamak için metin, yazı tipi boyutu, renk, opaklık, konum vb. gibi çeşitli özellikleri özelleştirebilirsiniz.

### S: GroupDocs.Annotation for .NET farklı belge formatlarıyla uyumlu mudur?

C: Evet, GroupDocs.Annotation PDF, Microsoft Word, Excel, PowerPoint ve resim formatları da dahil olmak üzere çok çeşitli belge formatlarını destekler.

### S: Tek bir belgeye birden fazla açıklama ekleyebilir miyim?

C: Kesinlikle, GroupDocs.Annotation tek bir belgeye farklı türlerde birden fazla açıklama eklemenize olanak tanır ve kapsamlı belge işaretlemesi sağlar.

### S: GroupDocs.Annotation işbirlikçi açıklama desteği sağlıyor mu?

C: Evet, GroupDocs.Annotation kullanıcıların yorum, yanıt ve açıklama eklemesine olanak tanıyarak işbirlikçi açıklama eklemeyi kolaylaştırır ve ekip üyeleri arasında etkili bir iş birliğini teşvik eder.

### S: GroupDocs.Annotation for .NET için deneme sürümü mevcut mu?

A: Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz: [Burada](https://releases.groupdocs.com/).