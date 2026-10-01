---
categories:
- Java Tutorials
date: '2026-09-30'
description: GroupDocs kullanarak Java ile PDF vurgularını nasıl oluşturacağınızı
  öğrenin. Bu adım adım öğretici, Java'da PDF'yi nasıl vurgulayacağınızı, yorum ekleyeceğinizi
  ve performansı nasıl optimize edeceğinizi gösterir.
keywords:
- create pdf highlights java
- highlight text pdf java
- groupdocs annotation java
- pdf annotation java tutorial
lastmod: '2026-09-30'
linktitle: Java PDF açıklama öğreticisi
og_description: GroupDocs.Annotation ile Java PDF vurguları oluşturun. Java'da vurgular
  eklemek, yorumlar eklemek ve performansı optimize etmek için bu adım adım öğreticiyi
  izleyin.
og_image_alt: Developer guide illustrating PDF highlight creation using GroupDocs.Annotation
  for Java
og_title: Java ile PDF vurguları oluşturma – Java geliştiricileri için tam rehber
schemas:
- author: GroupDocs
  dateModified: '2026-09-30'
  description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  headline: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  type: TechArticle
- description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  name: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  steps:
  - name: Initialize your annotator object
    text: '`Annotator` is the core class in GroupDocs.Annotation that loads a PDF
      and provides methods to add, edit, and save annotations. **What''s happening
      here?** - The `Annotator` constructor loads your PDF into memory. - We set an
      output path where the annotated PDF will be saved. - The input PDF remains '
  - name: Create interactive replies and comments
    text: '`Reply` and `Comment` objects enable threaded conversations on a highlight,
      turning a static annotation into a collaborative discussion. Reply represents
      a single comment in a thread, while Comment groups replies under a specific
      annotation. **Why this matters**: In real applications you often need '
  - name: Define precise highlight coordinates
    text: '`HighlightAnnotation` is the class that represents a highlight region on
      a PDF page. HighlightAnnotation defines a rectangular highlight region on a
      PDF page, specified by a set of points. **Understanding PDF coordinates**: -
      Origin (0,0) is at the bottom‑left of the page. - X increases to the right'
  - name: Configure your highlight annotation
    text: '`HighlightAnnotation` lets you customise colour, opacity, font colour,
      and page number. **Customization options explained**: - `setBackgroundColor(65535)`:
      Yellow highlight (RGB integer). - `setOpacity(0.5)`: 50 % transparency keeps
      the underlying text readable. - `setFontColor(0)`: Black text ensur'
  - name: Save your annotated PDF
    text: '`dispose()` releases native resources and finalizes the PDF file. `dispose()`
      releases native resources and finalizes the PDF file. **Resource management**:
      The `dispose()` call is crucial—it frees up memory and guarantees all changes
      are persisted. Always wrap the annotator in a try‑with‑resources '
  type: HowTo
- questions:
  - answer: Absolutely. It integrates with Spring Boot, Servlets, and other Java web
      frameworks. Expose a REST endpoint that accepts a PDF, applies highlights, and
      returns the annotated file.
    question: Can I use GroupDocs.Annotation in web applications?
  - answer: The library supports Unicode, so you can add comments and messages in
      any language. Just ensure your Java application uses UTF‑8 encoding.
    question: How do I handle annotations in different languages?
  - answer: Performance scales with the number of annotations, but PDF size has a
      larger impact. For documents with hundreds of highlights, consider lazy loading
      or pagination to keep memory usage low.
    question: What's the performance impact of adding many annotations?
  - answer: Yes. Load a PDF with existing annotations, update properties such as colour
      or position, and save the updated version. This is ideal for building annotation‑management
      tools.
    question: Can I modify existing annotations programmatically?
  - answer: GroupDocs.Annotation provides enumeration methods to read metadata (author,
      creation date, comment text, etc.). Export this data to CSV, JSON, or feed it
      into analytics pipelines.
    question: How do I extract annotation data for reporting?
  type: FAQPage
tags:
- pdf annotation
- groupdocs
- java library
- document processing
- create pdf highlights java
title: 'Java ile PDF vurguları nasıl oluşturulur: PDF''leri vurgulama için tam rehber'
type: docs
url: /tr/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/
weight: 1
---


# PDF vurgularını Java ile oluşturma: PDF'leri vurgulamak için eksiksiz rehber

## Giriş

Birden fazla belge sürümü arasında geri bildirimi yönetmekte zorlandınız mı? Yalnız değilsiniz. İster bir belge yönetim sistemi oluşturuyor olun, ister eğitim platformu yaratıyor olun, ister işbirlikçi araçlar geliştiriyor olun, **create pdf highlights java** sıfırdan uygulamak şaşırtıcı derecede zor olabilir.

İşte **GroupDocs.Annotation for Java** devreye giriyor. Bu güçlü kütüphane, karmaşık PDF ek açıklama görevlerini basit işlemlere dönüştürerek, düşük seviyeli PDF manipülasyonuyle uğraşmadan vurgulamalar, yorumlar ve yanıtlar eklemenizi sağlar.

Bu kapsamlı öğreticide, gerçek dünya örnekleriyle **highlight pdf in java** nasıl yapılacağını keşfedeceksiniz. Temel kurulumdan gelişmiş vurgulama tekniklerine kadar her şeyi adım adım inceleyecek ve üretim ortamlarında uygularken edindiğim pratik ipuçlarını paylaşacağız.

Tam olarak neler öğreneceksiniz:

- Java projenizde GroupDocs.Annotation'ı (doğru şekilde) kurma  
- Özel stil ile etkileşimli PDF vurgulamaları oluşturma  
- İşbirliği için zincirli yanıtlar ve yorumlar ekleme  
- Yaygın tuzakları ele alma ve performans optimizasyonu  
- Gerçek dünya uygulama stratejileri  

PDF'lerinizi etkileşimli, işbirlikçi belgelere dönüştürmeye hazır mısınız? Hadi başlayalım!

## Hızlı cevaplar
- **Java'da PDF vurgularını basitleştiren kütüphane nedir?** GroupDocs.Annotation for Java.  
- **Hangi Maven bağımlılığı kütüphaneyi ekler?** `com.groupdocs:groupdocs-annotation:25.2`.  
- **Geliştirme için lisansa ihtiyacım var mı?** Test için ücretsiz geçici bir lisans yeterli; üretim için ücretli lisans gerekir.  
- **Vurgulamalara yorum ekleyebilir miyim?** Evet, yanıtlar ve zincirli yorumlar ekleyebilirsiniz.  
- **Büyük PDF'lerde belleği nasıl yönetirim?** Kaydetme sonrası `dispose()` çağırarak try‑with‑resources kullanın.

## Java'da PDF vurguları nasıl oluşturulur?

Hedef PDF'yi `new Annotator(inputPath)` ile yükleyin ve `addAnnotation(highlight)` ardından `save(outputPath)` çağırın. Annotator, bir PDF belgesini yükleyen ve ek açıklamaları ekleme, düzenleme ve kaydetme yöntemleri sunan temel sınıftır. Bu iki adımlı akış, saniyeler içinde vurgulanmış bir PDF oluşturur, koordinat dönüşümünü otomatik olarak yönetir ve `dispose()` çağrıldığında kaynakları serbest bırakır. Manuel PDF ayrıştırma gerekmez.

## create pdf highlights java nedir?

`create pdf highlights java`, genellikle GroupDocs.Annotation gibi özel bir kütüphane aracılığıyla Java kodu kullanarak PDF dosyalarına vurgulama ek açıklamaları programlı olarak eklemeyi ifade eder. Bu süreç, manuel düzenleme yapmadan otomatik inceleme, işbirliği ve görsel vurgu sağlar.

## Java PDF işleme için neden GroupDocs.Annotation seçilmeli?

GroupDocs.Annotation, **30'dan fazla ek açıklama türünü** destekler ve belgeyi belleğe tamamen yüklemeden **500 MB**'a kadar PDF'leri işleyebilir. Sayfa‑seviyesi koordinatları otomatik olarak çözer, mevcut içeriği korur ve stil, yorumlama ve ek açıklama verilerini dışa aktarma için zengin bir API sunar.

## Önkoşullar ve ortam kurulumu

### Gereksinimler

- **Geliştirme ortamı**: Java 8+ (Java 11+ önerilir), Maven veya Gradle ve IntelliJ IDEA, Eclipse veya VS Code gibi bir IDE.  
- **Bilgi gereksinimleri**: Temel Java (koleksiyonlar, nesneler, dosya I/O), Maven bağımlılık yönetimi ve PDF koordinat sistemleri hakkında yüksek seviyeli bir fikir.  

### GroupDocs.Annotation for Java kurulumu

En kolay başlangıç yolu Maven'dir. `pom.xml` dosyanıza şu yapılandırmaları ekleyin:

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

**Pro ipucu**: Her zaman en son stabil sürümü kullanın. GroupDocs, performans iyileştirmeleri ve hata düzeltmeleri içeren güncellemeleri düzenli olarak yayınlar.

### Lisans kurulumu (bunu atlamayın!)

Üretimde GroupDocs.Annotation kullanmak için bir lisansa ihtiyacınız olacak. Lisanslamayı şu şekilde yapabilirsiniz:

**Geliştirme için**: Ücretsiz deneme veya [geçici lisans](https://purchase.groupdocs.com/temporary-license/) alın  
**Üretim için**: [GroupDocs web sitesinden](https://purchase.groupdocs.com/buy) bir lisans satın alın

Geçici lisans, test ve geliştirme için mükemmeldir—filigran olmadan tam işlevsellik sağlar.

## Adım adım uygulama rehberi

Şimdi heyecan verici kısma geliyoruz—tam bir PDF ek açıklama sistemi oluşturalım! Her bileşeni adım adım inceleyecek, kodun ne yaptığını ve neden bu şekilde yaptığımızı açıklayacağız.

### Adım 1: Annotator nesnesini başlatma

`Annotator`, PDF'yi yükleyen ve ek açıklamaları ekleme, düzenleme ve kaydetme yöntemleri sunan GroupDocs.Annotation'ın temel sınıfıdır.

```java
import com.groupdocs.annotation.Annotator;
import org.apache.commons.io.FilenameUtils;

String outputPath = "YOUR_OUTPUT_DIRECTORY/AnnotationOutput.pdf";
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/InputDocument.pdf");
```

**Burada ne oluyor?**  
- `Annotator` yapıcı metodu PDF'nizi belleğe yükler.  
- Ek açıklamalı PDF'nin kaydedileceği bir çıktı yolu belirleriz.  
- Girdi PDF'si değişmeden kalır—yeni bir ek açıklamalı sürüm oluşturuyoruz.

**Yaygın tuzak**: Dosya yollarının doğru olduğundan ve dizinlerin mevcut olduğundan emin olun. Birçok geliştirici basit yol sorunlarını ayıklamak için zaman harcar.

### Adım 2: Etkileşimli yanıtlar ve yorumlar oluşturma

`Reply` ve `Comment` nesneleri, bir vurgulama üzerinde zincirli konuşmalar yapmayı sağlar ve statik bir ek açıklamayı işbirlikçi bir tartışmaya dönüştürür. Reply, bir zincirdeki tek bir yorumu temsil ederken, Comment belirli bir ek açıklama altında yanıtları gruplar.

```java
import java.util.ArrayList;
import java.util.Calendar;
import java.util.List;

List<Reply> replies = new ArrayList<>();

// First reply
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply1);

// Second reply  
Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply2);
```

**Neden önemli**: Gerçek uygulamalarda genellikle kimin ne zaman ne söylediğini izlemek gerekir. Bu yanıt sistemi şu özellikleri oluşturmanıza olanak tanır:

- Vurgulanan metin üzerinde yorum zincirleri  
- Onay zincirli inceleme iş akışları  
- Belge değişiklikleri için denetim izleri  
- İşbirlikçi düzenleme ortamları  

**Gerçek dünya ipucu**: Varsayılan değerlere güvenmek yerine kullanıcı bilgilerini ve zaman damgalarını bir veritabanında saklayın.

### Adım 3: Kesin vurgulama koordinatlarını tanımlama

`HighlightAnnotation`, PDF sayfasında bir vurgulama bölgesi temsil eden sınıftır. HighlightAnnotation, bir dizi nokta ile belirtilen dikdörtgen bir vurgulama bölgesi tanımlar.

```java
import com.groupdocs.annotation.models.Point;
import java.util.ArrayList;
import java.util.List;

List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));   // Top-left corner
points.add(new Point(240, 730));  // Top-right corner  
points.add(new Point(80, 650));   // Bottom-left corner
points.add(new Point(240, 650));  // Bottom-right corner
```

**PDF koordinatlarını anlama**:  

- Orijin (0,0) sayfanın sol‑altısındadır.  
- X sağa, Y yukarı doğru artar.  
- Dört nokta hedef metnin etrafında bir sınırlama kutusu oluşturur.

**Koordinat bulma için pro ipucu**: İmleç koordinatlarını gösteren bir PDF görüntüleyici kullanın veya yaklaşık değerlerle başlayıp görsel sonuçlara göre ince ayar yapın.

### Adım 4: Vurgulama ek açıklamanızı yapılandırma

`HighlightAnnotation`, renk, opaklık, yazı rengi ve sayfa numarasını özelleştirmenize olanak tanır.

```java
import com.groupdocs.annotation.models.annotationmodels.HighlightAnnotation;

HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setBackgroundColor(65535);  // Yellow highlight
highlight.setCreatedOn(Calendar.getInstance().getTime());
highlight.setFontColor(0);            // Black text  
highlight.setMessage("This is a highlight annotation");
highlight.setOpacity(0.5);            // Semi‑transparent
highlight.setPageNumber(0);           // First page (zero‑indexed)
highlight.setPoints(points);
highlight.setReplies(replies);

// Add the highlight to the annotator
annotator.add(highlight);
```

**Özelleştirme seçenekleri açıklaması**:  

- `setBackgroundColor(65535)`: Sarı vurgulama (RGB tamsayı).  
- `setOpacity(0.5)`: %50 şeffaflık, alt metnin okunabilirliğini korur.  
- `setFontColor(0)`: Siyah metin iyi kontrast sağlar.  
- `setPageNumber(0)`: Sayfa indeksi (0 = ilk sayfa).  

**Renk seçimi ipuçları**:  

- Sarı (65535) klasik ve müdahalesizdir.  
- Önemli vurgulamalar için turuncu (16753920) veya kırmızı (16711680) deneyin.  
- En iyi okunabilirlik için opaklığı 0.3‑0.7 arasında tutun.

### Adım 5: Ek açıklamalı PDF'nizi kaydedin

`dispose()` yerel kaynakları serbest bırakır ve PDF dosyasını sonlandırır. `dispose()` yerel kaynakları serbest bırakır ve PDF dosyasını sonlandırır.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Kaynak yönetimi**: `dispose()` çağrısı çok önemlidir—belleği boşaltır ve tüm değişikliklerin kalıcı olmasını garantiler. Annotator'ı her zaman try‑with‑resources bloğuna sarın veya finally bloğunda `dispose()` çağırın.

## Yaygın sorunların giderilmesi

### Dosya yolu sorunları  

**Semptom**: `FileNotFoundException` veya “Dosyaya erişilemiyor”.  
**Çözüm**: Yolların proje köküne göre mutlak ya da göreceli olduğundan emin olun, dosya izinlerini kontrol edin ve kaydetmeden önce çıktı dizinlerinin var olduğunu doğrulayın.

### Koordinatlar beklenen konumla eşleşmiyor  

**Semptom**: Vurgulamalar yanlış yerlerde görünüyor.  
**Çözüm**: PDF koordinat sisteminin sol‑alt köşeden başladığını unutmayın. Farklı PDF oluşturucular hafif farklılıklar gösterebilir; örnek PDF'lerle test edin ve buna göre ayarlayın.

### Büyük PDF'lerde bellek sorunları  

**Semptom**: `OutOfMemoryError` veya yavaş performans.  
**Çözüm**: JVM yığın boyutunu artırın (ör. `-Xmx2G`), PDF'leri daha küçük partilerde işleyin ve her zaman `dispose()` çağırarak kaynakları serbest bırakın.

### Renk doğru görüntülenmiyor  

**Semptom**: Yanlış vurgulama renkleri veya görünmez ek açıklamalar.  
**Çözüm**: Hex dizgeleri yerine RGB tamsayı değerleri kullanın. Opaklık değerlerini 0.1 ile 0.9 arasında test edin. Arka plan ve yazı renklerinin iyi kontrast sağladığını doğrulayın.

## Performans optimizasyonu en iyi uygulamaları

### Bellek yönetimi

```java
// Good practice - use try-with-resources when available
try (Annotator annotator = new Annotator(inputPath)) {
    // Your annotation code here
    annotator.save(outputPath);
} // Automatically disposes resources
```

Annotator'ı try‑with‑resources bloğu içinde tahsis edin ve hemen serbest bırakın. Bu desen, çok sayıda belge işlenirken bellek sızıntılarını önler.

### Toplu işleme stratejisi

```java
for (String pdfPath : pdfPaths) {
    try (Annotator annotator = new Annotator(pdfPath)) {
        // Process single PDF
        addAnnotations(annotator);
        annotator.save(getOutputPath(pdfPath));
    }
    // Memory freed before next iteration
}
```

Birden fazla PDF için, hepsini belleğe yüklemek yerine sıralı olarak işleyin. Bu yaklaşım lineer ölçeklenir ve JVM ayak izini düşük tutar.

### Dosya boyutu hususları

- Büyük PDF'ler (>10 MB) daha fazla bellek ve işlem süresi tüketir.  
- Çok büyük belgeleri bölümlere ayırmayı düşünün.  
- Ek açıklama öncesinde giriş PDF'lerini optimize edin (görüntüleri sıkıştırın, kullanılmayan nesneleri kaldırın).

## Gerçek dünya uygulamaları ve kullanım senaryoları

### Belge inceleme sistemleri  

Hukuki sözleşmeler, teknik spesifikasyonlar ve uyum belgeleri için mükemmeldir. Her inceleyici için farklı vurgulama renkleri kullanın, izin kurallarını uygulayın ve raporlama için ek açıklama meta verilerini bir veritabanında saklayın.

### Eğitim platformları  

Ders kitabı vurgulama, ödev geri bildirimi ve işbirlikçi çalışma için idealdir. Öğrencilerin kişisel ek açıklamaları kaydetmesine izin verin, öğretmenlerin resmi yorum eklemesini sağlayın ve müfredat geliştikçe belgeleri sürüm kontrolüyle yönetin.

### Kalite güvencesi iş akışları  

Tasarım incelemeleri, süreç dokümantasyonu ve uyum kontrolü için harikadır. Mevcut QA araçlarıyla entegre edin, izleme için ek açıklama durumunu (açık/çözülmüş) kullanın ve ek açıklama verilerinden denetim raporları oluşturun.

### İşbirlikçi araştırma araçları  

Akademik makaleler, araştırma dokümantasyonu ve eş değerlendirme için uygundur. Gerçek zamanlı işbirliğini uygulayın, anonim incelemeleri destekleyin ve analiz için ek açıklamaları dışa aktarın.

## İleri düzey ipuçları ve en iyi uygulamalar

### Koordinat hesaplama yardımcı yöntemleri

```java
public class AnnotationUtils {
    public static List<Point> createRectangle(double x, double y, double width, double height) {
        List<Point> points = new ArrayList<>();
        points.add(new Point(x, y + height));      // Top‑left
        points.add(new Point(x + width, y + height)); // Top‑right  
        points.add(new Point(x, y));               // Bottom‑left
        points.add(new Point(x + width, y));       // Bottom‑right
        return points;
    }
}
```

Ekran koordinatlarını PDF puanlarına dönüştüren yardımcı yöntemler oluşturun, tekrarı azaltın ve okunabilirliği artırın.

### Ek açıklama şablonları

```java
public class AnnotationTemplates {
    public static HighlightAnnotation createStandardHighlight(List<Point> points, String message) {
        HighlightAnnotation highlight = new HighlightAnnotation();
        highlight.setBackgroundColor(65535);  // Yellow
        highlight.setOpacity(0.5);
        highlight.setFontColor(0);
        highlight.setMessage(message);
        highlight.setCreatedOn(Calendar.getInstance().getTime());
        highlight.setPoints(points);
        return highlight;
    }
}
```

Uygulamanızda tutarlılığı sağlamak için yeniden kullanılabilir ek açıklama yapılandırmaları (renk, opaklık, yazar) tanımlayın.

## Sıkça sorulan sorular

**S: GroupDocs.Annotation'ı web uygulamalarında kullanabilir miyim?**  
C: Kesinlikle. Spring Boot, Servlets ve diğer Java web çerçeveleriyle entegre olur. PDF kabul eden, vurgulama uygulayan ve ek açıklamalı dosyayı dönen bir REST uç noktası oluşturun.

**S: Farklı dillerdeki ek açıklamaları nasıl yönetirim?**  
C: Kütüphane Unicode'u destekler, bu yüzden yorumları ve mesajları herhangi bir dilde ekleyebilirsiniz. Java uygulamanızın UTF‑8 kodlamasını kullandığından emin olun.

**S: Çok sayıda ek açıklama eklemenin performans etkisi nedir?**  
C: Performans ek açıklama sayısıyla ölçeklenir, ancak PDF boyutu daha büyük bir etkiye sahiptir. Yüzlerce vurgulama içeren belgeler için bellek kullanımını düşük tutmak amacıyla tembel yükleme veya sayfalama düşünün.

**S: Mevcut ek açıklamaları programlı olarak değiştirebilir miyim?**  
C: Evet. Mevcut ek açıklamaları olan bir PDF yükleyin, renk veya konum gibi özellikleri güncelleyin ve güncellenmiş sürümü kaydedin. Bu, ek açıklama yönetim araçları oluşturmak için idealdir.

**S: Raporlama için ek açıklama verilerini nasıl çıkarırım?**  
C: GroupDocs.Annotation, meta verileri (yazar, oluşturma tarihi, yorum metni vb.) okumak için enumerasyon yöntemleri sunar. Bu verileri CSV, JSON formatına dışa aktarın veya analiz boru hatlarına besleyin.

## Temel kaynaklar ve dokümantasyon

- [GroupDocs.Annotation Java Documentation](https://docs.groupdocs.com/annotation/java/) – kapsamlı rehberler ve API referansları  
- [API Reference](https://reference.groupdocs.com/annotation/java/) – detaylı yöntem dokümantasyonu  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) – her zaman en son stabil sürümü kullanın  
- [Purchase License](https://purchase.groupdocs.com/buy) – üretim lisans seçenekleri  
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/) – geliştirme ve test için mükemmel  
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/) – uzmanlardan ve diğer geliştiricilerden yardım alın

---

**Son güncelleme:** 2026-09-30  
**Test edilen sürüm:** GroupDocs.Annotation 25.2  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [PDF Anotasyonlarını Düzenle Java - Tam GroupDocs Öğreticisi](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [PDF Anotasyonlarını Yükle Java - Tam GroupDocs Annotation Yönetim Rehberi](/annotation/java/annotation-management/groupdocs-annotation-java-manage-documents/)
- [Java'da Ok PDF Ekle – Tam GroupDocs Öğreticisi](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)