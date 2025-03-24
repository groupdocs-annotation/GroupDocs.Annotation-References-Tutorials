---
title: Tambahkan Anotasi Sorotan Teks ke Dokumen
linktitle: Tambahkan Anotasi Sorotan Teks ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi sorotan teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Tingkatkan kolaborasi dan produktivitas dengan komprehensif ini.
weight: 22
url: /id/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Perkenalan
Di bidang manajemen dokumen dan kolaborasi, GroupDocs.Annotation untuk .NET muncul sebagai solusi tangguh, memberdayakan pengembang untuk mengintegrasikan anotasi sorotan teks ke dalam aplikasi mereka dengan lancar. Tutorial ini berfungsi sebagai panduan komprehensif untuk menambahkan anotasi sorotan teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Melalui petunjuk langkah demi langkah dan penjelasan mendetail, Anda akan memperoleh kemahiran dalam memanfaatkan kemampuan perpustakaan canggih ini.
## Prasyarat
Sebelum mempelajari penerapan anotasi sorotan teks, pastikan Anda memiliki prasyarat berikut:
1. Pengaturan Lingkungan: Memiliki lingkungan pengembangan yang sesuai yang dikonfigurasi untuk pengembangan .NET.
2.  Instalasi GroupDocs.Annotation untuk .NET: Unduh dan instal GroupDocs.Annotation untuk .NET dari yang disediakan[tautan unduhan](https://releases.groupdocs.com/annotation/net/).
3. Keakraban dengan C#: Pemahaman dasar bahasa pemrograman C#.
4. Dokumen yang akan diberi anotasi: Siapkan dokumen (misalnya PDF) yang ingin Anda beri anotasi.

## Impor Namespace
Untuk memulai, impor namespace yang diperlukan dalam kode C# Anda untuk memanfaatkan fungsi GroupDocs.Annotation untuk .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Sekarang, mari kita uraikan proses penambahan anotasi sorotan teks menjadi beberapa langkah:
## Langkah 1: Tentukan Jalur Keluaran
Tentukan jalur keluaran tempat dokumen beranotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Annotator
 Buat sebuah instance dari`Annotator` kelas, meneruskan nama file dokumen sebagai parameter:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Langkah 3: Buat Anotasi Sorotan
 Buat contoh a`HighlightAnnotation` objek dan konfigurasikan propertinya:
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
Simpan dokumen beranotasi ke jalur keluaran yang ditentukan:
```csharp
annotator.Save(outputPath);
```

## Kesimpulan
Kesimpulannya, GroupDocs.Annotation untuk .NET menawarkan pendekatan yang disederhanakan untuk memasukkan anotasi sorotan teks ke dalam dokumen. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, pengembang dapat meningkatkan kolaborasi dokumen dan produktivitas dalam aplikasi mereka dengan lancar.
## FAQ
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, Word, Excel, dan banyak lagi. Lihat dokumentasi untuk daftar lengkap.
### Bisakah anotasi disesuaikan menurut kebutuhan spesifik?
Ya, pengembang memiliki kendali penuh atas properti dan tampilan anotasi, sehingga memungkinkan penyesuaian untuk memenuhi beragam kebutuhan.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation untuk .NET?
 Ya, Anda dapat menjelajahi fitur GroupDocs.Annotation untuk .NET dengan mengakses uji coba gratis dari yang disediakan[tautan](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan GroupDocs.Annotation untuk .NET?
 Untuk dukungan dan bantuan, Anda dapat mengunjungi forum GroupDocs.Annotation[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Opsi lisensi apa yang tersedia untuk GroupDocs.Annotation untuk .NET?
 GroupDocs.Annotation untuk .NET menawarkan berbagai opsi lisensi, termasuk lisensi sementara untuk tujuan pengujian dan lisensi komersial untuk lingkungan produksi. Kunjungi halaman pembelian[Di Sini](https://purchase.groupdocs.com/buy) untuk lebih jelasnya.