---
title: Belgeye Görüntü Açıklaması Ekleme (Yerel Yol)
linktitle: Belgeye Görüntü Açıklaması Ekleme (Yerel Yol)
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere resim açıklamalarını nasıl ekleyeceğinizi öğrenin. Belge işleme yeteneklerini kolaylıkla geliştirin.
weight: 14
url: /tr/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# Belgeye Görüntü Açıklaması Ekleme (Yerel Yol)

## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belgelere programlı olarak çeşitli türde ek açıklamalar eklemesine olanak tanıyan güçlü bir kitaplıktır. Bu eğitimde, yerel bir yol kullanarak bir belgeye resim açıklamalarının nasıl ekleneceğini öğreneceğiz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Temel C# programlama dili bilgisi.
2. Sisteminizde Visual Studio yüklü.
3. Projenizde yüklü veya başvurulan .NET kitaplığı için GroupDocs.Annotation.
4. Bir giriş belgesi (örneğin, PDF) ve açıklama için bir görüntü dosyası.
## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını C# dosyanıza aktarmanız gerekir. Bu ad alanları, GroupDocs.Annotation ile çalışmak için gereken sınıflara ve yöntemlere erişim sağlar.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Adım 1: Çıkış Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıkış yolunu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
Giriş belgesinin yolunu sağlayarak açıklayıcıyı başlatın.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ek açıklama kodu buraya gelecek
}
```
## 3. Adım: Resim Açıklaması Oluşturun
 Bir örneğini oluşturun`ImageAnnotation`sınıfını seçin ve konum, opaklık, sayfa numarası ve görüntü yolu gibi özelliklerini belirtin.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## 4. Adım: Ek Açıklama Ekle
 Oluşturulan görüntü açıklamasını belgeye şunu kullanarak ekleyin:`Add` açıklamacının yöntemi.
```csharp
annotator.Add(image);
```
## Adım 5: Belgeyi Kaydet
Açıklamalı belgeyi çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 6: Çıkış Yolunu Görüntüleyin
Belgenin başarıyla kaydedildiğini ve çıktı dosyasının konumunu belirten bir mesaj görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET kullanarak bir belgeye görüntü açıklamalarının nasıl ekleneceğini öğrendik. Bu basit adımları izleyerek, güçlü açıklama özellikleriyle belge işleme yeteneklerinizi geliştirebilirsiniz.
## SSS'ler
### PDF dışındaki belgelere açıklama ekleyebilir miyim?
Evet, GroupDocs.Annotation, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.
### GroupDocs.Annotation .NET Core ile uyumlu mu?
Evet, GroupDocs.Annotation hem .NET Framework hem de .NET Core ile uyumludur.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Ek açıklamaların görünümünü, boyutunu, rengini ve diğer özelliklerini kesinlikle ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Annotation işbirliğine dayalı açıklama ekleme desteği sağlıyor mu?
Evet, GroupDocs.Annotation, birden fazla kullanıcının aynı anda belgelere açıklama eklemesine olanak tanıyan ortak açıklama ekleme özellikleri sunar.
### Nerede ek yardım veya destek bulabilirim?
Topluluktan yardım ve destek almak için GroupDocs.Annotation forumunu ziyaret edebilirsiniz.