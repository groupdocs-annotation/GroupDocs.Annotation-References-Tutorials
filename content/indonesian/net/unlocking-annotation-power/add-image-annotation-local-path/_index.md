---
title: Tambahkan Anotasi Gambar ke Dokumen (Jalur Lokal)
linktitle: Tambahkan Anotasi Gambar ke Dokumen (Jalur Lokal)
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Tingkatkan kemampuan pemrosesan dokumen dengan mudah.
weight: 14
url: /id/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Perkenalan
GroupDocs.Annotation for .NET adalah perpustakaan canggih yang memungkinkan pengembang menambahkan berbagai jenis anotasi ke dokumen secara terprogram. Dalam tutorial ini, kita akan mempelajari cara menambahkan anotasi gambar ke dokumen menggunakan jalur lokal.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan dasar bahasa pemrograman C#.
2. Visual Studio diinstal pada sistem Anda.
3. GroupDocs.Annotation untuk perpustakaan .NET diinstal atau direferensikan dalam proyek Anda.
4. Dokumen masukan (misalnya PDF) dan file gambar untuk anotasi.
## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke file C# Anda. Namespace ini menyediakan akses ke kelas dan metode yang diperlukan untuk bekerja dengan GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Langkah 1: Tentukan Jalur Keluaran
Tentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Annotator
Inisialisasi anotator dengan menyediakan jalur ke dokumen masukan.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi ada di sini
}
```
## Langkah 3: Buat Anotasi Gambar
 Buat sebuah instance dari`ImageAnnotation`kelas dan tentukan propertinya seperti posisi, opacity, nomor halaman, dan jalur gambar.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Langkah 4: Tambahkan Anotasi
 Tambahkan anotasi gambar yang dibuat ke dokumen menggunakan`Add` metode anotator.
```csharp
annotator.Add(image);
```
## Langkah 5: Simpan Dokumen
Simpan dokumen beranotasi ke jalur keluaran.
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Tampilkan Jalur Keluaran
Menampilkan pesan yang menunjukkan keberhasilan penyimpanan dokumen dan lokasi file keluaran.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation untuk .NET. Dengan mengikuti langkah-langkah sederhana ini, Anda dapat meningkatkan kemampuan pemrosesan dokumen Anda dengan fitur anotasi yang canggih.
## FAQ
### Bisakah saya membuat anotasi pada dokumen selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, dan lainnya.
### Apakah GroupDocs.Annotation kompatibel dengan .NET Core?
Ya, GroupDocs.Annotation kompatibel dengan .NET Framework dan .NET Core.
### Bisakah saya menyesuaikan tampilan anotasi?
Tentu saja, Anda dapat menyesuaikan tampilan, ukuran, warna, dan properti anotasi lainnya sesuai dengan kebutuhan Anda.
### Apakah GroupDocs.Annotation memberikan dukungan untuk anotasi kolaboratif?
Ya, GroupDocs.Annotation menawarkan fitur anotasi kolaboratif yang memungkinkan banyak pengguna membuat anotasi dokumen secara bersamaan.
### Di mana saya bisa mendapatkan bantuan atau dukungan tambahan?
Anda dapat mengunjungi forum GroupDocs.Annotation untuk mendapatkan bantuan dan dukungan dari komunitas.