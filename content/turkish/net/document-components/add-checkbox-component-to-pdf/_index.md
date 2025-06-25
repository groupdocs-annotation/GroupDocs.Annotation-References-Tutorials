---
"description": "Groupdocs.Annotation for .NET kullanarak PDF belgelerine Onay Kutusu Bileşeni eklemeyi öğrenin. PDF'lerinizi etkileşimli öğelerle geliştirin."
"linktitle": "PDF Belgesine Onay Kutusu Bileşeni Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "PDF Belgesine Onay Kutusu Bileşeni Ekle"
"url": "/tr/net/document-components/add-checkbox-component-to-pdf/"
"weight": 11
---

# PDF Belgesine Onay Kutusu Bileşeni Ekle

## giriiş
Bu eğitimde, .NET için Groupdocs.Annotation'ı kullanarak bir PDF belgesine Onay Kutusu Bileşeni ekleme sürecinde size rehberlik edeceğiz.
## Ön koşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. Groupdocs.Annotation for .NET SDK: Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET geliştirme ortamınızın kurulu olduğundan emin olun.

## Ad Alanlarını İçe Aktar
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Şimdi örneği birden fazla adıma bölelim:
## Adım 1: Çıktı Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada, değiştirilen PDF belgesinin kaydedileceği çıktı yolunu tanımlıyoruz.
## Adım 2: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Başlat `Annotator` Giriş PDF belge yolunu geçirerek nesne.
## Adım 3: Onay Kutusu Bileşeni Oluşturun
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
Bir tane oluştur `CheckBoxComponent` nesne ve özelliklerini özelleştirin `Checked`, `Box` boyutlar, `PenColor`, `Style`ve birkaç yanıt ekleyin.
## Adım 4: Onay Kutusu Bileşeni Ekle
```csharp
annotator.Add(checkBox);
```
Oluşturulan onay kutusu bileşenini PDF belgesine ekleyin.
## Adım 5: Belgeyi Kaydedin
```csharp
annotator.Save("result.pdf");
```
Değiştirilen PDF belgesini onay kutusu bileşeniyle kaydedin.
## Adım 6: Çıkış Yolunu Görüntüle
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Değiştirilen PDF belgesinin kaydedildiği yolu görüntüleyin.

## Çözüm
Bu eğitimde, .NET için Groupdocs.Annotation kullanarak bir PDF belgesine Onay Kutusu Bileşeni eklemeyi öğrendik. Bu bilgiyle, PDF belgelerinizi etkileşimli öğelerle zenginleştirebilirsiniz.
## SSS
### Onay kutusunun görünümünü özelleştirebilir miyim?
Evet, ihtiyaçlarınıza göre renk, stil ve boyut gibi çeşitli özellikleri özelleştirebilirsiniz.
### Groupdocs.Annotation for .NET ticari kullanıma uygun mudur?
Evet, Groupdocs.Annotation for .NET işletmelere yönelik ticari lisanslar sunmaktadır.
### Satın almadan önce Groupdocs.Annotation for .NET'i deneyebilir miyim?
Evet, ücretsiz denemeden faydalanabilirsiniz [Burada](https://releases.groupdocs.com/).
### Groupdocs.Annotation for .NET için desteği nerede bulabilirim?
Destek ve kaynakları şu adreste bulabilirsiniz: [Groupdocs forumu](https://forum.groupdocs.com/c/annotation/10).
### Test amaçlı geçici lisansa ihtiyacım var mı?
Test için geçici lisansı şuradan alabilirsiniz: [Burada](https://purchase.groupdocs.com/temporary-license/).