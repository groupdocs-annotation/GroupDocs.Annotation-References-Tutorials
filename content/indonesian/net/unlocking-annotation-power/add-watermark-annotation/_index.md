---
title: Tambahkan Anotasi Tanda Air ke Dokumen
linktitle: Tambahkan Anotasi Tanda Air ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi tanda air ke dokumen Anda dengan mudah menggunakan GroupDocs.Annotation untuk .NET. Meningkatkan kejelasan dan keamanan dokumen.
type: docs
weight: 28
url: /id/net/unlocking-annotation-power/add-watermark-annotation/
---
## Perkenalan
Dalam tutorial ini, kita akan memandu proses menambahkan anotasi tanda air ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Anotasi tanda air berguna untuk menunjukkan status dokumen, menandainya sebagai rahasia, atau menambahkan informasi relevan lainnya.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  GroupDocs.Annotation untuk .NET: Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Pastikan Anda telah menginstal Visual Studio di sistem Anda.
3. Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# diperlukan untuk memahami dan mengimplementasikan contoh kode.

## Impor Namespace

Sebelum kita memulai pengkodean, mari impor namespace yang diperlukan:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Sekarang, mari kita uraikan proses penambahan anotasi tanda air menjadi beberapa langkah:

## Langkah 1: Tentukan Jalur Keluaran

 Pertama, kita perlu menentukan jalur keluaran tempat dokumen beranotasi akan disimpan. Kami akan menggunakan`Path` kelas dari`System.IO` namespace untuk menggabungkan jalur direktori keluaran dengan nama file.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Annotator

Selanjutnya, kita akan menginisialisasi anotator dengan menyediakan jalur dokumen masukan. Ini akan memungkinkan kita menambahkan anotasi ke dokumen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ditempatkan di sini
}
```

## Langkah 3: Buat Anotasi Tanda Air

Sekarang, mari buat objek anotasi watermark dengan properti yang diinginkan seperti sudut, posisi, teks, warna font, opacity, dll.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Langkah 4: Tambahkan Anotasi Tanda Air

 Sekarang, kita akan menambahkan anotasi watermark ke dokumen menggunakan`Add` metode objek anotator.

```csharp
annotator.Add(watermark);
```

## Langkah 5: Simpan Dokumen

Terakhir, kami akan menyimpan dokumen beranotasi ke jalur keluaran yang ditentukan.

```csharp
annotator.Save(outputPath);
```

## Kesimpulan

Dalam tutorial ini, kita mempelajari cara menambahkan anotasi tanda air ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Anotasi tanda air adalah alat yang berharga untuk menandai dokumen dengan informasi yang relevan atau menunjukkan statusnya.

## FAQ

### T: Dapatkah saya menyesuaikan tampilan anotasi tanda air?

J: Ya, Anda dapat menyesuaikan berbagai properti seperti teks, ukuran font, warna, opasitas, posisi, dll., untuk menyesuaikan tanda air sesuai kebutuhan Anda.

### T: Apakah GroupDocs.Annotation untuk .NET kompatibel dengan berbagai format dokumen?

J: Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk PDF, Microsoft Word, Excel, PowerPoint, dan format gambar.

### T: Dapatkah saya menambahkan beberapa anotasi ke satu dokumen?

J: Tentu saja, GroupDocs.Annotation memungkinkan Anda menambahkan beberapa anotasi dari jenis berbeda ke satu dokumen, sehingga memungkinkan markup dokumen komprehensif.

### T: Apakah GroupDocs.Annotation menyediakan dukungan untuk anotasi kolaboratif?

J: Ya, GroupDocs.Annotation memfasilitasi anotasi kolaboratif dengan memungkinkan pengguna menambahkan komentar, balasan, dan anotasi, sehingga mendorong kolaborasi yang efektif di antara anggota tim.

### T: Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?

 J: Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).