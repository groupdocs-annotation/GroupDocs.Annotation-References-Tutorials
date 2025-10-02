---
"description": "Pelajari cara menambahkan anotasi teks pada dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan kolaborasi dan proses peninjauan dokumen secara efisien."
"linktitle": "Tambahkan Anotasi Coretan Teks ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Coretan Teks ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Tambahkan Anotasi Coretan Teks ke Dokumen

## Perkenalan
Dalam tutorial ini, kita akan menjelajahi cara menambahkan anotasi teks pada dokumen menggunakan GroupDocs.Annotation for .NET. Pustaka ini menyediakan alat yang hebat untuk membuat anotasi pada berbagai jenis dokumen, meningkatkan kolaborasi, dan proses peninjauan dokumen.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. GroupDocs.Annotation untuk .NET: Instal pustakanya. Anda dapat mengunduhnya dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai untuk pengembangan .NET.
3. Dokumen: Siapkan dokumen yang ingin diberi anotasi, seperti berkas PDF.

## Mengimpor Ruang Nama
Pertama, impor namespace yang diperlukan untuk mengakses fungsionalitas GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang, mari kita uraikan proses penambahan anotasi teks menjadi beberapa langkah:
## Langkah 1: Tentukan Jalur Output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Di sini, kami menentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
## Langkah 2: Inisialisasi Anotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inisialisasi objek Annotator dengan menyediakan jalur ke dokumen input (file PDF dalam kasus ini).
## Langkah 3: Buat Anotasi Coretan
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
Buat objek StrikeoutAnnotation dengan properti yang diinginkan seperti pesan, opasitas, nomor halaman, warna latar belakang, titik (koordinat), dan balasan.
## Langkah 4: Tambahkan Anotasi
```csharp
annotator.Add(strikeout);
```
Tambahkan anotasi coretan yang dibuat ke dokumen.
## Langkah 5: Simpan Dokumen
```csharp
annotator.Save(outputPath);
```
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara menambahkan anotasi teks pada dokumen menggunakan GroupDocs.Annotation for .NET. Pustaka canggih ini memungkinkan anotasi dokumen yang efisien, meningkatkan kolaborasi, dan proses peninjauan dokumen.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan anotasi?
Tentu saja, Anda dapat menyesuaikan properti anotasi seperti warna, opasitas, ukuran font, dan lainnya sesuai kebutuhan Anda.
### Apakah GroupDocs.Annotation menyediakan fitur kolaborasi?
Ya, GroupDocs.Annotation memfasilitasi kolaborasi dengan memungkinkan pengguna untuk menambahkan komentar, balasan, dan anotasi ke dokumen.
### Apakah ada uji coba gratis yang tersedia?
Ya, Anda dapat memanfaatkan uji coba gratis dari [Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?
Anda bisa mendapatkan dukungan dari [Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).