---
"description": "GroupDocs.Annotation'ı kullanarak .NET'te belgelere elips ek açıklamalarının nasıl ekleneceğini öğrenin. İş birliğini ve iletişimi zahmetsizce geliştirin."
"linktitle": "Belgeye Elips Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Elips Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# Belgeye Elips Açıklaması Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye elips ek açıklamasının nasıl ekleneceğini öğreneceksiniz. Bu adım adım kılavuz, her adımı net bir şekilde anlamanızı sağlayarak sizi süreçte yönlendirecektir.
## Ön koşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i indirip kurduğunuzdan emin olun. Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. IDE (Bütünleşik Geliştirme Ortamı): Kodu yazmak ve çalıştırmak için sisteminizde Visual Studio gibi bir IDE'nin yüklü olması gerekir.

## Ad Alanlarını İçe Aktar
Öncelikle projenize gerekli namespace'leri import edin:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Ayarlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayın:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Annotator'ı Başlatın
Giriş belgesi yolunu sağlayarak açıklayıcıyı başlatın:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Adım 3: Elips Açıklaması Oluşturun
Bir örneğini oluşturun `EllipseAnnotation` sınıfını oluştur ve özelliklerini ayarla:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## Adım 4: Açıklama Ekle
Belgeye elips açıklamasını ekleyin:
```csharp
annotator.Add(ellipse);
```
## Adım 5: Belgeyi Kaydedin
Açıklamalı belgeyi çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```

## Çözüm
Tebrikler! GroupDocs.Annotation for .NET kullanarak bir belgeye elips ek açıklamasını başarıyla eklediniz. Artık bu işlevselliği, belge iş birliğini ve iletişimini geliştirmek için .NET uygulamalarınıza entegre edebilirsiniz.
## SSS
### Elips açıklamasının görünümünü özelleştirebilir miyim?
Evet, ihtiyaçlarınıza göre arka plan rengi, kenarlık rengi, opaklık vb. gibi çeşitli özellikleri özelleştirebilirsiniz.
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mudur?
GroupDocs.Annotation for .NET, PDF, DOCX, PPTX, XLSX ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Evet, tek bir belgeye elips, dikdörtgen, metin vb. gibi birden fazla açıklama ekleyebilirsiniz.
### Test amaçlı deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz: [Burada](https://releases.groupdocs.com/) Özelliklerini değerlendirmek için.
### GroupDocs.Annotation for .NET için teknik desteği nereden alabilirim?
GroupDocs.Annotation topluluk forumundan teknik destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).