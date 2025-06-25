---
"date": "2025-05-06"
"description": "Pelajari cara membuat pratinjau dokumen yang ringkas dan relevan dari kolom lembar kerja tertentu menggunakan GroupDocs.Annotation untuk .NET. Sempurna untuk menyederhanakan alur kerja dalam analisis data dan manajemen TI."
"title": "Hasilkan Pratinjau Lembar Excel yang Ditargetkan Menggunakan GroupDocs.Annotation .NET"
"url": "/id/net/document-preview/groupdocs-annotation-net-create-previews-worksheet-columns/"
"weight": 1
---

# Hasilkan Pratinjau Lembar Excel yang Ditargetkan Menggunakan GroupDocs.Annotation .NET
## Panduan Pratinjau Dokumen
### Perkenalan
Apakah Anda ingin meningkatkan kejelasan pemrosesan dokumen dengan berfokus pada titik data tertentu? Baik Anda seorang pengembang yang membuat alat analisis data, seorang profesional TI yang mengelola dokumen, atau siapa pun yang tertarik dalam merampingkan alur kerja, pratinjau dokumen yang ditargetkan dapat menghemat waktu dan meningkatkan efisiensi. Tutorial ini akan memandu Anda menggunakan GroupDocs.Annotation untuk .NET guna menghasilkan pratinjau dari kolom lembar kerja yang dipilih, memastikan keluaran Anda ringkas dan relevan.

#### Apa yang Akan Anda Pelajari:
- Cara mengatur GroupDocs.Annotation untuk .NET
- Membuat pratinjau dengan kolom lembar kerja yang ditentukan
- Mengonfigurasi opsi pratinjau untuk hasil yang optimal
- Aplikasi praktis fitur ini dalam skenario dunia nyata

Mari kita mulai dengan meninjau prasyarat yang diperlukan sebelum Anda mulai menerapkan solusi ini.
## Prasyarat
Sebelum terjun ke implementasi, pastikan Anda memiliki hal berikut:

### Pustaka dan Versi yang Diperlukan:
- **GroupDocs.Annotation untuk .NET**: Diperlukan versi 25.4.0 atau yang lebih baru.

### Persyaratan Pengaturan Lingkungan:
- Lingkungan pengembangan dengan .NET Framework atau .NET Core terpasang.

### Prasyarat Pengetahuan:
- Pemahaman dasar tentang pemrograman C#
- Keakraban dengan operasi I/O file di .NET
## Menyiapkan GroupDocs.Annotation untuk .NET
Untuk memulai, Anda perlu menginstal pustaka GroupDocs.Annotation. Berikut ini cara melakukannya menggunakan pengelola paket yang berbeda:

**Konsol Pengelola Paket NuGet**
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.KLIK NET**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Langkah-langkah Memperoleh Lisensi:
- **Uji Coba Gratis**: Unduh versi uji coba dari [Situs web GroupDocs](https://releases.groupdocs.com/annotation/net/) untuk menguji fitur.
- **Lisensi Sementara**: Dapatkan lisensi sementara untuk akses penuh selama pengembangan di [Halaman Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/).
- **Pembelian**:Untuk penggunaan produksi, beli lisensi melalui [Halaman Pembelian GroupDocs](https://purchase.groupdocs.com/buy).
### Inisialisasi dan Pengaturan Dasar dengan C#:
Berikut ini cara mengatur lingkungan Anda untuk mulai bekerja dengan GroupDocs.Annotation untuk .NET.
```csharp
using System;
using GroupDocs.Annotation;
// Inisialisasi objek Annotator dengan jalur dokumen.
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";
Annotator annotator = new Annotator(inputFilePath);
```
Sekarang setelah Anda menyiapkannya, mari beralih ke pembuatan pratinjau dari kolom lembar kerja tertentu.
## Panduan Implementasi
Panduan ini akan memandu Anda dalam mengimplementasikan fitur pembuatan pratinjau dokumen dengan kolom lembar kerja tertentu. Setiap bagian berfokus pada aspek tertentu dari proses implementasi.
### Membuat Pratinjau Dokumen dari Kolom Lembar Kerja Tertentu
**Ringkasan**Fitur ini memungkinkan pengembang untuk membuat pratinjau dokumen yang hanya menyertakan kolom yang dipilih dari lembar kerja Excel, sehingga meningkatkan kinerja dan relevansi.
#### Langkah 1: Tentukan Opsi Pratinjau
Mulailah dengan menyiapkan `PreviewOptions`Ini menentukan bagaimana dan di mana file pratinjau Anda akan disimpan.
```csharp
using System.IO;
using GroupDocs.Annotation.Options;
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY";
PreviewOptions previewOptions = new PreviewOptions(pageNumber => 
    new FileStream(Path.Combine(outputDirectoryPath, $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose());
```
**Penjelasan**: : Itu `PreviewOptions` konstruktor mengambil dua delegasi. Yang pertama menentukan jalur berkas untuk gambar pratinjau setiap halaman. Yang kedua memastikan bahwa aliran dibuang dengan benar setelah digunakan.
#### Langkah 2: Tentukan Kolom Lembar Kerja
Pilih kolom mana dari lembar kerja Anda yang ingin Anda sertakan dalam pratinjau dengan menambahkannya ke `WorksheetColumns`.
```csharp
// Sertakan kolom tertentu dari Sheet1.
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1\