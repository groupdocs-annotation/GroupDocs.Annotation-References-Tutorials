---
"date": "2025-05-06"
"description": "GroupDocs.Annotation'ı kullanarak Java belgelerinde alt çizgi açıklamalarının nasıl ekleneceğini ve kaldırılacağını öğrenin. Bu ayrıntılı kılavuzla belge yönetiminizi geliştirin."
"title": "GroupDocs'u Kullanarak Java'da Alt Çizgili Açıklamaları Ekleme ve Kaldırma&#58; Kapsamlı Bir Kılavuz"
"url": "/tr/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
"weight": 1
---

# Java Nasıl Uygulanır: GroupDocs ile Alt Çizgili Açıklamalar Ekleme ve Kaldırma

## giriiş

Belge yönetim sisteminizi programatik olarak ek açıklamalar ekleyerek veya kaldırarak mı geliştiriyorsunuz? Bu eğitim, Java'daki güçlü GroupDocs.Annotation kütüphanesini kullanarak alt çizgi ek açıklamalar eklemeniz ve bunları PDF'ler gibi belgelerden kaldırmanız konusunda size rehberlik eder.

**Ne Öğreneceksiniz:**
- Annotator sınıfını başlatın.
- Java için GroupDocs.Annotation'ı kullanarak yorumlarla birlikte alt çizgi açıklaması ekleyin.
- Belgedeki tüm açıklamaları kaldırın.
- GroupDocs.Annotation'ı verimli bir şekilde kullanmak için ortamınızı yapılandırın.

Bu işlevselliklerin projelerinizde nasıl kullanılabileceğini inceleyelim. Başlamadan önce gerekli ön koşulların karşılandığından emin olun.

## Ön koşullar

### Gerekli Kütüphaneler ve Bağımlılıklar
Bu eğitimi etkili bir şekilde takip edebilmek için şunlara sahip olduğunuzdan emin olun:
- **GroupDocs.Java için Açıklama**: 25.2 veya üzeri sürüm önerilir.
- **Java Geliştirme Kiti (JDK)**: Sürüm 8 veya üzeri gereklidir.

### Çevre Kurulum Gereksinimleri
Geliştirme ortamınızın IntelliJ IDEA veya Eclipse gibi bir IDE ve Maven gibi bir derleme aracı içerdiğinden emin olun.

### Bilgi Önkoşulları
Özellikle Maven üzerinden kütüphanelerle çalışmak için Java programlamanın temellerine hakim olmak faydalı olacaktır.

## GroupDocs.Annotation'ı Java İçin Ayarlama

Java projelerinizde GroupDocs.Annotation'ı kullanmaya başlamak için şu kurulum adımlarını izleyin:

**Maven Yapılandırması:**
Aşağıdaki yapılandırmayı şuraya ekleyin: `pom.xml` GroupDocs.Annotation'ı indirip entegre edebileceğiniz dosya.

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

**Lisans Edinimi:**
Kütüphanelerinin tüm yeteneklerini keşfetmek için GroupDocs'tan ücretsiz bir deneme sürümü indirerek veya geçici bir lisans edinerek başlayın. Üretim kullanımı için bir lisans satın almak gereklidir.

## Uygulama Kılavuzu

### Özellik 1: Açıklamayı Başlat ve Altı Çizili Açıklama Ekle

Bu bölüm, başlatma işleminde size rehberlik eder `Annotator` sınıf ve belgenize alt çizgi açıklaması ekleme.

#### Genel bakış
Açıklama eklemek, bir belgenin belirli bölümlerini vurgulamaya yardımcı olur. Burada, açıklama veya geri bildirim için yorumlarla metnin altını çizmeye odaklanıyoruz.

#### Adım Adım Uygulama

**1. Annotator'ı Başlat**
Bir tane oluştur `Annotator` nesneyi seçin ve PDF dosyanızı yükleyin.

```java
import com.groupdocs.annotation.Annotator;

// Açıklama eklemek istediğiniz belgeyi yükleyin
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Cevaplarla Yorumlar Oluşturun**
Alt çizgi açıklamasıyla ilişkili yorumları tanımlayın.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Alt Çizgi Açıklaması için Noktaları Tanımlayın**
Alt çizginin nerede görüneceğini belirlemek için koordinatları ayarlayın.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Alt Çizgili Açıklama Oluşturun ve Yapılandırın**
Alt çizgi açıklamasını oluşturun ve renk, opaklık ve yorumlar gibi özelliklerini ayarlayın.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // ARGB formatında sarı
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Açıklamalı Belgeyi Kaydedin**
Değişikliklerinizi yeni bir dosyaya kaydedin.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Sorun Giderme İpuçları
- Noktalara ait tüm koordinatların belge sınırları içerisinde olduğundan emin olun.
- Şunu doğrulayın: `outputPath` dizin mevcuttur ve yazılabilir.

### Özellik 2: Belgeyi Açıklama Olmadan Kaydet

Bu bölümde daha önce açıklama eklenmiş bir belgeden tüm açıklamaların nasıl kaldırılacağı anlatılmaktadır.

#### Genel bakış
Paylaşım veya arşivleme amacıyla belgenizin herhangi bir açıklama içermeyen temiz bir sürümünü kaydetmeniz gerekebilir.

#### Adım Adım Uygulama

**1. Açıklamalı Belge ile Açıklamacıyı Başlatın**
Mevcut ek açıklamalara sahip belgeyi yükleyin.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Açıklamaları Kaldırmak için Kaydetme Seçeneklerini Yapılandırın**
Çıktı dosyasında hiçbir açıklamanın kaydedilmeyeceğini belirtin.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Belgeyi Açıklamalar Olmadan Kaydedin**
Temizlenen belgenin yolunu tanımlayın ve kaydedin.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Pratik Uygulamalar

İşte bu özelliklerin faydalı olabileceği bazı gerçek dünya senaryoları:
1. **Belge İncelemesi**:Bir sözleşmenin veya raporun bölümlerini incelemek ve yorumlamak.
2. **Eğitim Araçları**:Öğrenciler için ders kitaplarına notlar veya düzeltmeler eklemek.
3. **İşbirlikli Düzenleme**:Geri bildirim için ekip üyeleri arasında açıklamalı taslakların paylaşılması.
4. **Yasal Belgeler**:Tartışmalar sırasında hukuki belgelerdeki önemli maddelerin altını çizmek.
5. **Pazarlama Materyalleri**: Broşürlerde dağıtımdan önce önemli bilgilerin vurgulanması.

## Performans Hususları
GroupDocs.Annotation ile çalışırken performansı optimize etmek için şu ipuçlarını göz önünde bulundurun:
- **Bellek Yönetimi**: Uygun şekilde bertaraf edin `Annotator` kaynakları serbest bırakmak için nesneler.
- **Toplu İşleme**: Birden fazla belgeye açıklama eklenecekse, sistem yükünü etkili bir şekilde yönetmek için bunları toplu olarak işleyin.
- **Kaynak Tahsisi**:Ortamınızın büyük dosyaları işlemek için yeterli belleğe ve işlem gücüne sahip olduğundan emin olun.

## Çözüm
GroupDocs.Annotation for Java kullanarak alt çizgi açıklamalarının nasıl ekleneceğini ve kaldırılacağını öğrendiniz. Bu eğitim, Annotator sınıfının başlatılmasını, açıklamalarla açıklamaların yapılandırılmasını ve herhangi bir açıklama olmadan belgelerin kaydedilmesini kapsıyordu. 

Daha detaylı araştırma için bu özellikleri mevcut belge yönetim sistemlerinize entegre etmeyi veya GroupDocs tarafından sağlanan diğer açıklama türlerini denemeyi düşünebilirsiniz.

## SSS Bölümü
1. **Tek bir çalışmada birden fazla alt çizgi açıklamasını nasıl yapılandırabilirim?**
   - Birden fazla oluştur `UnderlineAnnotation` nesneleri ve bunları sırayla kullanarak ekleyin `annotator.add()` yöntem.
2. **Bu kütüphaneyi kullanarak PDF'lerdeki resimlere açıklama ekleyebilir miyim?**
   - Evet, GroupDocs.Annotation PDF gibi belgelerdeki resimlere açıklama eklemeyi destekler.
3. **GroupDocs.Annotation hangi dosya formatlarını destekler?**
   - PDF, Word, Excel ve daha fazlası dahil olmak üzere çeşitli belge formatlarını destekler.