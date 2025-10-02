---
"description": "Groupdocs.Annotation for .NET kullanarak PDF belgelerini zahmetsizce nasıl döndüreceğinizi öğrenin. Belge yönetimi verimliliğini artırın."
"linktitle": "PDF Belgelerini Döndürme"
"second_title": "GroupDocs.Annotation .NET API"
"title": "PDF Belgelerini Döndürme"
"url": "/tr/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# PDF Belgelerini Döndürme

## giriiş
PDF belgelerini döndürmek, farklı şekilde görüntülenmesi veya işlenmesi gereken dosyalarla uğraşırken önemli bir görev olabilir. Bu eğitimde, .NET için Groupdocs.Annotation kullanarak PDF belgelerinin adım adım nasıl döndürüleceğini inceleyeceğiz.
## Ön koşullar
Eğitime başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:
1. Groupdocs.Annotation for .NET Kütüphanesi: Groupdocs.Annotation for .NET kütüphanesini indirip kurduğunuzdan emin olun. Buradan indirebilirsiniz [Burada](https://releases.groupdocs.com/annotation/net/).
2. C# Programlamanın Temel Bilgileri: Bu eğitim, C# programlama dili hakkında temel bir anlayışa sahip olduğunuzu ve .NET kütüphaneleriyle nasıl çalışacağınızı bildiğinizi varsayar.

## Ad Alanlarını İçe Aktar
Öncelikle Groupdocs.Annotation kütüphanesinin sağladığı işlevselliğe erişebilmek için gerekli ad alanlarını C# projenize aktarmanız gerekiyor.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Adım 1: PDF Belgesini Yükleyin
Döndürmek istediğiniz PDF belgesini yükleyerek başlayın `Annotator` sınıf.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Adım 2: Döndürmeyi Ayarlayın ve Sayfaları İşleyin
Döndürmek istediğiniz dönüş açısını ve sayfaları belirtin. Bu örnekte, ilk sayfayı saat yönünde 90 derece döndüreceğiz.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Adım 3: Döndürülmüş Belgeyi Kaydedin
Döndürülmüş PDF belgesini belirtilen değişikliklerle kaydedin.
```csharp
annotator.Save("result.pdf");
```
## Adım 4: Onay Ekranı
Kullanıcıya belgenin başarıyla döndürüldüğünü bildirin.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Çözüm
PDF belgelerini döndürmek temel bir işlemdir ve Groupdocs.Annotation for .NET ile basit ve etkili hale gelir. Bu eğitimde özetlenen adımları izleyerek PDF dosyalarını gereksinimlerinize göre kolayca döndürebilirsiniz.
## SSS
### Groupdocs.Annotation for .NET kullanarak bir PDF belgesindeki birden fazla sayfayı döndürebilir miyim?
Evet, döndürmek için birden fazla sayfa belirleyebilirsiniz. `ProcessPages` mülkiyet buna göre.
### Groupdocs.Annotation for .NET, .NET framework'ün tüm sürümleriyle uyumlu mudur?
Groupdocs.Annotation for .NET, .NET framework sürümlerinin geniş bir yelpazesini destekleyerek çoğu geliştirme ortamıyla uyumluluğu garanti altına alır.
### Groupdocs.Annotation for .NET, PDF belgelerini farklı yönlere döndürmek için seçenekler sunuyor mu?
Evet, ihtiyaçlarınıza göre PDF belgelerini saat yönünde, saat yönünün tersine veya özel açılarda döndürebilirsiniz.
### Groupdocs.Annotation for .NET'i mevcut belge yönetim sistemime entegre edebilir miyim?
Kesinlikle, Groupdocs.Annotation for .NET kusursuz entegrasyon seçenekleri sunarak belge yönetimi yeteneklerinizi zahmetsizce geliştirmenize olanak tanır.
### Groupdocs.Annotation for .NET için deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümünü şu adresten alabilirsiniz: [Burada](https://releases.groupdocs.com/).