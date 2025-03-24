---
title: PDF Belgesine Onay Kutusu Bileşeni Ekleme
linktitle: PDF Belgesine Onay Kutusu Bileşeni Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: Groupdocs.Annotation for .NET'i kullanarak PDF belgelerine Onay Kutusu Bileşenini nasıl ekleyeceğinizi öğrenin. PDF'lerinizi etkileşimli öğelerle geliştirin.
weight: 11
url: /tr/net/document-components/add-checkbox-component-to-pdf/
---
## giriiş
Bu öğreticide, Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesine Onay Kutusu Bileşeni ekleme sürecinde size yol göstereceğiz.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  Groupdocs.Annotation for .NET SDK: Şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Bir .NET geliştirme ortamı kurduğunuzdan emin olun.

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
Şimdi örneği birden çok adıma ayıralım:
## Adım 1: Çıkış Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada değiştirilen PDF belgesinin kaydedileceği çıktı yolunu tanımlıyoruz.
## 2. Adım: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Başlat`Annotator` giriş PDF belge yolunu ileterek nesneyi.
## 3. Adım: Onay Kutusu Bileşeni Oluşturun
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
 Oluşturmak`CheckBoxComponent` nesne ve onun gibi özelliklerini özelleştirin`Checked`, `Box` boyutlar,`PenColor`, `Style`ve birkaç yanıt ekleyin.
## Adım 4: Onay Kutusu Bileşenini Ekle
```csharp
annotator.Add(checkBox);
```
Oluşturulan onay kutusu bileşenini PDF belgesine ekleyin.
## Adım 5: Belgeyi Kaydet
```csharp
annotator.Save("result.pdf");
```
Değiştirilen PDF belgesini onay kutusu bileşeniyle kaydedin.
## Adım 6: Çıkış Yolunu Görüntüleyin
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Değiştirilen PDF belgesinin kaydedildiği yolu görüntüleyin.

## Çözüm
Bu öğreticide, Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesine Onay Kutusu Bileşeninin nasıl ekleneceğini öğrendik. Bu bilgiyle PDF belgelerinizi etkileşimli öğelerle geliştirebilirsiniz.
## SSS'ler
### Onay kutusunun görünümünü özelleştirebilir miyim?
Evet, renk, stil ve boyut gibi çeşitli özellikleri ihtiyaçlarınıza göre özelleştirebilirsiniz.
### Groupdocs.Annotation for .NET ticari kullanıma uygun mu?
Evet, Groupdocs.Annotation for .NET işletmeler için ticari lisanslar sunmaktadır.
### Satın almadan önce Groupdocs.Annotation for .NET'i deneyebilir miyim?
 Evet, ücretsiz deneme sürümünden yararlanabilirsiniz.[Burada](https://releases.groupdocs.com/).
### .NET için Groupdocs.Annotation desteğini nerede bulabilirim?
 Destek ve kaynakları şu adreste bulabilirsiniz:[Grup belgeleri forumu](https://forum.groupdocs.com/c/annotation/10).
### Test amacıyla geçici bir lisansa ihtiyacım var mı?
 Test için geçici bir lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).