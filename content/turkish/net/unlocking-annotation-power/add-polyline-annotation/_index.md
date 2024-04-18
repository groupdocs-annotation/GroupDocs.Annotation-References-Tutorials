---
title: Belgeye Çoklu Çizgi Açıklaması Ekleme
linktitle: Belgeye Çoklu Çizgi Açıklaması Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere sürekli çizgi açıklamalarını nasıl ekleyeceğinizi öğrenin. İşbirliğini ve belge inceleme süreçlerini zahmetsizce geliştirin.
type: docs
weight: 18
url: /tr/net/unlocking-annotation-power/add-polyline-annotation/
---
## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin PDF ve Microsoft Office belgelerine program aracılığıyla açıklama eklemesine olanak tanıyan güçlü bir araçtır. Özellikleri arasında, belgelere çoklu çizgi açıklamaları ekleme, işbirliğini ve belge inceleme süreçlerini geliştirme yeteneği yer almaktadır.
## Önkoşullar
Bu eğitime devam etmeden önce aşağıdakilere sahip olduğunuzdan emin olun:
- Sisteminizde Visual Studio yüklü.
- Temel C# programlama dili bilgisi.
-  GroupDocs.Annotation for .NET kitaplığı yüklendi. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).

## Ad Alanlarını İçe Aktar
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Tanımlayın
Öncelikle açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
Giriş belgesi adını sağlayarak açıklayıcıyı başlatın.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Adım 3: Çoklu Çizgi Açıklama Nesnesi Oluşturun
Bir çoklu çizgi açıklama nesnesi oluşturun ve konum, mesaj, opaklık, kalem rengi, kalem stili ve kalem genişliği gibi özelliklerini ayarlayın.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Adım 4: Çoklu Çizgi Açıklaması Ekleme
Ek açıklama nesnesini kullanarak sürekli çizgi açıklamasını belgeye ekleyin.
```csharp
annotator.Add(polyline);
```
## Adım 5: Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Görüntüleyin
Belgenin başarıyla kaydedildiğini onaylayan bir mesaj görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak bir belgeye sürekli çizgi ek açıklamasının nasıl ekleneceğini öğrendik. Bu özellik, işbirliği ve belge inceleme süreçlerini geliştirerek kullanıcıların geri bildirimlerini ve önerilerini etkili bir şekilde iletmesini kolaylaştırır.
## SSS'ler
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
GroupDocs.Annotation for .NET, PDF gibi popüler belge formatlarını ve Word, Excel ve PowerPoint dahil Microsoft Office formatlarını destekler.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Evet, ek açıklamaların renk, opaklık, stil ve genişlik gibi çeşitli özelliklerini gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.
### GroupDocs.Annotation for .NET ücretsiz deneme olanağı sunuyor mu?
 Evet, GroupDocs.Annotation for .NET'in ücretsiz deneme sürümünden şu adresi ziyaret ederek yararlanabilirsiniz:[bu bağlantı](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET belgelerini nerede bulabilirim?
 GroupDocs.Annotation for .NET belgelerini bulabilirsiniz.[Burada](https://reference.groupdocs.com/annotation/net/).
### GroupDocs.Annotation for .NET ile ilgili herhangi bir sorun veya sorgu için nasıl destek alabilirim?
 GroupDocs.Annotation forumunu ziyaret ederek destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).