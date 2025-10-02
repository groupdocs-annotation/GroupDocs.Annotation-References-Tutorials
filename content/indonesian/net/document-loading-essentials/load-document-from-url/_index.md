---
"description": "Pelajari cara membuat anotasi pada dokumen PDF secara terprogram menggunakan GroupDocs.Annotation for .NET. Tutorial langkah demi langkah dengan contoh kode."
"linktitle": "Muat Dokumen dari URL"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Muat Dokumen dari URL"
"url": "/id/net/document-loading-essentials/load-document-from-url/"
type: docs
"weight": 15
---

# Muat Dokumen dari URL

## Perkenalan
GroupDocs.Annotation untuk .NET adalah pustaka kaya fitur yang memungkinkan pengembang untuk menambahkan kapabilitas anotasi ke aplikasi .NET mereka dengan mudah. Dengan GroupDocs.Annotation, Anda dapat membuat anotasi pada dokumen PDF secara terprogram, yang memungkinkan pengguna untuk menyorot teks, menambahkan komentar, menggambar bentuk, dan banyak lagi. Tutorial ini akan memandu Anda melalui langkah-langkah memuat dokumen dari URL, menambahkan anotasi, dan menyimpan dokumen yang diberi anotasi menggunakan GroupDocs.Annotation untuk .NET.
## Prasyarat
Sebelum memulai, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Pastikan Anda telah menginstal Visual Studio di mesin pengembangan Anda.
2. GroupDocs.Annotation untuk .NET: Unduh dan instal GroupDocs.Annotation untuk .NET dari [situs web](https://releases.groupdocs.com/annotation/net/).
3. Pengetahuan Dasar C#: Biasakan diri Anda dengan bahasa pemrograman C#.
4. Koneksi Internet: Anda memerlukan koneksi internet untuk mengakses sumber daya eksternal dan mengunduh file contoh.

## Mengimpor Ruang Nama
Pertama, mari impor namespace yang diperlukan dalam proyek C# Anda:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Langkah 1: Muat Dokumen dari URL
Untuk memberi anotasi pada dokumen PDF dari URL, ikuti langkah-langkah berikut:
### Langkah 1.1: Tentukan Jalur Output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Langkah 1.2: Tentukan URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Langkah 1.3: Muat Dokumen
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Tambahkan anotasi di sini
    annotator.Save(outputPath);
}
```
## Langkah 2: Tambahkan Anotasi
Sekarang, mari tambahkan anotasi ke dokumen yang dimuat. Dalam contoh ini, kita akan menambahkan anotasi area:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Langkah 3: Simpan Dokumen Beranotasi
Terakhir, simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara membuat anotasi pada dokumen PDF menggunakan GroupDocs.Annotation untuk .NET. Dengan mengikuti panduan langkah demi langkah, Anda dapat mengintegrasikan fungsionalitas anotasi dengan mudah ke dalam aplikasi .NET Anda, sehingga pengguna dapat berkolaborasi secara efektif pada file PDF.

## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua kerangka kerja .NET?
Ya, GroupDocs.Annotation untuk .NET kompatibel dengan berbagai kerangka kerja .NET, termasuk .NET Framework, .NET Core, dan .NET Standard.
### Bisakah saya menyesuaikan tampilan anotasi?
Tentu saja! GroupDocs.Annotation untuk .NET menyediakan opsi penyesuaian yang luas, yang memungkinkan Anda mengubah tampilan dan perilaku anotasi sesuai dengan kebutuhan Anda.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat mengunduh uji coba gratis GroupDocs.Annotation untuk .NET dari [situs web](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Annotation untuk .NET?
Jika Anda mengalami masalah teknis atau memiliki pertanyaan tentang GroupDocs.Annotation untuk .NET, Anda dapat mencari bantuan dari [forum dukungan](https://forum.groupdocs.com/c/annotation/10).
### Di mana saya dapat membeli lisensi untuk GroupDocs.Annotation untuk .NET?
Anda dapat membeli lisensi untuk GroupDocs.Annotation untuk .NET dari [halaman pembelian](https://purchase.groupdocs.com/buy).