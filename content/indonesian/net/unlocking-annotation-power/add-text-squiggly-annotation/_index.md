---
"description": "Pelajari cara menambahkan anotasi teks bergelombang ke dokumen dengan mudah menggunakan Groupdocs.Annotation for .NET. Tingkatkan kolaborasi dan proses peninjauan dokumen."
"linktitle": "Tambahkan Anotasi Teks Berlekuk-lekuk ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Teks Berlekuk-lekuk ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# Tambahkan Anotasi Teks Berlekuk-lekuk ke Dokumen

## Perkenalan

Groupdocs.Annotation untuk .NET adalah pustaka serbaguna yang memungkinkan pengembang untuk mengintegrasikan kemampuan anotasi yang kuat ke dalam aplikasi .NET mereka dengan mudah. Baik Anda bekerja dengan PDF, dokumen Word, atau format file populer lainnya, Groupdocs.Annotation menyediakan solusi yang mudah untuk membuat anotasi dan meningkatkan kolaborasi dokumen.

## Prasyarat

Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:

## Mengimpor Ruang Nama

Pastikan untuk mengimpor namespace yang diperlukan untuk mengakses fungsionalitas yang disediakan oleh Groupdocs.Annotation untuk .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang setelah semua prasyarat telah terpenuhi, mari kita uraikan proses penambahan anotasi teks berkelok-kelok ke dalam beberapa langkah.

## Langkah 1: Tentukan Jalur Output

Tentukan jalur tempat penyimpanan dokumen yang diberi anotasi.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Anotator

Inisialisasi objek Annotator dengan menyediakan jalur dokumen input.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi ada di sini
}
```

## Langkah 3: Buat Anotasi Berlekuk-lekuk

Buat objek SquigglyAnnotation dan tentukan propertinya.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Tambahkan anotasi berkelok-kelok yang dibuat ke dokumen.

```csharp
annotator.Add(squiggly);
```

## Langkah 5: Simpan Dokumen

Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.

```csharp
annotator.Save(outputPath);
```

## Langkah 6: Tampilkan Konfirmasi

Menampilkan pesan yang mengonfirmasi keberhasilan penyimpanan dokumen yang diberi anotasi.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Sebagai kesimpulan, Groupdocs.Annotation untuk .NET menyediakan serangkaian alat yang tangguh bagi pengembang untuk mengintegrasikan fungsi anotasi dokumen ke dalam aplikasi .NET mereka dengan lancar. Dengan mengikuti panduan langkah demi langkah ini, Anda dapat dengan mudah menambahkan anotasi teks bergelombang ke dokumen Anda, meningkatkan kolaborasi dan proses peninjauan dokumen.

## Pertanyaan yang Sering Diajukan

### T: Dapatkah Groupdocs.Annotation mendukung anotasi pada berbagai format file?

A: Ya, Groupdocs.Annotation mendukung anotasi pada berbagai format file, termasuk PDF, dokumen Word, lembar Excel, dan banyak lagi.

### T: Apakah Groupdocs.Annotation kompatibel dengan aplikasi desktop dan web?

A: Tentu saja! Groupdocs.Annotation dapat diintegrasikan dengan mudah ke dalam aplikasi desktop dan web, menawarkan fleksibilitas dan keserbagunaan.

### T: Apakah ada opsi lisensi yang tersedia untuk Groupdocs.Annotation?

A: Ya, Groupdocs.Annotation menawarkan opsi lisensi fleksibel yang disesuaikan dengan kebutuhan individu atau perusahaan, termasuk lisensi sementara untuk tujuan uji coba.

### T: Bisakah anotasi yang dibuat menggunakan Groupdocs.Annotation disesuaikan?

A: Tentu saja! Groupdocs.Annotation menyediakan opsi penyesuaian yang luas untuk anotasi, yang memungkinkan pengembang untuk menyesuaikan anotasi dengan kebutuhan spesifik mereka.

### T: Apakah Groupdocs.Annotation menawarkan dukungan dan dokumentasi untuk pengembang?

A: Benar! Groupdocs.Annotation menyediakan dokumentasi yang komprehensif dan forum dukungan khusus untuk membantu pengembang dalam memanfaatkan fitur-fiturnya secara efektif.