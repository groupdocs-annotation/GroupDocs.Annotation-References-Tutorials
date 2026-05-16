---
categories:
- Java Development
date: '2026-05-16'
description: GroupDocs.Annotation kullanarak java ile açıklama yanıtları oluşturmayı
  öğrenin. Java'da PDF açıklamaları konusunda pratik örnekler, performans ipuçları
  ve en iyi uygulamalarla uzmanlaşın.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF Annotation Öğreticisi
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Java PDF Annotation Library: java ile açıklama yanıtı oluşturma'
type: docs
url: /tr/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF Açıklama Kütüphanesi: create annotation reply java

If you need to **create annotation reply java** for PDFs—whether you’re building a contract‑review portal, an e‑learning system, or a bulk‑processing pipeline—this guide shows you exactly how to do it with GroupDocs.Annotation for Java. We’ll walk through setup, squiggly annotation creation, reply threading, and performance tuning so you can ship a reliable solution in days, not weeks.

## Hızlı Yanıtlar
- **GroupDocs.Annotation'ın birincil amacı nedir?** Java'da PDF açıklamalarının programatik olarak oluşturulmasını, değiştirilmesini ve çıkarılmasını sağlar.  
- **Bir squiggly açıklama nasıl eklenir?** `SquigglyAnnotation` sınıfını örnekleyin, geometrisini ve stilini ayarlayın, ardından `annotator.add(...)` metodunu çağırın.  
- **Bir açıklamaya yanıt ekleyebilir miyim?** Evet—`Reply` nesneleri oluşturun, yazar ve metni ayarlayın ve bunları üst açıklama ile ilişkilendirin.  
- **Üretim için lisansa ihtiyacım var mı?** Kesinlikle; geçerli bir lisans olmadan çıktı su işareti içerir.  
- **Toplu işleme uygun mu?** Evet—her belgeyi açmak, açıklama eklemek ve kapatmak için try‑with‑resources kullanın, böylece bellek kullanımı düşük kalır.

## Java Geliştiricilerinin PDF Açıklama Kütüphanelerine Neden İhtiyacı Var

PDF'leri manuel olarak işaretlemek zaman alıcı ve hata yapmaya açıktır, özellikle yüzlerce sözleşme veya sınav kağıdını incelemeniz gerektiğinde. Bir Java PDF açıklama kütüphanesi bu işi otomatikleştirir, vurgular, dalgalı alt çizgiler ve dizili yorumları doğrudan dosyaya yerleştirmenizi sağlar. Sonuç, tüm işaretlemeleri ayrı bir görüntüleyiciye ihtiyaç duymadan koruyan, aranabilir ve taşınabilir bir belgedir.

**Bu kılavuzda öğrenecekleriniz**
- Maven projesinde GroupDocs.Annotation'ı kurma ve lisanslama
- Yerel Word alt çizgilerine benzeyen squiggly açıklamaları oluşturma
- İşbirlikçi inceleme için herhangi bir açıklamaya dizili yanıtlar ekleme
- Büyük PDF'leri işlerken bellek ve CPU kullanımını optimize etme
- Çözümü Spring Boot, mikro‑servisler veya masaüstü uygulamalarda dağıtma  

İster bir hukuk belgesi inceleme sistemi, ister eğitim notlandırma aracı, ister otomatik kalite‑kontrol hattı oluşturuyor olun, aşağıdaki teknikler size üretime hazır bir temel sağlayacaktır.

## create annotation reply java nedir?

`create annotation reply java`, Java kullanarak mevcut bir PDF açıklamasına bir yorum dizisi (Reply) ekleme programatik sürecidir. Yanıtlar, birden fazla inceleyicinin belgeyi terk etmeden belirli bir işaretleme üzerinde tartışmasına olanak tanır, sorunsuz ve yerinde işbirliği sağlar. Bu özellik, statik bir PDF'yi dosya içinde doğrudan bağlam ve denetim izlerini koruyan etkileşimli bir tartışma platformuna dönüştürür.

## Önkoşullar: Ortamınızı Hazırlama

Koda geçmeden önce, geliştirme istasyonunuzun bu gereksinimleri karşıladığını doğrulayın:

- **JDK** 8 veya üzeri (daha iyi çöp toplama performansı için JDK 11 + önerilir)  
- **Maven** veya **Gradle** bağımlılık yönetimi için (örnekler Maven kullanır)  
- Maven desteği olan bir IDE (IntelliJ IDEA, Eclipse veya VS Code)  
- IDE ve test çalıştırmaları için en az **2 GB** boş RAM  
- Deneyim için örnek PDF dosyaları (herhangi bir PDF editörüyle basit PDF'ler oluşturabilirsiniz)

GroupDocs.Annotation tamamen süreç içinde çalışır; harici PDF görüntüleyicileri veya yerel kütüphaneler gerekmez.

## GroupDocs.Annotation for Java Kurulumu

Kütüphaneyi entegre etmek birkaç adımlı bir süreçtir, ancak gözden kaçırılan birkaç gizli tuzak çalışma zamanı hatalarına yol açabilir.

### Maven Bağımlılık Yapılandırması

`pom.xml` dosyanıza depoyu ve bağımlılığı ekleyin. Maven'in artefakti çözebilmesi için `<repositories>` öğesini **<dependencies>**'den **önce** yerleştirin.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **Pro ipucu:** En son sürüm için GroupDocs sürüm sayfasını kontrol edin. Yeni sürümler genellikle yeni PDF standartları desteği ve performans iyileştirmeleri içerir.

### Lisans Kurulumu (Bunu Atlamayın!)

GroupDocs.Annotation üretim kullanımı için bir lisans dosyası gerektirir. Lisans olmadan, oluşturulan her PDF su işareti içerir.

- **Ücretsiz Deneme** – 30 gün için tam özellik seti, değerlendirme için ideal.  
- **Geçici Lisans** – Geliştirme ve iç testler için uygundur.  
- **Tam Lisans** – Herhangi bir ticari dağıtım için gereklidir.  

`GroupDocs.Annotation.lic` dosyasını resources klasörünüze yerleştirin ve başlangıçta yükleyin:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Yaygın tuzak:** Lisans adımını unutmak su işaretli PDF'lere ve sessizce başarısız olan API çağrılarına yol açar. Başlangıç rutininizde lisansı her zaman erken doğrulayın.

## Tam Uygulama Kılavuzu: Squiggly Açıklamaları Ekleme

Aşağıda, bir squiggly açıklama oluştururken **create annotation reply java** nasıl yapılacağını gösteren adım‑adım bir rehber bulunmaktadır. Her adım, her satırın “neden”ini anlamanız için kısa bir açıklama içerir.

### Adım 1: Gerekli Tüm Sınıfları İçe Aktarın

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` belge‑seviyesindeki tüm işlemler için giriş noktasıdır.  
- `Point` bir sayfadaki koordinatı temsil eder (X ve Y üst‑sol köşeden ölçülür).  
- `SquigglyAnnotation` hataları vurgulamak için kullanılan dalgalı alt çizgiyi tanımlar.  
- `Reply` bir açıklamaya eklenen dizili yorumları saklar.  
- `SaveOptions` çıktı formatını ve sıkıştırmayı kontrol etmenizi sağlar.

### Adım 2: Squiggly Açıklamanızı Oluşturun ve Yapılandırın

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation, PDF'de hataları vurgulamak için kullanılan dalgalı bir alt çizgi oluşturan bir sınıftır.

- **Koordinat sistemi**: Noktalar üst‑sol köşeden başlar. Yukarıdaki iki nokta (100, 200) ile (300, 200) arasında yatay bir dalgalı çizgi çizer.  
- **Opacity** 0.7, açıklamanın %70 opak olduğu ve altındaki metnin okunabilir kalmasını sağlar.

### Adım 3: Etkileşimli Yanıtlar Ekleyin (İsteğe Bağlı ama Güçlü)

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

Reply, bir açıklamaya eklenen yorum dizisini temsil eden bir sınıftır.

- Yanıtlar, açıklama üzerinde doğrudan **dizili bir tartışma** oluşturur, modern PDF inceleyicilerinin deneyimini yansıtır.  
- Her yanıt yazar bilgisi ve zaman damgası saklar; bunları daha sonra bir UI'de filtreleyebilir veya görüntüleyebilirsiniz.

### Adım 4: Açıklamayı Uygulayın ve Belgeyi Kaydedin

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- **try‑with‑resources** yapısı, `Annotator`'ı otomatik olarak kapatır, dosya tutamaçlarını ve yerel tamponları serbest bırakır.  
- `save`, değiştirilmiş PDF'yi `output.pdf` dosyasına yazar.  

> **Bellek notu:** `Annotator` yalnızca dokunduğunuz sayfaları yükler. Çok sayfalı PDF'lerde bu yaklaşım, tipik bir sunucuda yığın kullanımını 150 MB'nin altında tutar.

## Gelişmiş Yapılandırma Seçenekleri

### Açıklama Görünümünü Özelleştirme

Görsel stili marka yönergelerinize uyacak şekilde ince ayar yapabilirsiniz:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** çizgi kalınlığını (point cinsinden) kontrol eder.  
- **ARGB** formatu, şeffaflık için alfa kanalını içerir.

### Açıklamaları Hassas Bir Şekilde Konumlandırma

Farklı sayfa boyutlarına sahip PDF'lerde koordinatları doğru almak zor olabilir. Bu sistematik yaklaşımı izleyin:

1. **PDF'yi bir görüntüleyicide açın** (ör. Adobe Acrobat) ve hedef alan için cetvel değerlerini not alın.  
2. **Cetvel değerlerini** point'e çevirin (1 point = 1/72 inç).  
3. `annotator.getPageInfo(pageIndex)` kullanarak sayfa genişliğini ve yüksekliğini alın, ardından göreli konumları hesaplayın.

## Yaygın Sorunlar ve Çözümler

### Sorun: Açıklamalar Görünmüyor

**En olası nedenler**
- Noktalar sayfa sınırları dışındadır
- Lisans yüklenmemiş (su işareti açıklamayı gizler)
- Yanlış sayfa numarası (API'de sayfalar sıfır‑tabanlıdır)

**Çözüm kontrol listesi**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Sorun: Büyük Dosyalarda Düşük Performans

500‑sayfalık bir PDF'yi belleğe yüklemek hizmetinizi durdurabilir. Bunu şu şekilde hafifletin:

- **Bir seferde bir sayfa işleme** – belgeyi açın, tek bir sayfayı açıklayın, kaydedin ve ardından bir sonraki sayfaya geçin.  
- **Streaming** – tam belge tamponlamasını önlemek için `Annotator`'ın streaming API'sını kullanın.  
- **Caching** – sık erişilen PDF'leri hızlı bir önbellekte (ör. Redis) saklayın ve önbellek kopyasını açıklayın.

### Sorun: Renk Değerleri Çalışmıyor

GroupDocs, düz RGB yerine **ARGB** (Alpha, Red, Green, Blue) bekler. `0xFFFF0000` ARGB değeri tamamen opak kırmızı anlamına gelir. `0xFF0000` sağlarsanız kütüphane bunu yanlış yorumlar ve siyah bir açıklama ortaya çıkar.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Performans En İyi Uygulamaları

### Bellek Yönetimi

Bir toplu işte onlarca PDF'yi açıklarken, her dosyayı kendi try‑with‑resources bloğu içinde sarın:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Bu desen, her yinelemeden sonra yerel tamponların serbest bırakılmasını garanti eder, uzun süren işlemlerde **OutOfMemoryError** oluşmasını önler.

### Toplu İşleme Optimizasyonu

Yüksek verimli ortamlarda, sınırlı bir iş parçacığı havuzu ile birleştirilmiş paralel akışları düşünün:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Sınırlı havuz** iş parçacığı patlamasını önler, paralel akışlar ise CPU çekirdeklerini meşgul tutar.

### Dosya Boyutu Hususları

Büyük PDF'ler (> 100 MB) performansı düşürebilir. Bu stratejileri uygulayın:

- **Ön‑sıkıştırın** kaynak PDF'yi Ghostscript gibi bir araçla açıklamadan önce.  
- **Sadece gerekli sayfaları açıklayın** – işaretleme gerektirmeyen sayfaları atlayın.  
- Belgeyi mantıksal bölümlere (ör. bölüm başına) **bölün** ve her parçayı bağımsız işleyin.

## Gerçek‑Dünya Uygulamaları

### Belge İnceleme Sistemleri

Hukuk firmaları genellikle sorunlu maddeleri işaretlemeye ihtiyaç duyar. Squiggly açıklamaları ve dizili yanıtlar, birden fazla avukatın PDF'yi terk etmeden tek bir paragrafı tartışmasına olanak tanır:

- **Avukat A** bir madde altına kırmızı bir squiggly ekler ve “Belirsiz ifade” yazar.  
- **Avukat B** “‘material breach’ için tanım ekleyin” diye yanıt verir.  
- Tüm tartışma gömülü, aranabilir ve denetlenebilir kalır.

### Mevcut Sistemlerle Entegrasyon

GroupDocs.Annotation popüler Java çerçeveleriyle sorunsuz çalışır:

- **Spring Boot** – PDF çok parçalı yüklemesini kabul eden, açıklamalar ekleyen ve sonucu geri akış olarak sunan bir REST uç noktası `/api/annotate` ortaya çıkar.  
- **JSF** – web görünümünde anlık işaretleme için açıklama eylemlerini UI bileşenlerine bağlayın.  
- **Mikroservisler** – kütüphanenin küçük ayak izi (< 15 MB) Docker ile konteynerleştirmenize ve yatay olarak ölçeklendirmenize olanak tanır.

### İş Akışı Otomasyonu

Açıklamayı diğer GroupDocs ürünleriyle (ör. GroupDocs.Signature) birleştirerek uçtan‑uca iş akışları oluşturun:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Squiggly Açıklamaları Ne Zaman Kullanmalı vs. Alternatifler

| Kullanım‑durumu | Önerilen açıklama |
|----------------|-------------------|
| Yazım veya dilbilgisi hatalarını işaretleme | **Squiggly** – kelime işlemcilere benzer görsel ipucu |
| Bir hatayı ima etmeden önemli bölümleri vurgulama | **Highlight** – yarı saydam kaplama |
| Detaylı geri bildirim sağlama | **Text** veya **Comment** – serbest biçimli not kutusu |
| Bir belgeyi onaylama veya reddetme | **Stamp** – “Approved” veya “Rejected” rozeti |

## Sonuç

Artık GroupDocs.Annotation kullanarak **create annotation reply java** için eksiksiz, üretime hazır bir tarifiniz var. API'yi ustalıkla kullanarak, lisanslamayı yöneterek ve yukarıdaki performans ipuçlarını uygulayarak şunları yapabilirsiniz:

- Binlerce PDF'de hata işaretlemeyi otomatikleştirin  
- Dosyanın içinde işbirlikçi, dizili tartışmaları etkinleştirin  
- Devasa belgeleri işlerken bile bellek kullanımını düşük tutun  

**Sonraki adımlar**
1. Diğer açıklama türleriyle (vurgular, damgalar, metin) deney yapın.  
2. PDF'leri alan, açıklama ekleyen ve sonucu dönen bir REST servisi oluşturun.  
3. Analitik için mevcut yorumları çekmek üzere çıkarma API'sını (`annotator.get()`) keşfedin.  

Programatik PDF açıklamanın gücü, zahmetli manuel işaretlemeyi tekrarlanabilir, denetlenebilir kodla değiştirme yeteneğinde yatar. İster niş bir hukuk‑teknoloji ürünü ister genel amaçlı bir belge iş akışı motoru oluşturuyor olun, bu kılavuzdaki teknikler size ilerlemek için sağlam bir temel sağlar.

## Sıkça Sorulan Sorular

**Q: GroupDocs.Annotation'ı diğer Java PDF kütüphanelerinden daha iyi yapan nedir?**  
A: GroupDocs.Annotation sadece açıklama iş akışlarına odaklanır, 30'dan fazla açıklama türü, dizili yanıtlar ve 50+ dosya formatı için yerel destek sunar ve 500‑sayfalık PDF'lerde bellek ayak izini 200 MB'nin altında tutar.

**Q: Bu kütüphaneyi Spring Boot uygulamalarıyla kullanabilir miyim?**  
A: Kesinlikle. `Annotator` servisini enjekte eden bir `@RestController` oluşturun, çok parçalı yüklemeleri işleyin ve açıklamalı PDF'yi istemciye geri akış olarak gönderin. Eşzamanlı istekler için bir iş parçacığı havuzu yapılandırmayı unutmayın.

**Q: Farklı sayfa boyutlarına sahip belgelerle nasıl başa çıkabilirim?**  
A: `annotator.getPageInfo(pageIndex)` ile her sayfanın boyutlarını sorgulayın ve nokta değerlerini sabit kodlamak yerine göreli koordinatlar (ör. yüzde) hesaplayın. Bu, açıklamaların A4, Letter ve özel boyutlu sayfalarda doğru görünmesini sağlar.

**Q: PDF'lerden mevcut açıklamaları çıkarmanın bir yolu var mı?**  
A: Evet. `annotator.get()` çağırarak tüm açıklamaların bir koleksiyonunu alın, ardından yazar, yorum ve geometri gibi özellikleri okumak için yineleyin. Bu, taşıma veya analiz senaryoları için faydalıdır.

**Q: Çok‑kullanıcılı sistemlerde açıklama izinlerini yönetmenin en iyi yaklaşımı nedir?**  
A: Uygulama katmanında kimlik doğrulama uygulayın, her `Reply` ile kullanıcı kimliğini saklayın ve iş kurallarını (ör. sadece yazar veya bir yönetici yanıtı düzenleyebilir veya silebilir) zorlayın. API kendisi izinleri zorlamaz, size tam esneklik sağlar.

**Q: Yüzlerce PDF işlenirken bellek kullanımını nasıl optimize edebilirim?**  
A: Her belge için try‑with‑resources kullanın, sayfaları tek tek işleyin ve eşzamanlı bellek tüketimini sınırlamak için sınırlı bir iş parçacığı havuzu düşünün. VisualVM gibi araçlarla JVM yığınını izlemek `-Xmx` ayarını ince ayar yapmanıza yardımcı olur.

---

**Son Güncelleme:** 2026-05-16  
**Test Edilen Versiyon:** GroupDocs.Annotation 25.2 for Java  
**Yazar:** GroupDocs  

**Ek Kaynaklar**
- [GroupDocs.Annotation for Java Dokümantasyonu](https://docs.groupdocs.com/annotation/java/)
- [Tam API Referansı](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## İlgili Eğitimler

- [Java PDF Açıklama Kütüphanesi Eğitimi](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Java'da Açıklama Yanıtlarını Kaldırma - GroupDocs.Annotation ile ID'ye Göre Yanıtları Yönetme](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [PDF Açıklamalarını Düzenleme Java - Tam GroupDocs Eğitimi](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)