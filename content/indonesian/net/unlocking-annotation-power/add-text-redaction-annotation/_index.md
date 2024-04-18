---
title: Tambahkan Anotasi Redaksi Teks ke Dokumen
linktitle: Tambahkan Anotasi Redaksi Teks ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi redaksi teks ke dokumen PDF menggunakan GroupDocs.Annotation untuk .NET. Lindungi informasi sensitif dengan mudah.
type: docs
weight: 23
url: /id/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Perkenalan
Menambahkan anotasi redaksi teks ke dokumen dapat menjadi langkah penting dalam mengelola informasi sensitif dengan aman. GroupDocs.Annotation untuk .NET memberikan solusi yang kuat untuk mencapai hal ini dengan lancar. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan anotasi redaksi teks ke dokumen Anda langkah demi langkah.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  GroupDocs.Annotation untuk .NET: Pastikan Anda telah menginstal perpustakaan GroupDocs.Annotation untuk .NET. Anda dapat mengunduhnya dari[situs web](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan dengan IDE yang kompatibel dengan .NET seperti Visual Studio.

## Mengimpor Namespace
Pertama, mari impor namespace yang diperlukan ke proyek kita:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tentukan Jalur Keluaran
Tentukan jalur keluaran tempat Anda ingin menyimpan dokumen beranotasi. Pastikan itu dapat diakses dan ditulis.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Annotator
 Inisialisasi anotator dengan jalur dokumen masukan. Mengganti`"input.pdf"` dengan jalur ke dokumen Anda.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ditempatkan di sini
}
```
## Langkah 3: Buat Anotasi Redaksi Teks
 Membuat`TextRedactionAnnotation`objek dengan properti yang diperlukan seperti`PageNumber`, `FontColor` , Dan`Points`. Sesuaikan anotasi sesuai kebutuhan Anda.
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
Tambahkan anotasi yang dibuat ke dokumen menggunakan anotator dan simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Langkah 5: Periksa Keluaran
Terakhir, konfirmasikan bahwa dokumen telah berhasil disimpan ke jalur keluaran yang ditentukan.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari proses menambahkan anotasi redaksi teks ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Dengan langkah-langkah ini, kini Anda dapat mengelola informasi sensitif dalam dokumen Anda dengan aman.
## FAQ
### Bisakah saya menyesuaikan tampilan anotasi redaksi teks?
Ya, Anda dapat menyesuaikan berbagai properti seperti warna font, warna isian, dan opacity agar sesuai dengan kebutuhan Anda.
### Apakah ada versi uji coba yang tersedia sebelum membeli?
 Ya, Anda dapat mengakses versi uji coba gratis dari[situs web](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan jika saya menemui masalah?
 Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs.Annotation[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?
 Ya, Anda bisa mendapatkan lisensi sementara dari[halaman pembelian](https://purchase.groupdocs.com/temporary-license/)untuk pengujian.
### Bisakah saya menambahkan banyak anotasi ke satu dokumen?
Tentu saja, GroupDocs.Annotation memungkinkan Anda menambahkan berbagai jenis anotasi dan beberapa contoh ke satu dokumen.