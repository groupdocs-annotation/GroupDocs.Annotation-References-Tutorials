---
"description": "GroupDocs.Annotation for .NET'in gücünü keşfedin ve uygulamalarınıza belge açıklama yeteneklerini zahmetsizce ekleyin."
"linktitle": "Belgeye Arama Metni Parçası Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Arama Metni Parçası Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# Belgeye Arama Metni Parçası Açıklaması Ekle

## giriiş
.NET geliştirme alanında, GroupDocs.Annotation belgeleri sorunsuz bir şekilde ek açıklamalar eklemek için güçlü bir araç olarak öne çıkıyor. İster deneyimli bir geliştirici olun, ister .NET dünyasına yeni adım atıyor olun, bu kapsamlı eğitim size GroupDocs.Annotation for .NET'i kullanmanın temellerini, ad alanlarını içe aktarmaktan belgelerinize arama metni parçacığı ek açıklamaları eklemenin inceliklerinde ustalaşmaya kadar anlatacak.
## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin belge açıklama yeteneklerini uygulamalarına zahmetsizce dahil etmelerini sağlar. Sezgisel API'si ve sağlam özellikleriyle geliştiriciler, PDF'ler, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çeşitli belge biçimlerine açıklama ekleyebilir.
## Ön koşullar
GroupDocs.Annotation for .NET'e dalmadan önce, aşağıdaki ön koşulların mevcut olduğundan emin olun:

## Ad Alanlarını İçe Aktar
Öncelikle .NET projenizde GroupDocs.Annotation sınıflarına ve metodlarına erişmek için gerekli ad alanlarını içe aktarın:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Adım 1: Çıktı Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu tanımlayarak başlayın:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Annotator'ı Başlatın
Sonra, bir örneğini başlatın `Annotator` Açıklama eklemek istediğiniz belgenin yolunu sağlayarak sınıfa ekleyin:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Adım 3: Arama Metni Parçası Açıklaması Oluşturun
Bir tane oluştur `SearchTextFragment` Aranacak metin, yazı tipi boyutu, yazı tipi ailesi, yazı tipi rengi ve arka plan rengi gibi istenen özelliklere sahip nesne:
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
## Adım 4: Açıklama Ekle
Oluşturulan arama metni parçası açıklamasını, şunu kullanarak belgeye ekleyin: `Add` açıklayıcının yöntemi:
```csharp
annotator.Add(searchText);
```
## Adım 5: Açıklamalı Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin:
```csharp
annotator.Save(outputPath);
```
## Adım 6: Başarı Mesajını Göster
Kullanıcıya belgenin başarıyla kaydedildiğini bildirin:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation for .NET, belgelere açıklama ekleme sürecini basitleştirir, iş birliğini ve belge inceleme süreçlerini geliştirir. Bu kılavuzda özetlenen adımları izleyerek, belge açıklama yeteneklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edebilirsiniz.
## SSS
### GroupDocs.Annotation tüm belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation PDF'ler, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### Açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation, yazı tipi boyutu, renk ve stil gibi özellikleri ayarlamanıza olanak tanıyarak açıklamalar için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Annotation için ücretsiz deneme sürümü mevcut mu?
Evet, satın alma işlemi yapmadan önce özelliklerini ve yeteneklerini keşfetmek için GroupDocs.Annotation'ın ücretsiz deneme sürümüne erişebilirsiniz [Burada](https://releases.groupdocs.com/)..
### GroupDocs.Annotation için desteği nerede bulabilirim?
GroupDocs.Annotation ile ilgili destek ve yardım için GroupDocs'u ziyaret edebilirsiniz [forum](https://forum.groupdocs.com/c/annotation/10) Açıklamalarla ilgili soru ve tartışmalara ayrılmıştır.
### GroupDocs.Annotation için geçici lisansı nasıl alabilirim?
GroupDocs.Annotation için GroupDocs aracılığıyla geçici bir lisans edinebilirsiniz. [web sitesi](https://purchase.groupdocs.com/temporary-license/)Ürünü tam olarak değerlendirmenize olanak sağlar.