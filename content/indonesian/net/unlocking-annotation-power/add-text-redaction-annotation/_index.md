---
"description": "Pelajari cara menambahkan anotasi redaksi teks ke dokumen PDF menggunakan GroupDocs.Annotation for .NET. Lindungi informasi sensitif dengan mudah."
"linktitle": "Tambahkan Anotasi Redaksi Teks ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Redaksi Teks ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# Tambahkan Anotasi Redaksi Teks ke Dokumen

## Perkenalan
Menambahkan anotasi redaksi teks ke dokumen dapat menjadi langkah penting dalam mengelola informasi sensitif dengan aman. GroupDocs.Annotation untuk .NET menyediakan solusi yang kuat untuk mencapai hal ini dengan lancar. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan anotasi redaksi teks ke dokumen Anda langkah demi langkah.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. GroupDocs.Annotation untuk .NET: Pastikan Anda telah menginstal pustaka GroupDocs.Annotation untuk .NET. Anda dapat mengunduhnya dari [situs web](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan dengan IDE yang kompatibel dengan .NET seperti Visual Studio.

## Mengimpor Ruang Nama
Pertama, mari impor namespace yang diperlukan ke proyek kita:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tentukan Jalur Output
Tentukan jalur keluaran tempat Anda ingin menyimpan dokumen beranotasi. Pastikan dokumen tersebut dapat diakses dan ditulis.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Inisialisasi anotator dengan jalur dokumen input. Ganti `"input.pdf"` dengan jalur ke dokumen Anda.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ada di sini
}
```
## Langkah 3: Buat Anotasi Redaksi Teks
Membuat sebuah `TextRedactionAnnotation` objek dengan properti yang dibutuhkan seperti `PageNumber`Bahasa Indonesia: `FontColor`, Dan `Points`Sesuaikan anotasi sesuai kebutuhan Anda.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Langkah 4: Tambahkan Anotasi dan Simpan
Tambahkan anotasi yang dibuat ke dokumen menggunakan anotator dan simpan dokumen yang dianotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Langkah 5: Periksa Output
Terakhir, konfirmasikan bahwa dokumen telah berhasil disimpan ke jalur keluaran yang ditentukan.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kami telah membahas proses penambahan anotasi redaksi teks ke dokumen menggunakan GroupDocs.Annotation for .NET. Dengan langkah-langkah ini, kini Anda dapat mengelola informasi sensitif dalam dokumen Anda dengan aman.
## Pertanyaan yang Sering Diajukan
### Bisakah saya menyesuaikan tampilan anotasi penyuntingan teks?
Ya, Anda dapat menyesuaikan berbagai properti seperti warna font, warna isian, dan opasitas agar sesuai dengan kebutuhan Anda.
### Apakah ada versi uji coba yang tersedia sebelum membeli?
Ya, Anda dapat mengakses versi uji coba gratis dari [situs web](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan jika saya menemui masalah?
Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?
Ya, Anda dapat memperoleh lisensi sementara dari [halaman pembelian](https://purchase.groupdocs.com/temporary-license/) untuk pengujian.
### Bisakah saya menambahkan beberapa anotasi ke satu dokumen?
Tentu saja, GroupDocs.Annotation memungkinkan Anda menambahkan berbagai jenis anotasi dan beberapa contoh ke satu dokumen.