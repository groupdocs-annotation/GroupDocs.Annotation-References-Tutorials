---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Pelajari cara menambahkan anotasi coret pada PDF di Java menggunakan
  GroupDocs. Tutorial langkah demi langkah ini mencakup penyiapan, kode, pemecahan
  masalah, dan tips kinerja.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Panduan Coret Teks PDF Java
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
title: Cara Menambahkan Anotasi Coret pada PDF di Java – Panduan Lengkap GroupDocs
type: docs
url: /id/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Cara Menambahkan Anotasi Coret pada PDF di Java

Pernahkah Anda perlu mencoret teks dalam PDF secara programatis? Baik Anda sedang membangun sistem peninjauan dokumen, membuat alur kerja penyuntingan, atau hanya perlu menandai teks untuk dihapus, **cara menambahkan anotasi coret** di Java adalah keterampilan praktis yang menghemat waktu dan mengurangi upaya manual. Dalam panduan komprehensif ini Anda akan menemukan semua yang perlu diketahui untuk mengimplementasikan anotasi coret dengan GroupDocs.Annotation untuk Java, mulai dari penyiapan proyek hingga penyetelan kinerja.

## Jawaban Cepat
- **Langkah pertama apa?** Tambahkan dependensi Maven GroupDocs.Annotation ke `pom.xml` Anda.  
- **Bagaimana cara membuat coret?** Buat instance `Annotator`, definisikan `StrikeoutAnnotation` dengan titik‑titik, atur warna/keburaman, lalu panggil `addAnnotation`.  
- **Bisakah menambahkan komentar?** Ya, lampirkan objek `Comment` ke anotasi untuk kolaborasi.  
- **Bagaimana jika anotasi berada di tempat yang salah?** Sesuaikan titik koordinat; PDF menggunakan sistem asal kiri‑bawah.  
- **Apakah ada batas ukuran dokumen?** GroupDocs memproses PDF ratusan halaman tanpa memuat seluruh file ke memori.

## Apa itu “cara menambahkan coret” dalam anotasi PDF?
Frasa “cara menambahkan coret” mengacu pada proses menggambar garis melalui teks yang dipilih dalam dokumen PDF secara programatis menggunakan API anotasi. Di Java, GroupDocs.Annotation menyediakan kelas khusus `StrikeoutAnnotation` yang menangani rendering, styling, dan persistensi tanda coret.

## Mengapa Menggunakan GroupDocs untuk Coret PDF di Java?
GroupDocs.Annotation mendukung **lebih dari 50 format input dan output**—termasuk PDF, DOCX, XLSX, PPTX, HTML, dan tipe gambar umum—sehingga Anda tidak terikat pada satu jenis file. Ia menyediakan API tingkat tinggi yang mengabstraksi struktur PDF tingkat rendah, secara otomatis menangani penyematan font, rendering halaman, dan persistensi anotasi, yang memungkinkan pengembang fokus pada logika bisnis daripada detail internal PDF.

## Prasyarat dan Persyaratan Penyiapan

### Persyaratan Esensial
- **Java Development Kit (JDK):** Versi 8 atau lebih baru (JDK 11+ direkomendasikan untuk pengumpulan sampah optimal).  
- **GroupDocs.Annotation untuk Java:** Diintegrasikan melalui Maven (lihat potongan Maven di bawah).  
- **IDE:** IntelliJ IDEA, Eclipse, atau editor Java lain yang kompatibel.

### Penyiapan Dependensi Maven
Tambahkan blok dependensi berikut ke `pom.xml` Anda:

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

**Tip Pro:** Selalu periksa versi terbaru di halaman rilis GroupDocs; rilis yang lebih baru menambahkan fitur dan memperbaiki bug yang dapat memengaruhi rendering anotasi.

### Mengatur Lisensi Anda
GroupDocs.Annotation memerlukan lisensi yang valid untuk penggunaan produksi. Anda memiliki tiga opsi:

- **Uji Coba Gratis:** Unduh dari [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Lisensi Sementara:** Minta kunci pengembangan di [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Lisensi Penuh:** Beli untuk produksi di [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Uji coba menambahkan watermark halus, jadi rencanakan pengujian Anda sesuai.

## Panduan Implementasi Langkah‑per‑Langkah

### Memahami Komponen Inti
Definisi berikut memberi Anda model mental cepat:

- **Annotator:** Objek API utama yang memuat PDF dan menyediakan metode anotasi.  
- **StrikeoutAnnotation:** Mewakili garis coret visual dan opsi styling‑nya.  
- **Point:** Pasangan koordinat (X, Y) yang memberi tahu perpustakaan di mana garis dimulai dan berakhir.  
- **Comment:** Teks opsional yang dilampirkan pada anotasi untuk kolaborasi.

### Langkah 1: Menyiapkan Jalur File
Tentukan lokasi PDF sumber dan file tujuan. Jalur yang salah adalah penyebab umum error “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Peringatan Kesalahan Umum:** Pastikan direktori output ada dan dapat ditulisi; GroupDocs tidak akan membuat folder yang hilang secara otomatis.

### Langkah 2: Menginisialisasi Annotator
Buat instance `Annotator` yang memuat PDF ke memori.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**Apa yang terjadi di sini?** Perpustakaan mem-parsing struktur PDF, membangun representasi internal, dan menyiapkan kanvas anotasi per halaman. Untuk file ratusan halaman langkah ini dapat memakan beberapa detik.

### Langkah 3: Menambahkan Komentar (Opsional tetapi Direkomendasikan)
`Comment` adalah kelas yang mewakili catatan teks yang dilampirkan pada anotasi, memungkinkan kolaborator menjelaskan alasan coret.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Tip dunia nyata:** Gunakan komentar untuk menjelaskan mengapa teks dihapus—ini sangat berguna dalam alur kerja peninjauan hukum atau editorial.

### Langkah 4: Menentukan Koordinat Anotasi
Objek `Point` menyimpan pasangan koordinat X‑Y yang menentukan lokasi tepat anotasi pada halaman PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Penjelasan Sistem Koordinat:** Koordinat PDF dimulai dari sudut kiri‑bawah (0,0). Contoh ini membuat garis horizontal dari (80,730) ke (240,730) pada halaman target.

**Menemukan Koordinat yang Tepat:** Banyak pengembang membuat helper yang mengonversi persentase lebar/tinggi halaman menjadi poin absolut, sehingga kode tahan terhadap variasi ukuran halaman.

### Langkah 5: Membuat Anotasi Coret
`StrikeoutAnnotation` mengenkapsulasi garis visual, properti gaya seperti warna dan keburaman, serta metadata terkait untuk tanda coret.

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

**Nilai Warna:** `fontColor` menggunakan nilai RGB desimal (misalnya 65535 untuk kuning terang). Gunakan konverter daring jika Anda memerlukan nuansa merek tertentu.

**Rekomendasi Keburaman:** Keburaman `0.7` (70 %) memberikan petunjuk visual yang jelas sambil tetap membuat teks di bawahnya dapat dibaca.

### Langkah 6: Menerapkan Anotasi
`addAnnotation` adalah metode `Annotator` yang mendaftarkan anotasi yang telah dipersiapkan ke dokumen sehingga akan dirender dan disimpan.

```java
annotator.add(strikeout);
```

### Langkah 7: Menyimpan dan Membersihkan
`dispose()` melepaskan sumber daya native yang dipegang oleh instance `Annotator`, mencegah kebocoran memori setelah pemrosesan selesai.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Catatan Manajemen Memori:** Memanggil `dispose()` membebaskan sumber daya native dan mencegah kebocoran memori saat memproses batch PDF.

## Masalah Umum dan Cara Mengatasinya

### Masalah 1: Error “File Not Found”
**Gejala:** Exception dilempar saat konstruktor `Annotator` dipanggil.  
**Solusi:** Verifikasi jalur input dan output, serta pastikan aplikasi memiliki izin baca/tulis.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Masalah 2: Coret Muncul di Lokasi Salah
**Gejala:** Garis tidak sejajar dengan teks yang dimaksud.  
**Solusi:** Ingat bahwa koordinat Y pada PDF meningkat ke atas. Gunakan alat debugging visual atau cetak dimensi halaman untuk menyempurnakan titik‑titik.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Masalah 3: Anotasi Tidak Terlihat
**Gejala:** Tidak ada coret yang muncul setelah penyimpanan.  
**Penyebab & Solusi yang Mungkin:**
- **Keburaman terlalu rendah:** Sementara set keburaman ke `1.0` untuk memverifikasi visibilitas.  
- **Warna menyatu:** Gunakan warna kontras tinggi seperti merah (`255`).  
- **Indeks halaman salah:** Nomor halaman berbasis nol; pastikan Anda menargetkan halaman yang tepat.

### Masalah 4: Masalah Memori pada File Besar
**Gejala:** `OutOfMemoryError` atau kinerja melambat.  
**Solusi:**  
- Proses dokumen dalam batch lebih kecil.  
- Gunakan API streaming bila tersedia.  
- Selalu panggil `dispose()` setelah setiap dokumen.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Aplikasi Dunia Nyata dan Kasus Penggunaan

### Peninjauan Dokumen Hukum
Firma hukum menandai kontrak dengan coret untuk menunjukkan klausul yang dihapus sambil mempertahankan jejak audit.

### Penyuntingan Makalah Akademik
Profesor menggunakan coret untuk menyarankan penghapusan selama review sejawat, menjaga teks asli tetap terlihat untuk konteks.

### Sistem Manajemen Konten
Platform penerbitan secara otomatis menandai bagian yang melanggar kebijakan dengan coret sebelum moderasi manual.

### Kontrol Versi untuk Dokumen
Perusahaan memperlakukan anotasi coret sebagai “penanda penghapusan” dalam alur kerja kontrol versi berbasis dokumen, mirip dengan diff kode.

## Tips Optimasi Kinerja

### Strategi Pemrosesan Batch
Saat menangani banyak PDF, gunakan kembali satu instance `Annotator` bila memungkinkan dan proses file secara paralel menggunakan thread.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Praktik Terbaik Manajemen Memori
- Panggil `dispose()` pada setiap `Annotator`.  
- Batasi pemuatan dokumen bersamaan untuk menghindari tekanan pada heap.  
- Pantau penggunaan memori JVM dengan alat seperti VisualVM.

### Caching Koordinat
Jika Anda menerapkan tata letak anotasi yang sama pada banyak file, cache objek `Point` untuk menghindari perhitungan ulang.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Opsi Kustomisasi Lanjutan

### Pemilihan Warna Dinamis
Pilih warna pada waktu berjalan berdasarkan aturan bisnis (misalnya merah untuk penghapusan kritis, kuning untuk yang bersifat tentatif).

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

### Coret Multi‑Baris
Buat serangkaian pasangan `Point` untuk menggambar garis zig‑zag yang melintasi beberapa baris teks.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Daftar Periksa Pemecahan Masalah
1. **Izin File:** Pastikan akses baca/tulis.  
2. **Versi Perpustakaan:** Pastikan Anda menggunakan rilis GroupDocs.Annotation yang didukung.  
3. **Status Lisensi:** Pastikan file lisensi direferensikan dengan benar.  
4. **Kompatibilitas PDF:** Periksa bahwa PDF tidak rusak dan berada dalam batas ukuran yang didukung.  
5. **Validasi Koordinat:** Pastikan semua titik berada dalam batas halaman.  
6. **Ruang Heap:** Tingkatkan `-Xmx` JVM bila memproses file sangat besar.

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya mencoret teks yang melintasi beberapa baris?**  
J: Ya. Buat beberapa objek `Point` yang menelusuri jalur yang diinginkan; anotasi akan mengikuti polyline yang diberikan.

**T: Apa yang terjadi jika saya menentukan koordinat di luar batas halaman?**  
J: Anotasi akan terpotong dan mungkin tidak terlihat. Selalu validasi koordinat terhadap lebar dan tinggi halaman.

**T: Bisakah saya menghapus anotasi coret setelah menambahkannya?**  
J: Tentu. Gunakan metode `removeAnnotation` dengan ID anotasi atau filter berdasarkan tipe untuk menghapusnya secara programatis.

**T: Apakah ada batas berapa banyak anotasi yang dapat saya tambahkan ke satu PDF?**  
J: GroupDocs tidak menetapkan batas keras, tetapi kinerja dapat menurun setelah ribuan anotasi. Pertimbangkan paginasi atau rangkuman anotasi untuk set yang sangat besar.

**T: Bagaimana cara menangani PDF yang dilindungi kata sandi?**  
J: Kirimkan kata sandi ke konstruktor `Annotator`. Perpustakaan akan mendekripsi dokumen di memori sebelum menerapkan anotasi apa pun.

**T: Bagaimana saya menangani PDF dengan ukuran dan orientasi halaman yang berbeda?**  
J: Dapatkan dimensi tiap halaman melalui `annotator.getPageInfo(pageNumber)` dan hitung koordinat relatif terhadap dimensi tersebut untuk memastikan penempatan konsisten.

## Kesimpulan
Anda kini memiliki solusi lengkap dan siap produksi untuk **cara menambahkan anotasi coret** pada PDF di Java menggunakan GroupDocs.Annotation. Dengan menguasai penanganan jalur file, perhitungan koordinat, dan manajemen sumber daya, Anda dapat menyematkan kemampuan ini ke dalam alat peninjauan dokumen, pipeline konten, atau aplikasi berbasis Java apa pun yang memerlukan umpan balik visual yang tepat.

**Langkah Selanjutnya**
1. Clone proyek contoh dan jalankan terhadap PDF sampel.  
2. Bereksperimen dengan warna, keburaman, dan teks komentar yang berbeda.  
3. Integrasikan alur kerja anotasi ke layanan pemrosesan dokumen yang sudah ada.  
4. Jelajahi tipe anotasi terkait—highlight, sticky note, dan shape annotation—untuk memperluas toolkit manipulasi PDF Anda.

Siap untuk lebih? Selami dokumentasi resmi untuk wawasan API yang lebih mendalam.

## Sumber Daya Tambahan

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Dokumentasi umum untuk pustaka GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Referensi API lengkap  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Detail metode per metode  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Jaga pustaka Anda tetap terbaru  
- [Purchase License](https://purchase.groupdocs.com/buy) - Lisensi siap produksi  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Evaluasi sebelum membeli  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Pengujian pengembangan  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Bantuan komunitas dan dukungan resmi  

---

**Terakhir Diperbarui:** 2026-05-21  
**Diuji Dengan:** GroupDocs.Annotation 23.12 untuk Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)