---
title: Belgeye Metin Altı Çizili Açıklaması Ekleme
linktitle: Belgeye Metin Altı Çizili Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere metin altı çizili ek açıklamaları nasıl ekleyeceğinizi öğrenin. İşbirliğini ve iletişimi zahmetsizce geliştirin.
type: docs
weight: 27
url: /tr/net/unlocking-annotation-power/add-text-underline-annotation/
---
## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye metin altı çizili ek açıklama ekleme sürecini anlatacağız. Metin altı çizili ek açıklamalar, bir belgenin önemli pasajlar veya önemli noktalar gibi belirli bölümlerini vurgulamak için yararlı olabilir.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların kurulu olduğundan emin olun:
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Sisteminizde .NET Framework'ün kurulu olduğundan emin olun.

## Ad Alanlarını İçe Aktarma
Öncelikle gerekli namespace’leri projemize aktaralım:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Şimdi örneği birden çok adıma ayıralım:
## Adım 1: Çıkış Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Bu adımda açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## 2. Adım: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Burada, bir örneğini başlatıyoruz`Annotator` giriş belgesinin yolunu sağlayarak sınıf.
## 3. Adım: Altı Çizili Açıklama Oluşturun
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
 Bu adım bir oluşturmayı içerir`UnderlineAnnotation`yazı rengi, mesaj, opaklık, sayfa numarası, arka plan rengi, alt çizgi rengi, noktalar ve yanıtlar gibi çeşitli özelliklere sahip nesne.
## 4. Adım: Belgeye Ek Açıklama Ekleme
```csharp
annotator.Add(underline);
```
Burada belgeye altı çizili açıklamayı ekliyoruz.
## Adım 5: Açıklamalı Belgeyi Kaydetme
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye metin altı çizili ek açıklamanın nasıl ekleneceğini öğrendik. Bu güçlü kitaplık, belgelerde işbirliğini ve iletişimi geliştirmek için çeşitli açıklama seçenekleri sunar.
## SSS'ler
### Altı çizili açıklamanın görünümünü özelleştirebilir miyim?
Evet, renk, opaklık ve konum gibi özellikleri ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Annotation farklı belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Annotation, Word ve PDF dahil çok çeşitli belge formatlarını destekler.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Kesinlikle GroupDocs.Annotation, bir belgeye farklı türde birden fazla açıklama eklemenize olanak tanır.
### GroupDocs.Annotation'ın ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümüne şuradan erişebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için nereden destek alabilirim?
 GroupDocs.Annotation topluluk forumundan destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/annotation/10).