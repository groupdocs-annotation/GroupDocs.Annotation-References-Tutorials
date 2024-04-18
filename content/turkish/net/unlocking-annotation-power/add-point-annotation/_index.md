---
title: Belgeye Nokta Açıklaması Ekle
linktitle: Belgeye Nokta Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak PDF'lere Nokta Açıklaması eklemeyi öğrenin. Sorunsuz entegrasyon için adım adım kılavuz.
type: docs
weight: 17
url: /tr/net/unlocking-annotation-power/add-point-annotation/
---
## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belgelere programlı olarak çeşitli türde ek açıklamalar eklemesine olanak tanıyan güçlü bir araçtır. Bu eğitimde, C# kullanarak bir belgeye Nokta Açıklaması eklemeye odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. C# programlama dilinin temel anlayışı.
2. Sisteminizde Visual Studio yüklü.
3.  GroupDocs.Annotation for .NET kitaplığı yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).

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
## Adım 1: Çıkış Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Bu adımda açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## 2. Adım: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Burada başlatıyoruz`Annotator` giriş belgesini ("input.pdf") içeren nesne.
## 3. Adım: Nokta Açıklaması Oluşturun
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
 Bu adımda bir oluşturuyoruz.`PointAnnotation` nesneyi seçin ve konum, mesaj, sayfa numarası ve yanıtlar gibi özelliklerini belirtin.
## 4. Adım: Ek Açıklama Ekle
```csharp
annotator.Add(point);
```
Burada oluşturulan nokta açıklamasını belgeye ekliyoruz.
## Adım 5: Belgeyi Kaydet
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye Nokta Açıklaması eklemeyi öğrendik. Bu güçlü kütüphaneyle, açıklama işlevleri ekleyerek belge yönetimi uygulamalarınızı geliştirebilirsiniz.
## SSS'ler
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Annotation for .NET; PDF, Microsoft Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation for .NET, uygulamanızın ihtiyaçlarına uyacak şekilde ek açıklamaların görünümünü özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs.Annotation for .NET'in ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümünden yararlanabilirsiniz.[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET ile ilgili herhangi bir sorun veya sorgu için nasıl destek alabilirim?
 GroupDocs.Annotation forumundan destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amaçlı geçici lisans alabilir miyim?
 Evet, adresinden geçici lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).