---
title: Belgeyi FTP'den Yükle
linktitle: Belgeyi FTP'den Yükle
second_title: GroupDocs.Annotation .NET API'si
description: Sorunsuz belge açıklaması için .NET uygulamalarınızı GroupDocs.Annotation ile geliştirin. Adım adım eğitim dahildir.
weight: 12
url: /tr/net/document-loading-essentials/load-document-from-ftp/
---

# Belgeyi FTP'den Yükle

## giriiş
GroupDocs.Annotation for .NET, .NET uygulamaları içindeki belge açıklama yeteneklerini zahmetsizce kolaylaştırmak için tasarlanmış çok yönlü bir kitaplıktır. İster PDF'ler, Microsoft Office belgeleri, resimler veya diğer formatlarla çalışıyor olun, bu kitaplık, işbirliğini ve belge yönetimini geliştirmek amacıyla yorumlar, vurgular ve şekiller gibi ek açıklamalar eklemek için birleşik bir çözüm sunar.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:
1. C# bilgisi: C# programlama dilinde yeterlilik, bu eğitimde sağlanan kod örneklerini anlamak ve uygulamak için çok önemlidir.
2.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i şuradan indirip yüklediğinizden emin olun:[İndirme: {link](https://releases.groupdocs.com/annotation/net/). Kütüphaneyi .NET projenize başarıyla entegre etmek için kurulum talimatlarını izleyin.
## Ad Alanlarını İçe Aktar
GroupDocs.Annotation for .NET işlevlerini kullanmak için gerekli ad alanlarını C# projenize aktarmanız gerekir. Bu adımları takip et:

C# projenizde kod dosyanızın başına gerekli ad alanlarını ekleyin:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Şimdi, GroupDocs.Annotation for .NET'i kullanarak FTP'den bir belge yükleme ve belgeye ek açıklamalar ekleme sürecini derinlemesine inceleyelim.
## Adım 1: Çıkış Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu belirtin.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Belgeyi FTP'den Yükleyin
Sağlanan dosya yolunu kullanarak belgeyi FTP sunucusundan alın.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Ek açıklama kodu buraya eklenecek
}
```
## 3. Adım: Ek Açıklama Ekle
Alan açıklaması gibi istediğiniz açıklamayı tanımlayın ve belgeye ekleyin.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Adım 4: Açıklamalı Belgeyi Kaydetme
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Adım 5: FTP'den Dosyayı Alın
Dosyayı FTP sunucusundan alma yöntemini uygulayın.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Adım 6: FTP İsteği Oluşturun
Dosyayı indirmek için bir FTP isteği oluşturun.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## 7. Adım: Dosya Akışını Alın
Dosya akışını FTP yanıtından alın.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Çözüm
Sonuç olarak GroupDocs.Annotation for .NET, geliştiricilere belge açıklama işlevlerini .NET uygulamalarına sorunsuz bir şekilde entegre etme yetkisi verir. Bu eğitimde özetlenen adım adım kılavuzu izleyerek, uygulamalarınızdaki işbirliğini ve belge yönetimini geliştirerek belgeleri FTP'den verimli bir şekilde yükleyebilir ve kolaylıkla ek açıklamalar ekleyebilirsiniz.
## SSS'ler
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Annotation for .NET, PDF, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çok çeşitli belge formatlarını destekler.
### GroupDocs.Annotation for .NET kullanılarak eklenen ek açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle, GroupDocs.Annotation for .NET, renkler, stiller ve şekiller de dahil olmak üzere ek açıklama görünümü için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Annotation for .NET, bulut depolama hizmetleri için destek sağlıyor mu?
Evet, GroupDocs.Annotation for .NET, popüler bulut depolama hizmetleriyle sorunsuz bir şekilde bütünleşerek Dropbox, Google Drive ve OneDrive gibi hizmetlerden belge yüklemenize ve kaydetmenize olanak tanır.
### GroupDocs.Annotation for .NET'in deneme sürümü mevcut mu?
 Evet, GroupDocs.Annotation for .NET'in özelliklerini şuradan ücretsiz deneme sürümünü indirerek keşfedebilirsiniz.[yayın sayfası](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET için nasıl teknik yardım veya destek alabilirim?
 Teknik yardım, sorun giderme veya genel sorularınız için GroupDocs.Annotation for .NET sayfasını ziyaret edebilirsiniz.[destek Forumu](https://forum.groupdocs.com/c/annotation/10).