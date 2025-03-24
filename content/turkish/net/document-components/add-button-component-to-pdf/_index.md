---
title: PDF Belgesine Düğme Bileşeni Ekleme
linktitle: PDF Belgesine Düğme Bileşeni Ekleme
second_title: GroupDocs.Annotation .NET API'si
description: Groupdocs.Annotation for .NET'i kullanarak PDF belgelerinizi etkileşimli düğme bileşenleriyle geliştirin. Sorunsuz entegrasyon için adım adım eğitimimizi izleyin.
weight: 10
url: /tr/net/document-components/add-button-component-to-pdf/
---
## giriiş
Bu öğreticide, Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesine Düğme Bileşeni ekleme sürecinde size rehberlik edeceğiz. Bu adım adım kılavuz, bu özelliği projenize kolayca entegre edebilmenizi sağlayacaktır.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1.  Groupdocs.Annotation for .NET: Groupdocs.Annotation for .NET kitaplığını yüklediğinizden emin olun. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: .NET çerçevesinin kurulu olduğu uygun bir geliştirme ortamına sahip olun.

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
## Adım 2: Düğme Bileşeni Ekleme
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
## Adım 3: Çıkış Yolunu Görüntüleyin
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Tebrikler! Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesine başarıyla bir Düğme Bileşeni eklediniz.

## Çözüm
Bu öğreticide, Groupdocs.Annotation for .NET kullanarak Düğme Bileşenlerinin PDF belgelerine nasıl dahil edileceğini gösterdik. Bu adımları izleyerek PDF belgelerinizi etkileşimli özelliklerle geliştirebilirsiniz.
## SSS'ler
### Düğmenin görünümünü özelleştirebilir miyim?
Evet, düğme bileşeninin boyutu, rengi ve stili gibi çeşitli özelliklerini gereksinimlerinize göre özelleştirebilirsiniz.
### Groupdocs.Annotation for .NET tüm PDF sürümleriyle uyumlu mu?
Groupdocs.Annotation for .NET, çok çeşitli PDF sürümlerini destekleyerek çoğu belgeyle uyumluluk sağlar.
### Tek bir PDF belgesine birden fazla düğme bileşeni ekleyebilir miyim?
Kesinlikle, Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesine gerektiği kadar düğme bileşeni ekleyebilirsiniz.
### Groupdocs.Annotation for .NET diğer dosya formatları için destek sunuyor mu?
Evet, Groupdocs.Annotation for .NET, PDF'ye ek olarak DOCX, PPTX ve XLSX dahil diğer çeşitli belge formatlarını da destekler.
### Test amaçlı deneme sürümü mevcut mu?
 Evet, Groupdocs.Annotation for .NET'in ücretsiz deneme sürümüne şu adresten erişebilirsiniz:[Burada](https://releases.groupdocs.com/).