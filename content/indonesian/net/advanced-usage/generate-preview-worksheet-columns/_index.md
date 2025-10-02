---
"description": "Pelajari cara memberi anotasi pada dokumen menggunakan GroupDocs.Annotation untuk .NET. Tutorial langkah demi langkah untuk pengembang .NET. Sempurnakan aplikasi Anda."
"linktitle": "Hasilkan Kolom Lembar Kerja Pratinjau"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Hasilkan Kolom Lembar Kerja Pratinjau"
"url": "/id/net/advanced-usage/generate-preview-worksheet-columns/"
type: docs
"weight": 15
---

# Hasilkan Kolom Lembar Kerja Pratinjau

## Perkenalan
Selamat datang di tutorial lengkap kami tentang memanfaatkan kemampuan GroupDocs.Annotation untuk .NET! Dalam panduan ini, kami akan memandu Anda melalui proses penggunaan alat yang hebat ini untuk membuat anotasi dokumen secara efektif. Apakah Anda seorang pengembang berpengalaman atau pendatang baru di dunia pengembangan .NET, tutorial ini akan membekali Anda dengan pengetahuan dan keterampilan yang diperlukan untuk mengintegrasikan fitur anotasi dengan lancar ke dalam aplikasi Anda.
## Prasyarat
Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:
### 1. Pengaturan Lingkungan Pengembangan .NET
Pastikan Anda memiliki lingkungan pengembangan .NET yang berfungsi pada komputer Anda. Anda dapat mengunduh versi terbaru .NET SDK dari situs web Microsoft.
### 2. GroupDocs.Annotation untuk Pustaka .NET
Unduh dan instal pustaka GroupDocs.Annotation untuk .NET dari sumber yang disediakan [tautan unduhan](https://releases.groupdocs.com/annotation/net/)Ikuti petunjuk instalasi untuk mengintegrasikan pustaka ke dalam proyek Anda dengan sukses.
### 3. Dokumen Masukan
Siapkan contoh dokumen (misalnya, "input.xlsx") yang ingin Anda beri anotasi menggunakan GroupDocs.Annotation for .NET. Pastikan dokumen tersebut dapat diakses dari direktori proyek Anda.

## Mengimpor Ruang Nama
Untuk memulai, impor namespace yang diperlukan ke dalam proyek Anda. Namespace ini menyediakan akses ke kelas dan metode yang diperlukan untuk menjalankan tugas anotasi dokumen secara efektif.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

Sekarang setelah kita menyiapkan lingkungan pengembangan dan mengimpor namespace yang diperlukan, mari masuk ke pembuatan kolom lembar kerja pratinjau untuk dokumen kita.
## Langkah 1: Inisialisasi Opsi Pratinjau
```csharp
PreviewOptions previewOptions = new PreviewOptions(
    pageNumber => new FileStream(Path.Combine("Your Document Directory", $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose()
);
```
## Langkah 2: Tentukan Kolom Lembar Kerja
```csharp
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));
```
## Langkah 3: Inisialisasi Anotator dengan Dokumen Input
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## Langkah 4: Menampilkan Pesan Sukses
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Kesimpulan
Selamat! Anda telah berhasil mempelajari cara membuat kolom lembar kerja pratinjau menggunakan GroupDocs.Annotation untuk .NET. Dengan pengetahuan ini, kini Anda dapat menggabungkan kemampuan anotasi tingkat lanjut ke dalam aplikasi .NET Anda dengan mudah.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation kompatibel dengan kerangka kerja .NET lainnya?
Ya, GroupDocs.Annotation mendukung berbagai kerangka kerja .NET, termasuk .NET Core dan .NET Framework.
### Bisakah saya menyesuaikan tampilan anotasi yang dibuat dengan GroupDocs.Annotation?
Tentu saja! GroupDocs.Annotation menyediakan opsi penyesuaian yang luas untuk tampilan anotasi, termasuk warna, opasitas, dan jenis anotasi.
### Apakah GroupDocs.Annotation mendukung format dokumen selain Excel?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen, termasuk PDF, Word, PowerPoint, dan banyak lagi.
### Apakah dukungan teknis tersedia untuk pengguna GroupDocs.Annotation?
Ya, Anda dapat mengakses dukungan teknis dan forum komunitas melalui situs web yang disediakan. [tautan dukungan](https://forum.groupdocs.com/c/annotation/10).
### Dapatkah saya mencoba GroupDocs.Annotation sebelum membeli lisensi?
Tentu saja! Anda dapat mengunduh versi uji coba gratis GroupDocs.Annotation dari [situs web](https://releases.groupdocs.com/).