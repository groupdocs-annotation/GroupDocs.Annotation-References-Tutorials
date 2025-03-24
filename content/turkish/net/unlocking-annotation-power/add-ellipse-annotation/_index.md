---
title: Belgeye Elips Açıklaması Ekle
linktitle: Belgeye Elips Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation'ı kullanarak .NET'teki belgelere elips ek açıklamalarının nasıl ekleneceğini öğrenin. İşbirliğini ve iletişimi zahmetsizce geliştirin.
weight: 13
url: /tr/net/unlocking-annotation-power/add-ellipse-annotation/
---

# Belgeye Elips Açıklaması Ekle

## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye nasıl elips ek açıklaması ekleyeceğinizi öğreneceksiniz. Bu adım adım kılavuz, süreç boyunca size yol gösterecek ve her adımı net bir şekilde anlamanızı sağlayacaktır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i indirip yüklediğinizden emin olun. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).
2. IDE (Entegre Geliştirme Ortamı): Kodu yazmak ve yürütmek için sisteminizde Visual Studio gibi bir IDE'nin kurulu olması gerekir.

## Ad Alanlarını İçe Aktar
Öncelikle gerekli ad alanlarını projenize aktarın:
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
## 2. Adım: Annotator'ı Başlatın
Giriş belgesi yolunu sağlayarak açıklayıcıyı başlatın:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. Adım: Elips Ek Açıklaması Oluşturun
 Bir örneğini oluşturun`EllipseAnnotation` sınıfını seçin ve özelliklerini ayarlayın:
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
## 4. Adım: Ek Açıklama Ekle
Elips açıklamasını belgeye ekleyin:
```csharp
annotator.Add(ellipse);
```
## Adım 5: Belgeyi Kaydet
Açıklamalı belgeyi çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```

## Çözüm
Tebrikler! GroupDocs.Annotation for .NET'i kullanarak bir belgeye başarıyla elips ek açıklaması eklediniz. Belge işbirliğini ve iletişimi geliştirmek için artık bu işlevselliği .NET uygulamalarınıza entegre edebilirsiniz.
## SSS'ler
### Elips açıklamasının görünümünü özelleştirebilir miyim?
Evet, arka plan rengi, kenarlık rengi, opaklık vb. çeşitli özellikleri ihtiyaçlarınıza göre özelleştirebilirsiniz.
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
GroupDocs.Annotation for .NET, PDF, DOCX, PPTX, XLSX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Evet, tek bir belgeye elipsler, dikdörtgenler, metin vb. dahil olmak üzere birden fazla açıklama ekleyebilirsiniz.
### Test amaçlı deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/) Özelliklerini değerlendirmek için.
### GroupDocs.Annotation for .NET için nereden teknik destek alabilirim?
 GroupDocs.Annotation topluluk forumundan teknik destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).