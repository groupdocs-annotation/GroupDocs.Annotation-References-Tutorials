---
title: Tambahkan Anotasi Garis Bawah Teks ke Dokumen
linktitle: Tambahkan Anotasi Garis Bawah Teks ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi garis bawah teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Tingkatkan kolaborasi dan komunikasi dengan mudah.
weight: 27
url: /id/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Perkenalan
Dalam tutorial ini, kita akan memandu proses menambahkan anotasi garis bawah teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Anotasi garis bawah teks dapat berguna untuk menekankan bagian tertentu dari dokumen, seperti bagian penting atau poin penting.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menginstal prasyarat berikut:
1.  GroupDocs.Annotation untuk .NET: Unduh dan instal GroupDocs.Annotation untuk .NET dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework di sistem Anda.

## Mengimpor Namespace
Pertama, mari impor namespace yang diperlukan ke dalam proyek kita:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang, mari kita bagi contoh ini menjadi beberapa langkah:
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Pada langkah ini, kami menentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Di sini, kami menginisialisasi sebuah instance dari`Annotator` kelas dengan menyediakan jalur dokumen masukan.
## Langkah 3: Buat Anotasi Garis Bawah
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // berfungsi hanya mendukung dokumen Word dan PDF
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
 Langkah ini melibatkan pembuatan`UnderlineAnnotation`objek dengan berbagai properti seperti warna font, pesan, opacity, nomor halaman, warna latar belakang, warna garis bawah, titik, dan balasan.
## Langkah 4: Tambahkan Anotasi ke Dokumen
```csharp
annotator.Add(underline);
```
Di sini, kami menambahkan anotasi garis bawah pada dokumen.
## Langkah 5: Simpan Dokumen Beranotasi
```csharp
annotator.Save(outputPath);
```
Terakhir, kami menyimpan dokumen beranotasi ke jalur keluaran yang ditentukan.

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menambahkan anotasi garis bawah teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Pustaka canggih ini menyediakan berbagai opsi anotasi untuk meningkatkan kolaborasi dan komunikasi dokumen.
## FAQ
### Bisakah saya menyesuaikan tampilan anotasi yang digarisbawahi?
Ya, Anda dapat menyesuaikan properti seperti warna, opasitas, dan posisi sesuai kebutuhan Anda.
### Apakah GroupDocs.Annotation kompatibel dengan format dokumen yang berbeda?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk Word dan PDF.
### Bisakah saya menambahkan banyak anotasi ke satu dokumen?
Tentu saja, GroupDocs.Annotation memungkinkan Anda menambahkan beberapa anotasi dari jenis berbeda ke dokumen.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?
 Ya, Anda dapat mengakses versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?
 Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs.Annotation[Di Sini](https://forum.groupdocs.com/c/annotation/10).