---
title: Belgeye Filigran Açıklaması Ekleme
linktitle: Belgeye Filigran Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelerinize filigran açıklamalarını zahmetsizce nasıl ekleyeceğinizi öğrenin. Belge netliğini ve güvenliğini artırın.
weight: 28
url: /tr/net/unlocking-annotation-power/add-watermark-annotation/
---

# Belgeye Filigran Açıklaması Ekleme

## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye filigran ek açıklaması ekleme sürecini anlatacağız. Filigran ek açıklamaları bir belgenin durumunu belirtmek, onu gizli olarak işaretlemek veya diğer ilgili bilgileri eklemek için kullanışlıdır.

## Önkoşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  GroupDocs.Annotation for .NET: Şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Sisteminizde Visual Studio'nun kurulu olduğundan emin olun.
3. Temel C# Bilgisi: Kod örneklerini anlamak ve uygulamak için C# programlama diline aşinalık gereklidir.

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce gerekli ad alanlarını içe aktaralım:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Şimdi filigran ek açıklaması ekleme sürecini birden çok adıma ayıralım:

## Adım 1: Çıkış Yolunu Tanımlayın

 Öncelikle açıklamalı belgenin kaydedileceği çıktı yolunu tanımlamamız gerekiyor. biz kullanacağız`Path` gelen sınıf`System.IO` çıktı dizini yolunu dosya adıyla birleştirmek için ad alanı.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. Adım: Annotator'ı Başlatın

Daha sonra, giriş belgesinin yolunu sağlayarak açıklayıcıyı başlatacağız. Bu, belgeye ek açıklamalar eklememize olanak tanır.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```

## 3. Adım: Filigran Açıklaması Oluşturun

Şimdi açı, konum, metin, yazı tipi rengi, opaklık vb. gibi istenilen özelliklere sahip bir filigran açıklama nesnesi oluşturalım.

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

## 4. Adım: Filigran Açıklaması Ekleme

 Şimdi filigran açıklamasını belgeye şunu kullanarak ekleyeceğiz:`Add` ek açıklama nesnesinin yöntemi.

```csharp
annotator.Add(watermark);
```

## Adım 5: Belgeyi Kaydet

Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydedeceğiz.

```csharp
annotator.Save(outputPath);
```

## Çözüm

Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye filigran ek açıklamasının nasıl ekleneceğini öğrendik. Filigran ek açıklamaları, belgeleri ilgili bilgilerle işaretlemek veya durumlarını belirtmek için değerli bir araçtır.

## SSS'ler

### S: Filigran ek açıklamasının görünümünü özelleştirebilir miyim?

C: Evet, filigranı ihtiyaçlarınıza göre uyarlamak için metin, yazı tipi boyutu, renk, opaklık, konum vb. çeşitli özellikleri özelleştirebilirsiniz.

### S: GroupDocs.Annotation for .NET farklı belge formatlarıyla uyumlu mudur?

C: Evet, GroupDocs.Annotation; PDF, Microsoft Word, Excel, PowerPoint ve görüntü formatları da dahil olmak üzere çok çeşitli belge formatlarını destekler.

### S: Tek bir belgeye birden fazla açıklama ekleyebilir miyim?

C: Kesinlikle, GroupDocs.Annotation, tek bir belgeye farklı türde birden fazla açıklama eklemenizi sağlayarak kapsamlı belge işaretlemesine olanak tanır.

### S: GroupDocs.Annotation işbirliğine dayalı açıklama ekleme desteği sağlıyor mu?

C: Evet, GroupDocs.Annotation, kullanıcıların yorumlar, yanıtlar ve açıklamalar eklemesine olanak tanıyarak ekip üyeleri arasında etkili işbirliğini teşvik ederek ortak açıklama eklemeyi kolaylaştırır.

### S: GroupDocs.Annotation for .NET'in deneme sürümü mevcut mu?

 C: Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).