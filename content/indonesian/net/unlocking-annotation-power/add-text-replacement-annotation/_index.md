---
title: Tambahkan Anotasi Pengganti Teks ke Dokumen
linktitle: Tambahkan Anotasi Pengganti Teks ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi pengganti teks ke dokumen .NET Anda dengan mudah menggunakan GroupDocs.Annotation untuk .NET. Tingkatkan kemampuan manipulasi dokumen Anda.
weight: 24
url: /id/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan Anotasi Pengganti Teks ke dokumen Anda menggunakan GroupDocs.Annotation untuk .NET. Pustaka yang kuat ini memungkinkan pengembang untuk memanipulasi dan membuat anotasi berbagai jenis dokumen secara terprogram. Di akhir tutorial ini, Anda akan dibekali dengan pengetahuan untuk mengintegrasikan anotasi pengganti teks dengan lancar ke dalam aplikasi .NET Anda.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menginstal prasyarat berikut:
### 1. .NET Framework Terpasang
Pastikan Anda telah menginstal .NET Framework di mesin pengembangan Anda. Anda dapat mengunduhnya dari situs web Microsoft.
### 2. GroupDocs.Annotation untuk Perpustakaan .NET
 Unduh dan instal pustaka GroupDocs.Annotation untuk .NET dari[situs web](https://releases.groupdocs.com/annotation/net/). Perpustakaan ini menyediakan alat dan fungsi yang diperlukan untuk bekerja dengan anotasi dalam berbagai format dokumen.
### 3. Pengaturan Lingkungan Pengembangan
Siapkan lingkungan pengembangan pilihan Anda, seperti Visual Studio, untuk membuat dan menjalankan aplikasi .NET.

## Impor Namespace
Sebelum masuk ke bagian pengkodean, mari impor namespace yang diperlukan untuk bekerja dengan GroupDocs.Annotation untuk .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Di sini, kami menentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ditempatkan di sini
}
```
Kami menginisialisasi objek Annotator dengan menentukan dokumen masukan ("input.pdf") dalam blok penggunaan untuk memastikan pembuangan sumber daya dengan benar.
## Langkah 3: Buat Anotasi Pengganti
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
Di sini, kita membuat objek ReplacementAnnotation dengan berbagai properti seperti tanggal pembuatan, warna font, pesan, opacity, nomor halaman, warna latar belakang, titik (koordinat), balasan (komentar), dan teks yang akan diganti.
## Langkah 4: Tambahkan Anotasi
```csharp
annotator.Add(replacement);
```
Kami menambahkan anotasi pengganti yang dibuat ke anotator.
## Langkah 5: Simpan Dokumen
```csharp
annotator.Save(outputPath);
```
Terakhir, kami menyimpan dokumen beranotasi ke jalur keluaran yang ditentukan.
## Langkah 6: Tampilkan Pesan Sukses
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Pesan sukses ditampilkan yang menunjukkan bahwa dokumen telah berhasil disimpan.

## Kesimpulan
Dalam tutorial ini, kami telah membahas proses menambahkan anotasi pengganti teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Dengan mengikuti panduan langkah demi langkah dan memahami prasyaratnya, Anda dapat dengan mudah mengintegrasikan fungsi ini ke dalam aplikasi .NET Anda.
## FAQ
### Bisakah saya membuat anotasi pada dokumen dengan format berbeda menggunakan GroupDocs.Annotation untuk .NET?
Ya, GroupDocs.Annotation untuk .NET mendukung anotasi berbagai format dokumen seperti PDF, DOCX, PPTX, XLSX, dan banyak lagi.
### Apakah GroupDocs.Annotation untuk .NET cocok untuk aplikasi desktop dan web?
Ya, GroupDocs.Annotation untuk .NET dapat digunakan di aplikasi desktop dan web, memberikan fleksibilitas bagi pengembang.
### Bisakah saya menyesuaikan tampilan anotasi yang ditambahkan menggunakan GroupDocs.Annotation untuk .NET?
Tentu saja, Anda dapat menyesuaikan tampilan anotasi dengan mengubah properti seperti warna, opacity, font, dll.
### Apakah GroupDocs.Annotation untuk .NET menawarkan dukungan untuk fitur anotasi kolaboratif?
Ya, GroupDocs.Annotation untuk .NET menyediakan fitur untuk anotasi kolaboratif, memungkinkan banyak pengguna untuk membuat anotasi dokumen secara bersamaan.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat memanfaatkan uji coba gratis GroupDocs.Annotation untuk .NET dari[situs web](https://releases.groupdocs.com/).