---
title: Belgeye Metin Redaksiyon Açıklaması Ekleme
linktitle: Belgeye Metin Redaksiyon Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak PDF belgelerine metin redaksiyon açıklamalarını nasıl ekleyeceğinizi öğrenin. Hassas bilgileri zahmetsizce koruyun.
weight: 23
url: /tr/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## giriiş
Bir belgeye metin redaksiyonu açıklaması eklemek, hassas bilgilerin güvenli bir şekilde yönetilmesinde çok önemli bir adım olabilir. GroupDocs.Annotation for .NET, bunu sorunsuz bir şekilde başarmak için güçlü bir çözüm sağlar. Bu öğreticide, belgenize metin redaksiyonu ek açıklaması ekleme sürecinde size adım adım rehberlik edeceğiz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET kitaplığını yüklediğinizden emin olun. adresinden indirebilirsiniz.[İnternet sitesi](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio gibi .NET uyumlu bir IDE ile bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktarma
Öncelikle gerekli namespace’leri projemize aktaralım:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Tanımlayın
Açıklamalı belgeyi kaydetmek istediğiniz çıkış yolunu tanımlayın. Erişilebilir ve yazılabilir olduğundan emin olun.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
 Açıklayıcıyı giriş belgesi yolu ile başlatın. Yer değiştirmek`"input.pdf"` belgenizin yolu ile birlikte.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```
## 3. Adım: Metin Redaksiyonu Ek Açıklaması Oluşturun
 Oluşturmak`TextRedactionAnnotation`gibi gerekli özelliklere sahip nesne`PageNumber`, `FontColor` , Ve`Points`. Ek açıklamayı gereksinimlerinize göre özelleştirin.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## 4. Adım: Ek Açıklama Ekle ve Kaydet
Ek açıklamayı kullanarak oluşturulan açıklamayı belgeye ekleyin ve açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Adım 5: Çıktıyı Kontrol Edin
Son olarak belgenin belirtilen çıktı yoluna başarıyla kaydedildiğini onaylayın.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET kullanarak bir belgeye metin redaksiyonu ek açıklaması ekleme sürecini anlattık. Bu adımlarla artık belgelerinizdeki hassas bilgileri güvenli bir şekilde yönetebilirsiniz.
## SSS'ler
### Metin redaksiyon ek açıklamasının görünümünü özelleştirebilir miyim?
Evet, yazı tipi rengi, dolgu rengi ve opaklık gibi çeşitli özellikleri gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.
### Satın almadan önce deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümüne şuradan erişebilirsiniz:[İnternet sitesi](https://releases.groupdocs.com/).
### Herhangi bir sorunla karşılaşırsam nasıl destek alabilirim?
 GroupDocs.Annotation topluluk forumundan destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amacıyla geçici bir lisansa ihtiyacım var mı?
 Evet, geçici lisansı şu adresten alabilirsiniz:[satın alma sayfası](https://purchase.groupdocs.com/temporary-license/)test için.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Kesinlikle GroupDocs.Annotation, tek bir belgeye çeşitli türde ek açıklamalar ve birden çok örnek eklemenize olanak tanır.