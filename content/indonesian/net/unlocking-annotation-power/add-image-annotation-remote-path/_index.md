---
"description": "Pelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan pengelolaan dokumen dengan kemampuan anotasi yang canggih."
"linktitle": "Tambahkan Anotasi Gambar ke Dokumen (Jalur Jarak Jauh)"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Gambar ke Dokumen (Jalur Jarak Jauh)"
"url": "/id/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Tambahkan Anotasi Gambar ke Dokumen (Jalur Jarak Jauh)

## Perkenalan
Dalam tutorial ini, kita akan membahas proses penambahan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation for .NET. Pustaka ini menyediakan alat yang hebat untuk membuat anotasi berbagai jenis dokumen secara terprogram.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1. GroupDocs.Annotation untuk .NET: Unduh dan instal pustaka dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Pastikan Anda memiliki lingkungan pengembangan yang berfungsi untuk pengembangan .NET.
3. Dokumen: Siapkan dokumen yang ingin Anda beri anotasi. Untuk tutorial ini, kami akan menganggap Anda memiliki dokumen PDF bernama `input.pdf`.
4. Gambar untuk Anotasi: Pilih gambar yang ingin Anda gunakan untuk anotasi. Pastikan Anda telah menyiapkan URL gambar atau jalur lokal.

## Mengimpor Ruang Nama
Sebelum kita mulai membuat kode, mari impor namespace yang diperlukan:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Langkah 1: Tetapkan Jalur Output
Pertama, tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Buat contoh dari `Annotator` kelas dan tentukan dokumen masukan.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kode anotasi akan ada di sini
}
```
## Langkah 3: Tambahkan Anotasi Gambar
Sekarang, mari tambahkan anotasi gambar ke dokumen. Kita akan tentukan properti anotasi gambar seperti posisi, opasitas, nomor halaman, dan jalur gambar.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Tentukan posisi anotasi
    CreatedOn = DateTime.Now, // Tetapkan tanggal pembuatan
    Opacity = 0.7, // Atur opasitas (0 hingga 1)
    PageNumber = 0, // Tentukan nomor halaman
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Berikan URL gambar
};
annotator.Add(image); // Tambahkan anotasi gambar
```
## Langkah 4: Simpan Dokumen
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Save(outputPath);
```
## Langkah 5: Menampilkan Jalur Output
Beritahukan pengguna tentang operasi penyimpanan dokumen yang berhasil dan tampilkan jalur keluaran.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan anotasi gambar ke dokumen menggunakan GroupDocs.Annotation for .NET. Dengan mengikuti langkah-langkah ini, Anda dapat menyempurnakan aplikasi manajemen dokumen Anda dengan kemampuan anotasi yang canggih.
## Pertanyaan yang Sering Diajukan
### Bisakah GroupDocs.Annotation digunakan dengan format dokumen lain selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, dan banyak lagi.
### Apakah GroupDocs.Annotation kompatibel dengan .NET Core?
Ya, GroupDocs.Annotation kompatibel dengan .NET Framework dan .NET Core.
### Bisakah saya menyesuaikan tampilan anotasi?
Ya, Anda dapat menyesuaikan tampilan anotasi seperti warna, opasitas, dan ukuran.
### Apakah GroupDocs.Annotation mendukung fitur anotasi kolaboratif?
Ya, GroupDocs.Annotation menawarkan fitur anotasi kolaboratif untuk kolaborasi waktu nyata pada dokumen.
### Apakah ada versi uji coba yang tersedia untuk pengujian?
Ya, Anda bisa mendapatkan uji coba gratis GroupDocs.Annotation dari [Di Sini](https://releases.groupdocs.com/).