---
"description": "GroupDocs.Annotation for .NET'i kullanarak .NET belgelerinize metin değiştirme ek açıklamalarını zahmetsizce nasıl ekleyeceğinizi öğrenin. Belge düzenleme yeteneklerinizi geliştirin."
"linktitle": "Belgeye Metin Değiştirme Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Metin Değiştirme Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Belgeye Metin Değiştirme Açıklaması Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak belgelerinize bir Metin Değiştirme Açıklaması ekleme sürecinde size rehberlik edeceğiz. Bu güçlü kütüphane, geliştiricilerin çeşitli türdeki belgeleri programatik olarak düzenlemelerine ve açıklama eklemelerine olanak tanır. Bu eğitimin sonunda, metin değiştirme açıklamalarını .NET uygulamalarınıza sorunsuz bir şekilde entegre etmek için gereken bilgiyle donatılmış olacaksınız.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşulların yüklü olduğundan emin olun:
### 1. .NET Framework Yüklendi
Geliştirme makinenizde .NET Framework'ün yüklü olduğundan emin olun. Bunu Microsoft web sitesinden indirebilirsiniz.
### 2. .NET Kütüphanesi için GroupDocs.Annotation
GroupDocs.Annotation for .NET kitaplığını şu adresten indirin ve yükleyin: [web sitesi](https://releases.groupdocs.com/annotation/net/)Bu kütüphane, çeşitli belge formatlarındaki açıklamalarla çalışmak için gerekli araçları ve işlevleri sağlar.
### 3. Geliştirme Ortamı Kurulumu
.NET uygulamaları oluşturmak ve çalıştırmak için Visual Studio gibi tercih ettiğiniz geliştirme ortamını ayarlayın.

## Ad Alanlarını İçe Aktar
Kodlama kısmına dalmadan önce, .NET için GroupDocs.Annotation ile çalışmak için gereken gerekli ad alanlarını içe aktaralım:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Adım 1: Çıktı Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## Adım 2: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya yerleştirilecek
}
```
Kaynakların uygun şekilde bertaraf edilmesini sağlamak için, bir using bloğu içerisinde giriş belgesini ("input.pdf") belirterek Annotator nesnesini başlatırız.
## Adım 3: Yedek Açıklama Oluşturun
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    TextToReplace = "replaced text"
};
```
Burada, oluşturulma tarihi, yazı rengi, mesaj, opaklık, sayfa numarası, arka plan rengi, noktalar (koordinatlar), yanıtlar (yorumlar) ve değiştirilecek metin gibi çeşitli özelliklere sahip bir ReplacementAnnotation nesnesi oluşturuyoruz.
## Adım 4: Açıklama Ekle
```csharp
annotator.Add(replacement);
```
Oluşturulan yedek açıklamayı açıklamacıya ekliyoruz.
## Adım 5: Belgeyi Kaydedin
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.
## Adım 6: Başarı Mesajını Göster
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Belgenin başarıyla kaydedildiğini belirten bir başarı mesajı görüntülenir.

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak belgelere metin değiştirme ek açıklamaları ekleme sürecini ele aldık. Adım adım kılavuzu takip ederek ve ön koşulları anlayarak, bu işlevselliği .NET uygulamalarınıza kolayca entegre edebilirsiniz.
## SSS
### GroupDocs.Annotation for .NET kullanarak farklı formatlardaki belgelere ek açıklama ekleyebilir miyim?
Evet, GroupDocs.Annotation for .NET, PDF, DOCX, PPTX, XLSX gibi çeşitli belge biçimlerine açıklama eklemeyi destekler.
### GroupDocs.Annotation for .NET hem masaüstü hem de web uygulamaları için uygun mudur?
Evet, GroupDocs.Annotation for .NET hem masaüstü hem de web uygulamalarında kullanılabilir ve geliştiricilere esneklik sağlar.
### GroupDocs.Annotation for .NET kullanılarak eklenen açıklamaların görünümünü özelleştirebilir miyim?
Elbette, renk, opaklık, yazı tipi gibi özellikleri değiştirerek açıklamaların görünümünü özelleştirebilirsiniz.
### GroupDocs.Annotation for .NET işbirlikçi açıklama özelliklerini destekliyor mu?
Evet, GroupDocs.Annotation for .NET, birden fazla kullanıcının aynı anda belgelere açıklama eklemesine olanak tanıyan ortak açıklama özellikleri sunar.
### GroupDocs.Annotation for .NET için ücretsiz deneme sürümü mevcut mu?
Evet, GroupDocs.Annotation for .NET'in ücretsiz deneme sürümünden faydalanabilirsiniz. [web sitesi](https://releases.groupdocs.com/).