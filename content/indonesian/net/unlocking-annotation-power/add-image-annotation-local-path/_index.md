---
"description": "Pelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan kemampuan pemrosesan dokumen dengan mudah."
"linktitle": "Tambahkan Anotasi Gambar ke Dokumen (Jalur Lokal)"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Gambar ke Dokumen (Jalur Lokal)"
"url": "/id/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Tambahkan Anotasi Gambar ke Dokumen (Jalur Lokal)

## Perkenalan
GroupDocs.Annotation untuk .NET adalah pustaka canggih yang memungkinkan pengembang untuk menambahkan berbagai jenis anotasi ke dokumen secara terprogram. Dalam tutorial ini, kita akan mempelajari cara menambahkan anotasi gambar ke dokumen menggunakan jalur lokal.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan dasar tentang bahasa pemrograman C#.
2. Visual Studio terinstal di sistem Anda.
3. GroupDocs.Annotation untuk pustaka .NET yang terinstal atau tutorialsd dalam proyek Anda.
4. Dokumen masukan (misalnya, PDF) dan berkas gambar untuk anotasi.
## Mengimpor Ruang Nama
Pertama, Anda perlu mengimpor namespace yang diperlukan ke berkas C# Anda. Namespace ini menyediakan akses ke kelas dan metode yang diperlukan untuk bekerja dengan GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Langkah 1: Tentukan Jalur Output
Tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Inisialisasi anotator dengan memberikan jalur ke dokumen masukan.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi ada di sini
}
```
## Langkah 3: Buat Anotasi Gambar
Buat contoh dari `ImageAnnotation` kelas dan tentukan propertinya seperti posisi, opasitas, nomor halaman, dan jalur gambar.
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
Tambahkan anotasi gambar yang dibuat ke dokumen menggunakan `Add` metode pencatat.
```csharp
annotator.Add(image);
```
## Langkah 5: Simpan Dokumen
Simpan dokumen yang diberi anotasi ke jalur keluaran.
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Menampilkan Jalur Output
Menampilkan pesan yang menunjukkan keberhasilan penyimpanan dokumen dan lokasi berkas keluaran.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation for .NET. Dengan mengikuti langkah-langkah sederhana ini, Anda dapat meningkatkan kemampuan pemrosesan dokumen Anda dengan fitur anotasi yang canggih.
## Pertanyaan yang Sering Diajukan
### Bisakah saya memberi anotasi pada dokumen selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, dan banyak lagi.
### Apakah GroupDocs.Annotation kompatibel dengan .NET Core?
Ya, GroupDocs.Annotation kompatibel dengan .NET Framework dan .NET Core.
### Bisakah saya menyesuaikan tampilan anotasi?
Tentu saja, Anda dapat menyesuaikan tampilan, ukuran, warna, dan properti anotasi lainnya sesuai kebutuhan Anda.
### Apakah GroupDocs.Annotation menyediakan dukungan untuk anotasi kolaboratif?
Ya, GroupDocs.Annotation menawarkan fitur anotasi kolaboratif yang memungkinkan banyak pengguna untuk membuat anotasi dokumen secara bersamaan.
### Di mana saya dapat menemukan bantuan atau dukungan tambahan?
Anda dapat mengunjungi forum GroupDocs.Annotation untuk mendapatkan bantuan dan dukungan dari komunitas.