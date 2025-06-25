---
"description": "GroupDocs.Annotation for .NET kullanarak belgelere resim açıklamalarının nasıl ekleneceğini öğrenin. Güçlü açıklama yetenekleriyle belge yönetimini geliştirin."
"linktitle": "Belgeye Resim Açıklaması Ekle (Uzak Yol)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Resim Açıklaması Ekle (Uzak Yol)"
"url": "/tr/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Belgeye Resim Açıklaması Ekle (Uzak Yol)

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye resim açıklamaları ekleme sürecini ele alacağız. Bu kitaplık, çeşitli türdeki belgeleri programatik olarak açıklama eklemek için güçlü araçlar sağlar.
## Ön koşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET: Kütüphaneyi şu adresten indirin ve yükleyin: [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET geliştirme için çalışan bir geliştirme ortamı kurduğunuzdan emin olun.
3. Belge: Açıklama yapmak istediğiniz belgeyi hazırlayın. Bu eğitim için, adında bir PDF belgeniz olduğunu varsayacağız. `input.pdf`.
4. Açıklama için Resim: Açıklama için kullanmak istediğiniz resmi seçin. Resim URL'sinin veya yerel yolunun hazır olduğundan emin olun.

## Ad Alanlarını İçe Aktar
Kodlamaya başlamadan önce gerekli namespace'leri import edelim:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Adım 1: Çıkış Yolunu Ayarlayın
Öncelikle açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Annotator'ı Başlatın
Bir örneğini oluşturun `Annotator` sınıfını seçin ve giriş belgesini belirtin.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelecek
}
```
## Adım 3: Görüntü Açıklaması Ekle
Şimdi, belgeye resim açıklamasını ekleyelim. Resim açıklamasının konum, opaklık, sayfa numarası ve resim yolu gibi özelliklerini belirteceğiz.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Açıklamanın konumunu belirtin
    CreatedOn = DateTime.Now, // Oluşturulma tarihini ayarlayın
    Opacity = 0.7, // Opaklığı ayarla (0 ila 1)
    PageNumber = 0, // Sayfa numarasını belirtin
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Resmin URL'sini sağlayın
};
annotator.Add(image); // Resim açıklamasını ekle
```
## Adım 4: Belgeyi Kaydedin
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 5: Çıkış Yolunu Görüntüle
Kullanıcıya belge kaydetme işleminin başarılı olduğunu bildir ve çıktı yolunu görüntüle.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye resim açıklamalarının nasıl ekleneceğini öğrendik. Bu adımları izleyerek, belge yönetimi uygulamalarınızı güçlü açıklama yetenekleriyle geliştirebilirsiniz.
## SSS
### GroupDocs.Annotation PDF haricindeki diğer belge formatlarıyla da kullanılabilir mi?
Evet, GroupDocs.Annotation Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation .NET Core ile uyumlu mudur?
Evet, GroupDocs.Annotation hem .NET Framework hem de .NET Core ile uyumludur.
### Açıklamaların görünümünü özelleştirebilir miyim?
Evet, renk, opaklık ve boyut gibi açıklamaların görünümünü özelleştirebilirsiniz.
### GroupDocs.Annotation işbirlikçi açıklama özelliklerini destekliyor mu?
Evet, GroupDocs.Annotation belgeler üzerinde gerçek zamanlı işbirliği için işbirlikçi açıklama özellikleri sunar.
### Test için deneme sürümü mevcut mu?
Evet, GroupDocs.Annotation'ın ücretsiz deneme sürümünü şu adresten edinebilirsiniz: [Burada](https://releases.groupdocs.com/).