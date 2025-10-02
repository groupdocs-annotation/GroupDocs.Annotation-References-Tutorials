---
"description": "Pelajari cara menambahkan anotasi elips ke dokumen dalam .NET menggunakan GroupDocs.Annotation. Tingkatkan kolaborasi dan komunikasi dengan mudah."
"linktitle": "Tambahkan Anotasi Elips ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Elips ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# Tambahkan Anotasi Elips ke Dokumen

## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara menambahkan anotasi elips ke dokumen menggunakan GroupDocs.Annotation for .NET. Panduan langkah demi langkah ini akan memandu Anda melalui prosesnya, memastikan bahwa Anda memahami setiap langkah dengan jelas.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal berikut:
1. GroupDocs.Annotation untuk .NET: Pastikan Anda telah mengunduh dan menginstal GroupDocs.Annotation untuk .NET. Anda dapat mengunduhnya dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): Anda memerlukan IDE yang terpasang di sistem Anda, seperti Visual Studio, untuk menulis dan mengeksekusi kode.

## Mengimpor Ruang Nama
Pertama, impor namespace yang diperlukan ke proyek Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tetapkan Jalur Output
Tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Inisialisasi anotator dengan memberikan jalur dokumen input:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Langkah 3: Buat Anotasi Elips
Buat contoh dari `EllipseAnnotation` kelas dan atur propertinya:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
Tambahkan anotasi elips ke dokumen:
```csharp
annotator.Add(ellipse);
```
## Langkah 5: Simpan Dokumen
Simpan dokumen yang diberi anotasi ke jalur keluaran:
```csharp
annotator.Save(outputPath);
```

## Kesimpulan
Selamat! Anda telah berhasil menambahkan anotasi elips ke dokumen menggunakan GroupDocs.Annotation for .NET. Kini Anda dapat mengintegrasikan fungsi ini ke dalam aplikasi .NET Anda untuk meningkatkan kolaborasi dan komunikasi dokumen.
## Pertanyaan yang Sering Diajukan
### Bisakah saya menyesuaikan tampilan anotasi elips?
Ya, Anda dapat menyesuaikan berbagai properti seperti warna latar belakang, warna batas, opasitas, dsb., sesuai kebutuhan Anda.
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen termasuk PDF, DOCX, PPTX, XLSX, dan banyak lagi.
### Bisakah saya menambahkan beberapa anotasi ke satu dokumen?
Ya, Anda dapat menambahkan beberapa anotasi termasuk elips, persegi panjang, teks, dll., ke satu dokumen.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
Ya, Anda dapat mengunduh versi uji coba gratis dari [Di Sini](https://releases.groupdocs.com/) untuk mengevaluasi fitur-fiturnya.
### Di mana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Annotation untuk .NET?
Anda bisa mendapatkan dukungan teknis dari forum komunitas GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).