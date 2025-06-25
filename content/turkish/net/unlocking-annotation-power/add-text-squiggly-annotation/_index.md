---
"description": "Groupdocs.Annotation for .NET'i kullanarak belgelere kıvrımlı metin açıklamalarını zahmetsizce nasıl ekleyeceğinizi öğrenin. İş birliğini ve belge inceleme süreçlerini geliştirin."
"linktitle": "Belgeye Metin Dalgalı Açıklama Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Metin Dalgalı Açıklama Ekle"
"url": "/tr/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Belgeye Metin Dalgalı Açıklama Ekle

## giriiş

Groupdocs.Annotation for .NET, geliştiricilerin .NET uygulamalarına zahmetsizce güçlü açıklama yeteneklerini entegre etmelerini sağlayan çok yönlü bir kütüphanedir. İster PDF'lerle, ister Word belgeleriyle veya diğer popüler dosya biçimleriyle çalışın, Groupdocs.Annotation belge iş birliğini açıklama ve geliştirme için kusursuz bir çözüm sunar.

## Ön koşullar

Eğitime başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

## Ad Alanlarını İçe Aktar

Groupdocs.Annotation for .NET tarafından sağlanan işlevlere erişmek için gerekli ad alanlarını içe aktardığınızdan emin olun.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Artık ön koşulları tamamladığımıza göre, metne kıvrımlı açıklamalar ekleme sürecini birden fazla adıma bölelim.

## Adım 1: Çıktı Yolunu Tanımlayın

Açıklamalı belgenin kaydedileceği yolu tanımlayın.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Adım 2: Annotator'ı Başlatın

Giriş belgesi yolunu sağlayarak Annotator nesnesini başlatın.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelir
}
```

## Adım 3: Dalgalı Açıklama Oluşturun

Bir SquigglyAnnotation nesnesi oluşturun ve özelliklerini belirtin.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## Adım 4: Açıklama Ekle

Oluşturulan kıvrımlı açıklamayı belgeye ekleyin.

```csharp
annotator.Add(squiggly);
```

## Adım 5: Belgeyi Kaydedin

Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.

```csharp
annotator.Save(outputPath);
```

## Adım 6: Onay Ekranı

Açıklamalı belgenin başarıyla kaydedildiğini onaylayan bir mesaj görüntüle.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

Sonuç olarak, Groupdocs.Annotation for .NET, geliştiricilere belge açıklama işlevlerini .NET uygulamalarına sorunsuz bir şekilde entegre etmeleri için sağlam bir araç seti sağlar. Bu adım adım kılavuzu izleyerek, belgelerinize zahmetsizce kıvrımlı metin açıklamaları ekleyebilir, iş birliğini ve belge inceleme süreçlerini geliştirebilirsiniz.

## SSS

### S: Groupdocs.Annotation çeşitli dosya biçimlerine açıklama eklemeyi destekleyebilir mi?

C: Evet, Groupdocs.Annotation PDF'ler, Word belgeleri, Excel sayfaları ve daha fazlası dahil olmak üzere çok çeşitli dosya biçimlerine açıklama eklemeyi destekler.

### S: Groupdocs.Annotation masaüstü ve web uygulamalarıyla uyumlu mu?

C: Kesinlikle! Groupdocs.Annotation, hem masaüstü hem de web uygulamalarına sorunsuz bir şekilde entegre edilebilir, esneklik ve çok yönlülük sunar.

### S: Groupdocs.Annotation için herhangi bir lisanslama seçeneği mevcut mu?

C: Evet, Groupdocs.Annotation, deneme amaçlı geçici lisanslar da dahil olmak üzere, bireysel veya kurumsal ihtiyaçlara göre uyarlanmış esnek lisanslama seçenekleri sunar.

### S: Groupdocs.Annotation kullanılarak oluşturulan açıklamalar özelleştirilebilir mi?

A: Elbette! Groupdocs.Annotation, geliştiricilerin açıklamaları kendi özel gereksinimlerine göre uyarlamalarına olanak tanıyan açıklamalar için kapsamlı özelleştirme seçenekleri sunar.

### S: Groupdocs.Annotation geliştiricilere destek ve dokümantasyon sunuyor mu?

A: Kesinlikle! Groupdocs.Annotation, geliştiricilerin özelliklerini etkili bir şekilde kullanmalarına yardımcı olmak için kapsamlı belgeler ve özel destek forumları sağlar.