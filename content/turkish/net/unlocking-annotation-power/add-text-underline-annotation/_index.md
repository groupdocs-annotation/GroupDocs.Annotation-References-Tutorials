---
"description": "GroupDocs.Annotation for .NET kullanarak belgelere metin altı çizili ek açıklamalar eklemeyi öğrenin. İş birliğini ve iletişimi zahmetsizce geliştirin."
"linktitle": "Belgeye Metin Altı Çizili Açıklama Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Metin Altı Çizili Açıklama Ekle"
"url": "/tr/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Belgeye Metin Altı Çizili Açıklama Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye metin altı çizili açıklama ekleme sürecini ele alacağız. Metin altı çizili açıklamalar, önemli pasajlar veya anahtar noktalar gibi bir belgenin belirli bölümlerini vurgulamak için yararlı olabilir.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşulların yüklü olduğundan emin olun:
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i şu adresten indirin ve yükleyin: [Burada](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Sisteminizde .NET Framework'ün yüklü olduğundan emin olun.

## Ad Alanlarını İçe Aktarma
Öncelikle gerekli namespace'leri projemize aktaralım:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Şimdi örneği birden fazla adıma bölelim:
## Adım 1: Çıktı Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Bu adımda, açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## Adım 2: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Burada, bir örneğini başlatıyoruz `Annotator` Giriş belgesinin yolunu sağlayarak sınıf.
## Adım 3: Alt Çizgili Açıklama Oluşturun
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // yalnızca Word ve PDF belgelerini destekleyen çalışmalar
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Bu adım, bir `UnderlineAnnotation` Yazı tipi rengi, mesaj, opaklık, sayfa numarası, arka plan rengi, alt çizgi rengi, puan ve yanıtlar gibi çeşitli özelliklere sahip nesne.
## Adım 4: Belgeye Açıklama Ekleme
```csharp
annotator.Add(underline);
```
Burada belgeye alt çizgi açıklamasını ekliyoruz.
## Adım 5: Açıklamalı Belgeyi Kaydet
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye metin altı çizili açıklama eklemeyi öğrendik. Bu güçlü kitaplık, belge iş birliğini ve iletişimini geliştirmek için çeşitli açıklama seçenekleri sunar.
## SSS
### Alt çizgi açıklamalarının görünümünü özelleştirebilir miyim?
Evet, renk, opaklık ve konum gibi özellikleri ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Annotation farklı belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation Word ve PDF dahil olmak üzere çok çeşitli belge formatlarını destekler.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Kesinlikle, GroupDocs.Annotation bir belgeye farklı türlerde birden fazla açıklama eklemenize olanak tanır.
### GroupDocs.Annotation için ücretsiz deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümüne şu adresten erişebilirsiniz: [Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için desteği nereden alabilirim?
GroupDocs.Annotation topluluk forumundan destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).