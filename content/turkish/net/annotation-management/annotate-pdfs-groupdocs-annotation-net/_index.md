---
categories:
- PDF Processing
date: '2026-05-26'
description: GroupDocs Annotation for .NET kullanarak belge inceleme sisteminin nasıl
  oluşturulacağını öğrenin. Adım adım öğretici, kurulum, açıklama türleri, performans
  ayarı ve C# geliştiricileri için sorun giderme konularını kapsar.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Kılavuzu
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Belge İnceleme Sistemi Oluşturun: PDF Annotation .NET Kılavuzu'
type: docs
url: /tr/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Belge İnceleme Sistemi Oluşturma: PDF Açıklama .NET Kılavuzu

Eğer bir **belge inceleme sistemi oluşturma** istiyorsanız ve kullanıcıların .NET uygulamasından doğrudan PDF'lere yorum, vurgulama ve şekil eklemesini sağlamak istiyorsanız, doğru yerdesiniz. GroupDocs.Annotation for .NET, düşük seviyeli PDF işlemenin zorluklarını ortadan kaldırırken her açıklama türü üzerinde ince kontrol sağlar. Bu kılavuzda kütüphaneyi nasıl kuracağınızı, alan, elips ve metin açıklamaları eklemeyi, neyin kaydedileceğini filtrelemeyi ve çok sayfalı dosyalarda bile performansı hızlı tutmayı göreceksiniz.

## Hızlı Yanıtlar
- **.NET'te PDF açıklama işlemini hangi kütüphane yönetir?** GroupDocs.Annotation for .NET.  
- **Vurgulamaları, daireleri ve yorumları programlı olarak ekleyebilir miyim?** Evet – AreaAnnotation, EllipseAnnotation ve TextAnnotation nesnelerini kullanın.  
- **Üretim için lisans gerekli mi?** Geçerli bir GroupDocs lisansı, herhangi bir üretim dağıtımı için zorunludur.  
- **Ne kadar büyük bir PDF işlenebilir?** 500 MB'a kadar dosya, tüm dosyayı belleğe yüklemeden işlenebilir.  
- **Bu, bir belge inceleme sistemi oluşturmama yardımcı olur mu?** Kesinlikle – inceleyenler için toplu‑kaydetme, filtreleme ve sürümleme yapabilirsiniz.

## Belge inceleme sistemi nedir?
**Belge inceleme sistemi**, birden fazla paydaşın PDF dosyalarını koordine bir iş akışında açıklama, yorum ekleme ve onaylama yapmasını sağlayan bir yazılım çözümüdür. Geri bildirimleri merkezileştirir, değişiklikleri izler ve genellikle son onay için temiz bir sürüm dışa aktarır.

## Neden GroupDocs Annotation for .NET'i bir belge inceleme sistemi oluşturmak için kullanmalısınız?
GroupDocs Annotation, **30+ açıklama türünü** destekler, **500 MB**'a kadar PDF'leri işler ve **.NET Framework 4.6.1+**, **.NET Core 2.0+** ve **.NET 6+** üzerinde çalışır. API'si, PDF'nin iç yapısına dokunmadan açıklamaları eklemenize, kaldırmanıza ve filtrelemenize olanak tanır; bu da geliştirmeyi hızlandırır ve hataları azaltır.

## Önkoşullar ve Ortam Kurulumu

Kod yazmadan önce, geliştirme ortamınızın aşağıdaki kriterleri karşıladığından emin olun:

- **IDE:** Visual Studio 2019 ve üzeri veya C# uzantılı VS Code.  
- **Target Framework:** .NET Framework 4.6.1 + veya .NET Core 2.0 + (yeni projeler için .NET 6 önerilir).  
- **NuGet Erişimi:** nuget.org'dan paket kurma yeteneği.  
- **Örnek PDF'ler:** Açıklama yerleşimini test etmek için en az bir çok sayfalı PDF.  
- **Bellek ve Disk:** Minimum 4 GB RAM ve geçici dosyalar için yeterli boş disk alanı (açıklama işleme geçici akışlar oluşturabilir).

### Önerilen Geliştirme Uygulamaları
- Çözümünüzü kaynak kontrolünde (Git) tutun, böylece açıklama ile ilgili değişiklikleri geri alabilirsiniz.  
- Projenizde yapılandırma dosyalarını ve lisans anahtarlarını saklamak için özel bir **Annotations** klasörü kullanın.  
- **nullable reference types**'ı etkinleştirin (`<Nullable>enable</Nullable>`) böylece potansiyel null‑referans hatalarını erken yakalayabilirsiniz.

## Başlarken: GroupDocs.Annotation Kurulumu

### Kurulum Yöntemleri

**Seçenek 1: NuGet Paket Yöneticisi Konsolu**  
Paket Yöneticisi Konsolunda aşağıdaki komutu çalıştırın:  

`Install-Package GroupDocs.Annotation`

**Seçenek 2: .NET CLI (çapraz platform geliştirme için önerilir)**  
Bir terminalde çalıştırın:  

`dotnet add package GroupDocs.Annotation`

**Seçenek 3: Visual Studio Paket Yöneticisi UI**  
- Projeye sağ tıklayın → **Manage NuGet Packages**  
- **GroupDocs.Annotation** arayın  
- En son stabil sürümde **Install**'a tıklayın  

Üç yöntem de aynı ikiliyi kurar; iş akışınıza uyanı seçin.

### Lisans Yapılandırması

GroupDocs, üretim kullanımında geçerli bir lisans gerektirir. Üç seçeneğiniz var:

- **Ücretsiz Deneme:** Tam özellik setiyle 30‑günlük değerlendirme.  
- **Geçici Lisans:** Geliştirme ve test için genişletilmiş değerlendirme.  
- **Ticari Lisans:** Üretim ortamlarında sınırsız kullanım.

`License` sınıfı, tam işlevselliği etkinleştirmek için bir GroupDocs lisans dosyasını yükler ve uygular. Lisansı [GroupDocs purchase page](https://purchase.groupdocs.com/buy) adresinden edinebilirsiniz. `.lic` dosyasını aldıktan sonra, uygulamanızın okuyabileceği bir klasöre koyun ve `License` sınıfını başlangıçta ona yönlendirin.

### İlk Kurulum Doğrulaması

PDF'yi yükleyen ve sayfa sayısını konsola yazdıran küçük bir konsol programı oluşturun. Program bir istisna fırlatmadan çalışıyorsa, kütüphane doğru şekilde kurulmuş ve lisanslanmıştır.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Not:** Yukarıdaki kod sadece örnek amaçlıdır; final makaleye bir fenced code block eklemeniz **gerekmez**, ancak satır içi snippet tam API kullanımını gösterir.

Sayfa sayısı yazdırıldığını görürseniz, gerçek açıklamaları eklemeye hazırsınız.

## Temel Uygulama: PDF'lere Açıklama Ekleme

### Tanım Bağlantısı – Annotator

`Annotator` sınıfı, GroupDocs.Annotation for .NET'te tüm PDF açıklama işlemleri için giriş noktasıdır. PDF'yi belleğe yükler, açıklama ekleme, düzenleme ve alma yöntemlerini sunar ve değiştirilmiş belgeyi kaydetmeyi yönetir.

### Alan ve elips açıklamaları nasıl eklenir?

PDF'yi `new Annotator(...)` ile yükleyin, `AreaAnnotation` ve `EllipseAnnotation` nesnelerini oluşturun, koordinatlarını ayarlayın ve bunları annotator koleksiyonuna ekleyin. Son olarak, değişiklikleri kalıcı hale getirmek için `Save`'i çağırın. Bu iş akışı, bölümleri (alan) programlı olarak vurgulamanıza veya önemli grafikleri tek bir atomik işlemle daire içine almanıza olanak tanır.

#### Adım 1: Annotator'ı Başlat
```csharp
var annotator = new Annotator("input.pdf");
```

#### Adım 2: AreaAnnotation Oluştur
`AreaAnnotation`, PDF sayfasında dikdörtgen bir vurgulama alanını temsil eder.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Adım 3: EllipseAnnotation Oluştur
`EllipseAnnotation`, PDF sayfasında eliptik şekil açıklamasını temsil eder.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Adım 4: Açıklamaları Toplu Olarak Ekle
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Pro İpucu:** Açıklamaları bir listede toplayıp `Add`'i bir kez çağırmak, özellikle birçok sayfada düzinelerce işaret eklemeniz gerektiğinde I/O yükünü azaltır.

### Seçici açıklamaları nasıl kaydedilir?

`SaveOptions`, açıklamalı PDF'nin nasıl kaydedileceğini yapılandırır; hangi açıklama türlerinin dahil edileceğini de içerir. GroupDocs.Annotation, hangi açıklama türlerinin çıktı dosyasına yazılacağını filtrelemenizi sağlar. Bir `SaveOptions` örneği oluşturun, `AnnotationTypes` koleksiyonunu tutmak istediğiniz türlere ayarlayın ve seçenekleri `Save`'e geçirin. Bu, yalnızca inceleyenler için PDF'ler oluşturmak veya arşivlemeden önce geçici notları kaldırmak için mükemmeldir.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Gerçek Dünya Uygulama Senaryoları

### Senaryo 1: Belge İnceleme İş Akışı
Birden fazla inceleyen, **Area**, **Ellipse** ve **Text** açıklamaları ekler. İnceleme turundan sonra üç PDF oluşturursunuz:
1. Her yorumun bulunduğu tam sürüm.  
2. Yalnızca inceleyen sürümü (iç notları filtreler).  
3. Son onay için temiz sürüm (yalnızca vurgulamaları tutar).

### Senaryo 2: Otomatik Rapor Oluşturma
Arka ucunuz günlük satış raporlarını işler, ana metrikleri alan açıklamalarıyla otomatik olarak vurgular ve aykırı grafikleri elips açıklamalarıyla daire içine alır. Oluşturulan PDF'ler daha sonra paydaşlara manuel müdahale olmadan e-posta ile gönderilir.

### Senaryo 3: İşbirlikçi Hukuki Belgeler
Hukuk firmaları genellikle ortak yorumları genç asistan notlarından ayırmak zorundadır. Açıklamaları özel meta verilerle etiketleyerek ve seçici kaydetme kullanarak, genç notları gizleyen bir ortak‑inceleme PDF'si üretebilir, sürüm kontrolünü basitleştirebilirsiniz.

## Üretim Kullanımı için Performans Optimizasyonu

### Büyük PDF'lerde açıklama yaparken belleği nasıl yönetirsiniz?
`LoadOptions`, bir PDF'nin nasıl yükleneceğini (sayfa aralıkları veya şifreler gibi) belirtmenizi sağlar. PDF 100 MB'ı aştığında, sayfa aralığını kabul eden `LoadOptions` yapıcıyı kullanarak tüm dosyayı yüklemekten kaçının. Sayfaları toplu olarak işleyin, her `Annotator` örneğini bir `using` bloğu ile serbest bırakın ve her toplu işlemden sonra geçici dosyaları temizleyin. Bu yaklaşım, 500 sayfalık belgeler için bile en yüksek bellek kullanımını 200 MB altında tutar.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Bellek Yönetimi En İyi Uygulamaları
- **Her zaman `Annotator`'ı bir `using` ifadesi içinde sarın**; bu, yönetilmeyen kaynakların serbest bırakılmasını garanti eder.  
- **Açıklamaları toplu işleyin**: bir belge için tüm açıklamaları toplayın, ardından `Add`'i bir kez çağırın.  
- **Tam PDF'leri yüklemekten kaçının**; yalnızca sayfa alt kümesini değiştirmeniz gerektiğinde `LoadOptions.PageNumbers` kullanın.

### Büyük Dosya İşleme Stratejileri
1. **Sayfa bazlı işleme** – Bir seferde bir sayfayı yükleyin, açıklama ekleyin ve kaydedin.  
2. **Akış çıkışı** – `Save` metodunu bir `MemoryStream`'e yönlendirerek ara disk yazmalarını önleyin.  
3. **Geçici dosya temizliği** – Her işlemden sonra annotator tarafından oluşturulan geçici dosyaları silin.

### Eşzamanlı İşleme Dikkat Edilmesi Gerekenler
- **İş parçacığı güvenliği:** `Annotator` örnekleri iş parçacığı güvenli değildir. Her iş parçacığı için ayrı bir örnek oluşturun.  
- **Kaynak sınırlaması:** CPU çekirdek sayısına göre eşzamanlı işleri sınırlayın; bu, CPU aşırı yüklenmesini önler.  
- **Async API:** `SaveAsync`, açıklamalı belgeyi asenkron olarak kaydeder ve bir Task döndürür; bu, ASP.NET Core ortamlarında faydalıdır.

## Yaygın Sorunların Giderilmesi

### Sorun 1: “Dosya Bulunamadı” hataları
**Doğrudan cevap:** `new Annotator(...)`'a gönderdiğiniz dosya yolunun mutlak ya da çalışan derlemeye göre doğru göreceli olduğundan emin olun ve uygulama sürecinin o konumda okuma iznine sahip olduğundan emin olun. Dosya bir ağ paylaşımında bulunuyorsa, paylaşımı eşleyin veya UNC yollarını kullanın.

**Tipik çözümler:**  
- `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")` kullanın.  
- IIS uygulama havuzu kimliğine klasörde okuma/yazma izinleri verin.

### Sorun 2: Açıklamalar yanlış konumlarda görünüyor
**Doğrudan cevap:** Aynı koordinat sistemini (sol‑üst köken) kullandığınızdan ve sayfanın DPI'sının sağladığınız değerlerle eşleştiğinden emin olun. Sayfa boyutunu `annotator.GetPageInfo(pageNumber)` ile alın ve koordinatları bu boyuta göre hesaplayın.

**Tipik çözümler:**  
- PDF standart dışı DPI ile oluşturulmuşsa, koordinatları sayfanın ölçek faktörüyle çarpın.  
- Nokta (1/72 inç) ile piksel karıştırmadığınızdan emin olun.

### Sorun 3: Büyük dosyalarda performans sorunları
**Doğrudan cevap:** Sayfa aralıklı yüklemeye geçin, açıklamaları toplu işleyin ve her `Annotator` örneğini hızlıca serbest bırakın. Ayrıca `LoadOptions` içinde `MemoryCache` seçeneğini etkinleştirerek tamponları işlemler arasında yeniden kullanın.

**Tipik çözümler:**  
- `LoadOptions.UseMemoryCache = true` olarak ayarlayın.  
- Dosyaları `await annotator.SaveAsync(...)` ile asenkron işleyin.

### Sorun 4: Lisansla ilgili hatalar
**Doğrudan cevap:** `.lic` dosyasını uygulamanın okuyabileceği bir klasöre koyun ve diğer GroupDocs çağrılarından önce `License license = new License(); license.SetLicense("path/to/license.lic");` kodunu çalıştırın. Lisans sürümünün kullandığınız kütüphane sürümüyle eşleştiğini doğrulayın.

**Tipik çözümler:**  
- Lisans dosyasının bozuk olmadığını kontrol edin (dosya boyutunu karşılaştırın).  
- Aynı ortamda deneme lisansını ticari lisansla karıştırmadığınızdan emin olun.

## İleri Düzey İpuçları ve En İyi Uygulamalar

### Renk Yönetimi
Tutarlı renkler, inceleyenlerin okunabilirliğini artırır. Bir palet tanımlayın (örneğin, vurgulamalar için Sarı, kritik sorunlar için Kırmızı) ve bunu statik bir yardımcı sınıfta saklayın. Erişilebilirlik için yüksek kontrastlı renkler kullanmayı ve referans için PDF'ye bir lejand sayfası eklemeyi unutmayın.

### Hata Yönetimi Desenleri
Tüm açıklama çağrılarını, özellikle `GroupDocs.Annotation.Exceptions.AnnotationException` yakalayan try‑catch blokları içinde sarın. Hata mesajını, yığın izini ve PDF adını kaydedin; bu, hata ayıklamaya yardımcı olur.

### Test Stratejileri
- **Birim Testleri:** Bilinen boyutlarda küçük bir PDF kullanın, bir açıklama ekleyin ve `GetAnnotations()`'ın beklenen koordinatları döndürdüğünü doğrulayın.  
- **Entegrasyon Testleri:** 1 sayfadan 200 sayfaya kadar PDF'lerde tam iş akışını çalıştırın ve 50 MB altındaki dosyalar için işleme süresinin 5 saniyenin altında kalmasını doğrulayın.  
- **Yük Testleri:** k6 veya Apache JMeter gibi bir araçla 50 eşzamanlı açıklama isteği simüle edin ve CPU/bellek kullanımını izleyin.

## Sık Sorulan Sorular

**S: Farklı sayfa boyutlarına sahip PDF'leri nasıl yönetirim?**  
C: GroupDocs, her sayfanın boyutlarını otomatik olarak okur. Açıklamaları konumlandırırken, her zaman `annotator.GetPageInfo(pageNumber)` sorgulayın ve koordinatları o sayfanın genişliği ve yüksekliğine göre hesaplayın.

**S: Şifre korumalı PDF'lere açıklama ekleyebilir miyim?**  
C: Evet. Şifre dizesini kabul eden `LoadOptions` yapıcısını kullanın, örneğin `new LoadOptions { Password = "secret" }`, ve bunu `Annotator` yapıcısına geçirin.

**S: Tek bir PDF'ye ekleyebileceğim maksimum açıklama sayısı nedir?**  
C: Katı bir limit yoktur, ancak birkaç bin açıklamadan sonra performans düşer. Çok büyük açıklama setleri için, bunları mantıksal bölümlere ayırın ve her bölümü ayrı ayrı işleyin.

**S: Belirli açıklamaları programlı olarak nasıl kaldırırım?**  
C: Açıklamanın `Id`'sini `GetAnnotations()` ile alın, ardından `Delete(id)` çağırın veya istenmeyen `AnnotationType`'ı dışlayan bir `SaveOptions` örneği oluşturun.

**S: Renklerin ötesinde açıklama görünümünü özelleştirebilir miyim?**  
C: Kesinlikle. Opaklık, kenar kalınlığı, kesikli stil ve hatta damga açıklamaları için özel SVG simgeleri ekleyebilirsiniz.

**S: Tarama (görüntü‑tabanlı) bir PDF'ye açıklama eklemeye çalışırsam ne olur?**  
C: Açıklamalar, sayfa görüntüsünün üzerine bir katman nesnesi olarak işlenecek. Alt raster veriyi değiştirmezler, bu yüzden OCR katmanları varsa PDF aranabilir kalır.

**S: Çok büyük PDF'leri bellek tükenmeden nasıl yönetirim?**  
C: Belgeyi `LoadOptions.PageNumbers` kullanarak sayfa sayfa işleyin, her `Annotator` örneğini kullanım sonrası hemen serbest bırakın ve disk ani artışlarını önlemek için `MemoryStream`'e akış kaydetmeyi etkinleştirin.

## ASP.NET Uygulamalarıyla Entegrasyon

Bir web API aracılığıyla açıklama işlevselliğini dışa açtığınızda, aşağıdaki modeli izleyin:

1. **Controller, istemciden PDF akışını alır.**  
2. **Dosya boyutunu doğrular** (200 MB'den büyükse özel bir işlem yoksa reddeder).  
3. **`Annotator`'ı bir `using` bloğu içinde örnekler**; bu, serbest bırakmayı garanti eder.  
4. **Açıklamaları uygular**; JSON yükü açıklama türünü, koordinatları ve metni tanımlar.  
5. **Geçici bir konuma kaydeder**, ardından sonucu uygun `Content‑Disposition` başlığıyla istemciye akıtır.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Ek Kaynaklar
- [GroupDocs satın alma sayfası](https://purchase.groupdocs.com/buy)  
- [GroupDocs satın al](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation Dokümantasyonu](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API Referansı](https://reference.groupdocs.com/annotation/net/)  
- [En Son Sürümler](https://releases.groupdocs.com/annotation/net/)  
- [GroupDocs'ı Ücretsiz Deneyin](https://releases.groupdocs.com/annotation/net/)  
- [Geçici Lisans İste](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

## Sonuç ve Sonraki Adımlar

Artık GroupDocs.Annotation for .NET ile güçlendirilmiş bir **belge inceleme sistemi** oluşturmak için **tam, üretim‑hazır bir yol haritasına** sahipsiniz. Kütüphaneyi kurmayı, alan, elips ve metin açıklamaları eklemeyi, kaydetme filtrelerini kullanmayı ve büyük PDF'lerde bile bellek kullanımını düşük tutmayı öğrendiniz.

**Bugün yapabileceğiniz sonraki adımlar:**

1. `ArrowAnnotation` ve `StampAnnotation` gibi ek açıklama türleriyle **deney** yapın.  
2. İş akışını mevcut ASP.NET Core API'nize veya masaüstü WPF uygulamanıza **entegre** edin.  
3. Açıklama sürümleme ve özel meta veri gibi gelişmiş özellikleri keşfetmek için tam API referansını **inceleyin**.  
4. Yeni sürümlerden haberdar olmak ve eş eş destek almak için GroupDocs topluluk forumlarına **katılın**.

---

**Son Güncelleme:** 2026-05-26  
**Test Edilen Versiyon:** GroupDocs.Annotation 23.11 for .NET  
**Yazar:** GroupDocs  

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## İlgili Eğitimler

- [GroupDocs Annotation .NET Eğitimi - Belge Yönetimi için Tam Kılavuz](/annotation/net/annotation-management/)  
- [Document Preview .NET Eğitimleri - Tam GroupDocs.Annotation Kılavuzu](/annotation/net/document-preview/)  
- [GroupDocs Annotation Ölçülen Lisans Eğitimi - Tam .NET Kurulum Kılavuzu](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)