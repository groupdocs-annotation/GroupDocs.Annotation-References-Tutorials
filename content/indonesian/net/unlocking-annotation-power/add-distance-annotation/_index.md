---
"description": "Pelajari cara menambahkan anotasi jarak ke dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan kolaborasi dan komunikasi dengan mudah."
"linktitle": "Tambahkan Anotasi Jarak ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Jarak ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Tambahkan Anotasi Jarak ke Dokumen

## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara menambahkan anotasi jarak ke dokumen menggunakan GroupDocs.Annotation for .NET. Ikuti langkah-langkah berikut untuk menyelesaikan tugas:
## Prasyarat

Pastikan Anda memiliki prasyarat berikut sebelum melanjutkan:

- GroupDocs.Annotation untuk Pustaka .NET: Unduh dan instal pustaka GroupDocs.Annotation untuk .NET dari [tautan ini](https://releases.groupdocs.com/annotation/net/).
- Dokumen yang Akan Dianotasi: Siapkan dokumen (misalnya, PDF) yang ingin Anda tambahkan anotasi jarak.
- Lingkungan Pengembangan: Siapkan lingkungan pengembangan Anda dengan Visual Studio atau IDE lain pilihan Anda.

## Mengimpor Ruang Nama

Sebelum memulai, pastikan untuk menyertakan namespace yang diperlukan dalam kode Anda. Namespace ini penting untuk mengakses kelas dan metode yang diperlukan.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Langkah 1: Inisialisasi Anotator

Mulailah dengan menginisialisasi `Annotator` objek dengan jalur ke dokumen yang ingin Anda beri anotasi.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ada di sini
}
```

## Langkah 2: Buat Anotasi Jarak

Sekarang, buatlah `DistanceAnnotation` objek dan konfigurasikan propertinya seperti dimensi kotak, pesan, opasitas, warna pena, dll.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Langkah 3: Tambahkan Anotasi

Tambahkan anotasi jarak yang dibuat ke dokumen menggunakan `Add` metode objek anotator.

```csharp
annotator.Add(distance);
```

## Langkah 4: Simpan Dokumen

Simpan dokumen yang diberi anotasi ke lokasi yang diinginkan pada sistem Anda.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Langkah 5: Tampilkan Konfirmasi

Terakhir, tampilkan pesan yang mengonfirmasi keberhasilan penyimpanan dokumen yang diberi anotasi.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Menambahkan anotasi jarak ke dokumen menggunakan GroupDocs.Annotation for .NET merupakan proses yang mudah. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat menyempurnakan dokumen Anda dengan anotasi yang berharga, sehingga memudahkan kolaborasi dan komunikasi yang lebih baik.

## Pertanyaan yang Sering Diajukan

### T: Dapatkah saya menyesuaikan tampilan anotasi jarak?

A: Ya, Anda dapat menyesuaikan berbagai properti seperti warna, opasitas, gaya garis, dsb., agar sesuai dengan kebutuhan Anda.

### T: Apakah GroupDocs.Annotation mendukung anotasi pada berbagai jenis dokumen?

A: Ya, GroupDocs.Annotation mendukung anotasi pada berbagai format dokumen termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.

### T: Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?

A: Ya, Anda dapat mengakses uji coba gratis GroupDocs.Annotation dari [tautan ini](https://releases.groupdocs.com/).

### T: Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Annotation untuk .NET?

A: Anda dapat merujuk ke dokumentasi terperinci yang tersedia [Di Sini](https://tutorials.groupdocs.com/annotation/net/).

### T: Bagaimana saya bisa mendapatkan dukungan atau bantuan dengan GroupDocs.Annotation?

A: Anda dapat mencari dukungan dan bantuan dari forum komunitas GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).