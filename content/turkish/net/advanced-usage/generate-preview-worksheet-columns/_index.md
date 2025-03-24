---
title: Önizleme Çalışma Sayfası Sütunları Oluştur
linktitle: Önizleme Çalışma Sayfası Sütunları Oluştur
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelere nasıl açıklama ekleyeceğinizi öğrenin. .NET geliştiricileri için adım adım eğitim. Uygulamalarınızı geliştirin.
weight: 15
url: /tr/net/advanced-usage/generate-preview-worksheet-columns/
---
## giriiş
GroupDocs.Annotation for .NET'in yeteneklerinden yararlanmaya ilişkin kapsamlı eğitimimize hoş geldiniz! Bu kılavuzda, belgelere etkili bir şekilde açıklama eklemek için bu güçlü aracı kullanma sürecinde size yol göstereceğiz. İster deneyimli bir geliştirici olun ister .NET geliştirme dünyasına yeni giren biri olun, bu eğitim sizi ek açıklama özelliklerini uygulamalarınıza sorunsuz bir şekilde entegre etmek için gerekli bilgi ve becerilerle donatacaktır.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
### 1. .NET Geliştirme Ortamı Kurulumu
Makinenizde çalışan bir .NET geliştirme ortamının kurulu olduğundan emin olun. .NET SDK'nın en son sürümünü Microsoft web sitesinden indirebilirsiniz.
### 2. .NET Kitaplığı için GroupDocs.Annotation
 Sağlanan kaynaktan GroupDocs.Annotation for .NET kitaplığını indirip yükleyin.[İndirme: {link](https://releases.groupdocs.com/annotation/net/). Kütüphaneyi projenize başarıyla entegre etmek için kurulum talimatlarını izleyin.
### 3. Giriş Belgesi
GroupDocs.Annotation for .NET'i kullanarak açıklama eklemeyi planladığınız örnek bir belge (örneğin, "input.xlsx") hazırlayın. Belgeye proje dizininizden erişilebildiğinden emin olun.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını projenize aktarın. Bu ad alanları, belge açıklama görevlerini etkin bir şekilde gerçekleştirmek için gereken sınıflara ve yöntemlere erişim sağlar.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

Artık geliştirme ortamımızı kurduğumuza ve gerekli ad alanlarını içe aktardığımıza göre, belgemiz için önizleme çalışma sayfası sütunları oluşturmaya geçelim.
## 1. Adım: Önizleme Seçeneklerini Başlatın
```csharp
PreviewOptions previewOptions = new PreviewOptions(
    pageNumber => new FileStream(Path.Combine("Your Document Directory", $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose()
);
```
## Adım 2: Çalışma Sayfası Sütunlarını Tanımlayın
```csharp
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));
```
## 3. Adım: Giriş Belgesiyle Açıklayıcıyı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## Adım 4: Başarı Mesajını Görüntüleyin
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Çözüm
Tebrikler! GroupDocs.Annotation for .NET'i kullanarak önizleme çalışma sayfası sütunlarının nasıl oluşturulacağını başarıyla öğrendiniz. Bu bilgiyle artık gelişmiş açıklama özelliklerini .NET uygulamalarınıza kolaylıkla dahil edebilirsiniz.
## SSS'ler
### GroupDocs.Annotation diğer .NET çerçeveleriyle uyumlu mu?
Evet, GroupDocs.Annotation, .NET Core ve .NET Framework dahil olmak üzere çeşitli .NET çerçevelerini destekler.
### GroupDocs.Annotation ile oluşturulan ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation, renk, opaklık ve açıklama türü de dahil olmak üzere açıklama görünümü için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Annotation, Excel dışındaki belge formatlarını destekliyor mu?
Evet, GroupDocs.Annotation, PDF, Word, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Annotation kullanıcıları için teknik destek mevcut mu?
 Evet, sağlanan teknik destek ve topluluk forumlarına erişebilirsiniz.[destek bağlantısı](https://forum.groupdocs.com/c/annotation/10).
### Lisans satın almadan önce GroupDocs.Annotation'ı deneyebilir miyim?
 Elbette! GroupDocs.Annotation'ın ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[İnternet sitesi](https://releases.groupdocs.com/).