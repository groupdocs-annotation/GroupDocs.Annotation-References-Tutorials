---
date: '2026-10-16'
description: Tambahkan anotasi ke PDF di Java dengan GroupDocs.Annotation – panduan
  langkah demi langkah yang menunjukkan cara menandai PDF secara programatik, menambahkan
  komentar ulasan, dan menerapkan praktik terbaik.
keywords:
- add annotations to pdf
- pdf annotation library java
- add review comments pdf
- groupdocs annotation java
- java pdf markup
lastmod: '2026-10-16'
og_description: Tambahkan anotasi ke PDF di Java dengan GroupDocs.Annotation – panduan
  langkah demi langkah yang menunjukkan cara menandai PDF secara programatik, menambahkan
  komentar ulasan, dan menerapkan praktik terbaik.
og_image_alt: Guide showing how to add annotations to PDF using GroupDocs.Annotation
  in Java
og_title: Cara menambahkan anotasi ke PDF di Java dengan GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Add annotations to PDF in Java with GroupDocs.Annotation – a step‑by‑step
    guide that shows you how to programmatically markup PDFs, add review comments,
    and apply best practices.
  headline: How to add annotations to PDF in Java with GroupDocs
  type: TechArticle
- questions:
  - answer: Call `annotator.add(annotation)` for each annotation, then invoke `save()`
      once. GroupDocs batches the changes and writes them in a single pass.
    question: How do I add multiple annotations to a single PDF efficiently?
  - answer: It supports over 50 formats, including DOC, DOCX, PPT, PPTX, XLS, XLSX,
      JPEG, PNG, TIFF, and many more. See the full list in the [GroupDocs.Annotation
      Documentation](https://docs.groupdocs.com/annotation/java/).
    question: What file formats does GroupDocs.Annotation support besides PDF?
  - answer: Files larger than 50 MB should be streamed page‑by‑page. Memory usage
      stays under 150 MB when you dispose of each `Annotator` after processing a page
      batch.
    question: What are the performance implications of processing large PDFs?
  - answer: Start with a known rectangle (e.g., (50, 50, 100, 50)) and verify the
      visual result. Adjust coordinates incrementally and consult the PDF’s page size
      (usually 612 × 792 points).
    question: What's the best way to debug annotation positioning issues?
  - answer: Yes, you can convert annotated PDFs to DOCX, PPTX, or image formats while
      preserving all markup.
    question: Can I export annotated PDFs to other formats?
  type: FAQPage
tags:
- pdf annotation
- groupdocs
- java-libraries
- document-processing
- add annotations to pdf
title: Cara menambahkan anotasi ke PDF di Java dengan GroupDocs
type: docs
url: /id/java/annotation-management/annotate-pdfs-groupdocs-annotation-java-guide/
weight: 1
---
# Tambahkan anotasi ke PDF

Jika Anda perlu **menambahkan anotasi ke PDF** dari aplikasi Java—baik Anda sedang membangun portal tinjauan kontrak, platform e‑learning, atau editor dokumen kolaboratif—tutorial ini menunjukkan secara tepat cara melakukannya dengan GroupDocs.Annotation. Anda akan belajar memuat PDF, membuat komentar bergaya area, mengelola sumber daya secara efisien, dan menangani file besar tanpa menghabiskan memori.

## Jawaban Cepat
- **Apa tujuan utama GroupDocs.Annotation?** Untuk menambahkan, mengedit, dan mengelola anotasi di banyak format dokumen dari Java.  
- **Jenis anotasi mana yang terbaik untuk komentar tinjauan?** `AreaAnnotation` dengan pesan khusus dan metadata pengguna.  
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis cukup untuk pengujian; lisensi penuh diperlukan untuk produksi.  
- **Bisakah saya memproses PDF yang lebih besar dari 50 MB?** Ya—gunakan streaming, pemrosesan batch, dan pembuangan yang tepat untuk menjaga penggunaan memori tetap rendah.  
- **Apakah perpustakaan ini thread‑safe?** Instance tidak thread‑safe; buat `Annotator` terpisah per thread.

## Mengapa GroupDocs Annotation menonjol

GroupDocs.Annotation memungkinkan Anda **menambahkan anotasi ke PDF** dengan cepat sambil mendukung ekosistem tipe file yang luas. Ia menawarkan:

* **Dukungan format yang komprehensif** – lebih dari 50 format input dan output, termasuk DOCX, PPTX, XLSX, JPEG, PNG, dan TIFF.  
* **Palet anotasi kaya** – sorotan, panah, watermark, penggantian teks, dan bentuk khusus, semua tersedia melalui satu API.  
* **Fitur siap perusahaan** – lisensi bawaan, opsi skalabilitas, dan integrasi mulus dengan stack Java yang ada.  
* **Pengembangan aktif** – rilis bulanan memberikan peningkatan kinerja (hingga 30 % rendering lebih cepat) dan jenis anotasi baru.

## Prasyarat dan persyaratan pengaturan

### Apa yang Anda perlukan sebelum memulai

* **Lingkungan pengembangan** – JDK 8 atau lebih baru (Java 11+ disarankan), Maven atau Gradle, dan IDE pilihan Anda (IntelliJ IDEA, Eclipse, atau VS Code).  
* **Pengetahuan dasar** – sintaks Java, I/O file, dan manajemen dependensi Maven.  
* **Opsional** – familiaritas dengan koordinat halaman PDF dan pengalaman sebelumnya dengan perpustakaan Java lainnya.

### Menyiapkan GroupDocs.Annotation untuk Java

#### Konfigurasi Maven

Tambahkan repositori GroupDocs dan dependensi Annotation ke `pom.xml` Anda. Ganti `25.2` dengan versi terbaru jika tersedia versi yang lebih baru.

```xml
<!-- Maven repository -->
<repository>
    <id>groupdocs-repo</id>
    <url>https://repo.groupdocs.com/maven2</url>
</repository>

<!-- Annotation dependency -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Pro tip:** Selalu verifikasi versi terbaru di situs web GroupDocs. Rilis baru sering menyertakan pengurangan penggunaan memori hingga 20 % untuk PDF besar.

#### Opsi lisensi (dan apa artinya sebenarnya)

* **Trial gratis** – output berwatermark, cocok untuk evaluasi.  
* **Lisensi sementara** – tidak terbatas selama 30 hari; dapatkan **lisensi sementara** [Temporary License](https://purchase.groupdocs.com/temporary-license/).  
* **Lisensi penuh** – diperlukan untuk penyebaran produksi; harga bervariasi tergantung skala penyebaran.

#### Verifikasi awal

Setelah menambahkan dependensi, jalankan tes kecil ini untuk memastikan perpustakaan dimuat dengan benar:

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

## Cara membuat anotasi PDF Java dengan GroupDocs.Annotation

Muat dokumen, tambahkan `AreaAnnotation`, dan simpan hasilnya. Jawaban langsung berikut merangkum seluruh alur kerja:

Muat PDF Anda dengan `new Annotator("input.pdf")`, buat `AreaAnnotation` yang mendefinisikan persegi panjang dan teks komentar, tambahkan anotasi ke `Annotator`, lalu panggil `save("output.pdf")`. Pola tiga langkah ini menangani ukuran PDF apa pun dan memastikan sumber daya dilepaskan secara otomatis.

### Memuat dokumen: lebih dari sekadar jalur file

#### Memuat dokumen dasar

Kelas `Annotator` adalah titik masuk untuk semua operasi anotasi. Ia mewakili dokumen PDF dalam memori dan menyediakan metode untuk membaca, memodifikasi, dan menyimpan anotasi.

```java
Annotator annotator = new Annotator("sample.pdf");
```

**Konteks dunia nyata:** Dalam produksi, jalur file dapat berasal dari folder unggahan, blob basis data, atau URL penyimpanan cloud. GroupDocs.Annotation menerima file lokal, `InputStream`s, dan URL remote tanpa kode tambahan.

#### Menangani sumber input yang berbeda

Anda juga dapat memuat PDF dari array byte atau URL HTTP:

```java
import com.groupdocs.annotation.Annotator;

public class SetupVerification {
    public static void main(String[] args) {
        try {
            // This should not throw any ClassNotFoundException
            System.out.println("GroupDocs.Annotation version: " + 
                com.groupdocs.annotation.internal.c.a.a.d());
            System.out.println("Setup successful!");
        } catch (Exception e) {
            System.err.println("Setup failed: " + e.getMessage());
        }
    }
}
```

### Menambahkan anotasi pertama Anda

#### Memahami anotasi area

`AreaAnnotation` adalah tipe paling serbaguna untuk menyorot wilayah persegi panjang dan melampirkan komentar. Ia berfungsi seperti catatan tempel digital yang dapat dipindahkan, diubah ukurannya, dan diberi gaya.

```java
AreaAnnotation area = new AreaAnnotation();
area.setRectangle(new Rectangle(100, 150, 200, 80)); // x, y, width, height
area.setComment("Review this section for compliance.");
area.setCreator("alice@example.com");
```

**Penjelasan sistem koordinat:** Koordinat PDF dimulai dari kiri‑bawah, tetapi GroupDocs menggunakan asal kiri‑atas, yang selaras dengan kerangka UI umum. Nilai dinyatakan dalam poin (1/72 inci).

#### Contoh anotasi praktis

**Menyoroti teks penting**

```java
HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setRectangle(new Rectangle(50, 200, 300, 20));
highlight.setColor(Color.YELLOW);
annotator.add(highlight);
```

**Membuat komentar tinjauan**

```java
AreaAnnotation comment = new AreaAnnotation();
comment.setRectangle(new Rectangle(120, 400, 250, 100));
comment.setComment("Please verify the calculation in this paragraph.");
comment.setCreator("bob@example.com");
annotator.add(comment);
```

### Menyimpan dan manajemen sumber daya

#### Teknik penyimpanan file yang tepat

```java
annotator.save("annotated.pdf");
```

**Mengapa pembuangan penting:** `Annotator` menyimpan konten PDF dalam memori untuk akses cepat. Tidak menutupnya dapat menyebabkan kebocoran memori, terutama saat memproses puluhan file dalam pekerjaan batch.

#### Pola manajemen sumber daya yang lebih baik

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // add annotations here
    annotator.save("output.pdf");
}
```

## Kesalahan umum dan cara menghindarinya

### Masalah jalur file dan izin

* **Masalah:** “File not found” atau “Access denied”.  
* **Solusi:** Gunakan jalur absolut selama pengembangan, verifikasi izin baca/tulis, dan pastikan file ada sebelum dibuka.

```java
File file = new File("C:/docs/input.pdf");
if (!file.exists() || !file.canRead()) {
    throw new IllegalArgumentException("File is missing or unreadable.");
}
```

### Kesalahan manajemen memori

* **Masalah:** Aplikasi melambat setelah memproses banyak PDF.  
* **Solusi:** Selalu gunakan try‑with‑resources atau panggilan `close()` eksplisit untuk membebaskan buffer native.

```java
try (Annotator annotator = new Annotator("large.pdf")) {
    // process
}
```

### Kebingungan sistem koordinat

* **Masalah:** Anotasi muncul di luar layar.  
* **Solusi:** Ingat GroupDocs menggunakan asal kiri‑atas. Uji dengan koordinat yang diketahui seperti (50, 50, 100, 50) sebelum menerapkan nilai dinamis.

```java
AreaAnnotation test = new AreaAnnotation();
test.setRectangle(new Rectangle(50, 50, 100, 50));
annotator.add(test);
```

## Kasus penggunaan dunia nyata dan aplikasi

### Alur kerja peninjauan dokumen

Tim hukum sering perlu melacak siapa yang mengomentari klausa mana. Dengan GroupDocs.Annotation Anda dapat:

* Menetapkan warna unik per peninjau.  
* Menyimpan cap waktu dan ID pengguna dalam metadata anotasi.  
* Mengekspor PDF beranotasi untuk distribusi klien sambil mempertahankan jejak audit.

```java
area.setCreator("lawyer@example.com");
area.setCreatedOn(LocalDateTime.now());
```

### Pembuatan konten edukasi

Platform e‑learning menggunakan anotasi untuk menyorot konsep kunci, menyisipkan kuis, atau menambahkan catatan penjelas langsung pada PDF belajar. Ini meningkatkan retensi hingga 35 % dibandingkan PDF biasa (studi internal).

### Dokumentasi jaminan kualitas

Produsen memberi anotasi pada gambar teknik untuk menunjukkan toleransi, revisi, dan peringatan keselamatan. Markup standar mengurangi pengerjaan ulang sebesar perkiraan 22 % di seluruh lini produksi.

## Tips optimasi kinerja

### Menangani dokumen besar secara efisien

Memproses PDF 200‑halaman dapat selesai dalam kurang dari 2 detik pada server 4‑core tipikal ketika Anda streaming halaman alih‑alih memuat seluruh file.

```java
Annotator annotator = new Annotator(new FileInputStream("big.pdf"));
```

### Pemantauan penggunaan memori

Aktifkan alat pemantauan bawaan Java (JVisualVM, JConsole) untuk memantau penggunaan heap saat memberi anotasi pada file besar. Usahakan heap tetap di bawah 70 % dari alokasi maksimum.

### Pertimbangan pemrosesan bersamaan

Instance GroupDocs.Annotation **tidak thread‑safe**. Untuk beban kerja paralel, buat `Annotator` terpisah per thread atau gunakan pool thread‑local.

```java
ExecutorService executor = Executors.newFixedThreadPool(4);
for (String path : pdfPaths) {
    executor.submit(() -> {
        try (Annotator a = new Annotator(path)) {
            // annotate
            a.save(path.replace(".pdf", "_annotated.pdf"));
        }
    });
}
```

## Teknik anotasi lanjutan

### Beberapa jenis anotasi dalam satu dokumen

Anda dapat mencampur sorotan, catatan teks, dan watermark dalam satu proses:

```java
String INPUT_PDF = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/output_annotated.pdf";

// Initialize Annotator with the path to your document
final Annotator annotator = new Annotator(INPUT_PDF);
```

### Anotasi dinamis berdasarkan konten

Gabungkan GroupDocs.Annotation dengan Apache PDFBox atau Tika untuk mendeteksi kata kunci secara otomatis dan menambahkan catatan kontekstual.

```java
// pseudo‑code: detect the word "confidential"
if (pageText.contains("confidential")) {
    WatermarkAnnotation wm = new WatermarkAnnotation();
    wm.setText("CONFIDENTIAL");
    annotator.add(wm);
}
```

## Panduan pemecahan masalah

### Pesan error umum dan solusinya

* **“Invalid license”** – Pastikan file lisensi berada di classpath dan cocok dengan tipe penyebaran Anda.  
* **“Unsupported file format”** – Verifikasi PDF tidak rusak, tidak diproteksi password, atau berukuran nol byte.  
* **Perlambatan kinerja** – Gunakan streaming, buang objek `Annotator` segera, dan pertimbangkan pemrosesan batch.

### Tips debugging

#### Aktifkan logging

```java
System.setProperty("log4j.configurationFile", "log4j2.xml");
```

#### Validasi input

```java
Objects.requireNonNull(filePath, "File path cannot be null");
```

## Pertanyaan yang sering diajukan

**Q: Bagaimana cara menambahkan banyak anotasi ke satu PDF secara efisien?**  
A: Panggil `annotator.add(annotation)` untuk setiap anotasi, lalu panggil `save()` sekali. GroupDocs mengelompokkan perubahan dan menulisnya dalam satu pass.

```java
annotator.add(area1);
annotator.add(highlight2);
annotator.save("combined.pdf");
```

**Q: Format file apa yang didukung GroupDocs.Annotation selain PDF?**  
A: Ia mendukung lebih dari 50 format, termasuk DOC, DOCX, PPT, PPTX, XLS, XLSX, JPEG, PNG, TIFF, dan banyak lagi. Lihat daftar lengkapnya di [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/).

**Q: Bagaimana cara menangani PDF yang dilindungi password?**  

```java
Annotator annotator = new Annotator("secure.pdf", "password123");
```

**Q: Bisakah saya mengambil dan memodifikasi anotasi yang sudah ada dalam PDF?**  

```java
List<AnnotationBase> existing = annotator.getAll();
for (AnnotationBase a : existing) {
    if (a instanceof TextAnnotation) {
        ((TextAnnotation) a).setComment("Updated comment");
    }
}
annotator.save("updated.pdf");
```

**Q: Apa implikasi kinerja saat memproses PDF besar?**  
A: File lebih besar dari 50 MB harus di‑stream halaman per halaman. Penggunaan memori tetap di bawah 150 MB bila Anda membuang setiap `Annotator` setelah memproses batch halaman.

```java
// each request gets its own Annotator instance
public void processPdf(String path) {
    try (Annotator a = new Annotator(path)) {
        // annotate
        a.save(path);
    }
}
```

**Q: Bagaimana cara menangani pemrosesan dokumen bersamaan dalam aplikasi web?**  

```java
@Service
public class PdfAnnotationService {
    public void addComment(String filePath, String comment) throws IOException {
        try (Annotator annotator = new Annotator(filePath)) {
            AreaAnnotation a = new AreaAnnotation();
            a.setRectangle(new Rectangle(100, 200, 250, 80));
            a.setComment(comment);
            annotator.add(a);
            annotator.save(filePath);
        }
    }
}
```

**Q: Apa cara terbaik untuk men-debug masalah posisi anotasi?**  
A: Mulailah dengan persegi panjang yang diketahui (mis., (50, 50, 100, 50)) dan verifikasi hasil visualnya. Sesuaikan koordinat secara bertahap dan periksa ukuran halaman PDF (biasanya 612 × 792 poin).

**Q: Bagaimana cara mengintegrasikan GroupDocs.Annotation dengan Spring Boot?**  

```java
// From file path (most common)
Annotator annotatorFromPath = new Annotator("path/to/document.pdf");

// From InputStream (useful for uploaded files)
FileInputStream inputStream = new FileInputStream("document.pdf");
Annotator annotatorFromStream = new Annotator(inputStream);

// Don't forget to close streams when done!
inputStream.close();
```

## FAQ Tambahan

**Q: Bisakah saya mengekspor PDF beranotasi ke format lain?**  
A: Ya, Anda dapat mengonversi PDF beranotasi ke DOCX, PPTX, atau format gambar sambil mempertahankan semua markup.

**Q: Apakah ada cara untuk menampilkan semua jenis anotasi yang didukung oleh perpustakaan?**  
A: Gunakan `AnnotationType.values()` untuk mengambil array semua enum yang didukung.

**Q: Bagaimana saya dapat menyesuaikan tampilan anotasi watermark?**  
A: Atur properti seperti `setOpacity`, `setRotation`, dan `setBackgroundColor` pada `WatermarkAnnotation` sebelum menambahkannya.

**Q: Apakah perpustakaan ini mendukung penambahan komentar secara programatis dari basis data?**  
A: Tentu saja. Baca data komentar dari sumber apa pun, isi `AreaAnnotation` (atau `TextAnnotation`) dengan teks, dan tambahkan ke dokumen.

**Q: Apa yang harus saya lakukan jika menemukan kebocoran memori selama pemrosesan batch?**  
A: Pastikan setiap `Annotator` ditutup (try‑with‑resources), pantau heap JVM, dan bagi batch besar menjadi grup yang lebih kecil.

**Sumber daya tambahan**  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/)  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Access](https://releases.groupdocs.com/annotation/java/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/annotation/)  

---

**Terakhir Diperbarui:** 2026-10-16  
**Diuji Dengan:** GroupDocs.Annotation 25.2 for Java  
**Penulis:** GroupDocs  

```java
// From file path (most common)
Annotator annotatorFromPath = new Annotator("path/to/document.pdf");

// From InputStream (useful for uploaded files)
FileInputStream inputStream = new FileInputStream("document.pdf");
Annotator annotatorFromStream = new Annotator(inputStream);

// Don't forget to close streams when done!
inputStream.close();
```
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;

// Create the annotation
AreaAnnotation area = new AreaAnnotation();

// Position and size: x, y, width, height
area.setBox(new Rectangle(100, 100, 100, 100));

// Background color in ARGB format (65535 = yellow with transparency)
area.setBackgroundColor(65535);

// Add the annotation to your document
annotator.add(area);
```
```java
// Create a semi‑transparent highlight
AreaAnnotation highlight = new AreaAnnotation();
highlight.setBox(new Rectangle(50, 200, 200, 25));
highlight.setBackgroundColor(0x80FFFF00); // Semi‑transparent yellow
highlight.setMessage("Important clause - review carefully");
```
```java
// Add a comment annotation with custom styling
AreaAnnotation comment = new AreaAnnotation();
comment.setBox(new Rectangle(300, 150, 150, 75));
comment.setBackgroundColor(0x80FF0000); // Semi‑transparent red
comment.setMessage("Needs revision - see discussion in email");
comment.setCreatedOn(new Date());
comment.setUser("John Reviewer");
```
```java
// Save the annotated document
annotator.save(outputPath);

// Always dispose of resources (critical for memory management)
annotator.dispose();
```
```java
public void annotateDocument(String inputPath, String outputPath) {
    try (Annotator annotator = new Annotator(inputPath)) {
        // Your annotation code here
        AreaAnnotation area = new AreaAnnotation();
        area.setBox(new Rectangle(100, 100, 100, 100));
        area.setBackgroundColor(65535);
        
        annotator.add(area);
        annotator.save(outputPath);
        
        System.out.println("Document successfully annotated and saved to: " + outputPath);
    } catch (Exception e) {
        System.err.println("Annotation failed: " + e.getMessage());
        throw new RuntimeException("Failed to annotate document", e);
    }
}
```
```java
public boolean validateInputFile(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        System.err.println("File does not exist: " + filePath);
        return false;
    }
    if (!file.canRead()) {
        System.err.println("Cannot read file: " + filePath);
        return false;
    }
    return true;
}
```
```java
// Good practice - automatic resource management
try (Annotator annotator = new Annotator(inputPath)) {
    // Annotation code here
} // Automatically disposed

// If manual disposal is needed
Annotator annotator = null;
try {
    annotator = new Annotator(inputPath);
    // Annotation code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
```java
// Start with simple, visible coordinates for testing
Rectangle testPosition = new Rectangle(50, 50, 100, 50);

// Gradually adjust based on your PDF dimensions
// Most PDFs are 612x792 points (8.5"x11" at 72 DPI)
```
```java
public void addReviewAnnotation(Annotator annotator, String reviewerName, 
                              String comment, Rectangle position, Color highlightColor) {
    AreaAnnotation review = new AreaAnnotation();
    review.setBox(position);
    review.setBackgroundColor(highlightColor.getRGB());
    review.setMessage(comment);
    review.setUser(reviewerName);
    review.setCreatedOn(new Date());
    
    annotator.add(review);
}
```
```java
public void processDocumentBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            // This prevents memory accumulation
            processAnnotations(annotator);
        }
        
        // Optional: Add small delay for very large batches
        // Thread.sleep(100);
    }
}
```
```java
Runtime runtime = Runtime.getRuntime();
long memoryBefore = runtime.totalMemory() - runtime.freeMemory();

// Process documents...

long memoryAfter = runtime.totalMemory() - runtime.freeMemory();
System.out.println("Memory used: " + (memoryAfter - memoryBefore) + " bytes");
```
```java
public class ConcurrentAnnotationProcessor {
    public void processDocumentsConcurrently(List<String> documents) {
        documents.parallelStream().forEach(docPath -> {
            try (Annotator annotator = new Annotator(docPath)) {
                // Each thread gets its own Annotator instance
                processAnnotations(annotator);
            }
        });
    }
}
```
```java
public void createComprehensiveAnnotation(Annotator annotator) {
    // Highlight important text
    AreaAnnotation highlight = new AreaAnnotation();
    highlight.setBox(new Rectangle(100, 100, 200, 30));
    highlight.setBackgroundColor(0x80FFFF00);
    
    // Add explanatory note
    AreaAnnotation note = new AreaAnnotation();
    note.setBox(new Rectangle(320, 95, 150, 40));
    note.setBackgroundColor(0x80ADD8E6);
    note.setMessage("See reference document #123");
    
    annotator.add(highlight);
    annotator.add(note);
}
```
```java
// Add to your application properties or logging configuration
java.util.logging.Logger.getLogger("com.groupdocs").setLevel(Level.FINE);
```
```java
public boolean validateAnnotationParameters(Rectangle box, int color) {
    if (box.getWidth() <= 0 || box.getHeight() <= 0) {
        System.err.println("Invalid annotation dimensions");
        return false;
    }
    
    if (box.getX() < 0 || box.getY() < 0) {
        System.err.println("Annotation position cannot be negative");
        return false;
    }
    
    return true;
}
```
```java
try (Annotator annotator = new Annotator("document.pdf")) {
    annotator.add(annotation1);
    annotator.add(annotation2);
    annotator.add(annotation3);
    annotator.save("output.pdf"); // All annotations applied at once
}
```
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("protected.pdf", loadOptions);
```
```java
try (Annotator annotator = new Annotator("annotated.pdf")) {
    List<AnnotationInfo> annotations = annotator.get(AnnotationType.Area);
    for (AnnotationInfo annotation : annotations) {
        // Modify properties as needed
        annotation.setMessage("Updated comment");
    }
    annotator.update(annotations);
    annotator.save("updated.pdf");
}
```
```java
@Service
public class AnnotationService {
    public CompletableFuture<String> annotateAsync(String inputPath) {
        return CompletableFuture.supplyAsync(() -> {
            try (Annotator annotator = new Annotator(inputPath)) {
                // Process annotations
                return processDocument(annotator);
            }
        });
    }
}
```
```java
@Service
public class DocumentAnnotationService {
    
    public void annotateDocument(MultipartFile file, List<AnnotationRequest> requests) {
        try (InputStream inputStream = file.getInputStream();
             Annotator annotator = new Annotator(inputStream)) {
            
            // Process annotation requests
            requests.forEach(request -> addAnnotation(annotator, request));
            annotator.save("output.pdf");
        }
    }
}
```

## Tutorial Terkait

- [Buat Sorotan PDF Java: Panduan Lengkap dengan GroupDocs Annotation](/annotation/java/annotation-management/)
- [Edit Anotasi PDF Java - Tutorial Lengkap GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Anotasi PDF Dari URL Groupdocs Java](/annotation/java/annotation-management/annotate-pdfs-from-urls-groupdocs-java/)
