---
categories:
- Java Development
date: '2025-12-21'
description: Pelajari cara membuat file PDF Java yang bersih dan memberi anotasi PDF
  di Java menggunakan GroupDocs.Annotation, lengkap dengan contoh kode dan tips pemecahan
  masalah.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Buat PDF Bersih Java - Garis Bawah Anotasi dengan GroupDocs'
type: docs
url: /id/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Buat PDF Bersih Java: Anotasi Garis Bawah dengan GroupDocs

## Pendahuluan

Kesulitan dengan manajemen dokumen dan kolaborasi dalam aplikasi Java Anda? Anda tidak sendirian. Banyak pengembang menghadapi tantangan dalam mengimplementasikan fitur anotasi dokumen yang kuat dan dapat diandalkan di berbagai format file.

Dalam panduan ini, Anda akan **membuat PDF bersih Java** dan belajar cara **menambahkan anotasi PDF di Java** menggunakan GroupDocs.Annotation. Pada akhir tutorial, Anda akan tahu persis cara menambahkan anotasi garis bawah dengan komentar, menghapus anotasi yang ada, dan mengintegrasikan fitur-fitur ini secara mulus ke dalam proyek Anda.

**Apa yang akan Anda kuasai dalam panduan ini:**
- Menyiapkan GroupDocs.Annotation dalam proyek Java Anda (dengan cara yang tepat)  
- Menambahkan anotasi garis bawah dengan komentar khusus dan gaya  
- Menghapus semua anotasi untuk membuat versi dokumen bersih  
- Memecahkan masalah umum yang dihadapi pengembang  
- Mengoptimalkan kinerja untuk aplikasi produksi  

Apakah Anda membangun sistem review dokumen, platform edukasi, atau alat penyuntingan kolaboratif, tutorial ini menyediakan contoh kode praktis dan teruji untuk Anda.

## Jawaban Cepat
- **Bagaimana cara menambahkan anotasi garis bawah?** Gunakan `UnderlineAnnotation` dan `annotator.add()` lalu simpan dokumen.  
- **Bagaimana cara membuat file PDF bersih Java?** Muat file yang beranotasi, set `AnnotationType.NONE` dalam `SaveOptions`, dan simpan salinan baru.  
- **Perpustakaan apa yang diperlukan?** GroupDocs.Annotation v25.2 (atau lebih baru) dan repositori Maven-nya.  
- **Apakah saya memerlukan lisensi untuk produksi?** Ya—terapkan lisensi GroupDocs yang valid untuk menghindari watermark.  
- **Bisakah saya memproses banyak dokumen secara efisien?** Bungkus setiap `Annotator` dalam blok try‑with‑resources dan dispose setelah setiap file.

## Cara membuat file PDF bersih Java

Membuat file PDF bersih Java berarti menghasilkan versi dokumen **tanpa anotasi apa pun** sambil mempertahankan konten asli. Ini berguna untuk distribusi akhir, arsip, atau ketika Anda perlu membagikan salinan “bersih” setelah siklus review.

GroupDocs.Annotation membuat ini sederhana: muat file yang beranotasi, konfigurasikan `SaveOptions` untuk mengecualikan semua tipe anotasi, dan simpan hasilnya. Langkah-langkahnya diilustrasikan nanti di bagian **Menghapus Anotasi**.

## Cara menambahkan anotasi PDF di Java menggunakan GroupDocs

GroupDocs.Annotation menyediakan API yang kaya untuk **menambahkan anotasi PDF di Java**. Ia mendukung berbagai tipe anotasi, termasuk highlight, stempel, dan garis bawah. Dalam tutorial ini kami fokus pada anotasi garis bawah karena biasanya digunakan untuk menekankan teks sambil memungkinkan komentar berutas.

## Prasyarat dan Penyiapan Lingkungan

### Apa yang Anda Butuhkan Sebelum Memulai

**Persyaratan Lingkungan Pengembangan:**
- Java Development Kit (JDK) 8 atau lebih tinggi (JDK 11+ disarankan)  
- Maven 3.6+ atau Gradle 6.0+ untuk manajemen dependensi  
- IDE seperti IntelliJ IDEA, Eclipse, atau VS Code dengan ekstensi Java  
- Setidaknya 2 GB RAM yang tersedia (pemrosesan dokumen dapat intensif memori)

**Prasyarat Pengetahuan:**
Anda harus nyaman dengan konsep dasar Java—inisialisasi objek, pemanggilan metode, dan dependensi Maven. Pengalaman sebelumnya dengan perpustakaan pihak ketiga akan mempercepat adopsi.

**Dokumen Pengujian:**
Siapkan beberapa PDF contoh. PDF berbasis teks bekerja paling baik; gambar hasil scan mungkin memerlukan OCR sebelum anotasi.

### Penyiapan Maven: Menambahkan GroupDocs ke Proyek Anda

Berikut cara mengkonfigurasi proyek Maven Anda dengan benar (ini sering membuat banyak pengembang kebingungan pada percobaan pertama):

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
Unduh versi percobaan gratis dari situs web GroupDocs. Versi percobaan mencakup semua fitur tetapi menambahkan watermark pada dokumen yang diproses.

**Untuk Produksi:**  
Beli lisensi dan terapkan saat aplikasi dimulai. Tanpa lisensi yang valid, build produksi akan terbatas.

## Panduan Implementasi: Menambahkan Anotasi Garis Bawah

### Memahami Alur Kerja Anotasi

Sebelum kita masuk ke kode, mari tinjau alur kerja empat langkah yang terjadi ketika Anda **menambahkan anotasi PDF di Java**:

1. **Memuat Dokumen** – `Annotator` membaca file ke dalam memori.  
2. **Pembuatan Anotasi** – Tentukan properti seperti posisi, gaya, dan komentar.  
3. **Penerapan Anotasi** – Perpustakaan menyisipkan anotasi ke dalam struktur PDF.  
4. **Menyimpan Dokumen** – Menyimpan file yang telah dimodifikasi, opsional mempertahankan yang asli.

Proses ini tidak merusak; file sumber tetap tidak tersentuh kecuali Anda menimpanya.

### Langkah 1: Inisialisasi Annotator dan Muat Dokumen Anda

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Tips Pro:** Gunakan path absolut saat mengembangkan untuk menghindari error “file not found”. Di produksi, pertimbangkan memuat sumber daya dari classpath atau bucket penyimpanan cloud.

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

**Penggunaan Dunia Nyata:** Reviewer dapat mendiskusikan klausa tertentu dengan menambahkan balasan berutas, menjaga percakapan terikat pada anotasi yang tepat.

### Langkah 3: Menentukan Koordinat Anotasi (Mendapatkan Posisi yang Tepat)

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

**Manajemen Memori:** Pemanggilan `dispose()` melepaskan sumber daya native dan mencegah kebocoran memori—kritikal saat memproses banyak file secara batch.

## Menghapus Anotasi: Membuat Versi Dokumen Bersih

Terkadang Anda membutuhkan versi PDF **tanpa anotasi apa pun**—misalnya, saat menyerahkan kontrak akhir yang disetujui. GroupDocs memudahkan hal ini.

### Memahami Opsi Penghapusan Anotasi

Anda dapat:
- Menghapus **semua** anotasi (paling umum)  
- Menghapus tipe tertentu (mis., hanya highlight)  
- Menghapus anotasi berdasarkan penulis atau halaman

### Penghapusan Anotasi Langkah‑per‑Langkah

**Langkah 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Langkah 2: Configure Save Options for a Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Langkah 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Ini menghasilkan file **PDF bersih Java** yang tidak berisi objek anotasi, sempurna untuk distribusi akhir.

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

- **Jangan pernah berbagi** instance `Annotator` antar thread.  
- **Sinkronkan** akses file atau gunakan mekanisme kunci.  
- Pertimbangkan **pool** objek `Annotator` jika Anda membutuhkan throughput tinggi.

### Strategi Caching

- Cache templat anotasi yang sering digunakan.  
- Gunakan kembali koleksi `Point` untuk set koordinat umum.  
- Simpan **PDF templat** dalam memori jika Anda berulang kali menambahkan anotasi pada dokumen dasar yang sama.

## Aplikasi Dunia Nyata dan Kasus Penggunaan

### Sistem Review Dokumen

- **Review Hukum:** Garis bawahi klausa kontrak dan tambahkan komentar tentang risiko.  
- **Audit Kepatuhan:** Sorot bagian bermasalah dalam laporan keuangan.  
- **Review Sejawat Akademik:** Profesor menggarisbawahi bagian yang memerlukan klarifikasi.

### Platform Edukasi

- **Alat Anotasi Mahasiswa:** Biarkan pelajar menggarisbawahi konsep kunci dalam e‑book.  
- **Umpan Balik Guru:** Berikan komentar inline langsung pada tugas yang dikumpulkan.

### Alur Kerja Jaminan Kualitas

- **Review Dokumentasi Teknis:** Insinyur menggarisbawahi bagian yang perlu diperbarui.  
- **Prosedur Operasi Standar:** Petugas keselamatan menyorot langkah kritis.

### Sistem Manajemen Konten

- **Alur Kerja Editorial:** Editor menggarisbawahi teks yang memerlukan pengecekan fakta.  
- **Kontrol Versi:** Lacak riwayat anotasi di seluruh revisi dokumen.

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
- **Waktu pemrosesan per dokumen** – catat timestamp sebelum/setelah `annotator.save()`.  
- **Tingkat error** – tangkap pengecualian dan kategorikan.

### Masalah Umum Produksi

- **Penguncian file** – pastikan file yang diunggah ditutup sebelum anotasi.  
- **Edit bersamaan** – terapkan optimistic locking atau pemeriksaan versi.  
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

Anda kini memiliki semua yang diperlukan untuk **membuat file PDF bersih Java** dan **menambahkan anotasi PDF di Java** dengan anotasi garis bawah menggunakan GroupDocs.Annotation. Ingatlah untuk:

- Mengelola sumber daya dengan try‑with‑resources atau `dispose()` eksplisit.  
- Memvalidasi koordinat lebih awal untuk menghindari garis bawah yang salah tempat.  
- Menerapkan penanganan error yang kuat untuk stabilitas produksi.  
- Memanfaatkan gaya berbasis peran dan metadata agar sesuai dengan alur kerja Anda.

Langkah selanjutnya? Coba tambahkan tipe anotasi lain—highlight, stempel, atau penggantian teks—untuk membangun solusi review dokumen lengkap.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menambahkan anotasi pada beberapa area teks dalam satu operasi?**  
J: Buat beberapa objek `UnderlineAnnotation` dengan koordinat berbeda dan tambahkan secara berurutan menggunakan `annotator.add()`.

**T: Bisakah saya menambahkan anotasi pada gambar dalam dokumen PDF?**  
J: Ya. Gunakan sistem koordinat yang sama, pastikan titik-titik berada di dalam batas gambar.

**T: Format file apa saja selain PDF yang didukung oleh GroupDocs.Annotation?**  
J: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), dan format gambar seperti JPEG, PNG, TIFF.

**T: Bagaimana cara menangani dokumen sangat besar tanpa kehabisan memori?**  
J: Proses dokumen satu per satu, tingkatkan heap JVM (`-Xmx`), dan selalu segera dispose instance `Annotator`.

**T: Apakah memungkinkan mengekstrak anotasi yang ada dari dokumen?**  
J: Ya. Gunakan `annotator.get()` untuk mengambil semua anotasi, lalu filter berdasarkan tipe, penulis, atau halaman sesuai kebutuhan.

---

**Terakhir Diperbarui:** 2025-12-21  
**Diuji Dengan:** GroupDocs.Annotation 25.2  
**Penulis:** GroupDocs