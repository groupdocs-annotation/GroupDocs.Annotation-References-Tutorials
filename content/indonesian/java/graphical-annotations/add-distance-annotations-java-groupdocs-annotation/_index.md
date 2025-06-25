---
"date": "2025-05-06"
"description": "Pelajari cara menerapkan anotasi jarak dalam dokumen Java menggunakan GroupDocs.Annotation. Panduan langkah demi langkah ini mencakup penyiapan, konfigurasi, dan aplikasi praktis."
"title": "Cara Menambahkan Anotasi Jarak di Java dengan GroupDocs.Annotation&#58; Panduan Langkah demi Langkah"
"url": "/id/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/"
"weight": 1
---

# Cara Menambahkan Anotasi Jarak di Java Menggunakan GroupDocs.Annotation

Selamat datang di panduan lengkap kami tentang menambahkan anotasi jarak ke aplikasi dokumen berbasis Java Anda dengan GroupDocs.Annotation. Fitur ini penting untuk proyek yang memerlukan pengukuran yang tepat dalam dokumen digital, seperti gambar teknis atau rencana arsitektur.

## Apa yang Akan Anda Pelajari:
- **Memahami Dasar-Dasarnya**: Temukan apa itu anotasi jarak dan bagaimana anotasi jarak dapat menyempurnakan dokumen Anda.
- **Menyiapkan Lingkungan Anda**Ikuti panduan kami untuk mempersiapkan lingkungan pengembangan Anda dengan GroupDocs.Annotation untuk Java.
- **Menerapkan Anotasi Jarak**: Proses terperinci langkah demi langkah untuk menambahkan anotasi jarak dalam aplikasi Java.

Sebelum memulai, pastikan Anda telah memenuhi prasyarat yang diperlukan!

## Prasyarat

Pastikan hal berikut sebelum memulai:
### Pustaka dan Dependensi yang Diperlukan:
- **GroupDocs.Annotation untuk Java** versi 25.2 atau lebih baru.
- Maven untuk manajemen ketergantungan (disarankan).

### Persyaratan Pengaturan Lingkungan:
- Pengaturan Java Development Kit (JDK) yang berfungsi pada sistem Anda.
- Pemahaman dasar tentang konsep pemrograman Java.

### Prasyarat Pengetahuan:
- Keakraban dengan pemrograman berorientasi objek di Java.

## Menyiapkan GroupDocs.Annotation untuk Java

Integrasikan pustaka GroupDocs.Annotation ke dalam proyek Anda menggunakan Maven. Tambahkan konfigurasi berikut ke `pom.xml`:

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

### Langkah-langkah Memperoleh Lisensi:
1. **Uji Coba Gratis**: Mulailah dengan uji coba gratis untuk menjelajahi fitur-fiturnya.
2. **Lisensi Sementara**: Dapatkan lisensi sementara untuk kemampuan pengujian yang diperluas.
3. **Pembelian**Pertimbangkan untuk membeli lisensi komersial untuk akses penuh.

Inisialisasi GroupDocs.Annotation dalam proyek Anda seperti ini:

```java
import com.groupdocs.annotation.Annotator;

// Inisialisasi anotator dengan jalur file input
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

## Panduan Implementasi

### Menambahkan Anotasi Jarak ke Dokumen Anda

**Ringkasan**:Bagian ini memandu Anda menambahkan anotasi jarak, yang merepresentasikan pengukuran antara dua titik.

#### Langkah 1: Membuat dan Mengonfigurasi Balasan untuk Anotasi

Anotasi dapat bersifat interaktif. Berikut cara menambahkan balasan:

```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

#### Langkah 2: Konfigurasikan Anotasi Jarak

Atur anotasi jarak Anda dengan properti seperti posisi, ukuran, dan opasitas.

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Mengatur posisi dan ukuran anotasi
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Lampirkan balasan
```

#### Langkah 3: Tambahkan Anotasi ke Dokumen Anda

Tambahkan anotasi yang dikonfigurasi ke dokumen Anda dan simpan.

```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```

### Tips Pemecahan Masalah:
- **Periksa Jalur File**Pastikan jalur input dan output sudah benar.
- **Verifikasi Versi Perpustakaan**: Konfirmasikan bahwa Anda menggunakan versi GroupDocs.Annotation yang kompatibel untuk Java.

## Aplikasi Praktis

Catatan jarak dapat meningkatkan interaktivitas dokumen dalam berbagai cara:
1. **Manual Teknis**: Tandai pengukuran pada skema.
2. **Rencana Properti**: Sorot batas properti.
3. **Pencitraan Medis**: Memberi anotasi jarak antara struktur anatomi.
4. **Desain Arsitektur**: Memberikan dimensi yang tepat pada cetak biru.

Mengintegrasikan GroupDocs.Annotation dengan sistem lain dapat lebih memperluas kemampuannya, seperti penyimpanan cloud atau solusi manajemen dokumen.

## Pertimbangan Kinerja

Optimalkan kinerja aplikasi Anda dengan:
- Mengelola memori secara efektif saat memproses dokumen besar.
- Menggunakan pengaturan pengumpulan sampah Java yang tepat untuk menangani anotasi secara efisien.

Praktik terbaik untuk manajemen memori meliputi menutup instance anotator setelah digunakan dan menghindari penyimpanan objek yang tidak perlu dalam memori.

## Kesimpulan

Anda kini telah mempelajari cara menambahkan anotasi jarak menggunakan GroupDocs.Annotation untuk Java. Fitur ini membuka banyak kemungkinan untuk meningkatkan interaktivitas dan ketepatan dokumen.

**Langkah Berikutnya:**
- Jelajahi jenis anotasi lain yang didukung oleh GroupDocs.
- Integrasikan dengan sistem manajemen dokumen Anda yang sudah ada.

**Ajakan Bertindak**:Coba terapkan langkah-langkah ini dalam proyek Anda untuk melihat bagaimana langkah-langkah ini meningkatkan fungsionalitas aplikasi Anda!

## Bagian FAQ

1. **Apa itu anotasi jarak?**
   - Representasi visual yang digunakan untuk menunjukkan pengukuran antara dua titik dalam dokumen.
2. **Bisakah saya menggunakan GroupDocs.Annotation secara gratis?**
   - Ya, mulailah dengan uji coba gratis dan jelajahi fitur-fiturnya.
3. **Bagaimana cara mengatur opasitas suatu anotasi?**
   - Menggunakan `setOpacity()` metode pada objek anotasi Anda untuk menyesuaikan tingkat transparansi.
4. **Apa saja masalah umum saat menambahkan anotasi?**
   - Masalah umum meliputi jalur file yang salah, versi pustaka yang tidak kompatibel, atau properti anotasi yang salah dikonfigurasi.
5. **Di mana saya dapat menemukan lebih banyak sumber daya tentang GroupDocs.Annotation untuk Java?**
   - Kunjungi [dokumentasi resmi](https://docs.groupdocs.com/annotation/java/) dan referensi API untuk panduan dan contoh yang lengkap.

## Sumber daya
- [Dokumentasi](https://docs.groupdocs.com/annotation/java/)
- [Referensi API](https://reference.groupdocs.com/annotation/java/)
- [Unduh GroupDocs.Annotation](https://releases.groupdocs.com/annotation/java/)
- [Beli Lisensi GroupDocs](https://purchase.groupdocs.com/buy)
- [Uji Coba Gratis](https://releases.groupdocs.com/annotation/java/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)
- [Forum Dukungan](https://forum.groupdocs.com/c/annotation/)