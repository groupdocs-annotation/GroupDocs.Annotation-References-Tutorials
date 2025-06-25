---
"description": "GroupDocs.Annotation for .NET kullanarak belgelere resim açıklamalarının nasıl ekleneceğini öğrenin. Belge işleme yeteneklerini kolaylıkla geliştirin."
"linktitle": "Belgeye Resim Açıklaması Ekle (Yerel Yol)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Resim Açıklaması Ekle (Yerel Yol)"
"url": "/tr/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Belgeye Resim Açıklaması Ekle (Yerel Yol)

## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belgelere programatik olarak çeşitli türde açıklamalar eklemesine olanak tanıyan güçlü bir kütüphanedir. Bu eğitimde, yerel bir yol kullanarak bir belgeye resim açıklamalarının nasıl ekleneceğini öğreneceğiz.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:
1. C# programlama dilinin temel bilgisi.
2. Sisteminizde Visual Studio yüklü.
3. Projenizde .NET kütüphanesi için GroupDocs.Annotation veya tutorialsd yüklü olmalıdır.
4. Bir giriş belgesi (örneğin PDF) ve açıklama için bir resim dosyası.
## Ad Alanlarını İçe Aktar
Öncelikle, gerekli ad alanlarını C# dosyanıza aktarmanız gerekir. Bu ad alanları, GroupDocs.Annotation ile çalışmak için gereken sınıflara ve yöntemlere erişim sağlar.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Adım 1: Çıktı Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Annotator'ı Başlatın
Giriş belgesine giden yolu sağlayarak açıklayıcıyı başlatın.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelir
}
```
## Adım 3: Görüntü Açıklaması Oluşturun
Bir örneğini oluşturun `ImageAnnotation` sınıfını belirleyin ve konum, opaklık, sayfa numarası ve resim yolu gibi özelliklerini belirtin.
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
## Adım 4: Açıklama Ekle
Oluşturulan resim açıklamasını kullanarak belgeye ekleyin `Add` açıklayıcının yöntemi.
```csharp
annotator.Add(image);
```
## Adım 5: Belgeyi Kaydedin
Açıklamalı belgeyi çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 6: Çıkış Yolunu Görüntüle
Belgenin başarıyla kaydedildiğini ve çıktı dosyasının konumunu belirten bir mesaj görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye resim açıklamalarının nasıl ekleneceğini öğrendik. Bu basit adımları izleyerek, güçlü açıklama özellikleriyle belge işleme yeteneklerinizi geliştirebilirsiniz.
## SSS
### PDF dışındaki belgelere not ekleyebilir miyim?
Evet, GroupDocs.Annotation Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation .NET Core ile uyumlu mudur?
Evet, GroupDocs.Annotation hem .NET Framework hem de .NET Core ile uyumludur.
### Açıklamaların görünümünü özelleştirebilir miyim?
Elbette, gereksinimlerinize göre açıklamaların görünümünü, boyutunu, rengini ve diğer özelliklerini özelleştirebilirsiniz.
### GroupDocs.Annotation işbirlikçi açıklama desteği sağlıyor mu?
Evet, GroupDocs.Annotation birden fazla kullanıcının aynı anda belgelere açıklama eklemesine olanak tanıyan işbirlikçi açıklama özellikleri sunar.
### Ek yardım veya desteği nereden bulabilirim?
Topluluktan yardım ve destek almak için GroupDocs.Annotation forumunu ziyaret edebilirsiniz.