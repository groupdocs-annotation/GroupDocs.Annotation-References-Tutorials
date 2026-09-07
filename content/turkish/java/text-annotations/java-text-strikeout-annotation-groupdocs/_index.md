---
categories:
- Java Development
date: '2026-03-30'
description: GroupDocs.Annotation kullanarak Java'da üstü çizili açıklama eklemeyi
  öğrenin. Kod örnekleri, sorun giderme ipuçları ve belge işaretleme için en iyi uygulamaları
  içeren adım adım rehber.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: GroupDocs ile Üstü Çizili Açıklama Ekleme Java Öğreticisi
type: docs
url: /tr/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Java'da Üstü Çizili Not Ekleme - Tam GroupDocs Rehberi

Hiç bir belgeye bakıp “Bu metni üstü çizmem gerekiyor, ama kırmızı bir kalem tutamıyorum” diye düşündünüz mü? Yalnız değilsiniz. İster bir belge inceleme sistemi oluşturuyor olun, ister bir düzenleme iş akışı yaratıyor olun, ya da Java uygulamanızda silinmek üzere metni işaretlemeniz gerekiyor olsun, **add strikeout annotation java** temel bir beceridir. Bu öğreticide, üretimde gerçekten çalışan bir metin üstü çizme işlevselliğini uygulamak için bilmeniz gereken her şeyi adım adım anlatacağız.

## Hızlı Yanıtlar
- **Java'da üstü çizili notları destekleyen kütüphane nedir?** GroupDocs.Annotation for Java  
- **SEO için hedeflemem gereken birincil anahtar kelime nedir?** add strikeout annotation java  
- **Örnek kodu çalıştırmak için lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme veya geçici lisans çalışır; üretim için tam lisans gereklidir.  
- **Bunu PDF, DOCX ve PPTX dosyalarıyla kullanabilir miyim?** Evet – GroupDocs.Annotation tüm büyük belge formatlarını destekler.  
- **Hangi Java sürümü gereklidir?** JDK 8 veya üzeri (JDK 11+ önerilir).  

## add strikeout annotation java nedir?
Üstü çizili not, seçilen metnin üzerinden bir çizgi çizer ve içeriğin kaldırılması veya göz ardı edilmesi gerektiğini görsel olarak gösterir. Orijinal metni denetim izleri veya işbirlikçi incelemeler için bozmadan silme önerileri sunmanın yıkıcı olmayan bir yoludur.

## Java uygulamalarında üstü çizili notları neden kullanmalısınız?
- **Document review workflows** – inceleme yapanlar kaynağı değiştirmeden istenmeyen metni işaretleyebilir.  
- **Collaborative editing** – ekip üyeleri önerilen silmeleri anında görür.  
- **Legal and compliance** – değişikliklerin net bir denetim izini tutar.  
- **Content migration** – sistemler arasında içerik taşımadan önce eski bölümleri işaretler.  

## Önkoşullar ve Ortam Kurulumu
Kodlamaya başlamadan önce aşağıdakilere ihtiyacınız olacak:

- **Java Development Kit (JDK)** 8+ (JDK 11+ önerilir)  
- **Maven veya Gradle** bağımlılık yönetimi için  
- **IDE** – IntelliJ IDEA, Eclipse veya Java uzantılarına sahip VS Code  
- **GroupDocs.Annotation library** – örneklerde sürüm 25.2'yi kullanacağız  

*İyi olur:* Java notasyonları ve PDF işleme hakkında temel bilgi.

## GroupDocs.Annotation'ı Java için Kurma

### Gerçekten Çalışan Maven Yapılandırması
Depoyu ve bağımlılığı `pom.xml` dosyanıza aşağıdaki gibi ekleyin:

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

### Lisansınızı Alın
GroupDocs birkaç lisans seçeneği sunar:

- **Free trial** – test için mükemmel (kredi kartı gerekmez)  
- **Temporary license** – geliştirme ve test ortamları için ideal  
- **Full license** – üretim kullanımı için gereklidir; [satın alma sayfasına](https://purchase.groupdocs.com/buy) bakın

> **Pro tip:** API'yi keşfetmek için önce ücretsiz deneme sürümüyle başlayın, ardından gerçek bir özellik geliştirmeye hazır olduğunuzda geçici lisansa geçin.

### Hızlı Sağlamlık Kontrolü Kurulumu
Kütüphanenin doğru yüklendiğini doğrulamak için bu minimal programı çalıştırın:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Konsol hatasız bir başarı mesajı yazdırıyorsa, üstü çizili not eklemeye hazırsınız.

## add strikeout annotation java nasıl eklenir

Aşağıda, net adımlara bölünmüş tam, üretime hazır bir uygulama bulunmaktadır.

### Adım 1 – Annotator'ı Başlatma
`Annotator` örneğini kaynak belgeye işaret edecek şekilde oluşturun:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Neden önemli:** Mutlak ya da doğru çözümlenmiş göreli bir yol kullanmak “dosya bulunamadı” istisnalarını önler.

### Adım 2 – (İsteğe Bağlı) Yorum Yanıtlarını Hazırlama
Yanıt eklemek notu işbirliğine açık hale getirir:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

### Adım 3 – Üstü Çizili Alanı Tanımlama
Üstü çizmek istediğiniz metni çevreleyen dikdörtgeni belirtin:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Koordinat ipucu:** Orijin (0,0) sayfanın sol‑üst köşesidir; X sağa, Y aşağıya doğru artar. Bu değerleri ince ayar yapmak için koordinatları gösteren bir PDF görüntüleyici kullanın.

### Adım 4 – Üstü Çizili Notu Yapılandırma
Görünümü, sayfa numarasını ayarlayın ve yorumları ekleyin:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Renk notu:* `65535` tamsayı RGB formatında sarıya karşılık gelir. Diğer renkleri kullanmak için değeri değiştirin.

### Adım 5 – Notu Uygula ve Kaydet
Notu belgeye ekleyin ve çıktı dosyasını yazın:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Adım 6 – Kaynakları Temizleme (Kritik!)
Yerel kaynakları serbest bırakmak için annotator'ı her zaman dispose edin:

```java
if (annotator != null) {
    annotator.dispose();
}
```

Üretimde, kullanımı bir try‑with‑resources bloğu ya da `try/finally` yapısı içinde sarın.

## Yaygın Sorunlar ve Çözümleri

| Sorun | Semptom | Çözüm |
|---------|---------|-----|
| **File Not Found** | `Annotator` bir istisna fırlatır | Mutlak yollar kullanın, okuma izinlerini doğrulayın, başka bir işlemin dosyayı kilitlemediğinden emin olun |
| **Wrong Coordinates** | Üstü çizili not, hedeflenen metinden uzakta görünür | PDF görüntüleyicinin koordinat sistemini iki kez kontrol edin; noktaları buna göre ayarlayın |
| **Annotation Invisible** | Kaydetmeden sonra görünür bir üstü çizili not yok | `opacity` değerini artırın (ör. `0.9`), `pageNumber`'ı doğrulayın (0‑tabanlı), noktaların düzgün bir dikdörtgen oluşturduğundan emin olun |
| **OutOfMemoryError** | Uygulama büyük PDF'lerde çöküyor | JVM yığın boyutunu artırın (`-Xmx2048m`), belgeleri toplu işleyin, her zaman `dispose()` çağırın |

## Üretim İçin Performans En İyi Uygulamaları

### Bellek Yönetimi
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Toplu İşleme Stratejisi
Onlarca ya da yüzlerce dosyayı notlamak gerektiğinde:

- Her toplu işlemde 10‑20 belge işleyin.  
- Her dosya için başarı/başarısızlık kaydı tutun.  
- Bellek sızıntılarını önlemek için her belge için `Annotator`'ı yeniden başlatın.  

### Önbellekleme İpuçları
- Sık kullanılan belge şablonlarını önbelleğe alın.  
- Standart düzenler için önceden hesaplanmış koordinat haritalarını saklayın.  

## Gerçek Dünya Kullanım Senaryoları

1. **Document Review Systems** – Editörler, orijinal sözleşmeyi değiştirmeden silme önerir.  
2. **Legal Amendments** – Avukatlar, denetim için orijinal ifadeyi koruyarak madde kaldırmalarını izler.  
3. **Academic Peer Review** – İnceleyenler, kaldırılacak bölümleri işaretler ve satır içi yorumlar ekler.  
4. **Content Migration** – CMS geçişleri sırasında, üstü çizili notlar değiştirilmesi gereken eski içeriği vurgular.  

## Gelişmiş Özelleştirme

### Özel Stil
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Meta Veri Ekleme
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Sorun Giderme Kontrol Listesi
- ✅ Kaynak dosyayı manuel olarak açabiliyor musunuz?  
- ✅ Tüm GroupDocs bağımlılıkları sınıf yolunda mevcut mu?  
- ✅ Noktalar geçerli bir dikdörtgen oluşturuyor mu?  
- ✅ Sayfa numarası doğru mu (0‑tabanlı)?  
- ✅ Yeterli yığın belleği var mı?  
- ✅ Çıktı klasörü için yazma izniniz var mı?  
- ✅ Belge formatı destekleniyor mu (PDF, DOCX, PPTX, vb.)?  

## Sıkça Sorulan Sorular

**Q:** GroupDocs.Annotation'ı bir Spring Boot servisi içinde kullanabilir miyim?  
**A:** Evet. Maven bağımlılığını ekleyin, `Annotator` oluşturan bir servis sınıfını enjekte edin ve yaşam döngüsünü Spring'in bean kapsamlarıyla yönetin.

**Q:** Hangi belge formatları üstü çizili notları destekler?  
**A:** PDF, DOCX, PPTX ve GroupDocs.Annotation tarafından desteklenen birçok diğer format. PDF, en hassas koordinat işleme yeteneğini sunar.

**Q:** Farklı sayfa boyutlarına sahip belgeler nasıl ele alınır?  
**A:** `annotator.getPageInfo(pageNumber)` ile sayfa boyutlarını alın ve koordinatları buna göre ölçeklendirin.

**Q:** Mevcut bir üstü çizili notu düzenlemek veya silmek mümkün mü?  
**A:** Kesinlikle. `annotator.getAnnotations(pageNumber)` ile notları alın, ardından `annotator.update(updatedAnnotation)` ya da `annotator.delete(annotationId)` kullanın.

**Q:** Çok sayıda not eklemenin performans etkisi nedir?  
**A:** Yüzlerce not eklemek genellikle sorun olmaz, ancak bellek kullanımını izleyin. Çok büyük not kümeleri için, görünümü sayfalara bölmeyi veya isteğe bağlı olarak notları tembel yüklemeyi düşünün.

## Sonuç
Artık GroupDocs.Annotation kullanarak **add strikeout annotation java** için tam, üretime hazır bir rehberiniz var. Basit sağlamlık kontrolü örneğiyle başlayın, ardından toplu işleme, özel stil ve meta veri zenginleştirmeye ölçeklendirin. Koordinatları dikkatlice test etmeyi, kaynakları sorumlu bir şekilde yönetmeyi ve ortamınız için doğru lisans modelini seçmeyi unutmayın.

Daha fazlasını keşfetmeye hazır mısınız? Diğer not türlerine—vurgulama, not, resim, ok ve filigran—bakın ve tam özellikli bir belge işbirliği paketi oluşturun.

---

**Son Güncelleme:** 2026-03-30  
**Test Edilen Versiyon:** GroupDocs.Annotation 25.2 for Java  
**Yazar:** GroupDocs  

**Ek Kaynaklar**
- [GroupDocs Annotation Dokümantasyonu](https://docs.groupdocs.com/annotation/java/)
- [API Referans Kılavuzu](https://reference.groupdocs.com/annotation/java/)
- [En Son Sürümü İndir](https://releases.groupdocs.com/annotation/java/)
- [Tam Lisans Satın Al](https://purchase.groupdocs.com/buy)
- [Ücretsiz Deneme Başlat](https://releases.groupdocs.com/annotation/java/)
- [Geçici Lisans Al](https://purchase.groupdocs.com/temporary-license/)
- [Topluluk Destek Forumu](https://forum.groupdocs.com/c/annotation/)