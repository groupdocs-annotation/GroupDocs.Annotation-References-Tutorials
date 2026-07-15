---
categories:
- Java Development
date: '2026-05-16'
description: Pelajari cara membuat balasan anotasi java menggunakan GroupDocs.Annotation.
  Kuasai anotasi PDF di Java dengan contoh praktis, tips kinerja, dan praktik terbaik.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Tutorial Anotasi PDF Java
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
title: 'Perpustakaan Anotasi PDF Java: buat balasan anotasi java'
type: docs
url: /id/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Perpustakaan Anotasi PDF Java: buat balasan anotasi java

Jika Anda perlu **create annotation reply java** untuk PDF—apakah Anda sedang membangun portal peninjauan kontrak, sistem e‑learning, atau pipeline pemrosesan massal—panduan ini menunjukkan secara tepat cara melakukannya dengan GroupDocs.Annotation untuk Java. Kami akan membahas pengaturan, pembuatan anotasi bergelombang, penelusuran balasan, dan penyetelan kinerja sehingga Anda dapat mengirimkan solusi yang handal dalam hitungan hari, bukan minggu.

## Jawaban Cepat
- **Apa tujuan utama GroupDocs.Annotation?** Itu memungkinkan pembuatan, modifikasi, dan ekstraksi anotasi PDF secara programatis di Java.  
- **Bagaimana cara menambahkan anotasi bergelombang?** Buat instance `SquigglyAnnotation`, atur geometri dan gaya-nya, lalu panggil `annotator.add(...)`.  
- **Bisakah saya melampirkan balasan ke sebuah anotasi?** Ya—buat objek `Reply`, atur penulis dan teks, dan hubungkan mereka dengan anotasi induk.  
- **Apakah saya memerlukan lisensi untuk produksi?** Tentu saja; tanpa lisensi yang valid output akan berisi watermark.  
- **Apakah cocok untuk pemrosesan batch?** Ya—gunakan try‑with‑resources untuk membuka setiap dokumen, memberi anotasi, dan menutupnya, menjaga penggunaan memori tetap rendah.

## Mengapa Pengembang Java Membutuhkan Perpustakaan Anotasi PDF

Menandai PDF secara manual memakan waktu dan rawan kesalahan, terutama ketika Anda harus meninjau ratusan kontrak atau lembar ujian. Perpustakaan anotasi PDF Java mengotomatiskan pekerjaan ini, memungkinkan Anda menyematkan sorotan, garis bawah bergelombang, dan komentar berulir langsung dalam file. Hasilnya adalah dokumen yang dapat dicari, portabel, dan mempertahankan semua markup tanpa memerlukan penampil terpisah.

**Apa yang akan Anda kuasai dalam panduan ini**
- Menginstal dan melisensikan GroupDocs.Annotation dalam proyek Maven  
- Membuat anotasi bergelombang yang tampak seperti garis bawah Word asli  
- Menambahkan balasan berulir ke anotasi apa pun untuk peninjauan kolaboratif  
- Mengoptimalkan penggunaan memori dan CPU saat memproses PDF besar  
- Menyebarkan solusi dalam Spring Boot, micro‑services, atau aplikasi desktop  

Apakah Anda sedang membangun sistem peninjauan dokumen hukum, alat penilaian pendidikan, atau pipeline kontrol kualitas otomatis, teknik di bawah ini akan memberi Anda fondasi siap produksi.

## Apa itu create annotation reply java?

`create annotation reply java` adalah proses programatis untuk melampirkan utas komentar (Reply) ke anotasi PDF yang ada menggunakan Java. Balasan memungkinkan beberapa peninjau mendiskusikan markup tertentu tanpa meninggalkan dokumen, memungkinkan kolaborasi mulus di tempat. Kemampuan ini mengubah PDF statis menjadi platform diskusi interaktif, mempertahankan konteks dan jejak audit langsung dalam file.

## Prasyarat: Menyiapkan Lingkungan Anda

Sebelum kita masuk ke kode, pastikan workstation pengembangan Anda memenuhi spesifikasi berikut:

- **JDK** 8 atau lebih tinggi (JDK 11 + disarankan untuk kinerja garbage‑collection yang lebih baik)  
- **Maven** atau **Gradle** untuk manajemen dependensi (contoh menggunakan Maven)  
- IDE dengan dukungan Maven (IntelliJ IDEA, Eclipse, atau VS Code)  
- Setidaknya **2 GB** RAM bebas untuk IDE dan menjalankan tes  
- File PDF contoh untuk percobaan (Anda dapat membuat PDF sederhana dengan editor PDF apa pun)

GroupDocs.Annotation berjalan sepenuhnya dalam proses; tidak memerlukan penampil PDF eksternal atau pustaka native.

## Menyiapkan GroupDocs.Annotation untuk Java

Mengintegrasikan perpustakaan adalah proses beberapa langkah, tetapi beberapa jebakan tersembunyi dapat menyebabkan kesalahan runtime jika Anda melewatkannya.

### Konfigurasi Dependensi Maven

Tambahkan repositori dan dependensi ke `pom.xml` Anda. Letakkan elemen `<repositories>` **sebelum** `<dependencies>` untuk memastikan Maven dapat menyelesaikan artefak.

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

> **Tips Pro:** Periksa halaman rilis GroupDocs untuk versi terbaru. Rilis baru sering menyertakan dukungan untuk standar PDF yang muncul dan perbaikan kinerja.

### Pengaturan Lisensi (Jangan Lewatkan Ini!)

GroupDocs.Annotation memerlukan file lisensi untuk penggunaan produksi. Tanpanya, setiap PDF yang dihasilkan akan memiliki watermark.

1. **Uji Coba Gratis** – Set fitur lengkap selama 30 hari, ideal untuk evaluasi.  
2. **Lisensi Sementara** – Baik untuk pengembangan dan pengujian internal.  
3. **Lisensi Penuh** – Diperlukan untuk setiap penyebaran komersial.

Tempatkan file `GroupDocs.Annotation.lic` di folder resources Anda dan muat pada saat startup:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Kesalahan umum:** Lupa langkah lisensi menghasilkan PDF berwatermark dan panggilan API yang gagal secara diam-diam. Selalu validasi lisensi di awal rutinitas startup Anda.

## Panduan Implementasi Lengkap: Menambahkan Anotasi Bergelombang

Berikut adalah panduan langkah demi langkah yang menunjukkan cara **create annotation reply java** sambil membuat anotasi bergelombang. Setiap langkah menyertakan penjelasan singkat, sehingga Anda memahami “mengapa” di balik setiap baris.

### Langkah 1: Impor Semua Kelas yang Diperlukan

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` adalah titik masuk untuk semua operasi tingkat dokumen.  
- `Point` mewakili koordinat pada halaman (X dan Y diukur dari kiri‑atas).  
- `SquigglyAnnotation` mendefinisikan garis bawah bergelombang yang digunakan untuk menyoroti kesalahan.  
- `Reply` menyimpan komentar berulir yang terlampir pada anotasi.  
- `SaveOptions` memungkinkan Anda mengontrol format output dan kompresi.

### Langkah 2: Buat dan Konfigurasikan Anotasi Bergelombang Anda

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

SquigglyAnnotation adalah kelas yang membuat garis bawah bergelombang yang digunakan untuk menyoroti kesalahan dalam PDF.

- **Sistem koordinat**: Titik dimulai dari sudut kiri‑atas. Dua titik di atas menggambar garis bergelombang horizontal dari (100, 200) ke (300, 200).  
- **Opacity** 0.7 berarti anotasi 70 % tidak transparan, memungkinkan teks di bawahnya tetap terbaca.

### Langkah 3: Tambahkan Balasan Interaktif (Opsional tetapi Kuat)

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

Reply adalah kelas yang mewakili utas komentar yang terlampir pada anotasi.

- Balasan membuat **diskusi berulir** langsung pada anotasi, meniru pengalaman peninjau PDF modern.  
- Setiap balasan menyimpan informasi penulis dan stempel waktu, yang kemudian dapat Anda filter atau tampilkan di UI.

### Langkah 4: Terapkan Anotasi dan Simpan Dokumen

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- Konstruk **try‑with‑resources** secara otomatis menutup `Annotator`, melepaskan handle file dan buffer native.  
- `save` menulis PDF yang dimodifikasi ke `output.pdf`.  

> **Catatan Memori:** `Annotator` memuat hanya halaman yang Anda sentuh. Untuk PDF ratusan halaman, pendekatan ini menjaga penggunaan heap di bawah 150 MB pada server tipikal.

## Opsi Konfigurasi Lanjutan

### Menyesuaikan Penampilan Anotasi

Anda dapat menyetel halus gaya visual agar sesuai dengan pedoman merek Anda:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** mengontrol ketebalan garis (dalam poin).  
- **ARGB** format menyertakan saluran alfa untuk transparansi.

### Menempatkan Anotasi dengan Presisi

Mendapatkan koordinat yang tepat dapat menjadi rumit pada PDF dengan ukuran halaman yang bervariasi. Ikuti pendekatan sistematis ini:

1. **Buka PDF di penampil** (mis., Adobe Acrobat) dan catat nilai penggaris untuk area target.  
2. **Terjemahkan nilai penggaris** ke poin (1 point = 1/72 inch).  
3. **Gunakan `annotator.getPageInfo(pageIndex)`** untuk mengambil lebar dan tinggi halaman, lalu hitung posisi relatif.

## Masalah Umum dan Solusinya

### Masalah: Anotasi Tidak Muncul

**Penyebab paling mungkin**
- Titik berada di luar batas halaman  
- Lisensi tidak dimuat (watermark menyembunyikan anotasi)  
- Nomor halaman salah (halaman berbasis nol dalam API)  

**Solution checklist**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Masalah: Kinerja Buruk dengan File Besar

Memuat PDF 500‑halaman ke memori dapat memperlambat layanan Anda. Mitigasi dengan:

- **Memproses satu halaman pada satu waktu** – buka dokumen, beri anotasi satu halaman, simpan, lalu lanjut ke berikutnya.  
- **Streaming** – gunakan API streaming `Annotator` untuk menghindari buffering seluruh dokumen.  
- **Caching** – simpan PDF yang sering diakses dalam cache cepat (mis., Redis) dan beri anotasi pada salinan yang di‑cache.

### Masalah: Nilai Warna Tidak Berfungsi

GroupDocs mengharapkan **ARGB** (Alpha, Red, Green, Blue) bukan RGB biasa. Nilai ARGB `0xFFFF0000` berarti merah sepenuhnya tidak transparan. Jika Anda memberikan `0xFF0000` pustaka akan menafsirkannya secara tidak tepat, menghasilkan anotasi hitam.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Praktik Terbaik Kinerja

### Manajemen Memori

Saat memberi anotasi puluhan PDF dalam pekerjaan batch, bungkus setiap file dalam blok try‑with‑resources masing‑masing:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Pola ini menjamin buffer native dilepaskan setelah setiap iterasi, mencegah **OutOfMemoryError** pada proses yang berjalan lama.

### Optimasi Pemrosesan Batch

Untuk lingkungan throughput tinggi, pertimbangkan parallel streams yang digabungkan dengan thread pool terbatas:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Bounded pool** menghindari ledakan thread, sementara parallel streams menjaga inti CPU tetap sibuk.

### Pertimbangan Ukuran File

PDF besar (> 100 MB) dapat menurunkan kinerja. Terapkan strategi berikut:

- **Pra‑kompres** PDF sumber dengan alat seperti Ghostscript sebelum anotasi.  
- **Anotasi hanya halaman yang diperlukan** – lewati halaman yang tidak memerlukan markup.  
- **Bagi** dokumen menjadi bagian logis (mis., per bab) dan proses setiap bagian secara independen.

## Aplikasi Dunia Nyata

### Sistem Peninjauan Dokumen

Firma hukum sering perlu menandai klausa bermasalah. Anotasi bergelombang yang digabungkan dengan balasan berulir memungkinkan beberapa pengacara mendiskusikan satu paragraf tanpa meninggalkan PDF:

- **Pengacara A** menambahkan garis bergelombang merah di bawah klausa dan menulis “Ambiguous wording”.  
- **Pengacara B** membalas “Add definition for ‘material breach’”.  
- Seluruh diskusi tetap tersemat, dapat dicari, dan dapat diaudit.

### Integrasi dengan Sistem yang Ada

GroupDocs.Annotation bekerja mulus dengan kerangka kerja Java populer:

- **Spring Boot** – ekspos endpoint REST `/api/annotate` yang menerima unggahan multipart PDF, menambahkan anotasi, dan mengalirkan hasil kembali.  
- **JSF** – hubungkan tindakan anotasi ke komponen UI untuk markup langsung dalam tampilan web.  
- **Microservices** – jejak kecil pustaka (< 15 MB) memungkinkan Anda mengkontainerkannya dengan Docker dan menskalakan secara horizontal.

### Otomatisasi Alur Kerja

Gabungkan anotasi dengan produk GroupDocs lainnya (mis., GroupDocs.Signature) untuk membangun pipeline end‑to‑end:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Kapan Menggunakan Anotasi Bergelombang vs. Alternatif

| Kasus Penggunaan | Anotasi yang Direkomendasikan |
|------------------|------------------------------|
| Menandai kesalahan ejaan atau tata bahasa | **Squiggly** – petunjuk visual mirip dengan pengolah kata |
| Menyoroti bagian penting tanpa menyiratkan kesalahan | **Highlight** – lapisan transparan |
| Memberikan umpan balik terperinci | **Text** atau **Comment** – kotak catatan bebas |
| Menyetujui atau menolak dokumen | **Stamp** – label “Approved” atau “Rejected” |

## Kesimpulan

Anda kini memiliki resep lengkap yang siap produksi untuk **create annotation reply java** menggunakan GroupDocs.Annotation. Dengan menguasai API, menangani lisensi, dan menerapkan tips kinerja di atas, Anda dapat:
- Mengotomatiskan penandaan kesalahan pada ribuan PDF
- Mengaktifkan diskusi kolaboratif berulir di dalam file itu sendiri
- Menjaga penggunaan memori rendah bahkan saat memproses dokumen besar

**Langkah Selanjutnya**
1. Bereksperimen dengan tipe anotasi lain (highlight, stamp, text).  
2. Bangun layanan REST yang menerima PDF, memberi anotasi, dan mengembalikan hasilnya.  
3. Jelajahi API ekstraksi (`annotator.get()`) untuk mengambil komentar yang ada untuk analitik.  

Kekuatan anotasi PDF secara programatis terletak pada kemampuannya menggantikan markup manual yang melelahkan dengan kode yang dapat diulang dan diaudit. Baik Anda membangun produk legal‑tech khusus atau mesin alur kerja dokumen umum, teknik dalam panduan ini memberi Anda fondasi kuat untuk melangkah maju.

## Pertanyaan yang Sering Diajukan

**Q: Apa yang membuat GroupDocs.Annotation lebih baik daripada perpustakaan PDF Java lainnya?**  
A: GroupDocs.Annotation berfokus secara eksklusif pada alur kerja anotasi, menawarkan lebih dari 30 tipe anotasi, balasan berulir, dan dukungan native untuk lebih dari 50 format file sambil menjaga jejak memori di bawah 200 MB untuk PDF 500‑halaman.

**Q: Bisakah saya menggunakan perpustakaan ini dengan aplikasi Spring Boot?**  
A: Tentu saja. Buat `@RestController` yang menyuntikkan layanan `Annotator`, memproses unggahan multipart, dan mengalirkan PDF yang telah dianotasi kembali ke klien. Ingat untuk mengonfigurasi thread‑pool untuk permintaan bersamaan.

**Q: Bagaimana cara menangani dokumen dengan ukuran halaman yang berbeda?**  
A: Query dimensi setiap halaman melalui `annotator.getPageInfo(pageIndex)` dan hitung koordinat relatif (mis., persentase) alih-alih mengkodekan nilai poin secara keras. Ini memastikan anotasi muncul dengan benar pada halaman A4, Letter, dan ukuran khusus.

**Q: Apakah ada cara untuk mengekstrak anotasi yang ada dari PDF?**  
A: Ya. Panggil `annotator.get()` untuk mengambil koleksi semua anotasi, lalu iterasi untuk membaca properti seperti penulis, komentar, dan geometri. Ini berguna untuk skenario migrasi atau analitik.

**Q: Apa pendekatan terbaik untuk menangani izin anotasi dalam sistem multi‑pengguna?**  
A: Terapkan autentikasi di lapisan aplikasi, simpan ID pengguna dengan setiap `Reply`, dan terapkan aturan bisnis (mis., hanya penulis atau admin yang dapat mengedit atau menghapus balasan). API itu sendiri tidak menegakkan izin, memberi Anda fleksibilitas penuh.

**Q: Bagaimana cara mengoptimalkan penggunaan memori saat memproses ratusan PDF?**  
A: Gunakan try‑with‑resources untuk setiap dokumen, proses halaman secara individual, dan pertimbangkan thread pool terbatas untuk membatasi konsumsi memori bersamaan. Memantau heap JVM dengan alat seperti VisualVM membantu Anda menyesuaikan pengaturan `-Xmx`.

**Terakhir Diperbarui:** 2026-05-16  
**Diuji Dengan:** GroupDocs.Annotation 25.2 untuk Java  
**Penulis:** GroupDocs  

**Sumber Daya Tambahan**
- [Dokumentasi GroupDocs.Annotation untuk Java](https://docs.groupdocs.com/annotation/java/)
- [Referensi API Lengkap](https://reference.groupdocs.com/annotation/java/)

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

## Tutorial Terkait

- [Tutorial Perpustakaan Anotasi PDF Java](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Hapus Balasan Anotasi Java - Kelola Balasan berdasarkan ID dengan GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Edit Anotasi PDF Java - Tutorial Lengkap GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)