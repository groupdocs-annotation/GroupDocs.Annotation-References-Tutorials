---
"description": "Pelajari cara menambahkan anotasi tanda air ke dokumen Anda dengan mudah menggunakan GroupDocs.Annotation for .NET. Tingkatkan kejelasan dan keamanan dokumen."
"linktitle": "Tambahkan Anotasi Tanda Air ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Tanda Air ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Tambahkan Anotasi Tanda Air ke Dokumen

## Perkenalan
Dalam tutorial ini, kita akan membahas proses penambahan anotasi tanda air ke dokumen menggunakan GroupDocs.Annotation for .NET. Anotasi tanda air berguna untuk menunjukkan status dokumen, menandainya sebagai rahasia, atau menambahkan informasi relevan lainnya.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. GroupDocs.Annotation untuk .NET: Anda dapat mengunduhnya dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Pastikan Anda telah menginstal Visual Studio di sistem Anda.
3. Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# diperlukan untuk memahami dan menerapkan contoh kode.

## Mengimpor Ruang Nama

Sebelum kita mulai membuat kode, mari impor namespace yang diperlukan:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Sekarang, mari kita uraikan proses penambahan anotasi tanda air menjadi beberapa langkah:

## Langkah 1: Tentukan Jalur Output

Pertama, kita perlu menentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan. Kita akan menggunakan `Path` kelas dari `System.IO` namespace untuk menggabungkan jalur direktori keluaran dengan nama file.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Anotator

Selanjutnya, kita akan menginisialisasi anotator dengan memberikan jalur dokumen input. Ini akan memungkinkan kita untuk menambahkan anotasi ke dokumen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ada di sini
}
```

## Langkah 3: Buat Anotasi Tanda Air

Sekarang, mari membuat objek anotasi tanda air dengan properti yang diinginkan seperti sudut, posisi, teks, warna font, opasitas, dst.

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

Sekarang, kita akan menambahkan anotasi tanda air ke dokumen menggunakan `Add` metode objek anotator.

```csharp
annotator.Add(watermark);
```

## Langkah 5: Simpan Dokumen

Terakhir, kita akan menyimpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.

```csharp
annotator.Save(outputPath);
```

## Kesimpulan

Dalam tutorial ini, kita mempelajari cara menambahkan anotasi tanda air ke dokumen menggunakan GroupDocs.Annotation for .NET. Anotasi tanda air merupakan alat yang berguna untuk menandai dokumen dengan informasi yang relevan atau menunjukkan statusnya.

## Pertanyaan yang Sering Diajukan

### T: Dapatkah saya menyesuaikan tampilan anotasi tanda air?

A: Ya, Anda dapat menyesuaikan berbagai properti seperti teks, ukuran font, warna, opasitas, posisi, dll., untuk menyesuaikan tanda air menurut kebutuhan Anda.

### T: Apakah GroupDocs.Annotation untuk .NET kompatibel dengan berbagai format dokumen?

A: Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk PDF, Microsoft Word, Excel, PowerPoint, dan format gambar.

### T: Dapatkah saya menambahkan beberapa anotasi ke satu dokumen?

A: Tentu saja, GroupDocs.Annotation memungkinkan Anda menambahkan beberapa anotasi dengan tipe berbeda ke dalam satu dokumen, sehingga memungkinkan markup dokumen yang komprehensif.

### T: Apakah GroupDocs.Annotation menyediakan dukungan untuk anotasi kolaboratif?

A: Ya, GroupDocs.Annotation memfasilitasi anotasi kolaboratif dengan memungkinkan pengguna menambahkan komentar, balasan, dan anotasi, sehingga mendorong kolaborasi efektif di antara anggota tim.

### T: Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?

A: Ya, Anda dapat mengunduh versi uji coba gratis dari [Di Sini](https://releases.groupdocs.com/).