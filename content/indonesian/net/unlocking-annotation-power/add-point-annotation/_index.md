---
title: Tambahkan Anotasi Poin ke Dokumen
linktitle: Tambahkan Anotasi Poin ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan Anotasi Titik ke PDF menggunakan GroupDocs.Annotation untuk .NET. Panduan langkah demi langkah untuk integrasi yang lancar.
type: docs
weight: 17
url: /id/net/unlocking-annotation-power/add-point-annotation/
---
## Perkenalan
GroupDocs.Annotation for .NET adalah alat canggih yang memungkinkan pengembang menambahkan berbagai jenis anotasi ke dokumen secara terprogram. Dalam tutorial ini, kita akan fokus menambahkan Anotasi Titik ke dokumen menggunakan C#.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1. Pemahaman dasar bahasa pemrograman C#.
2. Visual Studio diinstal pada sistem Anda.
3.  GroupDocs.Annotation untuk perpustakaan .NET diinstal. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/annotation/net/).

## Mengimpor Namespace yang Diperlukan
Untuk memulai, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Pada langkah ini, kami menentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Di sini, kami menginisialisasi`Annotator` objek dengan dokumen masukan ("input.pdf").
## Langkah 3: Buat Anotasi Poin
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 Pada langkah ini, kita membuat a`PointAnnotation` objek dan tentukan propertinya seperti posisi, pesan, nomor halaman, dan balasan.
## Langkah 4: Tambahkan Anotasi
```csharp
annotator.Add(point);
```
Di sini, kami menambahkan anotasi titik yang dibuat ke dokumen.
## Langkah 5: Simpan Dokumen
```csharp
annotator.Save(outputPath);
```
Terakhir, kami menyimpan dokumen beranotasi ke jalur keluaran yang ditentukan.

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan Anotasi Titik ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Dengan perpustakaan canggih ini, Anda dapat meningkatkan aplikasi manajemen dokumen Anda dengan menggabungkan fungsi anotasi.
## FAQ
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan anotasi?
Sangat! GroupDocs.Annotation for .NET menyediakan opsi ekstensif untuk menyesuaikan tampilan anotasi agar sesuai dengan kebutuhan aplikasi Anda.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation untuk .NET?
 Ya, Anda dapat memanfaatkan uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan GroupDocs.Annotation untuk .NET?
 Anda bisa mendapatkan dukungan dari forum GroupDocs.Annotation[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Bisakah saya mendapatkan lisensi sementara untuk tujuan pengujian?
 Ya, Anda bisa mendapatkan lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).