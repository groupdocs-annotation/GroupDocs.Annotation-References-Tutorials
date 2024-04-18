---
title: Tambahkan Anotasi Teks Berlekuk-lekuk ke Dokumen
linktitle: Tambahkan Anotasi Teks Berlekuk-lekuk ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi teks berlekuk-lekuk ke dokumen dengan mudah menggunakan Groupdocs.Annotation untuk .NET. Meningkatkan kolaborasi dan proses peninjauan dokumen.
type: docs
weight: 25
url: /id/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Perkenalan

Groupdocs.Annotation for .NET adalah perpustakaan serbaguna yang memungkinkan pengembang mengintegrasikan kemampuan anotasi yang kuat ke dalam aplikasi .NET mereka dengan mudah. Baik Anda bekerja dengan PDF, dokumen Word, atau format file populer lainnya, Groupdocs.Annotation memberikan solusi sempurna untuk membuat anotasi dan meningkatkan kolaborasi dokumen.

## Prasyarat

Sebelum masuk ke tutorial, pastikan Anda memiliki prasyarat berikut:

## Impor Namespace

Pastikan untuk mengimpor namespace yang diperlukan untuk mengakses fungsionalitas yang disediakan oleh Groupdocs.Annotation untuk .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang kita sudah memenuhi prasyaratnya, mari kita uraikan proses penambahan anotasi teks berlekuk-lekuk menjadi beberapa langkah.

## Langkah 1: Tentukan Jalur Keluaran

Tentukan jalur di mana dokumen beranotasi akan disimpan.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Annotator

Inisialisasi objek Annotator dengan menyediakan jalur dokumen masukan.

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

Tambahkan anotasi berlekuk-lekuk yang dibuat ke dokumen.

```csharp
annotator.Add(squiggly);
```

## Langkah 5: Simpan Dokumen

Simpan dokumen beranotasi ke jalur keluaran yang ditentukan.

```csharp
annotator.Save(outputPath);
```

## Langkah 6: Tampilkan Konfirmasi

Menampilkan pesan yang mengonfirmasi keberhasilan penyimpanan dokumen beranotasi.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Kesimpulannya, Groupdocs.Annotation for .NET memberi pengembang seperangkat alat yang kuat untuk mengintegrasikan fungsi anotasi dokumen ke dalam aplikasi .NET mereka dengan lancar. Dengan mengikuti panduan langkah demi langkah ini, Anda dapat dengan mudah menambahkan anotasi teks berlekuk-lekuk ke dokumen Anda, sehingga meningkatkan kolaborasi dan proses peninjauan dokumen.

## FAQ

### T: Dapatkah Groupdocs.Annotation mendukung anotasi pada berbagai format file?

J: Ya, Groupdocs.Annotation mendukung anotasi pada berbagai format file, termasuk PDF, dokumen Word, lembar Excel, dan banyak lagi.

### T: Apakah Groupdocs.Annotation kompatibel dengan aplikasi desktop dan web?

J: Tentu saja! Groupdocs.Annotation dapat diintegrasikan dengan mulus ke dalam aplikasi desktop dan web, menawarkan fleksibilitas dan keserbagunaan.

### T: Apakah ada opsi lisensi yang tersedia untuk Groupdocs.Annotation?

J: Ya, Groupdocs.Annotation menawarkan opsi lisensi fleksibel yang disesuaikan dengan kebutuhan individu atau perusahaan, termasuk lisensi sementara untuk tujuan uji coba.

### T: Apakah anotasi yang dibuat menggunakan Groupdocs.Annotation dapat dikustomisasi?

J: Tentu saja! Groupdocs.Annotation menyediakan opsi penyesuaian ekstensif untuk anotasi, memungkinkan pengembang menyesuaikan anotasi dengan kebutuhan spesifik mereka.

### T: Apakah Groupdocs.Annotation menawarkan dukungan dan dokumentasi untuk pengembang?

J: Memang! Groupdocs.Annotation menyediakan dokumentasi komprehensif dan forum dukungan khusus untuk membantu pengembang dalam memanfaatkan fitur-fiturnya secara efektif.