---
title: Belgeye Bağlantı Açıklaması Ekle
linktitle: Belgeye Bağlantı Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: Groupdocs.Annotation for .NET'i kullanarak belgelere bağlantı açıklamalarını nasıl ekleyeceğinizi öğrenin. İşbirliğini ve etkileşimi zahmetsizce geliştirin.
weight: 16
url: /tr/net/unlocking-annotation-power/add-link-annotation/
---

# Belgeye Bağlantı Açıklaması Ekle

## giriiş
Groupdocs.Annotation for .NET, geliştiricilerin kapsamlı açıklama işlevlerini .NET uygulamalarına zahmetsizce entegre etmelerini sağlayan güçlü bir kitaplıktır. Sunduğu temel özelliklerden biri, belgelere bağlantı açıklamaları ekleyerek işbirliğini ve etkileşimi geliştirme yeteneğidir.
## Önkoşullar
Bağlantı ek açıklamaları ekleme sürecine dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
- C# programlama dilinin temel anlayışı.
- .NET kitaplığı için Groupdocs.Annotation yüklendi.
- Açıklama eklemek istediğiniz bir belgeye erişim.

## Ad Alanlarını İçe Aktar
Öncelikle Groupdocs.Annotation for .NET işlevlerini kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Bu, uygulamanızın belgelere açıklama eklemek için gereken sınıflara ve yöntemlere erişmesine olanak tanır.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Ayarlayın
Açıklamalı belgeyi kaydetmek istediğiniz yolu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
 Bir örneğini oluşturun`Annotator` açıklama eklemek istediğiniz belgenin yolunu sağlayarak sınıf.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```
## 3. Adım: Bağlantı Açıklaması Oluşturun
 Bir tanımla`LinkAnnotation` nesneyi seçin ve mesaj, opaklık, sayfa numarası, arka plan rengi, noktalar, yanıtlar ve URL gibi özelliklerini belirtin.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    },
    Url = "https://www.google.com"
};
```
## 4. Adım: Ek Açıklama Ekle
 Oluşturulan bağlantı açıklamasını kullanarak belgeye ekleyin.`Add` ek açıklama örneğinin yöntemi.
```csharp
annotator.Add(link);
```
## Adım 5: Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Görüntüleyin
Açıklamalı belgenin başarıyla kaydedildiği konusunda kullanıcıyı bilgilendirin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, yukarıdaki adımları izleyerek Groupdocs.Annotation for .NET'i kullanarak belgelere sorunsuz bir şekilde bağlantı açıklamaları ekleyebilirsiniz. Bu, belge işbirliğini geliştirir ve kullanıcılara etkileşimli özellikler sağlar.
## SSS'ler
### Groupdocs.Annotation for .NET tüm belge türleriyle uyumlu mudur?
Groupdocs.Annotation for .NET, PDF, Word, Excel ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Evet, ek açıklamaların renk, opaklık ve boyut gibi çeşitli özelliklerini gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.
### Groupdocs.Annotation for .NET gerçek zamanlı işbirliği özellikleri sunuyor mu?
Evet, Groupdocs.Annotation for .NET, birden fazla kullanıcının aynı anda belgelere açıklama eklemesine olanak tanıyan gerçek zamanlı işbirliği özellikleri sağlar.
### Groupdocs ürünleri için teknik destek mevcut mu?
 Evet, Groupdocs ürünleri için teknik desteğe forum ve destek aracılığıyla ulaşılabilir[Burada](https://forum.groupdocs.com/c/annotation/10).
### Satın almadan önce Groupdocs.Annotation for .NET'i deneyebilir miyim?
Evet, satın alma işlemi yapmadan önce özelliklerini keşfetmek için Groupdocs.Annotation for .NET'in ücretsiz denemesinden yararlanabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).