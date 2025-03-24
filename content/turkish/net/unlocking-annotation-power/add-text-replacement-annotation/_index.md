---
title: Belgeye Metin Değiştirme Açıklaması Ekle
linktitle: Belgeye Metin Değiştirme Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak .NET belgelerinize metin değiştirme ek açıklamalarını zahmetsizce nasıl ekleyeceğinizi öğrenin. Belge işleme yeteneklerinizi geliştirin.
weight: 24
url: /tr/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak belgelerinize Metin Değiştirme Ek Açıklaması ekleme sürecinde size rehberlik edeceğiz. Bu güçlü kitaplık, geliştiricilerin çeşitli belge türlerini programlı olarak değiştirmesine ve açıklama eklemesine olanak tanır. Bu eğitimin sonunda, metin değiştirme ek açıklamalarını .NET uygulamalarınıza sorunsuz bir şekilde entegre etme bilgisine sahip olacaksınız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların kurulu olduğundan emin olun:
### 1. .NET Framework Yüklü
Geliştirme makinenizde .NET Framework'ün kurulu olduğundan emin olun. Microsoft'un web sitesinden indirebilirsiniz.
### 2. .NET Kitaplığı için GroupDocs.Annotation
 GroupDocs.Annotation for .NET kitaplığını şuradan indirip yükleyin:[İnternet sitesi](https://releases.groupdocs.com/annotation/net/). Bu kitaplık, çeşitli belge formatlarındaki ek açıklamalarla çalışmak için gerekli araçları ve işlevleri sağlar.
### 3. Geliştirme Ortamı Kurulumu
.NET uygulamalarını oluşturmak ve çalıştırmak için Visual Studio gibi tercih ettiğiniz geliştirme ortamını kurun.

## Ad Alanlarını İçe Aktar
Kodlama kısmına dalmadan önce GroupDocs.Annotation for .NET ile çalışmak için gereken gerekli ad alanlarını içe aktaralım:
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
## Adım 1: Çıkış Yolunu Tanımlayın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Burada açıklamalı belgenin kaydedileceği çıktı yolunu tanımlıyoruz.
## 2. Adım: Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya yerleştirilecek
}
```
Kaynakların uygun şekilde atılmasını sağlamak için bir kullanım bloğu içinde giriş belgesini ("input.pdf") belirterek Annotator nesnesini başlatırız.
## 3. Adım: Değiştirme Ek Açıklaması Oluşturun
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
Burada oluşturulma tarihi, yazı tipi rengi, mesaj, opaklık, sayfa numarası, arka plan rengi, noktalar (koordinatlar), yanıtlar (yorumlar) ve değiştirilecek metin gibi çeşitli özelliklere sahip bir replacementAnnotation nesnesi oluşturuyoruz.
## 4. Adım: Ek Açıklama Ekle
```csharp
annotator.Add(replacement);
```
Oluşturulan değiştirme açıklamasını açıklayıcıya ekliyoruz.
## Adım 5: Belgeyi Kaydet
```csharp
annotator.Save(outputPath);
```
Son olarak açıklamalı belgeyi belirtilen çıktı yoluna kaydediyoruz.
## Adım 6: Başarı Mesajını Görüntüleyin
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Belgenin başarıyla kaydedildiğini belirten bir başarı mesajı görüntülenir.

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET kullanarak belgelere metin değiştirme ek açıklamaları ekleme sürecini ele aldık. Adım adım kılavuzu takip ederek ve önkoşulları anlayarak bu işlevselliği .NET uygulamalarınıza kolayca entegre edebilirsiniz.
## SSS'ler
### GroupDocs.Annotation for .NET'i kullanarak farklı formatlardaki belgelere açıklama ekleyebilir miyim?
Evet, GroupDocs.Annotation for .NET, PDF, DOCX, PPTX, XLSX ve daha fazlası gibi çeşitli belge formatlarına açıklama eklemeyi destekler.
### GroupDocs.Annotation for .NET hem masaüstü hem de web uygulamaları için uygun mu?
Evet, GroupDocs.Annotation for .NET hem masaüstü hem de web uygulamalarında kullanılabilir ve geliştiricilere esneklik sağlar.
### GroupDocs.Annotation for .NET kullanılarak eklenen ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle, renk, opaklık, yazı tipi vb. özellikleri değiştirerek açıklamaların görünümünü özelleştirebilirsiniz.
### GroupDocs.Annotation for .NET, işbirliğine dayalı açıklama özellikleri için destek sunuyor mu?
Evet, GroupDocs.Annotation for .NET, ortak açıklama eklemeye yönelik özellikler sağlayarak birden fazla kullanıcının aynı anda belgelere açıklama eklemesine olanak tanır.
### GroupDocs.Annotation for .NET'in ücretsiz deneme sürümü var mı?
Evet, GroupDocs.Annotation for .NET'in ücretsiz denemesinden şu adresten yararlanabilirsiniz:[İnternet sitesi](https://releases.groupdocs.com/).