---
title: Tambahkan Anotasi Fragmen Teks Pencarian ke Dokumen
linktitle: Tambahkan Anotasi Fragmen Teks Pencarian ke Dokumen
second_title: GroupDocs.Annotasi .NET API
description: Jelajahi kecanggihan GroupDocs.Annotation untuk .NET dan tambahkan kemampuan anotasi dokumen dengan mudah ke aplikasi Anda.
weight: 20
url: /id/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Perkenalan
Dalam bidang pengembangan .NET, GroupDocs.Annotation menonjol sebagai alat yang ampuh untuk membuat anotasi dokumen dengan lancar. Baik Anda seorang pengembang berpengalaman atau baru saja memasuki dunia .NET, tutorial komprehensif ini akan memandu Anda memahami esensi penggunaan GroupDocs.Annotation untuk .NET, mulai dari mengimpor namespace hingga menguasai seluk-beluk menambahkan anotasi fragmen teks pencarian ke dokumen.
## Perkenalan
GroupDocs.Annotation for .NET memberdayakan pengembang untuk menggabungkan kemampuan anotasi dokumen ke dalam aplikasi mereka dengan mudah. Dengan API intuitif dan fitur canggihnya, pengembang dapat membuat anotasi berbagai format dokumen, termasuk PDF, dokumen Microsoft Office, gambar, dan banyak lagi.
## Prasyarat
Sebelum mendalami GroupDocs.Annotation untuk .NET, pastikan Anda memiliki prasyarat berikut:

## Impor Namespace
Pertama, impor namespace yang diperlukan untuk mengakses kelas dan metode GroupDocs.Annotation di proyek .NET Anda:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tentukan Jalur Keluaran
Mulailah dengan menentukan jalur keluaran tempat dokumen beranotasi akan disimpan:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Annotator
 Selanjutnya, inisialisasi sebuah instance dari`Annotator` kelas dengan memberikan jalur ke dokumen yang ingin Anda beri anotasi:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Langkah 3: Buat Anotasi Fragmen Teks Pencarian
 Membuat`SearchTextFragment` objek dengan properti yang diinginkan, seperti teks yang akan dicari, ukuran font, jenis font, warna font, dan warna latar belakang:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Langkah 4: Tambahkan Anotasi
 Tambahkan anotasi fragmen teks pencarian yang dibuat ke dokumen menggunakan`Add` metode anotator:
```csharp
annotator.Add(searchText);
```
## Langkah 5: Simpan Dokumen Beranotasi
Simpan dokumen beranotasi ke jalur keluaran yang ditentukan:
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Tampilkan Pesan Sukses
Beri tahu pengguna bahwa dokumen telah berhasil disimpan:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Kesimpulannya, GroupDocs.Annotation untuk .NET menyederhanakan proses penambahan anotasi ke dokumen, meningkatkan kolaborasi dan proses peninjauan dokumen. Dengan mengikuti langkah-langkah yang diuraikan dalam panduan ini, Anda dapat mengintegrasikan kemampuan anotasi dokumen ke dalam aplikasi .NET Anda dengan lancar.
## FAQ
### Apakah GroupDocs.Annotation kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen, termasuk PDF, dokumen Microsoft Office, gambar, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan anotasi?
Sangat! GroupDocs.Annotation menyediakan opsi penyesuaian ekstensif untuk anotasi, memungkinkan Anda menyesuaikan properti seperti ukuran font, warna, dan gaya.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?
 Ya, Anda dapat mengakses uji coba gratis GroupDocs.Annotation untuk menjelajahi fitur dan kemampuannya sebelum melakukan pembelian[Di Sini](https://releases.groupdocs.com/)..
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Annotation?
 Untuk dukungan dan bantuan dengan GroupDocs.Annotation, Anda dapat mengunjungi GroupDocs[forum](https://forum.groupdocs.com/c/annotation/10) didedikasikan untuk pertanyaan dan diskusi terkait anotasi.
### Bagaimana cara mendapatkan lisensi sementara untuk GroupDocs.Annotation?
 Anda dapat memperoleh lisensi sementara untuk GroupDocs.Annotation melalui GroupDocs[situs web](https://purchase.groupdocs.com/temporary-license/), memungkinkan Anda mengevaluasi produk sepenuhnya.