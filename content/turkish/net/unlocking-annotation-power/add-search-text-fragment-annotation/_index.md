---
title: Belgeye Arama Metni Parçası Ek Açıklaması Ekle
linktitle: Belgeye Arama Metni Parçası Ek Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'in gücünü keşfedin ve uygulamalarınıza zahmetsizce belge açıklaması özellikleri ekleyin.
weight: 20
url: /tr/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Belgeye Arama Metni Parçası Ek Açıklaması Ekle

## giriiş
.NET geliştirme alanında GroupDocs.Annotation, belgelere sorunsuz bir şekilde açıklama eklemek için güçlü bir araç olarak öne çıkıyor. İster deneyimli bir geliştirici olun ister .NET dünyasına adım atın, bu kapsamlı eğitim size GroupDocs.Annotation for .NET'i kullanmanın temelleri konusunda, ad alanlarını içe aktarmaktan, arama metninize arama metni parçası ek açıklamaları eklemenin inceliklerini öğrenmeye kadar yol gösterecektir. belgeler.
## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belge açıklama özelliklerini uygulamalarına zahmetsizce dahil etmelerine olanak tanır. Sezgisel API'si ve sağlam özellikleri sayesinde geliştiriciler, PDF'ler, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çeşitli belge formatlarına açıklama ekleyebilir.
## Önkoşullar
GroupDocs.Annotation for .NET'e dalmadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:

## Ad Alanlarını İçe Aktar
Öncelikle, .NET projenizdeki GroupDocs.Annotation sınıflarına ve yöntemlerine erişmek için gerekli ad alanlarını içe aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıkış Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayarak başlayın:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. Adım: Annotator'ı Başlatın
 Daha sonra, bir örneğini başlatın`Annotator` açıklama eklemek istediğiniz belgenin yolunu sağlayarak sınıf:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. Adım: Arama Metni Parçası Ek Açıklamasını Oluşturun
 Oluşturmak`SearchTextFragment` Aranacak metin, yazı tipi boyutu, yazı tipi ailesi, yazı tipi rengi ve arka plan rengi gibi istenen özelliklere sahip nesne:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## 4. Adım: Ek Açıklama Ekle
 Oluşturulan arama metni parçası ek açıklamasını kullanarak belgeye ekleyin.`Add` açıklayıcının yöntemi:
```csharp
annotator.Add(searchText);
```
## Adım 5: Açıklamalı Belgeyi Kaydetme
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Görüntüleyin
Kullanıcıya belgenin başarıyla kaydedildiğini bildirin:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation for .NET, belgelere ek açıklamalar ekleme sürecini basitleştirir, işbirliğini ve belge inceleme süreçlerini geliştirir. Bu kılavuzda özetlenen adımları izleyerek belge açıklama özelliklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.
## SSS'ler
### GroupDocs.Annotation tüm belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Annotation, PDF'ler, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çok çeşitli belge formatlarını destekler.
### Ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation, ek açıklamalar için kapsamlı özelleştirme seçenekleri sunarak yazı tipi boyutu, renk ve stil gibi özellikleri ayarlamanıza olanak tanır.
### GroupDocs.Annotation'ın ücretsiz deneme sürümü mevcut mu?
 Evet, satın alma işlemi yapmadan önce özelliklerini ve yeteneklerini keşfetmek için GroupDocs.Annotation'ın ücretsiz deneme sürümüne erişebilirsiniz.[Burada](https://releases.groupdocs.com/)..
### GroupDocs.Annotation desteğini nerede bulabilirim?
 GroupDocs.Annotation ile ilgili destek ve yardım için GroupDocs'u ziyaret edebilirsiniz.[forum](https://forum.groupdocs.com/c/annotation/10) açıklamalarla ilgili sorgulara ve tartışmalara ayrılmıştır.
### GroupDocs.Annotation için nasıl geçici lisans edinebilirim?
 GroupDocs.Annotation için GroupDocs aracılığıyla geçici bir lisans alabilirsiniz.[İnternet sitesi](https://purchase.groupdocs.com/temporary-license/)ürünü tam olarak değerlendirmenizi sağlar.