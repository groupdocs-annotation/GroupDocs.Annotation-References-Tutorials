---
title: Belgeye Uzaklık Açıklaması Ekle
linktitle: Belgeye Uzaklık Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere mesafe açıklamalarını nasıl ekleyeceğinizi öğrenin. İşbirliğini ve iletişimi zahmetsizce geliştirin.
weight: 12
url: /tr/net/unlocking-annotation-power/add-distance-annotation/
---
## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye nasıl uzaklık açıklaması ekleyeceğinizi öğreneceksiniz. Görevi gerçekleştirmek için şu adımları izleyin:
## Önkoşullar

Devam etmeden önce aşağıdaki önkoşulların mevcut olduğundan emin olun:

-  GroupDocs.Annotation for .NET Kitaplığı: GroupDocs.Annotation for .NET kitaplığını şuradan indirip yükleyin:[bu bağlantı](https://releases.groupdocs.com/annotation/net/).
- Açıklama Eklenecek Belge: Mesafe açıklaması eklemek istediğiniz belgeyi (örneğin, PDF) hazırlayın.
- Geliştirme Ortamı: Geliştirme ortamınızı Visual Studio veya seçtiğiniz herhangi bir IDE ile kurun.

## Ad Alanlarını İçe Aktar

Başlamadan önce kodunuza gerekli ad alanlarını eklediğinizden emin olun. Bu ad alanları gerekli sınıflara ve yöntemlere erişim için gereklidir.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 1. Adım: Annotator'ı Başlatın

 Başlatarak başlayın`Annotator` Açıklama eklemek istediğiniz belgenin yolunu içeren nesne.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```

## Adım 2: Uzaklık Açıklaması Oluşturun

 Şimdi bir tane oluşturun`DistanceAnnotation` nesneyi seçin ve kutu boyutları, mesaj, opaklık, kalem rengi vb. gibi özelliklerini yapılandırın.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## 3. Adım: Ek Açıklama Ekle

 Oluşturulan mesafe açıklamasını belgeye şunu kullanarak ekleyin:`Add` ek açıklama nesnesinin yöntemi.

```csharp
annotator.Add(distance);
```

## Adım 4: Belgeyi Kaydet

Açıklamalı belgeyi sisteminizde istediğiniz konuma kaydedin.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Adım 5: Onayı Görüntüle

Son olarak, açıklamalı belgenin başarıyla kaydedildiğini onaylayan bir mesaj görüntüleyin.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

GroupDocs.Annotation for .NET kullanarak belgelere uzaklık açıklamaları eklemek basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek belgelerinizi değerli ek açıklamalarla geliştirebilir, daha iyi işbirliği ve iletişimi kolaylaştırabilirsiniz.

## SSS'ler

### S: Mesafe açıklamasının görünümünü özelleştirebilir miyim?

C: Evet, gereksinimlerinize uyacak şekilde renk, opaklık, çizgi stili vb. çeşitli özellikleri özelleştirebilirsiniz.

### S: GroupDocs.Annotation, farklı belge türlerindeki açıklamaları destekliyor mu?

C: Evet, GroupDocs.Annotation, PDF, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarındaki açıklamaları destekler.

### S: GroupDocs.Annotation'ın ücretsiz deneme sürümü mevcut mu?

 C: Evet, GroupDocs.Annotation'ın ücretsiz deneme sürümüne şu adresten erişebilirsiniz:[bu bağlantı](https://releases.groupdocs.com/).

### S: GroupDocs.Annotation for .NET belgelerini nerede bulabilirim?

 C: Mevcut ayrıntılı belgelere başvurabilirsiniz[Burada](https://tutorials.groupdocs.com/annotation/net/).

### S: GroupDocs.Annotation ile nasıl destek veya yardım alabilirim?

 C: GroupDocs.Annotation topluluk forumundan destek ve yardım alabilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).