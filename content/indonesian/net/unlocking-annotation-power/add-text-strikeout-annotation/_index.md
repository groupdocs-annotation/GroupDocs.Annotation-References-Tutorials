---
title: Tambahkan Anotasi Coretan Teks ke Dokumen
linktitle: Tambahkan Anotasi Coretan Teks ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi coretan teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Meningkatkan kolaborasi dan proses peninjauan dokumen secara efisien.
weight: 26
url: /id/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Tambahkan Anotasi Coretan Teks ke Dokumen

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menambahkan anotasi coretan teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Pustaka ini menyediakan alat canggih untuk membuat anotasi berbagai jenis dokumen, meningkatkan kolaborasi, dan proses peninjauan dokumen.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Annotation untuk .NET: Instal perpustakaan. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai untuk pengembangan .NET.
3. Dokumen: Siapkan dokumen untuk diberi anotasi, seperti file PDF.

## Mengimpor Namespace
Pertama, impor namespace yang diperlukan untuk mengakses fungsi GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang, mari kita uraikan proses penambahan anotasi coretan teks menjadi beberapa langkah:
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Di sini, kami menentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inisialisasi objek Annotator dengan menyediakan jalur ke dokumen masukan (dalam hal ini file PDF).
## Langkah 3: Buat Anotasi Coret
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Buat objek StrikeoutAnnotation dengan properti yang diinginkan seperti pesan, opacity, nomor halaman, warna latar belakang, titik (koordinat), dan balasan.
## Langkah 4: Tambahkan Anotasi
```csharp
annotator.Add(strikeout);
```
Tambahkan anotasi coretan yang dibuat ke dokumen.
## Langkah 5: Simpan Dokumen
```csharp
annotator.Save(outputPath);
```
Simpan dokumen beranotasi ke jalur keluaran yang ditentukan.

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menambahkan anotasi coretan teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Pustaka yang kuat ini memungkinkan anotasi dokumen yang efisien, meningkatkan kolaborasi dan proses peninjauan dokumen.
## FAQ
### Apakah GroupDocs.Annotation kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan anotasi?
Tentu saja, Anda dapat menyesuaikan properti anotasi seperti warna, opacity, ukuran font, dan lainnya sesuai dengan kebutuhan Anda.
### Apakah GroupDocs.Annotation menyediakan fitur kolaborasi?
Ya, GroupDocs.Annotation memfasilitasi kolaborasi dengan memungkinkan pengguna menambahkan komentar, balasan, dan anotasi ke dokumen.
### Apakah ada uji coba gratis yang tersedia?
 Ya, Anda dapat memanfaatkan uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?
 Anda bisa mendapatkan dukungan dari[GroupDocs.Forum anotasi](https://forum.groupdocs.com/c/annotation/10).