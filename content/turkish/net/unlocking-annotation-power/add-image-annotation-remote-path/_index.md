---
title: Belgeye Görüntü Açıklaması Ekleme (Uzak Yol)
linktitle: Belgeye Görüntü Açıklaması Ekleme (Uzak Yol)
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere resim açıklamalarını nasıl ekleyeceğinizi öğrenin. Güçlü açıklama özellikleriyle belge yönetimini geliştirin.
weight: 15
url: /tr/net/unlocking-annotation-power/add-image-annotation-remote-path/
---

# Belgeye Görüntü Açıklaması Ekleme (Uzak Yol)

## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye görüntü açıklamaları ekleme sürecini anlatacağız. Bu kitaplık, çeşitli belge türlerine programlı olarak açıklama eklemek için güçlü araçlar sağlar.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Annotation for .NET: Kitaplığı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET geliştirme için ayarlanmış, çalışan bir geliştirme ortamına sahip olduğunuzdan emin olun.
3.  Belge: Açıklama eklemek istediğiniz belgeyi hazırlayın. Bu eğitim için, adında bir PDF belgeniz olduğunu varsayacağız.`input.pdf`.
4. Ek Açıklama İçin Resim: Ek açıklama için kullanmak istediğiniz resmi seçin. Resim URL'sinin veya yerel yolun hazır olduğundan emin olun.

## Ad Alanlarını İçe Aktar
Kodlamaya başlamadan önce gerekli ad alanlarını içe aktaralım:
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
## 2. Adım: Annotator'ı Başlatın
 Bir örneğini oluşturun`Annotator` sınıf ve giriş belgesini belirtin.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```
## 3. Adım: Resim Açıklaması Ekleyin
Şimdi belgeye resim açıklamasını ekleyelim. Görüntü ek açıklamasının konum, opaklık, sayfa numarası ve görüntü yolu gibi özelliklerini belirleyeceğiz.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Ek açıklamanın konumunu belirtin
    CreatedOn = DateTime.Now, // Oluşturma tarihini ayarlayın
    Opacity = 0.7, // Opaklığı ayarla (0 - 1)
    PageNumber = 0, // Sayfa numarasını belirtin
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Resmin URL'sini sağlayın
};
annotator.Add(image); // Resim açıklamasını ekleyin
```
## Adım 4: Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 5: Çıkış Yolunu Görüntüleyin
Kullanıcıyı başarılı belge kaydetme işlemi hakkında bilgilendirin ve çıktı yolunu görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye görüntü açıklamalarının nasıl ekleneceğini öğrendik. Bu adımları izleyerek belge yönetimi uygulamalarınızı güçlü açıklama özellikleriyle geliştirebilirsiniz.
## SSS'ler
### GroupDocs.Annotation, PDF'nin yanı sıra diğer belge formatlarıyla da kullanılabilir mi?
Evet, GroupDocs.Annotation, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### GroupDocs.Annotation .NET Core ile uyumlu mu?
Evet, GroupDocs.Annotation hem .NET Framework hem de .NET Core ile uyumludur.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Evet, renk, opaklık ve boyut gibi ek açıklamaların görünümünü özelleştirebilirsiniz.
### GroupDocs.Annotation ortak açıklama ekleme özelliklerini destekliyor mu?
Evet, GroupDocs.Annotation, belgeler üzerinde gerçek zamanlı işbirliği için ortak açıklama ekleme özellikleri sunar.
### Test için mevcut bir deneme sürümü var mı?
 Evet, GroupDocs.Annotation'ın ücretsiz deneme sürümünü şu adresten edinebilirsiniz:[Burada](https://releases.groupdocs.com/).