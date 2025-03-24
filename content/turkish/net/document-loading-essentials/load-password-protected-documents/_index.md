---
title: Parola Korumalı Belgeleri Yükle
linktitle: Parola Korumalı Belgeleri Yükle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET ile işbirliğini ve belge incelemesini geliştirin. .NET uygulamalarınızda PDF'ye ve daha sorunsuz bir şekilde açıklama ekleyin.
weight: 17
url: /tr/net/document-loading-essentials/load-password-protected-documents/
---
## giriiş
Günümüzün hızlı dünyasında işbirliği başarının anahtarıdır. İster iş arkadaşlarınızla, müşterilerinizle veya ortaklarınızla bir proje üzerinde çalışıyor olun, belgelere verimli bir şekilde açıklama ekleme ve paylaşma yeteneği, verimliliği önemli ölçüde artırabilir ve iş akışlarını kolaylaştırabilir. GroupDocs.Annotation for .NET, PDF ve diğer belge formatlarına doğrudan .NET uygulamalarınızda açıklama eklemek için güçlü bir çözüm sunarak kusursuz işbirliği ve belge inceleme süreçlerine olanak tanır.
## Önkoşullar
GroupDocs.Annotation for .NET ile belge açıklamaları dünyasına dalmadan önce, mevcut olduğundan emin olmanız gereken birkaç önkoşul vardır:
### 1. .NET için GroupDocs.Annotation'ı yükleyin
 Başlamak için GroupDocs.Annotation for .NET kitaplığını indirip yüklemeniz gerekir. İndirme linkini bulabilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/). Kitaplığı .NET ortamınıza kurmak için sağlanan kurulum talimatlarını izleyin.
### 2. Lisans Alın veya Geçici Lisans Kullanın
 GroupDocs.Annotation for .NET, tam işlevselliğinin kilidini açmak için geçerli bir lisans gerektirir. GroupDocs web sitesinden bir lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy)veya değerlendirme amacıyla geçici bir lisans talep edebilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).
### 3. C# ve .NET Geliştirmeye aşinalık
GroupDocs.Annotation for .NET'i etkili bir şekilde kullanmak için C# programlama dili ve .NET geliştirme konusunda temel bir anlayış gereklidir. C# veya .NET'te yeniyseniz, çevrimiçi eğitimler ve kaynaklar aracılığıyla dil ve çerçeveye aşina olmayı düşünün.

## Gerekli Ad Alanlarını İçe Aktarın
Belgelere açıklama eklemeye başlamadan önce gerekli ad alanlarını C# projenize aktardığınızdan emin olun. Bu, GroupDocs.Annotation for .NET tarafından sağlanan sınıflara ve yöntemlere sorunsuz bir şekilde erişmenizi sağlar.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Artık önkoşulları yerine getirdiğinize ve gerekli ad alanlarını içe aktardığınıza göre, GroupDocs.Annotation for .NET'i kullanarak parola korumalı bir belgeye açıklama eklemeye geçelim. Aşağıda bu görevi gerçekleştirmenize yardımcı olacak adım adım bir kılavuz bulunmaktadır:
## 1. Adım: Belgeyi Yükleyin
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
```
Bu adımda, açıklamalı belgenin çıkış yolunu tanımlıyoruz ve parola korumalı belgeyi açmak için gereken parola dahil yükleme seçeneklerini belirliyoruz.
## 2. Adım: Açıklayıcıyı Başlatın
```csharp
using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
```
 Burada bir örneğini oluşturuyoruz.`Annotator` sınıf, giriş belgesine giden yolu ve yükleme seçeneklerini parametre olarak iletir.`using` beyanı şunları sağlar:`Annotator` nesne kullanımdan sonra uygun şekilde atılır.
## 3. Adım: Ek Açıklamalar Ekleyin
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
 Bu adımda yeni bir tane oluşturuyoruz.`AreaAnnotation` Açıklama kutusunun konumu ve boyutunun yanı sıra arka plan rengini de belirten nesne. Daha sonra ek açıklamayı belgeye şunu kullanarak ekliyoruz:`Add` yöntemi`Annotator` nesne.
## Adım 4: Açıklamalı Belgeyi Kaydedin
```csharp
annotator.Save(outputPath);
```
 Son olarak, açıklamalı belgeyi belirtilen çıktı yoluna aşağıdaki komutu kullanarak kaydederiz:`Save` yöntemi`Annotator` nesne.
## Adım 5: Onay Mesajını Görüntüleyin
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Kullanıcıya geri bildirim sağlamak için belgenin başarıyla kaydedildiğini belirten bir onay mesajı görüntüler ve çıktı dosyasının konumunu belirtiriz.

## Çözüm
Sonuç olarak, GroupDocs.Annotation for .NET, .NET uygulamaları içindeki belgelere açıklama eklemek için sağlam ve zengin özelliklere sahip bir çözüm sunar. Bu makalede verilen adım adım kılavuzu takip ederek belge açıklama özelliklerini projelerinize kolayca entegre edebilir, gelişmiş işbirliği ve belge inceleme süreçlerine olanak tanıyabilirsiniz.
## SSS'ler
### S: GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation for .NET, PDF, Microsoft Word, Excel, PowerPoint ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### S: GroupDocs.Annotation for .NET ile oluşturulan ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle! GroupDocs.Annotation for .NET, ek açıklamalar için kapsamlı özelleştirme seçenekleri sunarak renk, boyut, opaklık ve daha fazlası gibi çeşitli hususları kontrol etmenize olanak tanır.
### S: GroupDocs.Annotation for .NET'in deneme sürümü mevcut mu?
 Evet, GroupDocs.Annotation for .NET'in ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/)Deneme sürümü, satın alma işlemi yapmadan önce ürünü değerlendirmenize olanak tanır.
### S: GroupDocs.Annotation for .NET desteğini nasıl alabilirim?
 GroupDocs.Annotation for .NET'i kullanırken herhangi bir sorunuz varsa veya herhangi bir sorunla karşılaşırsanız destek forumunu ziyaret edebilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10) topluluktan ve GroupDocs destek ekibinden yardım istemek.
### S: GroupDocs.Annotation for .NET'i hem web hem de masaüstü uygulamalarına entegre edebilir miyim?
Evet, GroupDocs.Annotation for .NET, hem web hem de masaüstü uygulamalarıyla uyumlu olacak şekilde tasarlanmıştır ve belge açıklama işlevselliğini projelerinize nasıl dahil edeceğiniz konusunda esneklik sağlar.