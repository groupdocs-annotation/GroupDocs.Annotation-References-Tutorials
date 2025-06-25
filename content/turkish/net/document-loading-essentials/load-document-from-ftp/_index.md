---
"description": "Kusursuz belge açıklamaları için .NET uygulamalarınızı GroupDocs.Annotation ile geliştirin. Adım adım eğitim dahildir."
"linktitle": "FTP'den Belge Yükle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "FTP'den Belge Yükle"
"url": "/tr/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# FTP'den Belge Yükle

## giriiş
GroupDocs.Annotation for .NET, .NET uygulamaları içinde belge açıklama yeteneklerini zahmetsizce kolaylaştırmak için tasarlanmış çok yönlü bir kütüphanedir. İster PDF'lerle, ister Microsoft Office belgeleriyle, ister resimlerle veya diğer biçimlerle uğraşıyor olun, bu kütüphane iş birliğini ve belge yönetimini geliştirmek için yorumlar, vurgular ve şekiller gibi açıklamalar eklemek için birleşik bir çözüm sunar.
## Ön koşullar
Eğitime başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:
1. C# Bilgisi: Bu eğitimde sunulan kod örneklerini anlamak ve uygulamak için C# programlama dilinde yeterliliğe sahip olmak şarttır.
2. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET'i indirip kurduğunuzdan emin olun. [indirme bağlantısı](https://releases.groupdocs.com/annotation/net/)Kütüphaneyi .NET projenize başarılı bir şekilde entegre etmek için kurulum talimatlarını izleyin.
## Ad Alanlarını İçe Aktar
GroupDocs.Annotation for .NET işlevselliklerini kullanmak için, gerekli ad alanlarını C# projenize aktarmanız gerekir. Şu adımları izleyin:

C# projenizde, kod dosyanızın başına gerekli ad alanlarını ekleyin:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Şimdi, .NET için GroupDocs.Annotation'ı kullanarak FTP'den bir belgeyi yükleme ve ona açıklamalar ekleme sürecini inceleyelim.
## Adım 1: Çıktı Yolunu Tanımlayın
Açıklamalı belgenin kaydedileceği çıktı yolunu belirtin.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Adım 2: Belgeyi FTP'den Yükle
Sağlanan dosya yolunu kullanarak belgeyi FTP sunucusundan alın.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Açıklama kodu buraya eklenecek
}
```
## Adım 3: Açıklama Ekle
İstenilen açıklamayı (örneğin alan açıklaması) tanımlayın ve belgeye ekleyin.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Adım 4: Açıklamalı Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Adım 5: Dosyayı FTP'den Alın
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
## Adım 7: Dosya Akışını Alın
FTP yanıtından dosya akışını alın.
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
Sonuç olarak, GroupDocs.Annotation for .NET, geliştiricilerin belge açıklama işlevlerini .NET uygulamalarına sorunsuz bir şekilde entegre etmelerini sağlar. Bu eğitimde özetlenen adım adım kılavuzu izleyerek, FTP'den belgeleri verimli bir şekilde yükleyebilir ve kolayca açıklamalar ekleyebilir, böylece uygulamalarınızdaki iş birliğini ve belge yönetimini geliştirebilirsiniz.
## SSS
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mudur?
Evet, GroupDocs.Annotation for .NET, PDF, Microsoft Office belgeleri, resimler ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation for .NET kullanılarak eklenen açıklamaların görünümünü özelleştirebilir miyim?
Kesinlikle, GroupDocs.Annotation for .NET, renkler, stiller ve şekiller de dahil olmak üzere açıklama görünümü için kapsamlı özelleştirme seçenekleri sunar.
### GroupDocs.Annotation for .NET bulut depolama servislerini destekliyor mu?
Evet, GroupDocs.Annotation for .NET, popüler bulut depolama hizmetleriyle sorunsuz bir şekilde bütünleşerek Dropbox, Google Drive ve OneDrive gibi hizmetlerden belgeleri yüklemenize ve kaydetmenize olanak tanır.
### GroupDocs.Annotation for .NET için deneme sürümü mevcut mu?
Evet, GroupDocs.Annotation for .NET'in özelliklerini ücretsiz deneme sürümünü indirerek keşfedebilirsiniz. [yayın sayfası](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET için teknik yardım veya desteği nasıl alabilirim?
Teknik yardım, sorun giderme veya genel sorular için GroupDocs.Annotation for .NET sayfasını ziyaret edebilirsiniz. [destek forumu](https://forum.groupdocs.com/c/annotation/10).