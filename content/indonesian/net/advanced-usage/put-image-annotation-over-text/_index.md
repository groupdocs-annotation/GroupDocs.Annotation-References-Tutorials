---
title: Letakkan Anotasi Gambar di atas Teks
linktitle: Letakkan Anotasi Gambar di atas Teks
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi gambar pada teks di .NET menggunakan GroupDocs.Annotation untuk manajemen dokumen dan kolaborasi yang efisien.
weight: 21
url: /id/net/advanced-usage/put-image-annotation-over-text/
---
## Perkenalan
Dalam dunia pengembangan .NET, GroupDocs.Annotation menawarkan solusi canggih untuk menambahkan anotasi ke dokumen, menjadikan kolaborasi dan manajemen dokumen lebih efisien. Salah satu persyaratan umum adalah menempatkan anotasi gambar di atas teks, yang dapat dilakukan dengan lancar menggunakan GroupDocs.Annotation untuk .NET.
## Prasyarat
Sebelum mendalami proses menempatkan anotasi gambar di atas teks menggunakan GroupDocs.Annotation untuk .NET, pastikan Anda memiliki hal berikut:
1.  GroupDocs.Annotation untuk .NET Library: Unduh dan instal perpustakaan dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai, seperti Visual Studio atau .NET IDE lainnya.
3. File Dokumen dan Gambar: Siapkan file dokumen (PDF, DOCX, dll.) dan file gambar yang ingin Anda gunakan untuk anotasi.
4. Pemahaman Dasar C#: Keakraban dengan bahasa pemrograman C# diperlukan untuk mengimplementasikan cuplikan kode yang disediakan dalam tutorial ini.

## Impor Namespace
Sebelum melanjutkan proses anotasi, pastikan Anda mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Langkah 1: Tentukan Jalur Keluaran
Pertama, tentukan jalur keluaran tempat dokumen beranotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Langkah 2: Inisialisasi Annotator
 Inisialisasi`Annotator` objek dengan menyediakan jalur dokumen masukan:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ditempatkan di sini
}
```
## Langkah 3: Buat Anotasi Gambar
 Buat sebuah`ImageAnnotation` objek dengan properti yang diinginkan seperti dimensi kotak, opacity, nomor halaman, jalur gambar, dan indeks-z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Langkah 4: Tambahkan Anotasi
 Tambahkan anotasi gambar ke dokumen menggunakan`Add` metode`Annotator` obyek:
```csharp
annotator.Add(image);
```
## Langkah 5: Simpan Dokumen Beranotasi
Simpan dokumen beranotasi ke jalur keluaran yang ditentukan:
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Tampilkan Pesan Sukses
Tampilkan pesan sukses dengan jalur ke dokumen beranotasi:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Kesimpulannya, menambahkan anotasi gambar di atas teks dalam aplikasi .NET menggunakan GroupDocs.Annotation adalah proses yang mudah. Dengan mengikuti panduan langkah demi langkah yang disediakan dalam tutorial ini, Anda dapat membuat anotasi dokumen secara efisien dan meningkatkan kemampuan kolaborasi dan manajemen dokumen dalam proyek .NET Anda.
## FAQ
### Bisakah saya membuat anotasi pada dokumen selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen seperti DOCX, XLSX, PPTX, dan lainnya.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?
 Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs.Annotation[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?
 Ya, Anda bisa mendapatkan lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/) untuk tujuan pengujian.
### Bisakah saya menyesuaikan tampilan anotasi?
Ya, GroupDocs.Annotation menyediakan berbagai opsi untuk menyesuaikan tampilan anotasi seperti warna, opacity, ukuran font, dll.