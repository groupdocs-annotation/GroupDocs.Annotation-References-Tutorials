---
title: Tambahkan Komponen Tombol ke Dokumen PDF
linktitle: Tambahkan Komponen Tombol ke Dokumen PDF
second_title: GroupDocs.Annotasi .NET API
description: Sempurnakan dokumen PDF Anda dengan komponen tombol interaktif menggunakan Groupdocs.Annotation untuk .NET. Ikuti tutorial langkah demi langkah kami untuk integrasi yang lancar.
weight: 10
url: /id/net/document-components/add-button-component-to-pdf/
---

# Tambahkan Komponen Tombol ke Dokumen PDF

## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan Komponen Tombol ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET. Panduan langkah demi langkah ini akan memastikan bahwa Anda dapat dengan mudah mengintegrasikan fitur ini ke dalam proyek Anda.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki prasyarat berikut:
1.  Groupdocs.Annotation untuk .NET: Pastikan Anda telah menginstal Groupdocs.Annotation untuk perpustakaan .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai dengan kerangka .NET yang diinstal.

## Impor Namespace
Sebelum melanjutkan, impor namespace yang diperlukan ke dalam proyek Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Inisialisasi Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Tambahkan Komponen Tombol
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## Langkah 3: Tampilkan Jalur Keluaran
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Selamat! Anda telah berhasil menambahkan Komponen Tombol ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET.

## Kesimpulan
Dalam tutorial ini, kami telah mendemonstrasikan cara memasukkan Komponen Tombol ke dalam dokumen PDF menggunakan Groupdocs.Annotation untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat menyempurnakan dokumen PDF Anda dengan fitur interaktif.
## FAQ
### Bisakah saya menyesuaikan tampilan tombol?
Ya, Anda dapat menyesuaikan berbagai properti seperti ukuran, warna, dan gaya komponen tombol sesuai kebutuhan Anda.
### Apakah Groupdocs.Annotation for .NET kompatibel dengan semua versi PDF?
Groupdocs.Annotation for .NET mendukung berbagai versi PDF, memastikan kompatibilitas dengan sebagian besar dokumen.
### Bisakah saya menambahkan beberapa komponen tombol ke satu dokumen PDF?
Tentu saja, Anda dapat menambahkan komponen tombol sebanyak yang diperlukan ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET.
### Apakah Groupdocs.Annotation untuk .NET menawarkan dukungan untuk format file lain?
Ya, selain PDF, Groupdocs.Annotation for .NET mendukung berbagai format dokumen lain termasuk DOCX, PPTX, dan XLSX.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
 Ya, Anda dapat mengakses uji coba gratis Groupdocs.Annotation untuk .NET dari[Di Sini](https://releases.groupdocs.com/).