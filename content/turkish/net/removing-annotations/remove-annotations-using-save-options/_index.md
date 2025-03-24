---
title: .NET'te Kaydetme Seçeneklerini Kullanarak Ek Açıklamaları Kaldırma
linktitle: .NET'te Kaydetme Seçeneklerini Kullanarak Ek Açıklamaları Kaldırma
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation'ı kullanarak PDF'den ve .NET'teki diğer belgelerden ek açıklamaları nasıl kaldıracağınızı öğrenin. Kod örnekleri içeren adım adım kılavuz.
weight: 14
url: /tr/net/removing-annotations/remove-annotations-using-save-options/
---

# .NET'te Kaydetme Seçeneklerini Kullanarak Ek Açıklamaları Kaldırma

## giriiş

GroupDocs.Annotation for .NET, geliştiricilerin .NET uygulamalarına kolaylıkla açıklama ekleme işlevselliği eklemelerine olanak tanıyan güçlü bir araçtır. İster bir belge yönetim sistemi, işbirliği platformu veya belge işlemeyi içeren başka bir uygulama üzerinde çalışıyor olun, GroupDocs.Annotation, PDF ve diğer belge formatlarına sorunsuz bir şekilde açıklama eklemek için kapsamlı bir dizi özellik sunar.

## Önkoşullar

GroupDocs.Annotation for .NET'i kullanarak belgelere açıklama ekleme dünyasına dalmadan önce, aşağıdaki önkoşulların yerine getirildiğinden emin olun:

### 1. .NET için GroupDocs.Annotation'ı yükleyin

 GroupDocs.Annotation for .NET'i indirip yükleyerek başlayın. En son sürümü adresinden indirebilirsiniz.[download page](https://releases.groupdocs.com/annotation/net/).

## Ad Alanlarını İçe Aktarma

.NET projenizde GroupDocs.Annotation'ı kullanmaya başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Yaygın olarak kullanacağınız ad alanları şunlardır:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Şimdi, .NET'teki Kaydetme Seçenekleri özelliğini kullanarak bir belgeden ek açıklamaları kaldırma sürecini inceleyelim:

## Adım 1: Çıkış Yolunu Tanımlayın

İlk olarak, kaldırılan ek açıklamalara sahip belgenin kaydedileceği çıktı yolunu tanımlayın. Şunu kullanabilirsiniz:`Path.Combine` dizin yolunu çıktı dosyası adıyla birleştirme yöntemi.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. Adım: Annotator'ı Başlatın

 Daha sonra, bir örneğini başlatın`Annotator` Ek açıklamaları içeren belgenin yolunu sağlayarak sınıf.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Ek açıklama kaldırma kodu buraya gelecek
}
```

## 3. Adım: Ek Açıklama Kaldırma ile Belgeyi Kaydetme

 Şimdi, şunu kullan:`Save` yöntemi`Annotator` sınıfla birlikte`SaveOptions` Belgeyi kaldırılan ek açıklamalarla kaydetmek için. İçinde`SaveOptions` , yı kur`AnnotationTypes` mülkiyet`AnnotationType.None` Tüm ek açıklamaları kaldırmak için.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Adım 4: Başarı Mesajını Görüntüleyin

Son olarak, belgenin ek açıklamalar kaldırılarak başarıyla kaydedildiğini belirten bir başarı mesajı görüntüleyin.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

Sonuç olarak, GroupDocs.Annotation for .NET, belgelerden ek açıklamaların kaldırılması sürecini basitleştirir. Geliştiriciler, yukarıda özetlenen adım adım kılavuzu izleyerek ek açıklama kaldırma işlevini .NET uygulamalarına sorunsuz bir şekilde entegre edebilir.

## SSS'ler

### S: GroupDocs.Annotation, PDF'nin yanı sıra diğer belge formatlarındaki ek açıklamaları kaldırabilir mi?

C: GroupDocs.Annotation, PDF, Word, Excel ve PowerPoint dahil olmak üzere çeşitli belge formatlarını destekleyerek çok çeşitli belgelerden ek açıklamaları kaldırmanıza olanak tanır.

### S: GroupDocs.Annotation'ın mevcut .NET projelerine entegrasyonu kolay mıdır?

C: Evet, GroupDocs.Annotation basit bir API ve kapsamlı belgeler sunarak geliştiricilerin açıklama özelliklerini .NET uygulamalarına entegre etmelerini kolaylaştırır.

### S: GroupDocs.Annotation, ek açıklamaların seçici olarak kaldırılmasını destekliyor mu?

C: Evet, GroupDocs.Annotation, geliştiricilerin hangi türdeki ek açıklamaların kaldırılacağını belirtmesine olanak tanıyarak, onlara belgelerindeki ek açıklamaları yönetme konusunda esneklik sağlar.

### S: Satın almadan önce GroupDocs.Annotation'ı ücretsiz olarak deneyebilir miyim?

 C: Evet, GroupDocs.Annotation'ın ücretsiz deneme sürümünü şuradan indirebilirsiniz:[sürümler sayfası](https://releases.groupdocs.com/) Bir satın alma kararı vermeden önce özelliklerini keşfetmek için.

### S: GroupDocs.Annotation için nereden destek alabilirim?

 C: Teknik yardım ve topluluk desteği için şu adresi ziyaret edebilirsiniz:[GroupDocs.Annotation forumu](https://forum.groupdocs.com/c/annotation/10).