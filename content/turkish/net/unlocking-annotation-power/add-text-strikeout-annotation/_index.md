---
"description": "GroupDocs.Annotation for .NET kullanarak belgelere metin üstü çizili ek açıklamaların nasıl ekleneceğini öğrenin. İş birliğini ve belge inceleme süreçlerini verimli bir şekilde geliştirin."
"linktitle": "Belgeye Metin Üstü Çizili Açıklama Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Metin Üstü Çizili Açıklama Ekle"
"url": "/tr/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Belgeye Metin Üstü Çizili Açıklama Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye metin üstü çizili açıklama eklemeyi inceleyeceğiz. Bu kitaplık, çeşitli belge türlerine açıklama eklemek, iş birliğini ve belge inceleme süreçlerini geliştirmek için güçlü araçlar sağlar.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET: Kütüphaneyi yükleyin. Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET geliştirme için uygun bir geliştirme ortamı kurun.
3. Belge: PDF dosyası gibi not ekleyebileceğiniz bir belgeyi hazır bulundurun.

## Ad Alanlarını İçe Aktarma
Öncelikle GroupDocs'un işlevlerine erişmek için gerekli ad alanlarını içe aktarın.Açıklama:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Şimdi, bir metnin üstünü çizili olarak ekleme işlemini birden fazla adıma bölelim:
## Adım 1: Çıktı Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## Adım 2: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Giriş belgesine (bu durumda PDF dosyası) giden yolu sağlayarak Annotator nesnesini başlatın.
## Adım 3: Üstü Çizili Açıklama Oluşturun
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
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
    }
};
```
Mesaj, opaklık, sayfa numarası, arka plan rengi, noktalar (koordinatlar) ve yanıtlar gibi istediğiniz özelliklere sahip bir StrikeoutAnnotation nesnesi oluşturun.
## Adım 4: Açıklama Ekle
```csharp
annotator.Add(strikeout);
```
Oluşturulan üstü çizili açıklamayı belgeye ekleyin.
## Adım 5: Belgeyi Kaydedin
```csharp
annotator.Save(outputPath);
```
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye metin üstü çizili açıklama eklemeyi öğrendik. Bu güçlü kitaplık, verimli belge açıklaması sağlayarak iş birliğini ve belge inceleme süreçlerini geliştirir.
## SSS
### GroupDocs.Annotation çeşitli belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation PDF, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### Açıklamaların görünümünü özelleştirebilir miyim?
Elbette, renk, opaklık, yazı tipi boyutu gibi açıklama özelliklerini ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Annotation işbirliği özellikleri sunuyor mu?
Evet, GroupDocs.Annotation kullanıcıların belgelere yorum, yanıt ve açıklama eklemesine olanak tanıyarak iş birliğini kolaylaştırır.
### Ücretsiz deneme imkanı var mı?
Evet, ücretsiz denemeden faydalanabilirsiniz [Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için desteği nereden alabilirim?
Destek alabilirsiniz [GroupDocs.Açıklama forumu](https://forum.groupdocs.com/c/annotation/10).