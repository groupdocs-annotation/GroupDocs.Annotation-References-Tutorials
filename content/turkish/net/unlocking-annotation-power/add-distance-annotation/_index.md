---
"description": "GroupDocs.Annotation for .NET kullanarak belgelere uzaklık açıklamalarının nasıl ekleneceğini öğrenin. İş birliğini ve iletişimi zahmetsizce geliştirin."
"linktitle": "Belgeye Mesafe Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Mesafe Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Belgeye Mesafe Açıklaması Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye mesafe açıklaması eklemeyi öğreneceksiniz. Görevi tamamlamak için şu adımları izleyin:
## Ön koşullar

Devam etmeden önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- GroupDocs.Annotation for .NET Kitaplığı: GroupDocs.Annotation for .NET kitaplığını şu adresten indirin ve yükleyin: [bu bağlantı](https://releases.groupdocs.com/annotation/net/).
- Açıklama Yapılacak Belge: Mesafe açıklaması eklemek istediğiniz belgeyi (örneğin PDF) hazırlayın.
- Geliştirme Ortamı: Visual Studio veya tercih ettiğiniz herhangi bir IDE ile geliştirme ortamınızı kurun.

## Ad Alanlarını İçe Aktar

Başlamadan önce, kodunuza gerekli ad alanlarını eklediğinizden emin olun. Bu ad alanları, gerekli sınıflara ve yöntemlere erişmek için olmazsa olmazdır.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Adım 1: Annotator'ı Başlatın

Başlatma ile başlayın `Annotator` Açıklama eklemek istediğiniz belgenin yolunu içeren nesne.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelecek
}
```

## Adım 2: Mesafe Açıklaması Oluşturun

Şimdi bir tane yaratın `DistanceAnnotation` nesneyi oluşturun ve kutu boyutları, mesaj, opaklık, kalem rengi vb. gibi özelliklerini yapılandırın.

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

## Adım 3: Açıklama Ekle

Oluşturulan mesafe açıklamasını belgeye şunu kullanarak ekleyin: `Add` açıklayıcı nesnenin yöntemi.

```csharp
annotator.Add(distance);
```

## Adım 4: Belgeyi Kaydedin

Açıklamalı belgeyi sisteminizde istediğiniz yere kaydedin.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Adım 5: Onay Ekranı

Son olarak, açıklamalı belgenin başarıyla kaydedildiğini onaylayan bir mesaj görüntülenir.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

GroupDocs.Annotation for .NET kullanarak belgelere mesafe açıklamaları eklemek basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek belgelerinizi değerli açıklamalarla zenginleştirebilir, daha iyi iş birliği ve iletişim sağlayabilirsiniz.

## SSS

### S: Mesafe açıklamasının görünümünü özelleştirebilir miyim?

C: Evet, ihtiyaçlarınıza uyacak şekilde renk, opaklık, çizgi stili vb. gibi çeşitli özellikleri özelleştirebilirsiniz.

### S: GroupDocs.Annotation farklı türdeki belgelere ek açıklama eklemeyi destekliyor mu?

C: Evet, GroupDocs.Annotation PDF, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerine ek açıklama eklemeyi destekler.

### S: GroupDocs.Annotation için ücretsiz deneme sürümü mevcut mu?

A: Evet, GroupDocs.Annotation'ın ücretsiz deneme sürümüne şu adresten erişebilirsiniz: [bu bağlantı](https://releases.groupdocs.com/).

### S: GroupDocs.Annotation for .NET belgelerini nerede bulabilirim?

A: Mevcut ayrıntılı belgelere başvurabilirsiniz [Burada](https://tutorials.groupdocs.com/annotation/net/).

### S: GroupDocs.Annotation ile ilgili destek veya yardımı nasıl alabilirim?

A: GroupDocs.Annotation topluluk forumundan destek ve yardım alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).