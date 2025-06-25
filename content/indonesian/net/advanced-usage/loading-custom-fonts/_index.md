---
"description": "Pelajari cara memuat font kustom dengan lancar di GroupDocs.Annotation for .NET untuk menyempurnakan anotasi dokumen. Ikuti langkah demi langkah kami untuk integrasi yang mudah."
"linktitle": "Memuat Font Kustom"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Memuat Font Kustom"
"url": "/id/net/advanced-usage/loading-custom-fonts/"
"weight": 20
---

# Memuat Font Kustom

## Perkenalan
GroupDocs.Annotation untuk .NET adalah pustaka canggih yang memungkinkan pengembang untuk menambahkan fitur anotasi ke aplikasi .NET mereka dengan mudah. Salah satu fungsi utama yang ditawarkannya adalah kemampuan untuk memuat font khusus, yang memungkinkan penyesuaian dan fleksibilitas yang lebih baik dalam anotasi dokumen.
## Prasyarat
Sebelum melanjutkan tutorial, pastikan Anda memiliki prasyarat berikut:
1. GroupDocs.Annotation untuk Pustaka .NET: Unduh dan instal pustaka dari [Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan .NET: Pastikan Anda memiliki lingkungan kerja yang disiapkan untuk pengembangan .NET.
3. Akses ke Font Kustom: Siapkan font kustom yang ingin Anda muat ke aplikasi Anda.

## Mengimpor Ruang Nama
Dalam proyek .NET Anda, impor namespace yang diperlukan untuk memanfaatkan GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Buat Instansi Objek Anotator
Buat contoh dari `Annotator` kelas dengan menyediakan jalur ke dokumen PDF input beserta direktori font kustom:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Kode Anda untuk operasi selanjutnya akan ada di sini
}
```
## Langkah 2: Konfigurasikan Opsi Pratinjau
Tentukan opsi pratinjau untuk menentukan bagaimana pratinjau dokumen akan dibuat. Anda dapat mengatur opsi seperti format pratinjau, nomor halaman, dll.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Langkah 3: Hasilkan Pratinjau Dokumen
Memanfaatkan `GeneratePreview` metode dari `Document` properti untuk menghasilkan pratinjau dengan font khusus:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Langkah 4: Menampilkan Jalur Output
Terakhir, tampilkan pesan yang menunjukkan keberhasilan pembuatan pratinjau dokumen beserta jalur direktori keluaran:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Kesimpulan
Kesimpulannya, memuat font kustom di GroupDocs.Annotation untuk .NET memberi pengembang fleksibilitas untuk menyesuaikan anotasi dokumen sesuai dengan kebutuhan mereka. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat mengintegrasikan font kustom ke dalam aplikasi .NET Anda dengan lancar dan meningkatkan pengalaman anotasi bagi pengguna.
## Pertanyaan yang Sering Diajukan
### Bisakah saya memuat beberapa font khusus secara bersamaan?
Ya, Anda dapat menentukan beberapa direktori font saat membuat instance `Annotator` obyek.
### Apakah ada batasan pada jenis font yang didukung?
GroupDocs.Annotation untuk .NET mendukung berbagai jenis font, termasuk font TrueType (.ttf) dan OpenType (.otf).
### Bisakah saya mengubah font yang dimuat secara dinamis saat runtime?
Ya, Anda dapat memodifikasi direktori font secara dinamis dan memuat ulang anotasi dokumen sesuai kebutuhan.
### Apakah GroupDocs.Annotation mendukung penyematan font pada dokumen keluaran?
Ya, Anda dapat menanamkan font khusus dalam dokumen keluaran untuk memastikan tampilan yang konsisten di berbagai platform.
### Apakah ada cara untuk menangani lisensi font dalam aplikasi?
GroupDocs.Annotation menyediakan opsi untuk mengelola lisensi font, termasuk lisensi sementara untuk tujuan evaluasi.