---
categories:
- Java PDF Processing
date: '2026-05-21'
description: GroupDocs kullanarak Java'da PDF'lere strikeout annotations eklemeyi
  öğrenin. Bu adım adım öğretici, kurulum, kod, sorun giderme ve performans ipuçlarını
  kapsar.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF Metin Strikeout Rehberi
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Java'da PDF'lere strikeout annotations eklemek – Tam GroupDocs Rehberi
type: docs
url: /tr/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# PDF'lerde Java ile Üstü Çizili Açıklamaları Nasıl Eklenir

PDF'de metni programlı olarak üstü çizmek gerektiğinde? İster bir belge inceleme sistemi oluşturuyor olun, ister bir düzenleme iş akışı kuruyor olun ya da sadece metni silmek için işaretlemeniz gereksin, **üstü çizme** açıklamaları Java'da pratik bir beceridir ve zaman tasarrufu sağlar, manuel çabayı azaltır. Bu kapsamlı rehberde, proje kurulumundan performans ayarına kadar GroupDocs.Annotation for Java ile üstü çizili açıklamaları nasıl uygulayacağınızı öğreneceksiniz.

## Hızlı Yanıtlar
- **İlk adım nedir?** GroupDocs.Annotation Maven bağımlılığını `pom.xml` dosyanıza ekleyin.  
- **Üstü çizme nasıl oluşturulur?** `Annotator` sınıfını örnekleyin, `StrikeoutAnnotation`'ı noktalarla tanımlayın, renk/opaklık ayarlayın, ardından `addAnnotation` metodunu çağırın.  
- **Yorum ekleyebilir miyim?** Evet, iş birliği için bir `Comment` nesnesini açıklamaya ekleyin.  
- **Açıklama yanlış konumda olursa ne olur?** Koordinat noktalarını ayarlayın; PDF alt‑sol köken sistemini kullanır.  
- **Belge boyutu için bir limit var mı?** GroupDocs, tüm dosyayı belleğe yüklemeden çok sayfalı PDF'leri işler.

## PDF Açıklamasında “üstü çizme ekleme” nedir?
“üstü çizme ekleme” ifadesi, bir PDF belgesi içinde seçili metnin üzerinden programlı olarak bir çizgi çizmeyi sağlayan bir açıklama API'si sürecini tanımlar. Java’da GroupDocs.Annotation, üstü çizgi işaretlerinin oluşturulması, stillendirilmesi ve kalıcılığını yöneten özel bir `StrikeoutAnnotation` sınıfı sunar.

## Java PDF Üstü Çizme için GroupDocs Neden Kullanılmalı?
GroupDocs.Annotation **50+ giriş ve çıkış formatını** destekler—PDF, DOCX, XLSX, PPTX, HTML ve yaygın görüntü türleri dahil—bu sayede tek bir dosya tipine bağlı kalmazsınız. Düşük‑seviye PDF yapısını soyutlayan yüksek‑seviye bir API sağlar, font gömme, sayfa renderlama ve açıklama kalıcılığını otomatik olarak yönetir; böylece geliştiriciler iş mantığına odaklanır, PDF iç detaylarıyla uğraşmaz.

## Önkoşullar ve Kurulum Gereksinimleri

### Temel Gereksinimler
- **Java Development Kit (JDK):** Versiyon 8 veya üzeri (optimum çöp toplama için JDK 11+ önerilir).  
- **GroupDocs.Annotation for Java:** Maven aracılığıyla entegre edilir (aşağıdaki Maven kod bloğuna bakın).  
- **IDE:** IntelliJ IDEA, Eclipse veya herhangi bir Java‑uyumlu editör.

### Maven Bağımlılıkları Kurulumu
`pom.xml` dosyanıza aşağıdaki bağımlılık bloğunu ekleyin:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/annotation/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

**Pro Tip:** En yeni sürümü her zaman GroupDocs sürüm sayfasından kontrol edin; yeni sürümler özellik ekler ve açıklama renderını etkileyebilecek hataları düzeltir.

### Lisansınızı Alın
GroupDocs.Annotation, üretim kullanımı için geçerli bir lisans gerektirir. Üç seçeneğiniz var:

- **Ücretsiz Deneme:** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/) adresinden indirin.  
- **Geçici Lisans:** [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/) adresinden bir geliştirme anahtarı talep edin.  
- **Tam Lisans:** Üretim için [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) üzerinden satın alın.

Deneme sürümü hafif bir filigran ekler, bu yüzden test planınızı buna göre yapın.

## Adım‑Adım Uygulama Kılavuzu

### Temel Bileşenleri Anlamak
Aşağıdaki tanımlar size hızlı bir zihinsel model sunar:

- **Annotator:** PDF'yi yükleyen ve açıklama metodlarını ortaya çıkaran temel API nesnesi.  
- **StrikeoutAnnotation:** Görsel üstü çizgi ve stil seçeneklerini temsil eder.  
- **Point:** Çizginin başlangıç ve bitiş noktalarını belirten (X, Y) koordinat çifti.  
- **Comment:** İş birliği için açıklamaya eklenebilen isteğe bağlı metin.

### Adım 1: Dosya Yollarını Ayarlama
Kaynak PDF'nizin ve hedef dosyanızın konumlarını tanımlayın. Yanlış yollar “File Not Found” hatalarının yaygın bir kaynağıdır.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Çıktı klasörünün var olduğundan ve yazılabilir olduğundan emin olun; GroupDocs eksik klasörleri otomatik oluşturmaz.

### Adım 2: Annotator'ı Başlatma
PDF'yi belleğe yükleyen bir `Annotator` örneği oluşturun.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** Kütüphane PDF yapısını ayrıştırır, dahili bir temsil oluşturur ve sayfa bazlı bir açıklama kanvası hazırlar. Çok sayfalı dosyalarda bu adım birkaç saniye sürebilir.

### Adım 3: Yorum Ekleme (İsteğe Bağlı ama Önerilir)
`Comment`, bir açıklamaya eklenen metinsel notu temsil eder; iş birliği yapanların üstü çizme nedenini açıklamasına olanak tanır.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Yorumları, metnin neden kaldırıldığını açıklamak için kullanın—bu, özellikle hukuki veya editöryel inceleme iş akışlarında faydalıdır.

### Adım 4: Açıklama Koordinatlarını Tanımlama
`Point` nesneleri, bir PDF sayfasındaki açıklamanın tam konumunu tanımlayan X‑Y koordinat çiftlerini saklar.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF koordinatları alt‑sol köşeden (0,0) başlar. Örnek, hedef sayfada (80,730) ile (240,730) arasında yatay bir çizgi oluşturur.

**Finding the Right Coordinates:** Birçok geliştirici, sayfa genişliği/yüksekliğinin yüzdelerini mutlak noktalara dönüştüren bir yardımcı fonksiyon yazar; bu sayede kod farklı sayfa boyutlarına karşı dayanıklı olur.

### Adım 5: Üstü Çizili Açıklama Oluşturma
`StrikeoutAnnotation`, görsel çizgiyi, renk ve opaklık gibi stil özelliklerini ve üstü çizgi işaretiyle ilişkili meta verileri kapsar.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** `fontColor` ondalık RGB değerleri kullanır (ör. parlak sarı için 65535). Marka renkleri gerekiyorsa çevrimiçi bir dönüştürücü kullanın.

**Opacity Recommendation:** `0.7` ( %70 ) opaklık, alt metni okunabilir tutarken net bir görsel ipucu sağlar.

### Adım 6: Açıklamayı Uygulama
`addAnnotation`, hazırlanan açıklamayı belgeye kaydeder; böylece render edilip kaydedilir.

```java
annotator.add(strikeout);
```

### Adım 7: Kaydetme ve Temizleme
`dispose()` yöntemi, `Annotator` örneği tarafından tutulan yerel kaynakları serbest bırakır; işlem tamamlandığında bellek sızıntılarını önler.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** `dispose()` çağrısı yerel kaynakları serbest bırakır ve PDF toplu işleme sırasında bellek sızıntılarını engeller.

## Yaygın Sorunlar ve Çözüm Yolları

### Sorun 1: “File Not Found” Hataları
**Symptoms:** `Annotator` oluşturulurken istisna fırlatılır.  
**Solution:** Giriş ve çıkış yollarını doğrulayın, uygulamanın okuma/yazma izinlerine sahip olduğundan emin olun.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Sorun 2: Üstü Çizili Açıklama Yanlış Konumda Görünüyor
**Symptoms:** Çizgi, hedef metinle hizalanmaz.  
**Solution:** PDF Y‑koordinatlarının yukarı doğru arttığını unutmayın. Görsel hata ayıklama aracı kullanın veya sayfa boyutlarını yazdırarak noktaları ince ayar yapın.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Sorun 3: Açıklama Görünmüyor
**Symptoms:** Kaydetme sonrası üstü çizgi görünmez.  
**Possible Causes & Fixes:**  
- **Opacity too low:** Görünürlüğü doğrulamak için opaklığı geçici olarak `1.0` yapın.  
- **Color blending:** Kırmızı (`255`) gibi yüksek kontrastlı bir renk kullanın.  
- **Incorrect page index:** Sayfa numaraları sıfır‑tabanlıdır; doğru sayfayı hedeflediğinizden emin olun.

### Sorun 4: Büyük Dosyalarda Bellek Sorunları
**Symptoms:** `OutOfMemoryError` veya yavaş performans.  
**Solutions:**  
- Belgeleri daha küçük partilerde işleyin.  
- Mevcutsa streaming API'yi kullanın.  
- Her belge işleminden sonra daima `dispose()` çağırın.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Gerçek Dünya Uygulamaları ve Kullanım Senaryoları

### Hukuki Belge İncelemesi
Hukuk firmaları, silinen maddeleri göstermek için sözleşmelere üstü çizgi ekler; aynı zamanda denetim izini korur.

### Akademik Makale Düzenleme
Profesörler, hakem incelemesi sırasında kaldırma önerileri için üstü çizgiler kullanır; orijinal metin bağlam için görünür kalır.

### İçerik Yönetim Sistemleri
Yayın platformları, manuel denetimden önce politika ihlali bölümlerini otomatik olarak üstü çizgiyle işaretler.

### Belgeler İçin Versiyon Kontrolü
Kurumsallar, üstü çizgi açıklamalarını belge‑merkezli bir versiyon kontrol iş akışında “silme işaretleri” olarak ele alır; kod farklarına benzer.

## Performans Optimizasyon İpuçları

### Toplu İşleme Stratejisi
Birçok PDF işlenirken, mümkün olduğunca tek bir `Annotator` örneği yeniden kullanın ve dosyaları paralel iş parçacıklarında işleyin.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Bellek Yönetimi En İyi Uygulamalar
- Her `Annotator` için `dispose()` çağırın.  
- Yığın baskısını önlemek için eşzamanlı belge yüklemelerini sınırlayın.  
- VisualVM gibi araçlarla JVM bellek kullanımını izleyin.

### Koordinat Önbellekleme
Aynı açıklama düzenini birden çok dosyada uyguluyorsanız, `Point` nesnelerini önbelleğe alarak yeniden hesaplamayı önleyin.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Gelişmiş Özelleştirme Seçenekleri

### Dinamik Renk Seçimi
İş kurallarına göre (ör. kritik silmeler için kırmızı, geçici silmeler için sarı) çalışma zamanında renk seçin.

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Çok Satırlı Üstü Çizgiler
Birden fazla `Point` çifti oluşturarak metnin birkaç satırını kesen zig‑zag bir çizgi çizin.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Sorun Giderme Kontrol Listesi
1. **File Permissions:** Okuma/yazma erişimini doğrulayın.  
2. **Library Version:** Desteklenen bir GroupDocs.Annotation sürümü kullandığınızdan emin olun.  
3. **License Status:** Lisans dosyasının doğru referans edildiğini onaylayın.  
4. **PDF Compatibility:** PDF'nin bozuk olmadığını ve desteklenen boyut limitleri içinde olduğunu kontrol edin.  
5. **Coordinate Validation:** Tüm noktaların sayfa sınırları içinde olduğundan emin olun.  
6. **Heap Space:** Çok büyük dosyalar işliyorsanız JVM `-Xmx` değerini artırın.

## Sıkça Sorulan Sorular

**S: Birden fazla satırda metni üstü çizebilir miyim?**  
C: Evet. İstenen yolu izleyen birkaç `Point` nesnesi oluşturun; açıklama sağlanan çokgen çizgiyi takip eder.

**S: Koordinatları sayfa sınırlarının dışına belirlersem ne olur?**  
C: Açıklama kırpılır ve görünmez hale gelebilir. Koordinatları her zaman sayfanın genişliği ve yüksekliğiyle karşılaştırarak doğrulayın.

**S: Ekledikten sonra üstü çizgi açıklamalarını kaldırabilir miyim?**  
C: Kesinlikle. `removeAnnotation` metodunu açıklamanın ID'siyle ya da türüne göre filtreleyerek programatik olarak silin.

**S: Tek bir PDF'ye kaç açıklama ekleyebileceğimde bir limit var mı?**  
C: GroupDocs katı bir sınır koymaz, ancak binlerce açıklama sonrası performans düşebilir. Çok büyük setler için sayfalama veya özetleme düşünün.

**S: Şifre korumalı PDF'lerle nasıl çalışırım?**  
C: Şifreyi `Annotator` yapıcısına geçirin. Kütüphane, açıklamaları uygulamadan önce belgeyi bellekte çözer.

**S: Farklı sayfa boyutları ve yönelimlerine sahip PDF'leri nasıl yönetirim?**  
C: `annotator.getPageInfo(pageNumber)` ile her sayfanın boyutlarını alın ve koordinatları bu boyutlara göre hesaplayarak tutarlı yerleştirme sağlayın.

## Sonuç
Artık GroupDocs.Annotation kullanarak Java’da PDF’lere **üstü çizme** açıklamaları eklemek için eksiksiz, üretim‑hazır bir çözüme sahipsiniz. Dosya yolu yönetimi, koordinat hesaplaması ve kaynak yönetimini ustalıkla ele alarak bu yeteneği belge inceleme araçlarına, içerik hatlarına veya kesin görsel geri bildirim gerektiren herhangi bir Java‑tabanlı uygulamaya entegre edebilirsiniz.

**Next Steps**
1. Örnek projeyi klonlayın ve bir örnek PDF üzerinde çalıştırın.  
2. Farklı renkler, opaklıklar ve yorum metinleriyle deneyler yapın.  
3. Açıklama iş akışını mevcut belge‑işleme servisinize entegre edin.  
4. İlgili diğer açıklama türlerini keşfedin—vurgulamalar, yapışkan notlar ve şekil açıklamaları—PDF manipülasyon araç setinizi genişletin.

Daha fazlasına hazır mısınız? Daha derin API içgörüleri için resmi dokümantasyona dalın.

## Ek Kaynaklar

- [GroupDocs dokümantasyonu](https://docs.groupdocs.com/annotation/java/) - GroupDocs kütüphaneleri için genel dokümantasyon  
- [GroupDocs.Annotation Dokümantasyonu](https://docs.groupdocs.com/annotation/java/) - Tam API referansı  
- [API Referans Kılavuzu](https://reference.groupdocs.com/annotation/java/) - Metot‑metot detaylar  
- [En Son Sürümü İndir](https://releases.groupdocs.com/annotation/java/) - Kütüphanenizi güncel tutun  
- [Lisans Satın Al](https://purchase.groupdocs.com/buy) - Üretim‑hazır lisanslama  
- [Ücretsiz Deneme İndir](https://releases.groupdocs.com/annotation/java/) - Satın almadan değerlendirin  
- [Geçici Lisans Talebi](https://purchase.groupdocs.com/temporary-license/) - Geliştirme testi  
- [Destek Forumu](https://forum.groupdocs.com/c/annotation/) - Topluluk yardımı ve resmi destek  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## İlgili Eğitimler

- [PDF Açıklama Ekle Java – Tam GroupDocs Kılavuzu](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Açıklama Eğitimi - PDF'leri Vurgulama İçin Tam Kılavuz](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [Java’da PDF’ye Ok Eklemek – Tam GroupDocs Eğitimi](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)