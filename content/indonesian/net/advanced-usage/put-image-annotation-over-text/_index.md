---
"description": "Pelajari cara menambahkan anotasi gambar pada teks dalam .NET menggunakan GroupDocs.Annotation untuk manajemen dokumen dan kolaborasi yang efisien."
"linktitle": "Letakkan Anotasi Gambar di Atas Teks"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Letakkan Anotasi Gambar di Atas Teks"
"url": "/id/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Letakkan Anotasi Gambar di Atas Teks

## Perkenalan
Dalam dunia pengembangan .NET, GroupDocs.Annotation menawarkan solusi yang hebat untuk menambahkan anotasi ke dokumen, menjadikan kolaborasi dan pengelolaan dokumen lebih efisien. Salah satu persyaratan umum adalah menempatkan anotasi gambar di atas teks, yang dapat dilakukan dengan mudah menggunakan GroupDocs.Annotation untuk .NET.
## Prasyarat
Sebelum menyelami proses menempatkan anotasi gambar di atas teks menggunakan GroupDocs.Annotation untuk .NET, pastikan Anda memiliki hal berikut:
1. GroupDocs.Annotation untuk Pustaka .NET: Unduh dan instal pustaka dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai, seperti Visual Studio atau IDE .NET lainnya.
3. Berkas Dokumen dan Gambar: Siapkan berkas dokumen (PDF, DOCX, dll.) dan berkas gambar yang ingin Anda gunakan untuk anotasi.
4. Pemahaman Dasar tentang C#: Keakraban dengan bahasa pemrograman C# diperlukan untuk mengimplementasikan potongan kode yang disediakan dalam tutorial ini.

## Mengimpor Ruang Nama
Sebelum melanjutkan proses anotasi, pastikan Anda mengimpor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Langkah 1: Tentukan Jalur Output
Pertama, tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Langkah 2: Inisialisasi Anotator
Inisialisasi `Annotator` objek dengan menyediakan jalur dokumen input:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ada di sini
}
```
## Langkah 3: Buat Anotasi Gambar
Membuat sebuah `ImageAnnotation` objek dengan properti yang diinginkan seperti dimensi kotak, opasitas, nomor halaman, jalur gambar, dan indeks-z:
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
Tambahkan anotasi gambar ke dokumen menggunakan `Add` metode dari `Annotator` obyek:
```csharp
annotator.Add(image);
```
## Langkah 5: Simpan Dokumen Beranotasi
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan:
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Menampilkan Pesan Sukses
Menampilkan pesan sukses dengan jalur ke dokumen yang diberi anotasi:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Kesimpulannya, menambahkan anotasi gambar di atas teks dalam aplikasi .NET menggunakan GroupDocs.Annotation merupakan proses yang mudah. Dengan mengikuti panduan langkah demi langkah yang disediakan dalam tutorial ini, Anda dapat membuat anotasi dokumen secara efisien dan meningkatkan kemampuan kolaborasi dan manajemen dokumen dalam proyek .NET Anda.
## Pertanyaan yang Sering Diajukan
### Bisakah saya memberi anotasi pada dokumen selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen seperti DOCX, XLSX, PPTX, dan banyak lagi.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?
Ya, Anda dapat mengunduh versi uji coba gratis dari [Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?
Anda bisa mendapatkan dukungan dari forum komunitas GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?
Ya, Anda bisa mendapatkan lisensi sementara dari [Di Sini](https://purchase.groupdocs.com/temporary-license/) untuk tujuan pengujian.
### Bisakah saya menyesuaikan tampilan anotasi?
Ya, GroupDocs.Annotation menyediakan berbagai opsi untuk menyesuaikan tampilan anotasi seperti warna, opasitas, ukuran font, dll.