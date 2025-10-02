---
"description": "Verimli belge yönetimi ve işbirliği için GroupDocs.Annotation'ı kullanarak .NET'te metin üzerine resim açıklamalarının nasıl ekleneceğini öğrenin."
"linktitle": "Metnin Üzerine Resim Açıklaması Yerleştirin"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Metnin Üzerine Resim Açıklaması Yerleştirin"
"url": "/tr/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Metnin Üzerine Resim Açıklaması Yerleştirin

## giriiş
.NET geliştirme dünyasında, GroupDocs.Annotation belgelere ek açıklamalar eklemek, işbirliğini ve belge yönetimini daha verimli hale getirmek için güçlü bir çözüm sunar. Yaygın bir gereksinim, .NET için GroupDocs.Annotation kullanılarak sorunsuz bir şekilde gerçekleştirilebilen metin üzerine resim ek açıklamaları koymaktır.
## Ön koşullar
GroupDocs.Annotation for .NET kullanarak metin üzerine resim açıklamaları ekleme sürecine dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET Kütüphanesi: Kütüphaneyi şu adresten indirin ve yükleyin: [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET IDE gibi uygun bir geliştirme ortamı kurun.
3. Belge ve Resim Dosyaları: Açıklama yapmak istediğiniz belge dosyasını (PDF, DOCX, vb.) ve resim dosyasını hazırlayın.
4. C# Temel Anlayışı: Bu eğitimde sunulan kod parçacıklarını uygulamak için C# programlama diline aşinalık gereklidir.

## Ad Alanlarını İçe Aktar
Açıklama sürecine geçmeden önce, C# projenize gerekli ad alanlarını aktardığınızdan emin olun:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Adım 1: Çıktı Yolunu Tanımlayın
Öncelikle açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayalım:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Adım 2: Annotator'ı Başlatın
Başlat `Annotator` Giriş belgesi yolunu sağlayarak nesne:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelecek
}
```
## Adım 3: Görüntü Açıklaması Oluşturun
Bir tane oluştur `ImageAnnotation` kutu boyutları, opaklık, sayfa numarası, resim yolu ve z-indeksi gibi istenen özelliklere sahip nesne:
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
## Adım 4: Açıklama Ekle
Belgeye resim açıklamasını şu şekilde ekleyin: `Add` yöntemi `Annotator` nesne:
```csharp
annotator.Add(image);
```
## Adım 5: Açıklamalı Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Göster
Açıklamalı belgenin yolunu içeren bir başarı mesajı görüntüleyin:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation kullanarak .NET uygulamalarında metin üzerine resim açıklamaları eklemek basit bir işlemdir. Bu eğitimde sağlanan adım adım kılavuzu izleyerek, belgeleri etkili bir şekilde açıklayabilir ve .NET projelerinizde işbirliği ve belge yönetimi yeteneklerini geliştirebilirsiniz.
## SSS
### PDF dışındaki belgelere de açıklama ekleyebilir miyim?
Evet, GroupDocs.Annotation DOCX, XLSX, PPTX gibi çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation için ücretsiz deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz: [Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için nasıl destek alabilirim?
GroupDocs.Annotation topluluk forumundan destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amaçlı geçici lisansa ihtiyacım var mı?
Evet, geçici bir lisans alabilirsiniz. [Burada](https://purchase.groupdocs.com/temporary-license/) test amaçlı.
### Açıklamaların görünümünü özelleştirebilir miyim?
Evet, GroupDocs.Annotation renk, opaklık, yazı tipi boyutu gibi açıklamaların görünümünü özelleştirmek için çeşitli seçenekler sunar.