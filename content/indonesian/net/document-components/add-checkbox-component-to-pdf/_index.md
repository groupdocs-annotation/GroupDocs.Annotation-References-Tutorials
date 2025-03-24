---
title: Tambahkan Komponen Kotak Centang ke Dokumen PDF
linktitle: Tambahkan Komponen Kotak Centang ke Dokumen PDF
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan Komponen Kotak Centang ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET. Sempurnakan PDF Anda dengan elemen interaktif.
weight: 11
url: /id/net/document-components/add-checkbox-component-to-pdf/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan Komponen Kotak Centang ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1.  Groupdocs.Annotation untuk .NET SDK: Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan pengembangan .NET.

## Impor Namespace
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Sekarang, mari kita bagi contoh ini menjadi beberapa langkah:
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Di sini, kami menentukan jalur keluaran tempat dokumen PDF yang dimodifikasi akan disimpan.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Inisialisasi`Annotator` objek dengan melewati jalur dokumen PDF input.
## Langkah 3: Buat Komponen Kotak Centang
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 Membuat`CheckBoxComponent` objek dan sesuaikan propertinya seperti`Checked`, `Box` ukuran,`PenColor`, `Style`dan tambahkan beberapa balasan.
## Langkah 4: Tambahkan Komponen Kotak Centang
```csharp
annotator.Add(checkBox);
```
Tambahkan komponen kotak centang yang dibuat ke dokumen PDF.
## Langkah 5: Simpan Dokumen
```csharp
annotator.Save("result.pdf");
```
Simpan dokumen PDF yang dimodifikasi dengan komponen kotak centang.
## Langkah 6: Tampilkan Jalur Keluaran
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Menampilkan jalur penyimpanan dokumen PDF yang dimodifikasi.

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan Komponen Kotak Centang ke dokumen PDF menggunakan Groupdocs.Annotation untuk .NET. Dengan pengetahuan ini, Anda dapat menyempurnakan dokumen PDF Anda dengan elemen interaktif.
## FAQ
### Bisakah saya menyesuaikan tampilan kotak centang?
Ya, Anda dapat menyesuaikan berbagai properti seperti warna, gaya, dan ukuran sesuai kebutuhan Anda.
### Apakah Groupdocs.Annotation untuk .NET cocok untuk penggunaan komersial?
Ya, Groupdocs.Annotation untuk .NET menawarkan lisensi komersial untuk bisnis.
### Bisakah saya mencoba Groupdocs.Annotation untuk .NET sebelum membeli?
 Ya, Anda dapat memanfaatkan uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dukungan untuk Groupdocs.Annotation untuk .NET?
 Anda dapat menemukan dukungan dan sumber daya di[Forum Grupdocs](https://forum.groupdocs.com/c/annotation/10).
### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?
 Anda dapat memperoleh lisensi sementara untuk pengujian dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).