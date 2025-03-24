---
title: PDF Belgelerini Döndürme
linktitle: PDF Belgelerini Döndürme
second_title: GroupDocs.Annotation .NET API'si
description: Groupdocs.Annotation for .NET'i kullanarak PDF belgelerini zahmetsizce nasıl döndüreceğinizi öğrenin. Belge yönetimi verimliliğini artırın.
weight: 22
url: /tr/net/advanced-usage/rotating-pdf-documents/
---
## giriiş
Farklı şekilde görüntülenmesi veya işlenmesi gereken dosyalarla uğraşırken PDF belgelerini döndürmek çok önemli bir görev olabilir. Bu öğreticide, Groupdocs.Annotation for .NET'i kullanarak PDF belgelerinin adım adım nasıl döndürüleceğini keşfedeceğiz.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  Groupdocs.Annotation for .NET Library: Groupdocs.Annotation for .NET kitaplığını indirip yüklediğinizden emin olun. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).
2. Temel C# Programlama Bilgisi: Bu eğitimde, C# programlama dili ve .NET kitaplıklarıyla nasıl çalışılacağı konusunda temel bilgiye sahip olduğunuz varsayılmaktadır.

## Ad Alanlarını İçe Aktar
Groupdocs.Annotation kitaplığı tarafından sağlanan işlevselliğe erişmek için öncelikle gerekli ad alanlarını C# projenize aktarmanız gerekir.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 1. Adım: PDF Belgesini Yükleyin
 Döndürmek istediğiniz PDF belgesini kullanarak yükleyin.`Annotator` sınıf.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Adım 2: Rotasyon ve İşlem Sayfalarını Ayarlayın
Döndürme açısını ve döndürmek istediğiniz sayfaları belirtin. Bu örnekte ilk sayfayı saat yönünde 90 derece döndüreceğiz.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## 3. Adım: Döndürülmüş Belgeyi Kaydetme
Döndürülmüş PDF belgesini belirtilen değişikliklerle kaydedin.
```csharp
annotator.Save("result.pdf");
```
## Adım 4: Onayı Görüntüle
Kullanıcıya belgenin başarıyla döndürüldüğünü bildirin.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Çözüm
PDF belgelerini döndürmek temel bir işlemdir ve Groupdocs.Annotation for .NET ile bu işlem basit ve verimli hale gelir. Bu eğitimde özetlenen adımları izleyerek PDF dosyalarını gereksinimlerinize göre kolayca döndürebilirsiniz.
## SSS'ler
### Groupdocs.Annotation for .NET'i kullanarak bir PDF belgesindeki birden fazla sayfayı döndürebilir miyim?
 Evet, döndürmek için birden fazla sayfa belirleyebilirsiniz.`ProcessPages` buna göre mülk.
### Groupdocs.Annotation for .NET, .NET framework'ün tüm sürümleriyle uyumlu mu?
Groupdocs.Annotation for .NET, çok çeşitli .NET framework sürümlerini destekleyerek çoğu geliştirme ortamıyla uyumluluk sağlar.
### Groupdocs.Annotation for .NET, PDF belgelerini farklı yönlere döndürme seçenekleri sunuyor mu?
Evet, PDF belgelerini gereksinimlerinize göre saat yönünde, saat yönünün tersine veya özel açılarda döndürebilirsiniz.
### Groupdocs.Annotation for .NET'i mevcut belge yönetim sistemime entegre edebilir miyim?
Kesinlikle, Groupdocs.Annotation for .NET kusursuz entegrasyon seçenekleri sunarak belge yönetimi yeteneklerini zahmetsizce geliştirmenize olanak tanır.
### Groupdocs.Annotation for .NET'in deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şuradan edinebilirsiniz:[Burada](https://releases.groupdocs.com/).