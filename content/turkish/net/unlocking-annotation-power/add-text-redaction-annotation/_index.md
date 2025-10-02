---
"description": "GroupDocs.Annotation for .NET kullanarak PDF belgelerine metin düzenleme ek açıklamalarının nasıl ekleneceğini öğrenin. Hassas bilgileri zahmetsizce koruyun."
"linktitle": "Belgeye Metin Düzenleme Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Metin Düzenleme Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Belgeye Metin Düzenleme Açıklaması Ekle

## giriiş
Bir belgeye metin redaksiyon açıklaması eklemek, hassas bilgileri güvenli bir şekilde yönetmede önemli bir adım olabilir. GroupDocs.Annotation for .NET bunu sorunsuz bir şekilde başarmak için sağlam bir çözüm sunar. Bu eğitimde, belgenize adım adım metin redaksiyon açıklaması ekleme sürecinde size rehberlik edeceğiz.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET kitaplığını yüklediğinizden emin olun. Bunu şu adresten indirebilirsiniz: [web sitesi](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio gibi .NET uyumlu bir IDE ile bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktarma
Öncelikle projemize gerekli namespace'leri import edelim:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıktı Yolunu Tanımlayın
Açıklamalı belgeyi kaydetmek istediğiniz çıktı yolunu tanımlayın. Erişilebilir ve yazılabilir olduğundan emin olun.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Annotator'ı Başlatın
Açıklayıcıyı giriş belgesi yoluyla başlatın. Değiştir `"input.pdf"` belgenizin yolunu belirtin.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Açıklama kodu buraya gelecek
}
```
## Adım 3: Metin Düzenleme Açıklaması Oluşturun
Bir tane oluştur `TextRedactionAnnotation` gerekli özelliklere sahip nesne örneğin `PageNumber`, `FontColor`, Ve `Points`. İhtiyaçlarınıza göre açıklamayı özelleştirin.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Adım 4: Açıklama Ekle ve Kaydet
Oluşturulan açıklamayı, açıklamayı yapan aracı kullanarak belgeye ekleyin ve açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Adım 5: Çıktıyı Kontrol Edin
Son olarak belgenin belirtilen çıktı yoluna başarıyla kaydedildiğini doğrulayın.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir belgeye metin düzenleme açıklaması ekleme sürecini ele aldık. Bu adımlarla artık belgelerinizdeki hassas bilgileri güvenli bir şekilde yönetebilirsiniz.
## SSS
### Metin düzenleme açıklamasının görünümünü özelleştirebilir miyim?
Evet, ihtiyaçlarınıza uyacak şekilde yazı tipi rengi, dolgu rengi ve opaklık gibi çeşitli özellikleri özelleştirebilirsiniz.
### Satın almadan önce deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümüne şuradan erişebilirsiniz: [web sitesi](https://releases.groupdocs.com/).
### Herhangi bir sorunla karşılaşırsam nasıl destek alabilirim?
GroupDocs.Annotation topluluk forumundan destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).
### Test amaçlı geçici lisansa ihtiyacım var mı?
Evet, geçici bir lisans alabilirsiniz. [satın alma sayfası](https://purchase.groupdocs.com/temporary-license/) test için.
### Tek bir belgeye birden fazla açıklama ekleyebilir miyim?
Kesinlikle, GroupDocs.Annotation tek bir belgeye çeşitli türde açıklamalar ve birden fazla örnek eklemenize olanak tanır.