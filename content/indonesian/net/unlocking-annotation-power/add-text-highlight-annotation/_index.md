---
"description": "Pelajari cara menambahkan anotasi sorotan teks ke dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan kolaborasi dan produktivitas dengan panduan lengkap ini."
"linktitle": "Tambahkan Anotasi Sorotan Teks ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Sorotan Teks ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Tambahkan Anotasi Sorotan Teks ke Dokumen

## Perkenalan
Dalam bidang manajemen dan kolaborasi dokumen, GroupDocs.Annotation for .NET muncul sebagai solusi yang tangguh, memberdayakan pengembang untuk mengintegrasikan anotasi penyorotan teks ke dalam aplikasi mereka dengan lancar. Tutorial ini berfungsi sebagai panduan komprehensif untuk menambahkan anotasi penyorotan teks ke dokumen menggunakan GroupDocs.Annotation for .NET. Melalui petunjuk langkah demi langkah dan penjelasan terperinci, Anda akan memperoleh kemahiran dalam memanfaatkan kemampuan pustaka yang hebat ini.
## Prasyarat
Sebelum mempelajari penerapan anotasi penyorotan teks, pastikan Anda memiliki prasyarat berikut:
1. Pengaturan Lingkungan: Miliki lingkungan pengembangan yang sesuai yang dikonfigurasi untuk pengembangan .NET.
2. Pemasangan GroupDocs.Annotation untuk .NET: Unduh dan pasang GroupDocs.Annotation untuk .NET dari sumber yang disediakan. [tautan unduhan](https://releases.groupdocs.com/annotation/net/).
3. Keakraban dengan C#: Pemahaman dasar tentang bahasa pemrograman C#.
4. Dokumen yang Akan Dianotasi: Siapkan dokumen (misalnya, PDF) yang ingin Anda anotasi.

## Mengimpor Ruang Nama
Untuk memulai, impor namespace yang diperlukan dalam kode C# Anda untuk memanfaatkan fungsionalitas GroupDocs.Annotation untuk .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Sekarang, mari kita uraikan proses penambahan anotasi sorotan teks ke dalam beberapa langkah:
## Langkah 1: Tentukan Jalur Output
Tentukan jalur keluaran tempat dokumen beranotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Buat contoh dari `Annotator` kelas, meneruskan nama berkas dokumen sebagai parameter:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Langkah 3: Buat Anotasi Sorotan
Membuat contoh sebuah `HighlightAnnotation` objek dan konfigurasikan propertinya:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## Langkah 4: Tambahkan Anotasi
Tambahkan anotasi sorotan yang dibuat ke dokumen:
```csharp
annotator.Add(highlight);
```
## Langkah 5: Simpan Dokumen Beranotasi
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan:
```csharp
annotator.Save(outputPath);
```

## Kesimpulan
Sebagai kesimpulan, GroupDocs.Annotation untuk .NET menawarkan pendekatan yang efisien untuk memasukkan anotasi penyorotan teks ke dalam dokumen. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, pengembang dapat meningkatkan kolaborasi dan produktivitas dokumen dalam aplikasi mereka dengan lancar.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, Word, Excel, dan lainnya. Lihat dokumentasi untuk daftar lengkapnya.
### Bisakah anotasi disesuaikan menurut persyaratan tertentu?
Ya, pengembang memiliki kontrol penuh atas properti dan tampilan anotasi, memungkinkan penyesuaian untuk memenuhi beragam kebutuhan.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat menjelajahi fitur GroupDocs.Annotation untuk .NET dengan mengakses uji coba gratis dari situs yang disediakan. [link](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan GroupDocs.Annotation untuk .NET?
Untuk dukungan dan bantuan, Anda dapat mengunjungi forum GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Pilihan lisensi apa yang tersedia untuk GroupDocs.Annotation untuk .NET?
GroupDocs.Annotation untuk .NET menawarkan berbagai opsi lisensi, termasuk lisensi sementara untuk tujuan pengujian dan lisensi komersial untuk lingkungan produksi. Kunjungi halaman pembelian [Di Sini](https://purchase.groupdocs.com/buy) untuk lebih jelasnya.