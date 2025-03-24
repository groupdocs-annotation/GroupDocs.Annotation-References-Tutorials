---
title: Belgeye Üstü Çizili Metin Açıklaması Ekleme
linktitle: Belgeye Üstü Çizili Metin Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere üstü çizili metin açıklamalarını nasıl ekleyeceğinizi öğrenin. İşbirliği ve belge inceleme süreçlerini verimli bir şekilde geliştirin.
weight: 26
url: /tr/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Belgeye Üstü Çizili Metin Açıklaması Ekleme

## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye üstü çizili açıklama ekinin nasıl ekleneceğini inceleyeceğiz. Bu kitaplık, çeşitli belge türlerine açıklama eklemek, işbirliğini ve belge inceleme süreçlerini geliştirmek için güçlü araçlar sağlar.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  GroupDocs.Annotation for .NET: Kitaplığı yükleyin. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET geliştirme için uygun bir geliştirme ortamı oluşturun.
3. Belge: PDF dosyası gibi açıklama eklemeye hazır bir belgeniz olsun.

## Ad Alanlarını İçe Aktarma
Öncelikle GroupDocs.Annotation'un işlevlerine erişmek için gerekli ad alanlarını içe aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Şimdi, üstü çizili bir metin açıklaması ekleme sürecini birden çok adıma ayıralım:
## Adım 1: Çıkış Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## 2. Adım: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Giriş belgesinin (bu durumda PDF dosyası) yolunu sağlayarak Annotator nesnesini başlatın.
## 3. Adım: Üzerini Çizilen Ek Açıklama Oluşturun
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
Mesaj, opaklık, sayfa numarası, arka plan rengi, noktalar (koordinatlar) ve yanıtlar gibi istenen özelliklere sahip bir StrikeoutAnnotation nesnesi oluşturun.
## 4. Adım: Ek Açıklama Ekle
```csharp
annotator.Add(strikeout);
```
Oluşturulan üstü çizili açıklamayı belgeye ekleyin.
## Adım 5: Belgeyi Kaydet
```csharp
annotator.Save(outputPath);
```
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET kullanarak bir belgeye üstü çizili metin açıklamasının nasıl ekleneceğini öğrendik. Bu güçlü kitaplık, verimli belge açıklamasına olanak tanır, işbirliğini ve belge inceleme süreçlerini geliştirir.
## SSS'ler
### GroupDocs.Annotation çeşitli belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Annotation, PDF, Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle, renk, opaklık, yazı tipi boyutu ve daha fazlası gibi ek açıklama özelliklerini gereksinimlerinize göre özelleştirebilirsiniz.
### GroupDocs.Annotation işbirliği özellikleri sağlıyor mu?
Evet, GroupDocs.Annotation, kullanıcıların belgelere yorum, yanıt ve ek açıklamalar eklemesine olanak tanıyarak işbirliğini kolaylaştırır.
### Ücretsiz deneme mevcut mu?
 Evet, ücretsiz deneme sürümünden yararlanabilirsiniz.[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için nereden destek alabilirim?
 adresinden destek alabilirsiniz.[GroupDocs.Annotation forumu](https://forum.groupdocs.com/c/annotation/10).