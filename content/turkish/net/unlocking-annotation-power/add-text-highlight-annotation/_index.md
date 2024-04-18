---
title: Belgeye Metin Vurgu Açıklaması Ekleme
linktitle: Belgeye Metin Vurgu Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere metin vurgulama ek açıklamalarını nasıl ekleyeceğinizi öğrenin. Bu kapsamlı ürünle işbirliğini ve üretkenliği artırın.
type: docs
weight: 22
url: /tr/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## giriiş
Belge yönetimi ve işbirliği alanında GroupDocs.Annotation for .NET, geliştiricilerin metin vurgulama ek açıklamalarını uygulamalarına sorunsuz bir şekilde entegre etmelerine olanak tanıyan güçlü bir çözüm olarak ortaya çıkıyor. Bu öğretici, GroupDocs.Annotation for .NET kullanarak belgelere metin vurgulama ek açıklamaları ekleme konusunda kapsamlı bir kılavuz görevi görür. Adım adım talimatlar ve ayrıntılı açıklamalar sayesinde bu güçlü kütüphanenin yeteneklerinden yararlanma konusunda yeterlilik kazanacaksınız.
## Önkoşullar
Metin vurgulama ek açıklamalarının uygulanmasına başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1. Ortam Kurulumu: .NET geliştirme için yapılandırılmış uygun bir geliştirme ortamına sahip olun.
2.  GroupDocs.Annotation for .NET kurulumu: Sağlanan kaynaktan GroupDocs.Annotation for .NET'i indirip yükleyin.[İndirme: {link](https://releases.groupdocs.com/annotation/net/).
3. C#'a aşinalık: C# programlama dilinin temel anlayışı.
4. Açıklama Eklenecek Belge: Açıklama eklemeyi düşündüğünüz bir belge (örneğin, PDF) hazırlayın.

## Ad Alanlarını İçe Aktar
Başlamak için, GroupDocs.Annotation for .NET işlevlerini kullanmak üzere C# kodunuza gerekli ad alanlarını içe aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Şimdi, metin vurgulama ek açıklamalarını ekleme sürecini birden çok adıma ayıralım:
## Adım 1: Çıkış Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu belirtin:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
 Bir örneğini oluşturun`Annotator` sınıf, belge dosya adını parametre olarak ileterek:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 3. Adım: Vurgu Ek Açıklaması Oluşturun
 Bir örnek oluştur`HighlightAnnotation` nesne ve özelliklerini yapılandırın:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## 4. Adım: Ek Açıklama Ekle
Oluşturulan vurgulama açıklamasını belgeye ekleyin:
```csharp
annotator.Add(highlight);
```
## Adım 5: Açıklamalı Belgeyi Kaydetme
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation for .NET, metin vurgulama ek açıklamalarını belgelere dahil etmek için kolaylaştırılmış bir yaklaşım sunar. Geliştiriciler, bu eğitimde özetlenen adımları izleyerek, uygulamalarında belge işbirliğini ve üretkenliği sorunsuz bir şekilde geliştirebilirler.
## SSS'ler
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
GroupDocs.Annotation for .NET, PDF, Word, Excel ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler. Tam liste için belgelere bakın.
### Ek açıklamalar belirli gereksinimlere göre özelleştirilebilir mi?
Evet, geliştiriciler ek açıklamaların özellikleri ve görünümü üzerinde tam kontrole sahiptir ve bu da farklı ihtiyaçları karşılayacak şekilde özelleştirme yapılmasına olanak tanır.
### GroupDocs.Annotation for .NET'in ücretsiz deneme sürümü var mı?
 Evet, sağlanan ücretsiz deneme sürümüne erişerek GroupDocs.Annotation for .NET'in özelliklerini keşfedebilirsiniz.[bağlantı](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET ile ilgili herhangi bir sorun veya sorgu için nasıl destek alabilirim?
 Destek ve yardım için GroupDocs.Annotation forumunu ziyaret edebilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET için hangi lisanslama seçenekleri mevcut?
 GroupDocs.Annotation for .NET, test amaçlı geçici lisanslar ve üretim ortamları için ticari lisanslar dahil olmak üzere çeşitli lisanslama seçenekleri sunar. Satın alma sayfasını ziyaret edin[Burada](https://purchase.groupdocs.com/buy) daha fazla ayrıntı için.