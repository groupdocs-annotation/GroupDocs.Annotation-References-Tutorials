---
title: Metnin Üzerine Resim Açıklamasını Yerleştirin
linktitle: Metnin Üzerine Resim Açıklamasını Yerleştirin
second_title: GroupDocs.Annotation .NET API'si
description: Verimli belge yönetimi ve işbirliği için GroupDocs.Annotation'ı kullanarak .NET'te metnin üzerine resim açıklamalarını nasıl ekleyeceğinizi öğrenin.
weight: 21
url: /tr/net/advanced-usage/put-image-annotation-over-text/
---

# Metnin Üzerine Resim Açıklamasını Yerleştirin

## giriiş
.NET geliştirme dünyasında GroupDocs.Annotation, belgelere açıklamalar eklemek, işbirliğini ve belge yönetimini daha verimli hale getirmek için güçlü bir çözüm sunar. Yaygın gereksinimlerden biri, GroupDocs.Annotation for .NET kullanılarak sorunsuz bir şekilde gerçekleştirilebilen metin üzerine resim açıklamaları koymaktır.
## Önkoşullar
GroupDocs.Annotation for .NET'i kullanarak metnin üzerine resim açıklamaları yerleştirme sürecine dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Annotation for .NET Library: Kitaplığı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio veya başka herhangi bir .NET IDE gibi uygun bir geliştirme ortamı kurun.
3. Belge ve Resim Dosyaları: Ek açıklamalar için kullanmak istediğiniz belge dosyasını (PDF, DOCX vb.) ve resim dosyasını hazırlayın.
4. Temel C# Anlayışı: Bu eğitimde sağlanan kod parçacıklarını uygulamak için C# programlama diline aşinalık gereklidir.

## Ad Alanlarını İçe Aktar
Ek açıklama işlemine devam etmeden önce C# projenize gerekli ad alanlarını içe aktardığınızdan emin olun:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Adım 1: Çıkış Yolunu Tanımlayın
İlk olarak, açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayın:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 2. Adım: Annotator'ı Başlatın
 Başlat`Annotator` giriş belgesi yolunu sağlayarak nesne:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```
## 3. Adım: Resim Açıklaması Oluşturun
 Oluşturduğunuz bir`ImageAnnotation` kutu boyutları, opaklık, sayfa numarası, görüntü yolu ve z-endeksi gibi istenen özelliklere sahip nesne:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## 4. Adım: Ek Açıklama Ekle
 kullanarak görüntü açıklamasını belgeye ekleyin.`Add` yöntemi`Annotator` nesne:
```csharp
annotator.Add(image);
```
## Adım 5: Açıklamalı Belgeyi Kaydetme
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Görüntüleyin
Açıklamalı belgenin yolunu içeren bir başarı mesajı görüntüleyin:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation'ı kullanarak .NET uygulamalarında metnin üzerine resim açıklamaları eklemek basit bir işlemdir. Bu öğreticide sağlanan adım adım kılavuzu izleyerek, .NET projelerinizde belgelere verimli bir şekilde açıklama ekleyebilir ve işbirliği ve belge yönetimi yeteneklerini geliştirebilirsiniz.
## SSS'ler
### PDF dışındaki belgelere açıklama ekleyebilir miyim?
Evet, GroupDocs.Annotation, DOCX, XLSX, PPTX ve daha fazlası gibi çeşitli belge formatlarını destekler.
### GroupDocs.Annotation'ın ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için nasıl destek alabilirim?
 GroupDocs.Annotation topluluk forumundan destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amacıyla geçici bir lisansa ihtiyacım var mı?
 Evet, adresinden geçici lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/) test amaçlı.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Evet, GroupDocs.Annotation, ek açıklamaların görünümünü özelleştirmek için renk, opaklık, yazı tipi boyutu vb. gibi çeşitli seçenekler sunar.