---
"description": "GroupDocs.Annotation for .NET kullanarak PDF'lere Nokta Açıklaması eklemeyi öğrenin. Sorunsuz entegrasyon için adım adım kılavuz."
"linktitle": "Belgeye Nokta Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Nokta Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Belgeye Nokta Açıklaması Ekle

## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belgelere programatik olarak çeşitli türde açıklamalar eklemesine olanak tanıyan güçlü bir araçtır. Bu eğitimde, C# kullanarak bir belgeye Nokta Açıklaması eklemeye odaklanacağız.
## Ön koşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. C# programlama dilinin temel düzeyde anlaşılması.
2. Sisteminizde Visual Studio yüklü.
3. GroupDocs.Annotation for .NET kütüphanesi yüklendi. Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).

## Gerekli Ad Alanlarını İçe Aktarma
Başlamak için gerekli ad alanlarını C# projenize aktarmanız gerekir:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıktı Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Bu adımda, açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## Adım 2: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Burada, şunu başlatıyoruz: `Annotator` Giriş belgesine sahip nesne ("input.pdf").
## Adım 3: Nokta Açıklaması Oluşturun
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
Bu adımda bir tane oluşturuyoruz `PointAnnotation` nesneyi seçin ve konum, mesaj, sayfa numarası ve yanıtlar gibi özelliklerini belirtin.
## Adım 4: Açıklama Ekle
```csharp
annotator.Add(point);
```
Burada oluşturulan nokta açıklamasını dokümana ekliyoruz.
## Adım 5: Belgeyi Kaydedin
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye Nokta Açıklaması eklemeyi öğrendik. Bu güçlü kütüphaneyle, açıklama işlevlerini dahil ederek belge yönetimi uygulamalarınızı geliştirebilirsiniz.
## SSS
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation for .NET, PDF, Microsoft Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### Açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation for .NET, uygulamanızın ihtiyaçlarına uyacak şekilde açıklamaların görünümünü özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs.Annotation for .NET için ücretsiz deneme sürümü mevcut mu?
Evet, ücretsiz denemeden faydalanabilirsiniz [Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET ile ilgili herhangi bir sorun veya sorgu için nasıl destek alabilirim?
GroupDocs.Annotation forumundan destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amaçlı geçici lisans alabilir miyim?
Evet, geçici bir lisans alabilirsiniz. [Burada](https://purchase.groupdocs.com/temporary-license/).