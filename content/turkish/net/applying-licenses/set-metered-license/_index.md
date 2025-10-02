---
"description": ".NET uygulamalarınızda kaynak kullanımını ve belge açıklama yeteneklerini kontrol etmek için GroupDocs.Annotation .NET için ölçülü bir lisans ayarlamayı öğrenin."
"linktitle": "Ölçülü Lisans Ayarla"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ölçülü Lisans Ayarla"
"url": "/tr/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# Ölçülü Lisans Ayarla

## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin .NET uygulamalarına zahmetsizce belge açıklama yetenekleri eklemesini sağlayan güçlü bir kütüphanedir. İster bir belge yönetim sistemi, ister bir işbirliği platformu veya belge incelemesi ve işaretlemesi içeren herhangi bir uygulama oluşturuyor olun, GroupDocs.Annotation for .NET süreci kolaylaştırmak için kapsamlı bir araç seti sunar.
Bu eğitimde, GroupDocs.Annotation .NET için ölçülü bir lisans kurma sürecini inceleyeceğiz. Ölçülü bir lisans, yalnızca tükettiğiniz kaynaklar için ödeme yapmanızı sağlayarak, her ölçekteki proje için uygun maliyetli bir çözümdür. Aşağıda özetlenen adımları izleyerek, kaynak kullanımını optimize ederken ve bütçe kontrolünü korurken GroupDocs.Annotation'ı .NET uygulamanıza sorunsuz bir şekilde entegre edebileceksiniz.
## Ön koşullar
Eğitime başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET Kütüphanesi: Kütüphaneyi şu adresten indirin: [web sitesi](https://releases.groupdocs.com/annotation/net/).
2. GroupDocs Hesabına Erişim: Ölçülü lisansı kurmak için gereken genel ve özel anahtarları edinmek için bir GroupDocs hesabına ihtiyacınız olacak. Henüz bir hesabınız yoksa, ücretsiz denemeye kaydolabilirsiniz [Burada](https://releases.groupdocs.com/).
3. C# ve .NET Framework'ün Temel Anlayışı: Bu eğitimde özetlenen adımları uygulamak için C# programlama dili ve .NET framework'e aşina olmak faydalı olacaktır.

## Ad Alanlarını İçe Aktar
Başlamak için, gerekli ad alanlarını C# projenize aktardığınızdan emin olun. Bu ad alanları, GroupDocs.Annotation işlevselliğiyle etkileşim kurmak için gereklidir.
```csharp
using System;
```
## Adım 1: Genel ve Özel Anahtarları Elde Edin
Ölçülü lisansı ayarlamadan önce, GroupDocs hesabınızın panosundan genel ve özel anahtarlarınızı edinmeniz gerekir.
1. GroupDocs hesabınıza giriş yapın.
2. Lisans yönetimi bölümüne gidin.
3. GroupDocs tarafından sağlanan genel ve özel anahtarlarınızı kopyalayın.
## Adım 2: Ölçülü Lisans Ayarlayın
Açık ve özel anahtarlarınızı aldıktan sonra, .NET uygulamanızda ölçülü lisansı ayarlayabilirsiniz.
```csharp
string publicKey = "*****"; // ***** ifadesini açık anahtarınızla değiştirin
string privateKey = "*****"; // *****'ı özel anahtarınızla değiştirin
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation .NET için ölçülü bir lisans kurmak, belge açıklama projeleriniz için verimli kaynak kullanımı ve maliyet etkinliği sağlayan basit bir işlemdir. Bu eğitimde özetlenen adımları izleyerek, GroupDocs.Annotation'ı .NET uygulamanıza sorunsuz bir şekilde entegre edebilir ve belge iş birliği ve inceleme yeteneklerini geliştirebilirsiniz.
## SSS
### GroupDocs.Annotation for .NET'i ticari projelerde kullanabilir miyim?
Evet, GroupDocs.Annotation for .NET hem ticari hem de ticari olmayan projelerde kullanılabilir. Ancak, projenizin gereksinimlerine göre uygun bir lisans edinmeniz gerekir.
### GroupDocs.Annotation for .NET için deneme sürümü mevcut mu?
Evet, GroupDocs.Annotation for .NET'in ücretsiz deneme sürümünden yararlanmak için şu adresi ziyaret edin: [bu bağlantı](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET için teknik desteği nasıl alabilirim?
GroupDocs forumunu ziyaret ederek teknik destek alabilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).
### Geçici lisans seçenekleri mevcut mudur?
Evet, kısa süreli kullanım veya değerlendirme amaçları için GroupDocs'tan geçici bir lisans alabilirsiniz. Ziyaret edin [bu bağlantı](https://purchase.groupdocs.com/temporary-license/) Daha fazla bilgi için.
### Projemin gereksinimlerine göre açıklama özelliklerini özelleştirebilir miyim?
Evet, GroupDocs.Annotation for .NET kapsamlı özelleştirme seçenekleri sunarak, açıklama özelliklerini özel proje ihtiyaçlarınıza göre uyarlamanıza olanak tanır.