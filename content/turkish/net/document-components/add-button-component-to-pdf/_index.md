---
"description": "Groupdocs.Annotation for .NET kullanarak PDF belgelerinizi etkileşimli düğme bileşenleriyle geliştirin. Sorunsuz entegrasyon için adım adım eğitimimizi izleyin."
"linktitle": "PDF Belgesine Düğme Bileşeni Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "PDF Belgesine Düğme Bileşeni Ekle"
"url": "/tr/net/document-components/add-button-component-to-pdf/"
type: docs
"weight": 10
---

# PDF Belgesine Düğme Bileşeni Ekle

## giriiş
Bu eğitimde, .NET için Groupdocs.Annotation kullanarak bir PDF belgesine Button Component ekleme sürecinde size rehberlik edeceğiz. Bu adım adım kılavuz, bu özelliği projenize kolayca entegre edebilmenizi sağlayacaktır.
## Ön koşullar
Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:
1. Groupdocs.Annotation for .NET: Groupdocs.Annotation for .NET kütüphanesini yüklediğinizden emin olun. Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET Framework'ün yüklü olduğu uygun bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktar
Devam etmeden önce gerekli ad alanlarını projenize aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Başlatın
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Düğme Bileşeni Ekle
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## Adım 3: Çıkış Yolunu Görüntüle
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Tebrikler! Groupdocs.Annotation for .NET kullanarak bir PDF belgesine Düğme Bileşeni'ni başarıyla eklediniz.

## Çözüm
Bu eğitimde, .NET için Groupdocs.Annotation kullanarak Düğme Bileşenlerini PDF belgelerine nasıl dahil edeceğinizi gösterdik. Bu adımları izleyerek, PDF belgelerinizi etkileşimli özelliklerle geliştirebilirsiniz.
## SSS
### Butonun görünümünü özelleştirebilir miyim?
Evet, düğme bileşeninin boyutu, rengi ve stili gibi çeşitli özelliklerini ihtiyaçlarınıza göre özelleştirebilirsiniz.
### Groupdocs.Annotation for .NET tüm PDF sürümleriyle uyumlu mudur?
Groupdocs.Annotation for .NET, çok çeşitli PDF sürümlerini destekleyerek çoğu belgeyle uyumluluğu garanti eder.
### Tek bir PDF belgesine birden fazla düğme bileşeni ekleyebilir miyim?
Kesinlikle, Groupdocs.Annotation for .NET kullanarak bir PDF belgesine ihtiyacınız olduğu kadar çok düğme bileşeni ekleyebilirsiniz.
### Groupdocs.Annotation for .NET diğer dosya formatlarını destekliyor mu?
Evet, PDF'ye ek olarak, Groupdocs.Annotation for .NET DOCX, PPTX ve XLSX dahil olmak üzere çeşitli diğer belge biçimlerini de destekler.
### Test amaçlı deneme sürümü mevcut mu?
Evet, Groupdocs.Annotation for .NET'in ücretsiz deneme sürümüne şu adresten erişebilirsiniz: [Burada](https://releases.groupdocs.com/).