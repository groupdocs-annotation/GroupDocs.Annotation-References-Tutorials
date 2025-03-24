---
title: Ölçülü Lisansı Ayarla
linktitle: Ölçülü Lisansı Ayarla
second_title: GroupDocs.Annotation .NET API'si
description: .NET uygulamalarınızdaki kaynak kullanımı ve belge ek açıklama yetenekleri için GroupDocs.Annotation .NET için ölçülü bir lisansın nasıl ayarlanacağını öğrenin.
weight: 12
url: /tr/net/applying-licenses/set-metered-license/
---

# Ölçülü Lisansı Ayarla

## giriiş
GroupDocs.Annotation for .NET, geliştiricilerin .NET uygulamalarına zahmetsizce belge açıklama özellikleri eklemesine olanak tanıyan güçlü bir kitaplıktır. İster bir belge yönetim sistemi, işbirliği platformu veya belge inceleme ve işaretlemeyi içeren herhangi bir uygulama oluşturuyor olun, GroupDocs.Annotation for .NET, süreci kolaylaştırmak için kapsamlı bir araç seti sağlar.
Bu öğreticide, GroupDocs.Annotation .NET için ölçülü lisans ayarlama sürecini ayrıntılı olarak ele alacağız. Ölçülü lisans, yalnızca tükettiğiniz kaynaklar için ödeme yapmanıza olanak tanır ve bu da onu her ölçekteki proje için uygun maliyetli bir çözüm haline getirir. Aşağıda özetlenen adımları izleyerek, kaynak kullanımını optimize ederken ve bütçe kontrolünü sürdürürken GroupDocs.Annotation'ı .NET uygulamanıza sorunsuz bir şekilde entegre edebileceksiniz.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  GroupDocs.Annotation for .NET Kitaplığı: Kitaplığı şu adresten indirin:[İnternet sitesi](https://releases.groupdocs.com/annotation/net/).
2. GroupDocs Hesabına Erişim: Ölçülü lisansı ayarlamak için gereken genel ve özel anahtarları edinmek için bir GroupDocs hesabına ihtiyacınız olacak. Henüz bir hesabınız yoksa ücretsiz denemeye kaydolabilirsiniz[Burada](https://releases.groupdocs.com/).
3. C# ve .NET Framework Hakkında Temel Anlayış: C# programlama dili ve .NET framework'e aşinalık, bu eğitimde özetlenen adımların uygulanmasında faydalı olacaktır.

## Ad Alanlarını İçe Aktar
Başlamak için gerekli ad alanlarını C# projenize aktardığınızdan emin olun. Bu ad alanları GroupDocs.Annotation işleviyle etkileşim kurmak için gereklidir.
```csharp
using System;
```
## Adım 1: Genel ve Özel Anahtarları Alın
Ölçülü lisansı ayarlamadan önce genel ve özel anahtarlarınızı GroupDocs hesap kontrol panelinizden almanız gerekir.
1. GroupDocs hesabınızda oturum açın.
2. Lisans yönetimi bölümüne gidin.
3. GroupDocs tarafından sağlanan genel ve özel anahtarlarınızı kopyalayın.
## 2. Adım: Ölçülü Lisansı Ayarlayın
Genel ve özel anahtarlarınızı aldıktan sonra, .NET uygulamanızda ölçülü lisansı ayarlayabilirsiniz.
```csharp
string publicKey = "*****"; // *****'yı genel anahtarınızla değiştirin
string privateKey = "*****"; // *****'yı özel anahtarınızla değiştirin
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation .NET için ölçülü bir lisans ayarlamak, belge açıklama projeleriniz için verimli kaynak kullanımı ve maliyet etkinliği sağlayan basit bir işlemdir. Bu öğreticide özetlenen adımları izleyerek GroupDocs.Annotation'ı .NET uygulamanıza sorunsuz bir şekilde entegre edebilir ve belge işbirliği ve inceleme yeteneklerini geliştirebilirsiniz.
## SSS'ler
### GroupDocs.Annotation for .NET'i ticari projelerde kullanabilir miyim?
Evet, GroupDocs.Annotation for .NET hem ticari hem de ticari olmayan projelerde kullanılabilir. Ancak proje gereksinimlerinize göre uygun bir lisans almanız gerekir.
### GroupDocs.Annotation for .NET'in deneme sürümü mevcut mu?
 Evet, GroupDocs.Annotation for .NET'in ücretsiz deneme sürümünden şu adresi ziyaret ederek yararlanabilirsiniz:[bu bağlantı](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET için nasıl teknik destek alabilirim?
 GroupDocs forumunu ziyaret ederek teknik destek alabilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).
### Herhangi bir geçici lisans seçeneği mevcut mu?
 Evet, kısa süreli kullanım veya değerlendirme amacıyla GroupDocs'tan geçici bir lisans alabilirsiniz. Ziyaret etmek[bu bağlantı](https://purchase.groupdocs.com/temporary-license/) daha fazla bilgi için.
### Ek açıklama özelliklerini proje gereksinimlerime göre özelleştirebilir miyim?
Evet, GroupDocs.Annotation for .NET, kapsamlı özelleştirme seçenekleri sunarak, ek açıklama özelliklerini özel proje ihtiyaçlarınıza uyacak şekilde uyarlamanıza olanak tanır.