---
title: Belgeye Dalgalı Metin Açıklaması Ekleme
linktitle: Belgeye Dalgalı Metin Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: Groupdocs.Annotation for .NET'i kullanarak belgelere zahmetsizce dalgalı metin açıklamaları eklemeyi öğrenin. İşbirliği ve belge inceleme süreçlerini geliştirin.
weight: 25
url: /tr/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# Belgeye Dalgalı Metin Açıklaması Ekleme

## giriiş

Groupdocs.Annotation for .NET, geliştiricilerin güçlü açıklama özelliklerini .NET uygulamalarına zahmetsizce entegre etmelerine olanak tanıyan çok yönlü bir kitaplıktır. İster PDF'lerle, ister Word belgeleriyle, ister diğer popüler dosya formatlarıyla çalışıyor olun, Groupdocs.Annotation, belgeye açıklama eklemek ve belge işbirliğini geliştirmek için kusursuz bir çözüm sunar.

## Önkoşullar

Eğiticiye dalmadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:

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

Artık önkoşulları ele aldığımıza göre, dalgalı metin açıklamaları ekleme sürecini birden çok adıma ayıralım.

## Adım 1: Çıkış Yolunu Tanımlayın

Açıklamalı belgenin kaydedileceği yolu tanımlayın.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. Adım: Annotator'ı Başlatın

Giriş belgesi yolunu sağlayarak Annotator nesnesini başlatın.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```

## 3. Adım: Dalgalı Ek Açıklama Oluşturun

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

## 4. Adım: Ek Açıklama Ekle

Oluşturulan dalgalı açıklamayı belgeye ekleyin.

```csharp
annotator.Add(squiggly);
```

## Adım 5: Belgeyi Kaydet

Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.

```csharp
annotator.Save(outputPath);
```

## Adım 6: Onayı Görüntüle

Açıklamalı belgenin başarıyla kaydedildiğini onaylayan bir mesaj görüntüler.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

Sonuç olarak Groupdocs.Annotation for .NET, geliştiricilere belge açıklama işlevlerini .NET uygulamalarına sorunsuz bir şekilde entegre etmeleri için güçlü bir araç seti sağlar. Bu adım adım kılavuzu izleyerek belgelerinize zahmetsizce metin açıklamaları ekleyebilir, işbirliği ve belge inceleme süreçlerini geliştirebilirsiniz.

## SSS'ler

### S: Groupdocs.Annotation çeşitli dosya formatlarında açıklama eklemeyi destekleyebilir mi?

C: Evet, Groupdocs.Annotation, PDF'ler, Word belgeleri, Excel sayfaları ve daha fazlası dahil olmak üzere çok çeşitli dosya formatlarında açıklama eklemeyi destekler.

### S: Groupdocs.Annotation hem masaüstü hem de web uygulamalarıyla uyumlu mudur?

C: Kesinlikle! Groupdocs.Annotation, esneklik ve çok yönlülük sunarak hem masaüstü hem de web uygulamalarına sorunsuz bir şekilde entegre edilebilir.

### S: Groupdocs.Annotation için herhangi bir lisanslama seçeneği mevcut mu?

C: Evet, Groupdocs.Annotation, deneme amaçlı geçici lisanslar da dahil olmak üzere bireysel veya kurumsal ihtiyaçlara uyacak şekilde uyarlanmış esnek lisanslama seçenekleri sunar.

### S: Groupdocs.Annotation kullanılarak oluşturulan ek açıklamalar özelleştirilebilir mi?

C: Kesinlikle! Groupdocs.Annotation, ek açıklamalar için kapsamlı özelleştirme seçenekleri sunarak geliştiricilerin ek açıklamaları kendi özel gereksinimlerine göre uyarlamasına olanak tanır.

### S: Groupdocs.Annotation geliştiriciler için destek ve dokümantasyon sunuyor mu?

C: Gerçekten! Groupdocs.Annotation, geliştiricilerin özelliklerini etkili bir şekilde kullanmalarına yardımcı olmak için kapsamlı belgeler ve özel destek forumları sağlar.