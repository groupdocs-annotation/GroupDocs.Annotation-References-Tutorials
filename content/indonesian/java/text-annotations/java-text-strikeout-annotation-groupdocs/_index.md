---
categories:
- Java Development
date: '2026-03-30'
description: Pelajari cara menambahkan anotasi coret java menggunakan GroupDocs.Annotation.
  Panduan langkah demi langkah dengan contoh kode, tips pemecahan masalah, dan praktik
  terbaik untuk penandaan dokumen.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: 'Tutorial Java: Menambahkan Anotasi Coret dengan GroupDocs'
type: docs
url: /id/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Tambahkan Anotasi Coret Java - Panduan Lengkap GroupDocs

Pernah menemukan diri Anda menatap sebuah dokumen berpikir, “Saya perlu mencoret teks ini, tapi saya tidak bisa hanya mengambil pena merah”? Anda tidak sendirian. Baik Anda sedang membangun sistem peninjauan dokumen, membuat alur kerja penyuntingan, atau hanya perlu menandai teks untuk dihapus dalam aplikasi Java Anda, **add strikeout annotation java** adalah keterampilan penting. Dalam tutorial ini kami akan membahas semua yang perlu Anda ketahui untuk mengimplementasikan fungsi coret teks yang benar-benar bekerja di produksi.

## Jawaban Cepat
- **Perpustakaan apa yang mendukung anotasi coret di Java?** GroupDocs.Annotation for Java  
- **Kata kunci utama apa yang harus saya targetkan untuk SEO?** add strikeout annotation java  
- **Apakah saya memerlukan lisensi untuk menjalankan kode contoh?** Versi percobaan gratis atau lisensi sementara dapat digunakan untuk pengembangan; lisensi penuh diperlukan untuk produksi.  
- **Bisakah saya menggunakan ini dengan file PDF, DOCX, dan PPTX?** Ya – GroupDocs.Annotation mendukung semua format dokumen utama.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi (JDK 11+ disarankan).

## Apa itu add strikeout annotation java?
Anotasi coret menggambar garis melalui teks yang dipilih, secara visual menunjukkan bahwa konten tersebut harus dihapus atau diabaikan. Ini adalah cara non‑destruktif untuk menyarankan penghapusan sambil menjaga teks asli tetap utuh untuk jejak audit atau peninjauan kolaboratif.

## Mengapa menggunakan anotasi coret dalam aplikasi Java?
- **Alur kerja peninjauan dokumen** – peninjau dapat menandai teks yang tidak diinginkan tanpa mengubah sumber.  
- **Penyuntingan kolaboratif** – anggota tim melihat penghapusan yang disarankan secara langsung.  
- **Legal dan kepatuhan** – menjaga jejak audit perubahan yang jelas.  
- **Migrasi konten** – menandai bagian usang sebelum memindahkan konten antar sistem.  

## Prasyarat dan Penyiapan Lingkungan
Anda akan memerlukan hal‑hal berikut sebelum menyelam ke kode:

- **Java Development Kit (JDK)** 8+ (JDK 11+ disarankan)  
- **Maven atau Gradle** untuk manajemen dependensi  
- **IDE** – IntelliJ IDEA, Eclipse, atau VS Code dengan ekstensi Java  
- **Perpustakaan GroupDocs.Annotation** – kami akan menggunakan versi 25.2 dalam contoh  

*Sebagai tambahan:* pengetahuan dasar tentang anotasi Java dan penanganan PDF.

## Menyiapkan GroupDocs.Annotation untuk Java

### Konfigurasi Maven yang Benar-benar Berfungsi
Tambahkan repositori dan dependensi ke `pom.xml` Anda persis seperti yang ditunjukkan:

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

### Mengatur Lisensi Anda
GroupDocs menawarkan beberapa opsi lisensi:

- **Percobaan gratis** – sempurna untuk pengujian (tidak memerlukan kartu kredit)  
- **Lisensi sementara** – ideal untuk pengembangan dan staging  
- **Lisensi penuh** – diperlukan untuk penggunaan produksi; lihat [halaman pembelian](https://purchase.groupdocs.com/buy)

> **Tips pro:** Mulailah dengan percobaan gratis untuk menjelajahi API, kemudian beralih ke lisensi sementara ketika Anda siap membangun fitur dunia nyata.

### Penyiapan Pemeriksaan Kesehatan Cepat
Jalankan program minimal ini untuk memverifikasi bahwa perpustakaan dimuat dengan benar:

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

Jika konsol mencetak pesan keberhasilan tanpa error, Anda siap menambahkan anotasi coret.

## Cara menambahkan anotasi coret java

Berikut adalah implementasi lengkap yang siap produksi, dibagi menjadi langkah‑langkah jelas.

### Langkah 1 – Inisialisasi Annotator
Buat instance `Annotator` yang menunjuk ke dokumen sumber:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Mengapa ini penting:** Menggunakan path absolut atau path relatif yang terresolusi dengan benar mencegah pengecualian “file tidak ditemukan”.

### Langkah 2 – (Opsional) Siapkan Balasan Komentar
Menambahkan balasan membuat anotasi menjadi kolaboratif:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Komentar ini muncul ketika pengguna mengarahkan kursor ke coret.

### Langkah 3 – Tentukan Area Coret
Tentukan persegi panjang yang melingkupi teks yang ingin Anda coret:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Tips koordinat:** Origin (0,0) berada di sudut kiri‑atas halaman; X bertambah ke kanan, Y bertambah ke bawah. Gunakan PDF viewer yang menampilkan koordinat untuk menyetel nilai‑nilai ini dengan tepat.

### Langkah 4 – Konfigurasikan Anotasi Coret
Atur tampilan, nomor halaman, dan lampirkan komentar:

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

*Catatan warna:* `65535` sesuai dengan kuning dalam format RGB integer. Ubah nilai tersebut untuk menggunakan warna lain.

### Langkah 5 – Terapkan Anotasi dan Simpan
Tambahkan anotasi ke dokumen dan tulis file output:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Langkah 6 – Bersihkan Sumber Daya (Kritis!)
Selalu dispose annotator untuk membebaskan sumber daya native:

```java
if (annotator != null) {
    annotator.dispose();
}
```

Di produksi, bungkus penggunaan dalam blok `try‑with‑resources` atau konstruk `try/finally`.

## Masalah Umum dan Cara Memperbaikinya

| Masalah | Gejala | Solusi |
|---------|--------|--------|
| **File Tidak Ditemukan** | `Annotator` melemparkan pengecualian | Gunakan path absolut, verifikasi izin baca, pastikan tidak ada proses lain yang mengunci file |
| **Koordinat Salah** | Coret muncul jauh dari teks yang dimaksud | Periksa kembali sistem koordinat PDF viewer; sesuaikan titik‑titiknya sesuai |
| **Anotasi Tidak Terlihat** | Tidak ada coret yang terlihat setelah menyimpan | Tingkatkan `opacity` (mis., `0.9`), verifikasi `pageNumber` (berbasis 0), pastikan titik‑titik membentuk persegi panjang yang tepat |
| **OutOfMemoryError** | Aplikasi crash pada PDF besar | Tingkatkan heap JVM (`-Xmx2048m`), proses dokumen secara batch, selalu panggil `dispose()` |

## Praktik Terbaik Kinerja untuk Produksi

### Manajemen Memori
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

### Strategi Pemrosesan Batch
Saat Anda perlu memberi anotasi pada puluhan atau ratusan file:

- Proses 10‑20 dokumen per batch.  
- Catat keberhasilan/kegagalan untuk setiap file.  
- Inisialisasi ulang `Annotator` untuk setiap dokumen guna menghindari kebocoran memori.  

### Tips Caching
- Cache templat dokumen yang sering digunakan.  
- Simpan peta koordinat yang telah dihitung sebelumnya untuk tata letak standar.  

## Kasus Penggunaan Dunia Nyata

1. **Sistem Peninjauan Dokumen** – Editor menyarankan penghapusan tanpa mengubah kontrak asli.  
2. **Amandemen Hukum** – Pengacara melacak penghapusan klausul sambil mempertahankan kata‑kata asli untuk audit.  
3. **Peer Review Akademik** – Reviewer menandai bagian untuk dihapus dan menambahkan komentar inline.  
4. **Migrasi Konten** – Selama migrasi CMS, coret menyoroti salinan usang yang perlu diganti.  

## Kustomisasi Lanjutan

### Gaya Kustom
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Menambahkan Metadata
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Daftar Periksa Pemecahan Masalah
- ✅ Bisakah Anda membuka file sumber secara manual?  
- ✅ Apakah semua dependensi GroupDocs ada di classpath?  
- ✅ Apakah titik‑titik membentuk persegi panjang yang valid?  
- ✅ Apakah nomor halaman benar (berbasis 0)?  
- ✅ Apakah memori heap cukup?  
- ✅ Apakah Anda memiliki izin menulis untuk folder output?  
- ✅ Apakah format dokumen didukung (PDF, DOCX, PPTX, dll.)?  

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menggunakan GroupDocs.Annotation di dalam layanan Spring Boot?**  
A: Ya. Tambahkan dependensi Maven, injeksikan kelas layanan yang membuat `Annotator`, dan kelola siklus hidupnya dengan scope bean Spring.

**Q: Format dokumen apa yang mendukung anotasi coret?**  
A: PDF, DOCX, PPTX, dan banyak format lain yang didukung oleh GroupDocs.Annotation. PDF menawarkan penanganan koordinat paling tepat.

**Q: Bagaimana cara menangani dokumen dengan ukuran halaman yang bervariasi?**  
A: Dapatkan dimensi halaman melalui `annotator.getPageInfo(pageNumber)` dan skalakan koordinat Anda sesuai.

**Q: Apakah memungkinkan mengedit atau menghapus anotasi coret yang sudah ada?**  
A: Tentu saja. Gunakan `annotator.getAnnotations(pageNumber)` untuk mengambil, lalu `annotator.update(updatedAnnotation)` atau `annotator.delete(annotationId)`.

**Q: Apa dampak kinerja menambahkan banyak anotasi?**  
A: Menambahkan ratusan anotasi umumnya tidak masalah, tetapi pantau penggunaan memori. Untuk set anotasi yang sangat besar, pertimbangkan mempaginasikan tampilan atau memuat anotasi secara lazy‑load saat dibutuhkan.

## Kesimpulan
Anda kini memiliki panduan lengkap yang siap produksi untuk **add strikeout annotation java** menggunakan GroupDocs.Annotation. Mulailah dengan contoh pemeriksaan kesehatan sederhana, lalu tingkatkan ke pemrosesan batch, gaya kustom, dan penambahan metadata. Ingatlah untuk menguji koordinat dengan cermat, mengelola sumber daya secara bertanggung jawab, dan memilih model lisensi yang tepat untuk lingkungan Anda.

Siap menjelajahi lebih lanjut? Lihat tipe anotasi lain—highlight, note, image, arrow, dan watermark—untuk membangun suite kolaborasi dokumen berfitur lengkap.

---

**Terakhir Diperbarui:** 2026-03-30  
**Diuji Dengan:** GroupDocs.Annotation 25.2 for Java  
**Penulis:** GroupDocs  

**Sumber Daya Tambahan**

- [Dokumentasi GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Panduan Referensi API](https://reference.groupdocs.com/annotation/java/)
- [Unduh Versi Terbaru](https://releases.groupdocs.com/annotation/java/)
- [Beli Lisensi Penuh](https://purchase.groupdocs.com/buy)
- [Mulai Percobaan Gratis](https://releases.groupdocs.com/annotation/java/)
- [Dapatkan Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)
- [Forum Dukungan Komunitas](https://forum.groupdocs.com/c/annotation/)