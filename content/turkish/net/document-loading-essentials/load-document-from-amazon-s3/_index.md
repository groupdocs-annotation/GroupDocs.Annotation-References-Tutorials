---
categories:
- Document Management
date: '2026-07-06'
description: AWS kimlik bilgilerini nasıl yapılandıracağınızı ve GroupDocs Annotation'ı
  C# kullanarak Amazon S3 ile nasıl entegre edeceğinizi öğrenin. Belgeleri yükleme,
  açıklama ekleme ve yönetme konusunda adım adım kılavuz.
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: Amazon S3'ten Belge Yükle
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: GroupDocs Annotation S3 Entegrasyonu için AWS Kimlik Bilgilerini Yapılandırma
type: docs
url: /tr/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# AWS Kimlik Bilgilerini GroupDocs Annotation S3 Entegrasyonu için Yapılandırma

Bu öğreticide, **AWS kimlik bilgilerini yapılandırmayı** ve GroupDocs.Annotation'ı Amazon S3 ile C# kullanarak sorunsuz bir şekilde entegre etmeyi öğreneceksiniz. Bir S3 kovasından belge yüklemeyi, ek açıklamalar eklemeyi ve sonucu buluta geri kaydetmeyi adım adım gösterecek, aynı zamanda en iyi uygulama güvenliği ve performans ipuçlarını ele alacağız.

## Hızlı Yanıtlar
- **AWS kimlik bilgilerini nasıl yapılandırırım?** `AmazonS3Client` yapıcısını `BasicAWSCredentials` ile kullanın veya otomatik kimlik bilgisi çözümü için IAM rollerine güvenin.  
- **Hangi NuGet paketleri gereklidir?** `GroupDocs.Annotation` ve `AWSSDK.S3`.  
- **100 MB'den büyük PDF'leri ek açıklama yapabilir miyim?** Evet – tüm dosyayı belleğe yüklememek için akış ve async API'lerini kullanın.  
- **Entegrasyon iş parçacığı güvenli mi?** Her istek için ayrı bir `Annotator` örneği oluşturun; SDK kendisi durum bilgisizdir.  
- **S3'teki belgeleri şifrelemem gerekiyor mu?** Uyumluluk ve veri koruması için sunucu tarafı şifrelemeyi (SSE‑S3 veya SSE‑KMS) etkinleştirin.

## Neden Belge Ek Açıklaması için S3 Kullanmalı?
S3'ü belge ek açıklaması için kullanmak, dosyalarınızı güvenli tutarken son derece ölçeklenebilir, maliyet‑etkin ve küresel olarak erişilebilir bir depolama çözümü sunar.  
- **Scalability**: S3, neredeyse sınırsız nesne yönetir, dosya başına 5 TB ve saniyede milyonlarca istek destekler.  
- **Cost‑Effectiveness**: Sadece gerçekten kullandığınız depolama için ödeme yaparsınız, otomatik sınıflandırma daha düşük maliyetli sınıflara geçiş sağlar.  
- **Global Accessibility**: Herhangi bir AWS bölgesinden düşük gecikmeli erişim, ek açıklamalı belgelerinizin her zaman ulaşılabilir olmasını sağlar.  
- **Security**: Yerleşik şifreleme (SSE‑S3, SSE‑KMS) ve ayrıntılı IAM politikaları hassas verileri korur.  
- **Integration**: Mevcut AWS hizmetleriyle (CloudFront, Lambda ve IAM gibi) yerel olarak çalışır.

## Önkoşullar

Başlamadan önce, aşağıdaki temel gereksinimlerin hazır olduğundan emin olun:

1. **C# Geliştirme Ortamı** – .NET desteği olan Visual Studio veya VS Code.  
2. **GroupDocs.Annotation for .NET** – [resmi web sitesinden](https://releases.groupdocs.com/annotation/net/) indirin.  
3. **AWS S3 Erişimi** – Hedef kova için okuma/yazma izinlerine sahip geçerli AWS kimlik bilgileri.  
4. **Temel C# Bilgisi** – Sınıflar, async/await ve akışlar hakkında anlayış.  
5. **Amazon S3 SDK** – NuGet (`AWSSDK.S3`) üzerinden kurun.  

## S3 Erişimi için AWS kimlik bilgileri nasıl yapılandırılır?
`BasicAWSCredentials` bir AWS erişim anahtarı kimliği ve gizli erişim anahtarını tutan bir sınıftır.  
`AmazonS3Client` S3 hizmetleriyle etkileşim için kullanılan AWS SDK istemcisidir.

AWS anahtarlarınızı bir kez yükleyin ve SDK'nın her istek için yeniden kullanmasına izin verin. En basit yol, bir `BasicAWSCredentials` nesnesi oluşturup `AmazonS3Client` yapıcısına geçirmek. Üretim iş yükleri için, gizli anahtarları sabit kodlamaktan kaçınmak amacıyla IAM rolleri veya ortam değişkenlerini tercih edin.

**Pro ipucu:** EC2, ECS veya Lambda üzerinde çalışırken, açık kimlik bilgilerini atlayın ve SDK'nın örnek profilinden geçici kimlik bilgilerini otomatik olarak almasına izin verin.

## Ad Alanlarını İçe Aktarma

Şimdi S3 entegrasyonumuz için gerekli tüm ad alanlarını içe aktaralım:
```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

Bu içe aktarmalar, AWS S3 işlemlerine ve GroupDocs ek açıklama işlevselliğine erişim sağlar. `Amazon.S3` ad alanı bulut depolama etkileşimlerimizi yönetirken, `GroupDocs.Annotation.Models` ek açıklama çerçevesini sunar.

## Adım Adım Uygulama

Şimdi S3'ten bir belge yükleme ve ek açıklama ekleme sürecinin tamamını adım adım inceleyelim. Bu süreci, takip edebileceğiniz yönetilebilir adımlara böleceğiz.

### Adım 1: Çıktı Yolunu Tanımlama

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

Bu, ek açıklamalı belgenizin kaydedileceği yerel bir yol oluşturur. `Path.Combine` yöntemi, platformlar arası uyumluluğu sağlar ve belge türü bütünlüğünü korumak için orijinal dosya uzantısını korur.

**Pro Tip**: Çıktı dosya adınızda bir zaman damgası kullanarak önceki ek açıklamaların üzerine yazılmasını önleyin: `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`.

### Adım 2: Belge Anahtarını Belirleme

```csharp
string key = "sample.pdf";
```

Bu, S3 kovasındaki belgenizin benzersiz tanımlayıcısıdır. Gerçek dünyada, genellikle bunu kullanıcı girişi, bir veritabanı kaydı veya bir API parametresi aracılığıyla alırsınız. Anahtarın S3 nesne adıyla tam olarak eşleştiğinden emin olun, klasör ön ekleri dahil (ör. `documents/2025/sample.pdf`).

### Adım 3: Annotator'ı Başlatma

`Annotator`, GroupDocs.Annotation içinde düzenlenebilir bir belge oturumunu temsil eden temel sınıftır. Ek açıklama ekleme, değiştirme ve silme yöntemlerini sağlar.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

S3 indirme akışını bir `using` bloğu içinde sararak, hem akışın hem de annotator örneğinin doğru şekilde serbest bırakılmasını sağlarız.

### Adım 4: Alan Ek Açıklaması Oluşturma

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

Bu, belgenizde dikdörtgen bir ek açıklama oluşturur. `Rectangle(100, 100, 100, 100)` parametreleri sırasıyla X konumu, Y konumu, genişlik ve yükseklik değerlerini temsil eder. `BackgroundColor` değeri `65535` sarı bir vurgulama oluşturur – bunu standart RGB renk kodlarıyla özelleştirebilirsiniz.

**Alan Ek Açıklamaları için Yaygın Kullanım Durumları**:
- Sözleşmelerde önemli bölümleri vurgulama  
- Teknik özelliklerde inceleme alanlarını işaretleme  
- Sunum slaytlarına görsel açıklamalar ekleme  

### Adım 5: Belgeye Ek Açıklama Ekleme

```csharp
annotator.Add(area);
```

Bu yöntem, alan ek açıklamamızı belgeye ekler. Farklı ek açıklama türlerini (metin yorumları, oklar veya damgalar gibi) eklemek için `Add()` metodunu birden fazla kez çağırabilirsiniz. Ek açıklamalar, belgeyi açıkça kaydedene kadar bellekte kalır.

### Adım 6: Ek Açıklamalı Belgeyi Kaydetme

```csharp
annotator.Save(outputPath);
```

Şimdi ek açıklamalı belgeyi belirttiğimiz çıktı yoluna kaydediyoruz. Bu, tüm ek açıklamaları gömülü yeni bir dosya oluşturur. Sonucu tekrar S3'e kaydetmeniz gereken yaygın bir üretim senaryosu için, bu adımın ardından S3 SDK'sını kullanarak dosyayı yükleyebilirsiniz.

### Adım 7: Başarı Mesajını Görüntüleme

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Basit bir onay mesajı, hata ayıklamaya yardımcı olur ve kullanıcı geri bildirimi sağlar. Gerçek bir uygulamada bunu uygun günlükleme veya UI bildirimiyle değiştirirsiniz.

## S3 İndirme Yönteminin Uygulanması

`DownloadFile(key)` yöntemine referans verdiğimizi fark edeceksiniz ancak henüz uygulamadık. İşte bu temel yardımcı fonksiyonu oluşturmanın yolu:
```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**Güvenlik Notu**: Üretim kodunda AWS kimlik bilgilerini asla sabit kodlamayın. IAM rolleri, ortam değişkenleri veya paylaşılan kimlik bilgileri dosyasını kullanarak gizli anahtarları kaynak kontrolünden uzak tutun.

## Amazon S3'ten Bir Belge Nasıl Yüklenir?
`GetObjectAsync` S3'ten bir nesne alıp akış içeren bir yanıt döndüren asenkron bir yöntemdir.  
`MemoryStream` .NET akışı, verileri bellekte saklar ve disk I/O olmadan hızlı okuma/yazma sağlar.  
`Annotator` (daha önce tanımlandığı gibi) belgeyi ek açıklama için yükleyen sınıftır.

PDF'yi doğrudan `GetObjectAsync` yöntemiyle S3'ten yükleyin, yanıt akışını bir `MemoryStream` içine sarın ve `Annotator` yapıcısına geçirin. Bu yaklaşım, orijinal dosyayı diske yazmadan, I/O yükünü azaltır ve büyük dosyalarla çalışırken bellek kullanımını kontrol altında tutar.
```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## Yaygın Entegrasyon Sorunları ve Çözümleri

Gerçek dünya uygulama deneyimine dayanarak, karşılaşacağınız en sık sorunlar ve çözümleri aşağıdadır:

### Sorun 1: "Access Denied" Hataları
**Problem**: Uygulamanız S3 nesnelerine erişemiyor.  
**Çözüm**: IAM kullanıcı veya rolünüzün belirli kova ve nesneler için `s3:GetObject` iznine sahip olduğunu doğrulayın.

### Sorun 2: Büyük Dosya Zaman Aşımı
**Problem**: 50 MB üzerindeki belgeler zaman aşımı hatalarına neden olur.  
**Çözüm**: Asenkron işlemler uygulayın ve zaman aşımı değerlerini artırın:
```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### Sorun 3: Birden Çok Belgeyle Bellek Sorunları
**Problem**: Çok sayıda belge işlemek bellek yetersizliği istisnalarına yol açar.  
**Çözüm**: Akışları hızlı bir şekilde serbest bırakın ve belgeleri toplu olarak işleyin.

### Sorun 4: Bölge Uyumsuzluğu Hataları
**Problem**: S3 istemcisi kovayı bulamıyor.  
**Çözüm**: `RegionEndpoint`'in, kovanın gerçek bölgesiyle eşleştiğinden emin olun.

## Performans ve Güvenlik En İyi Uygulamaları

### Performans Optimizasyonu
- **Use Async Methods**: `GetObjectAsync()` yöntemini senkron çağrılara tercih edin.  
- **Implement Caching**: Sık erişilen belgeleri kısa bir süre için yerel olarak saklayın.  
- **Batch Operations**: Uygun olduğunda birden fazla dosyayı paralel olarak işleyin.  
- **Stream Processing**: Büyük belgeleri belleğe tamamen yüklemekten kaçının; akışlarla çalışın.

### Güvenlik Hususları
- **Use IAM Roles**: Sabit kodlanmış kimlik bilgilerini ortadan kaldırın.  
- **Enable S3 Encryption**: Sunucu tarafı şifrelemeyi (SSE‑S3 veya SSE‑KMS) etkinleştirin.  
- **Implement Access Logging**: Kimlerin hangi belgelere eriştiğini izleyin.  
- **Validate File Types**: İşleme almadan önce uzantı ve MIME tiplerini kontrol edin.

## Gerçek Dünya Kullanım Senaryoları

Bu S3 entegrasyon modeli, birçok sektörde öne çıkar:
1. **Hukuki Belge İncelemesi** – Hukuk firmaları S3'te depolanan sözleşmeleri ek açıklama yapar.  
2. **Eğitim Platformları** – Öğretmenler bulutta barındırılan öğrenci gönderilerini işaretler.  
3. **İnşaat Yönetimi** – Mimarlar bölgeler arası planları ek açıklama yapar.  
4. **Tıbbi Kayıtlar** – Sağlık hizmeti sağlayıcıları hasta belgelerine güvenli bir şekilde not ekler.  
5. **Finansal Hizmetler** – Denetçiler S3'te depolanan uyumluluk belgeleri üzerinde iş birliği yapar.

## Sorun Giderme Kılavuzu

**S3'ten Belge Yüklenemiyor**  
- AWS kimlik bilgilerini ve kova izinlerini doğrulayın.  
- Kova adını ve nesne anahtarının yazımını iki kez kontrol edin.  
- Belgenin S3'te bozuk olmadığından emin olun.

**Ek Açıklamalar Görünmüyor**  
- `annotator.Save()` metodunu ek açıklamaları ekledikten sonra çağırdığınızdan emin olun.  
- Kullandığınız ek açıklama türünü belgenin formatının desteklediğini kontrol edin.  
- Ek açıklama koordinatlarının sayfa sınırları içinde olduğundan emin olun.

**Performans Sorunları**  
- S3 istek oranlarını izleyin ve üssel geri çekilme (exponential back‑off) uygulayın.  
- Sık erişilen dosyalar için CloudFront CDN kullanın.  
- Küresel uygulamalar için S3 Transfer Acceleration'ı değerlendirin.

## Sık Sorulan Sorular

**S: GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?**  
**C:** GroupDocs.Annotation, PDF, DOCX, PPTX ve HTML dahil olmak üzere 50'den fazla giriş ve çıkış formatını destekler; ancak ek açıklama türleri formatlara göre değişebilir.

**S: GroupDocs.Annotation for .NET'i satın almadan deneyebilir miyim?**  
**C:** Evet, ücretsiz deneme sürümüne [buradan](https://releases.groupdocs.com/) erişerek GroupDocs.Annotation for .NET'in özelliklerini keşfedebilirsiniz. Bu, S3 entegrasyonu ve ek açıklama yeteneklerini risksiz bir şekilde test etmenizi sağlar.

**S: GroupDocs.Annotation for .NET için dokümantasyonu nerede bulabilirim?**  
**C:** GroupDocs.Annotation for .NET için kapsamlı dokümantasyon [burada](https://tutorials.groupdocs.com/annotation/net/) mevcuttur. Belgeler API referansları, ileri düzey örnekler ve entegrasyon kılavuzlarını içerir.

**S: GroupDocs.Annotation for .NET'i değerlendirmek için geçici bir lisansa ihtiyacım var mı?**  
**C:** Değerlendirme amaçlı geçici bir lisansı [buradan](https://purchase.groupdocs.com/temporary-license/) alabilirsiniz. Bu, deneme sınırlamalarını kaldırır ve üretim senaryolarını tam olarak test etmenizi sağlar.

**S: GroupDocs.Annotation for .NET için yardım veya destek nereden alabilirim?**  
**C:** Herhangi bir soru veya destek ile ilgili sorun için GroupDocs.Annotation forumunu [buradan](https://forum.groupdocs.com/c/annotation/10) ziyaret edebilirsiniz. Topluluk ve destek ekibi entegrasyon sorunlarını çözmek için aktiftir ve yardımcıdır.

**S: Ek açıklamalı belgeleri yerel depolama yerine S3'e geri kaydedebilir miyim?**  
**C:** Kesinlikle! `annotator.Save(localPath)` metodunu çağırdıktan sonra, ek açıklamalı dosyayı `PutObjectAsync()` yöntemiyle S3'e yükleyebilirsiniz. Bu, web uygulamaları için ideal bir bulut‑to‑bulut iş akışı oluşturur.

**S: S3 belge ek açıklaması için desteklenen maksimum dosya boyutu nedir?**  
**C:** GroupDocs.Annotation büyük dosyaları işleyebilse de, pratik sınırlamalar sunucu belleği ve S3 transfer zaman aşımına bağlıdır. 100 MB üzerindeki dosyalar için akış veya parçalı işleme uygulayarak bellek tükenmesini önleyin.

**Son Güncelleme:** 2026-07-06  
**Test Edilen Versiyon:** GroupDocs.Annotation 23.12 for .NET  
**Yazar:** GroupDocs  

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## İlgili Öğreticiler

- [GroupDocs.Annotation .NET Belge Yükleme](/annotation/net/document-loading-essentials/)
- [FTP'den Belgeleri .NET ile Nasıl Yüklenir - Tam GroupDocs Rehberi](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [Belge Önizleme .NET Öğreticileri - Tam GroupDocs.Annotation Rehberi](/annotation/net/document-preview/)
