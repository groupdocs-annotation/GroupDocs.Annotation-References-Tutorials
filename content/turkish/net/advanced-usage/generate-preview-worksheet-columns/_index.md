---
"description": "GroupDocs.Annotation for .NET kullanarak belgeleri nasıl ek açıklama ekleyeceğinizi öğrenin. .NET geliştiricileri için adım adım eğitim. Uygulamalarınızı geliştirin."
"linktitle": "Önizleme Çalışma Sayfası Sütunlarını Oluştur"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Önizleme Çalışma Sayfası Sütunlarını Oluştur"
"url": "/tr/net/advanced-usage/generate-preview-worksheet-columns/"
type: docs
"weight": 15
---

# Önizleme Çalışma Sayfası Sütunlarını Oluştur

## giriiş
GroupDocs.Annotation for .NET'in yeteneklerinden yararlanmaya yönelik kapsamlı eğitimimize hoş geldiniz! Bu kılavuzda, bu güçlü aracı belgeleri etkili bir şekilde ek açıklamalarla açıklama yapmak için kullanma sürecinde size yol göstereceğiz. İster deneyimli bir geliştirici olun, ister .NET geliştirme dünyasına yeni adım atmış olun, bu eğitim size ek açıklama özelliklerini uygulamalarınıza sorunsuz bir şekilde entegre etmek için gereken bilgi ve becerileri kazandıracaktır.
## Ön koşullar
Eğitime başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:
### 1. .NET Geliştirme Ortamı Kurulumu
Makinenizde çalışan bir .NET geliştirme ortamının kurulu olduğundan emin olun. .NET SDK'nın en son sürümünü Microsoft web sitesinden indirebilirsiniz.
### 2. .NET Kütüphanesi için GroupDocs.Annotation
Sağlanan GroupDocs.Annotation for .NET kitaplığını indirin ve yükleyin [indirme bağlantısı](https://releases.groupdocs.com/annotation/net/)Kütüphaneyi projenize başarılı bir şekilde entegre etmek için kurulum talimatlarını izleyin.
### 3. Giriş Belgesi
GroupDocs.Annotation for .NET kullanarak açıklama eklemeyi planladığınız bir örnek belge hazırlayın (örneğin, "input.xlsx"). Belgenin proje dizininizden erişilebilir olduğundan emin olun.

## Ad Alanlarını İçe Aktar
Başlamak için, gerekli ad alanlarını projenize aktarın. Bu ad alanları, belge açıklama görevlerini etkili bir şekilde gerçekleştirmek için gereken sınıflara ve yöntemlere erişim sağlar.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

Artık geliştirme ortamımızı kurduğumuza ve gerekli ad alanlarını içe aktardığımıza göre, belgemiz için önizleme çalışma sayfası sütunlarını oluşturmaya geçelim.
## Adım 1: Önizleme Seçeneklerini Başlatın
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
## Adım 3: Giriş Belgesi ile Annotator'ı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## Adım 4: Başarı Mesajını Göster
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Çözüm
Tebrikler! GroupDocs.Annotation for .NET kullanarak önizleme çalışma sayfası sütunlarını nasıl oluşturacağınızı başarıyla öğrendiniz. Bu bilgiyle artık gelişmiş açıklama yeteneklerini .NET uygulamalarınıza kolayca dahil edebilirsiniz.
## SSS
### GroupDocs.Annotation diğer .NET framework'leriyle uyumlu mudur?
Evet, GroupDocs.Annotation .NET Core ve .NET Framework dahil olmak üzere çeşitli .NET çerçevelerini destekler.
### GroupDocs.Annotation ile oluşturulan açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation, renk, opaklık ve açıklama türü de dahil olmak üzere açıklama görünümü için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Annotation Excel dışındaki belge biçimlerini destekliyor mu?
Evet, GroupDocs.Annotation PDF, Word, PowerPoint ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation kullanıcıları için teknik destek mevcut mu?
Evet, sağlanan teknik destek ve topluluk forumlarına erişebilirsiniz. [destek bağlantısı](https://forum.groupdocs.com/c/annotation/10).
### Lisans satın almadan önce GroupDocs.Annotation'ı deneyebilir miyim?
Elbette! GroupDocs.Annotation'ın ücretsiz deneme sürümünü şuradan indirebilirsiniz: [web sitesi](https://releases.groupdocs.com/).