---
"date": "2025-05-06"
"description": "Pelajari cara menambahkan dan menghapus anotasi garis bawah dalam dokumen Java menggunakan GroupDocs.Annotation. Tingkatkan pengelolaan dokumen Anda dengan panduan terperinci ini."
"title": "Menambahkan dan Menghapus Anotasi Garis Bawah di Java menggunakan GroupDocs&#58; Panduan Lengkap"
"url": "/id/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Cara Menerapkan Java: Menambahkan dan Menghapus Anotasi Garis Bawah dengan GroupDocs

## Perkenalan

Meningkatkan sistem manajemen dokumen Anda dengan menambahkan atau menghapus anotasi secara terprogram? Tutorial ini memandu Anda menggunakan pustaka GroupDocs.Annotation yang canggih di Java untuk menambahkan anotasi garis bawah dan menghapusnya dari dokumen seperti PDF.

**Apa yang Akan Anda Pelajari:**
- Inisialisasi kelas Annotator.
- Tambahkan anotasi garis bawah dengan komentar menggunakan GroupDocs.Annotation untuk Java.
- Hapus semua anotasi dari dokumen.
- Konfigurasikan lingkungan Anda untuk menggunakan GroupDocs.Annotation secara efisien.

Mari kita bahas bagaimana fungsi-fungsi ini dapat dimanfaatkan dalam proyek Anda. Pastikan Anda telah memenuhi prasyarat yang diperlukan sebelum memulai.

## Prasyarat

### Pustaka dan Ketergantungan yang Diperlukan
Untuk mengikuti tutorial ini secara efektif, pastikan Anda memiliki:
- **GroupDocs.Annotation untuk Java**: Versi 25.2 atau yang lebih baru direkomendasikan.
- **Kit Pengembangan Java (JDK)**: Diperlukan versi 8 atau lebih tinggi.

### Persyaratan Pengaturan Lingkungan
Pastikan lingkungan pengembangan Anda menyertakan IDE seperti IntelliJ IDEA atau Eclipse dan alat pembangunan seperti Maven.

### Prasyarat Pengetahuan
Pemahaman dasar tentang pemrograman Java, terutama bekerja dengan pustaka melalui Maven, akan bermanfaat.

## Menyiapkan GroupDocs.Annotation untuk Java

Untuk mulai menggunakan GroupDocs.Annotation di proyek Java Anda, ikuti langkah-langkah pengaturan berikut:

**Konfigurasi Maven:**
Tambahkan konfigurasi berikut ke `pom.xml` file untuk mengunduh dan mengintegrasikan GroupDocs.Annotation.

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

**Akuisisi Lisensi:**
Mulailah dengan mengunduh uji coba gratis atau memperoleh lisensi sementara dari GroupDocs untuk menjelajahi kemampuan penuh pustaka mereka. Untuk penggunaan produksi, pembelian lisensi diperlukan.

## Panduan Implementasi

### Fitur 1: Inisialisasi Anotator dan Tambahkan Anotasi Garis Bawah

Bagian ini memandu Anda melalui inisialisasi `Annotator` kelas dan menambahkan anotasi garis bawah ke dokumen Anda.

#### Ringkasan
Menambahkan anotasi membantu menyorot bagian-bagian tertentu dari suatu dokumen. Di sini, kami fokus pada menggarisbawahi teks dengan komentar untuk klarifikasi atau umpan balik.

#### Implementasi Langkah demi Langkah

**1. Inisialisasi Anotator**
Membuat sebuah `Annotator` objek dan muat berkas PDF Anda.

```java
import com.groupdocs.annotation.Annotator;

// Muat dokumen yang ingin Anda beri anotasi
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Buat Komentar dengan Balasan**
Tentukan komentar yang terkait dengan anotasi garis bawah.

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

**3. Tentukan Titik untuk Anotasi Garis Bawah**
Tetapkan koordinat untuk menentukan di mana garis bawah akan muncul.

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

**4. Membuat dan Mengonfigurasi Anotasi Garis Bawah**
Buat anotasi garis bawah dan atur propertinya seperti warna, opasitas, dan komentar.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Kuning dalam format ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Simpan Dokumen Beranotasi**
Simpan perubahan Anda ke berkas baru.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Tips Pemecahan Masalah
- Pastikan semua koordinat titik berada dalam batas dokumen.
- Verifikasi bahwa `outputPath` direktori ada dan dapat ditulis.

### Fitur 2: Simpan Dokumen Tanpa Anotasi

Bagian ini membahas cara menghapus semua anotasi dari dokumen yang telah diberi anotasi sebelumnya.

#### Ringkasan
Anda mungkin perlu menyimpan versi dokumen yang bersih tanpa anotasi apa pun untuk tujuan berbagi atau pengarsipan.

#### Implementasi Langkah demi Langkah

**1. Inisialisasi Annotator dengan Dokumen yang Dianotasi**
Muat dokumen yang memiliki anotasi yang ada.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Konfigurasikan Opsi Penyimpanan untuk Menghapus Anotasi**
Tentukan bahwa tidak ada anotasi yang harus disimpan dalam berkas keluaran.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Simpan Dokumen Tanpa Anotasi**
Tentukan jalur untuk dokumen yang telah dibersihkan dan simpan.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Aplikasi Praktis

Berikut adalah beberapa skenario dunia nyata di mana fitur-fitur ini dapat bermanfaat:
1. **Tinjauan Dokumen**: Menyoroti dan memberi komentar pada bagian kontrak atau laporan untuk ditinjau.
2. **Alat Pendidikan**: Memberi anotasi pada buku teks dengan catatan atau koreksi untuk siswa.
3. **Pengeditan Kolaboratif**: Berbagi draf beranotasi di antara anggota tim untuk mendapatkan umpan balik.
4. **Dokumentasi Hukum**: Menggarisbawahi klausul utama dalam dokumen hukum selama diskusi.
5. **Materi Pemasaran**: Menyorot informasi penting dalam brosur sebelum didistribusikan.

## Pertimbangan Kinerja
Saat bekerja dengan GroupDocs.Annotation, pertimbangkan kiat berikut untuk mengoptimalkan kinerja:
- **Manajemen Memori**: Buang dengan benar `Annotator` objek untuk membebaskan sumber daya.
- **Pemrosesan Batch**: Jika membuat anotasi pada beberapa dokumen, proseslah secara bertahap untuk mengelola beban sistem secara efektif.
- **Alokasi Sumber Daya**: Pastikan lingkungan Anda memiliki memori dan daya pemrosesan yang cukup untuk menangani file besar.

## Kesimpulan
Anda telah mempelajari cara menambahkan dan menghapus anotasi garis bawah menggunakan GroupDocs.Annotation untuk Java. Tutorial ini membahas inisialisasi kelas Annotator, mengonfigurasi anotasi dengan komentar, dan menyimpan dokumen tanpa anotasi apa pun. 

Untuk eksplorasi lebih lanjut, pertimbangkan untuk mengintegrasikan fitur-fitur ini ke dalam sistem manajemen dokumen Anda yang sudah ada atau bereksperimen dengan jenis anotasi lain yang disediakan oleh GroupDocs.

## Bagian FAQ
1. **Bagaimana cara mengonfigurasi beberapa anotasi garis bawah sekaligus?**
   - Buat beberapa `UnderlineAnnotation` objek dan menambahkannya secara berurutan menggunakan `annotator.add()` metode.
2. **Bisakah saya memberi anotasi pada gambar dalam PDF menggunakan pustaka ini?**
   - Ya, GroupDocs.Annotation mendukung pemberian anotasi pada gambar dalam dokumen seperti PDF.
3. **Format file apa yang didukung GroupDocs.Annotation?**
   - Mendukung berbagai format dokumen termasuk PDF, Word, Excel, dan banyak lagi.