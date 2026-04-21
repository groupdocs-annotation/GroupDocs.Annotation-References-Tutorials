---
categories:
- Java Development
date: '2026-03-24'
description: Pelajari cara membuat file PDF Java yang bersih, mengelola memori PDF
  Java, dan memberi anotasi PDF di Java menggunakan GroupDocs.Annotation, lengkap
  dengan contoh kode dan tips pemecahan masalah.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Buat PDF Bersih dengan Java: Anotasi Garis Bawah menggunakan GroupDocs'
type: docs
url: /id/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Buat PDF Java Bersih: Anotasi Garis Bawah dengan GroupDocs

Jika Anda perlu **membuat PDF Java bersih** dan menambahkan anotasi kolaboratif, Anda berada di tempat yang tepat. Kesulitan dengan manajemen dokumen dan kolaborasi dalam aplikasi Java Anda? Anda tidak sendirian. Banyak pengembang menghadapi tantangan dalam mengimplementasikan fitur anotasi dokumen yang kuat dan dapat diandalkan di berbagai format file.

Dalam panduan ini, Anda akan **membuat PDF Java bersih** dan belajar cara **menambahkan anotasi PDF di Java** menggunakan GroupDocs.Annotation. Pada akhir tutorial, Anda akan tahu persis cara menambahkan anotasi garis bawah dengan komentar, menghapus anotasi yang ada, dan mengintegrasikan fitur‑fitur ini secara mulus ke dalam proyek Anda.

**Apa yang akan Anda kuasai dalam panduan ini:**
- Menyiapkan GroupDocs.Annotation dalam proyek Java Anda (dengan cara yang tepat)  
- Menambahkan anotasi garis bawah dengan komentar khusus dan gaya  
- Menghapus semua anotasi untuk membuat versi dokumen bersih  
- Memecahkan masalah umum yang dihadapi pengembang  
- Mengoptimalkan kinerja untuk aplikasi produksi  

Apakah Anda membangun sistem tinjauan dokumen, platform edukasi, atau alat penyuntingan kolaboratif, tutorial ini mencakup semua yang Anda butuhkan dengan contoh kode yang praktis dan teruji.

## Jawaban Cepat
- **Bagaimana cara menambahkan anotasi garis bawah?** Gunakan `UnderlineAnnotation` dan `annotator.add()` lalu simpan dokumen.  
- **Bagaimana cara membuat file PDF Java bersih?** Muat file yang beranotasi, set `AnnotationType.NONE` pada `SaveOptions`, dan simpan salinan baru.  
- **Perpustakaan apa yang diperlukan?** GroupDocs.Annotation v25.2 (atau lebih baru) dan repositori Maven‑nya.  
- **Apakah saya memerlukan lisensi untuk produksi?** Ya—terapkan lisensi GroupDocs yang valid untuk menghindari watermark.  
- **Bisakah saya memproses banyak dokumen secara efisien?** Bungkus setiap `Annotator` dalam blok try‑with‑resources dan dispose setelah setiap file.

## Cara membuat file PDF Java bersih
Membuat file PDF Java bersih berarti menghasilkan versi dokumen **tanpa anotasi apa pun** sambil mempertahankan konten asli. Ini berguna untuk distribusi akhir, arsip, atau ketika Anda perlu membagikan salinan “bersih” setelah siklus tinjauan.

GroupDocs.Annotation mempermudah hal ini: muat file yang beranotasi, konfigurasikan `SaveOptions` untuk mengecualikan semua tipe anotasi, dan simpan hasilnya. Langkah‑langkahnya diilustrasikan nanti pada bagian **Menghapus Anotasi**.

## Mengapa membuat file PDF Java bersih?
Versi bersih menghilangkan tanda‑tanda reviewer, komentar, dan highlight, memberikan Anda dokumen yang dipoles siap untuk klien, regulator, atau rilis publik. Ini juga mengurangi ukuran file dan mencegah pengungkapan tidak sengaja catatan internal—kritikal untuk alur kerja hukum dan kepatuhan.

## Cara menambahkan anotasi PDF di Java menggunakan GroupDocs
GroupDocs.Annotation menyediakan API yang kaya untuk **menambahkan anotasi PDF di Java**. Ia mendukung berbagai tipe anotasi, termasuk highlight, stamp, dan underline. Dalam tutorial ini kami fokus pada anotasi garis bawah karena sering dipakai untuk menekankan teks sambil memungkinkan komentar beruntai.

## Prasyarat dan Penyiapan Lingkungan

### Apa yang Anda Butuhkan Sebelum Memulai

**Persyaratan Lingkungan Pengembangan:**
- Java Development Kit (JDK) 8 atau lebih tinggi (JDK 11+ disarankan)  
- Maven 3.6+ atau Gradle 6.0+ untuk manajemen dependensi  
- IDE seperti IntelliJ IDEA, Eclipse, atau VS Code dengan ekstensi Java  
- Minimal 2 GB RAM yang tersedia (pemrosesan dokumen dapat intensif memori)

**Prasyarat Pengetahuan:**
Anda sebaiknya sudah nyaman dengan konsep dasar Java—inisialisasi objek, pemanggilan metode, dan dependensi Maven. Pengalaman sebelumnya dengan pustaka pihak ketiga akan mempercepat adopsi.

**Dokumen Pengujian:**
Siapkan beberapa PDF contoh. PDF berbasis teks bekerja paling baik; gambar hasil scan mungkin memerlukan OCR sebelum dapat dianotasi.

### Penyiapan Maven: Menambahkan GroupDocs ke Proyek Anda

Berikut cara mengonfigurasi proyek Maven dengan benar (ini sering membuat bingung banyak pengembang pada percobaan pertama):

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

**Penting:** Versi 25.2 adalah rilis stabil terbaru pada saat penulisan. Periksa repositori GroupDocs secara berkala untuk versi yang lebih baru yang mencakup perbaikan bug dan peningkatan kinerja.

### Penyiapan Lisensi (Jangan Lewatkan Ini)

**Untuk Pengembangan/Pengujian:**  
Unduh trial gratis dari situs web GroupDocs. Trial mencakup semua fitur tetapi menambahkan watermark pada dokumen yang diproses.

**Untuk Produksi:**  
Beli lisensi dan terapkan saat aplikasi dimulai. Tanpa lisensi yang valid, build produksi akan terbatas.

## Panduan Implementasi: Menambahkan Anotasi Garis Bawah

### Memahami Alur Kerja Anotasi

Sebelum masuk ke kode, mari lihat alur kerja empat langkah yang terjadi ketika Anda **menambahkan anotasi PDF di Java**:

1. **Pemuatan Dokumen** – `Annotator` membaca file ke memori.  
2. **Pembuatan Anotasi** – Tentukan properti seperti posisi, gaya, dan komentar.  
3. **Penerapan Anotasi** – Perpustakaan menyuntikkan anotasi ke struktur PDF.  
4. **Penyimpanan Dokumen** – Simpan file yang telah dimodifikasi, opsional mempertahankan yang asli.

Proses ini tidak merusak; file sumber tetap tidak tersentuh kecuali Anda menimpanya.

### Langkah 1: Inisialisasi Annotator dan Muat Dokumen Anda

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Tips Pro:** Gunakan path absolut saat pengembangan untuk menghindari error “file not found”. Pada produksi, pertimbangkan memuat sumber daya dari classpath atau bucket penyimpanan cloud.

### Langkah 2: Membuat Komentar dan Balasan (Bagian Kolaboratif)

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

**Penggunaan Dunia Nyata:** Reviewer dapat mendiskusikan klausa tertentu dengan menambahkan balasan beruntai, menjaga percakapan tetap terikat pada anotasi yang tepat.

### Langkah 3: Menentukan Koordinat Anotasi (Menentukan Posisi yang Tepat)

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

**Sistem Koordinat:**  
- Titik 1 & 2 menentukan tepi atas garis bawah.  
- Titik 3 & 4 menentukan tepi bawah.  
- Selisih Y (730 vs 650) mengontrol ketebalan.

### Langkah 4: Membuat dan Mengonfigurasi Anotasi Garis Bawah

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Tips Warna & Opasitas:**  
- `FontColor` menggunakan ARGB; `65535` (0x00FFFF) menghasilkan kuning cerah.  
- Untuk merah, gunakan `16711680` (0xFF0000); untuk biru, `255` (0x0000FF).  
- Nilai opasitas antara 0.5 dan 0.8 memberikan keterbacaan yang baik tanpa menutupi teks.

### Langkah 5: Menyimpan Dokumen yang Beranotasi

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Manajemen Memori:** Pemanggilan `dispose()` melepaskan sumber daya native dan mencegah kebocoran memori—kritikal saat memproses banyak file dalam batch.

## Menghapus Anotasi: Membuat Versi Dokumen Bersih

Kadang‑kadang Anda memerlukan versi PDF **tanpa anotasi apa pun**—misalnya, saat menyerahkan kontrak final yang telah disetujui. GroupDocs mempermudah hal ini.

### Memahami Opsi Penghapusan Anotasi

Anda dapat:
- Menghapus **semua** anotasi (paling umum)  
- Menghapus tipe tertentu (misalnya hanya highlight)  
- Menghapus anotasi berdasarkan penulis atau halaman  

### Langkah‑per‑Langkah Penghapusan Anotasi

**Langkah 1: Muat Dokumen yang Sebelumnya Beranotasi**

```java
Annotator annotator = new Annotator(outputPath);
```

**Langkah 2: Konfigurasikan Save Options untuk Output Bersih**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Langkah 3: Simpan Versi Bersih**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Ini menghasilkan file **PDF Java bersih** yang tidak mengandung objek anotasi, sempurna untuk distribusi akhir.

## Masalah Umum dan Solusinya

### Masalah 1: Error “Document not found”

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Masalah 2: Anotasi Muncul di Lokasi yang Salah

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Masalah 3: Masalah Memori dengan Dokumen Besar

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Masalah 4: Masalah Lisensi di Produksi

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## Praktik Terbaik Kinerja untuk Aplikasi Produksi

### Strategi Manajemen Memori

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Pertimbangan Threading

GroupDocs.Annotation **tidak thread‑safe** secara default. Jika aplikasi Anda memproses dokumen secara bersamaan:

- **Jangan pernah** membagikan instance `Annotator` antar thread.  
- **Sinkronkan** akses file atau gunakan mekanisme lock.  
- Pertimbangkan **pool** objek `Annotator` jika Anda membutuhkan throughput tinggi.

### Strategi Caching

- Cache template anotasi yang sering dipakai.  
- Reuse koleksi `Point` untuk set koordinat umum.  
- Simpan **template PDF** di memori jika Anda berulang‑ulang mengannotasi dokumen dasar yang sama.

## Tips Manajemen Memori PDF Java
Penggunaan memori yang efisien sangat penting saat menangani PDF besar atau memproses banyak file dalam batch. Berikut beberapa rekomendasi praktis:

- **Gunakan try‑with‑resources** untuk setiap `Annotator` agar disposal terjamin.  
- **Tingkatkan heap JVM** (`-Xmx`) hanya bila diperlukan; pantau penggunaan dengan alat profiling.  
- **Proses dokumen secara berurutan** bila memungkinkan, membebaskan memori setelah tiap file.  
- **Hindari memuat PDF yang sama berulang‑ulang**; reuse stream yang sama bila perlu membaca berulang.

Menerapkan praktik‑praktik ini membantu aplikasi tetap responsif dan mencegah crash out‑of‑memory selama beban anotasi berat.

## Aplikasi Dunia Nyata dan Kasus Penggunaan

### Sistem Tinjauan Dokumen

- **Tinjauan Hukum:** Garis bawahi klausa kontrak dan tambahkan komentar tentang risiko.  
- **Audit Kepatuhan:** Highlight bagian bermasalah dalam laporan keuangan.  
- **Tinjauan Akademik:** Profesor garis bawahi bagian yang memerlukan klarifikasi.

### Platform Edukasi

- **Alat Anotasi Mahasiswa:** Biarkan pelajar menggarisbawahi konsep kunci dalam e‑book.  
- **Umpan Balik Guru:** Berikan komentar inline langsung pada tugas yang dikirim.

### Alur Kerja Quality Assurance

- **Tinjauan Dokumentasi Teknis:** Insinyur garis bawahi bagian yang perlu diperbarui.  
- **Prosedur Operasional Standar:** Petugas keamanan menyoroti langkah kritis.

### Sistem Manajemen Konten

- **Alur Editorial:** Editor garis bawahi teks yang memerlukan verifikasi fakta.  
- **Kontrol Versi:** Lacak riwayat anotasi lintas revisi dokumen.

## Tips Lanjutan untuk Implementasi Profesional

### Gaya Anotasi Kustom

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadata Anotasi untuk Pelacakan

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integrasi dengan Sistem Manajemen Pengguna

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Memecahkan Masalah Produksi

### Pemantauan Kinerja

Pantau metrik berikut di produksi:
- **Penggunaan heap** – pastikan `dispose()` dipanggil.  
- **Waktu proses per dokumen** – log timestamp sebelum dan sesudah `annotator.save()`.  
- **Tingkat error** – tangkap exception dan kategorikan.

### Gotchas Umum di Produksi

- **File locking** – pastikan file yang di‑upload ditutup sebelum anotasi.  
- **Edit bersamaan** – terapkan optimistic locking atau pengecekan versi.  
- **File besar (> 50 MB)** – tingkatkan timeout JVM dan pertimbangkan API streaming.

### Praktik Terbaik Penanganan Error

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Kesimpulan

Anda kini memiliki semua yang diperlukan untuk **membuat PDF Java bersih** dan **menambahkan anotasi PDF di Java** dengan anotasi garis bawah menggunakan GroupDocs.Annotation. Ingat untuk:

- Kelola sumber daya dengan try‑with‑resources atau `dispose()` eksplisit.  
- Validasi koordinat lebih awal untuk menghindari garis bawah yang salah tempat.  
- Terapkan penanganan error yang kuat untuk stabilitas produksi.  
- Manfaatkan styling berbasis peran dan metadata agar sesuai dengan alur kerja Anda.

Langkah selanjutnya? Coba tambahkan tipe anotasi lain—highlight, stamp, atau penggantian teks—untuk membangun solusi tinjauan dokumen lengkap.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara mengannotasi beberapa area teks dalam satu operasi?**  
J: Buat beberapa objek `UnderlineAnnotation` dengan koordinat berbeda dan tambahkan secara berurutan menggunakan `annotator.add()`.

**T: Bisakah saya mengannotasi gambar dalam dokumen PDF?**  
J: Ya. Gunakan sistem koordinat yang sama, pastikan titik‑titik berada di dalam batas gambar.

**T: Format file apa saja selain PDF yang didukung oleh GroupDocs.Annotation?**  
J: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), dan format gambar seperti JPEG, PNG, TIFF.

**T: Bagaimana cara menangani dokumen sangat besar tanpa kehabisan memori?**  
J: Proses dokumen satu per satu, tingkatkan heap JVM (`-Xmx`), dan selalu dispose instance `Annotator` sesegera mungkin.

**T: Apakah mungkin mengekstrak anotasi yang sudah ada dari sebuah dokumen?**  
J: Ya. Gunakan `annotator.get()` untuk mengambil semua anotasi, lalu filter berdasarkan tipe, penulis, atau halaman sesuai kebutuhan.

---

**Terakhir Diperbarui:** 2026-03-24  
**Diuji Dengan:** GroupDocs.Annotation 25.2  
**Penulis:** GroupDocs