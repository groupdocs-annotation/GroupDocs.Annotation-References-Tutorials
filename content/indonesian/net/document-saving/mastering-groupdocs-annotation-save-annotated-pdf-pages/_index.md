---
"date": "2025-05-06"
"description": "Pelajari cara menyimpan halaman PDF yang diberi anotasi secara efisien menggunakan GroupDocs.Annotation for .NET. Tingkatkan pengelolaan dan kolaborasi dokumen dengan panduan terperinci ini."
"title": "Cara Menyimpan Halaman Beranotasi dalam PDF Menggunakan GroupDocs.Annotation untuk .NET"
"url": "/id/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# Cara Menyimpan Halaman Beranotasi dalam PDF Menggunakan GroupDocs.Annotation untuk .NET

## Perkenalan

Kesulitan menyimpan halaman beranotasi tertentu dari dokumen PDF Anda? Panduan lengkap ini menunjukkan cara melakukannya secara efisien menggunakan GroupDocs.Annotation untuk .NET. Dengan memanfaatkan kemampuan anotasi, sederhanakan pengelolaan dokumen dan tingkatkan kolaborasi dengan berfokus pada konten yang relevan.

Dalam tutorial ini, Anda akan mempelajari:
- Menyiapkan lingkungan pengembangan Anda dengan GroupDocs.Annotation
- Menambahkan berbagai jenis anotasi
- Menyimpan hanya halaman yang diberi anotasi secara efektif

Siap untuk memulai? Pastikan Anda telah menyiapkan semuanya.

### Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:
- **Kerangka .NET** (versi 4.6 atau lebih baru) atau **.NET Inti/5+**
- Editor kode seperti Visual Studio
- Pengetahuan dasar tentang pengaturan proyek C# dan .NET

## Menyiapkan GroupDocs.Annotation untuk .NET

Untuk mulai menggunakan GroupDocs.Annotation, instal melalui NuGet.

**Konsol Pengelola Paket NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.KLIK NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Akuisisi Lisensi

GroupDocs menawarkan uji coba gratis untuk menjelajahi perangkat lunak mereka secara menyeluruh. Untuk penggunaan lebih lama, beli lisensi atau minta lisensi sementara:
- **Uji Coba Gratis**: Jelajahi fitur tanpa batasan untuk periode awal.
- **Lisensi Sementara**: Gunakan GroupDocs.Annotation dalam produksi untuk sementara.
- **Pembelian**Amankan kebutuhan jangka panjang Anda dengan lisensi komersial.

Setelah terinstal, inisialisasikan perpustakaan sebagai berikut:

```csharp
using GroupDocs.Annotation;

// Pengaturan dasar untuk memuat dan memberi anotasi pada dokumen
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Panduan Implementasi

### Menambahkan Anotasi

#### Ringkasan

Anotasi membantu menyorot area penting dalam dokumen Anda. Mari kita coba menambahkan anotasi `AreaAnnotation` dan sebuah `EllipseAnnotation`.

**Langkah 1: Buat Anotasi Area**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Tentukan anotasi area
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posisi dan ukuran
    BackgroundColor = 65535,                // Nilai warna ARGB untuk sorotan
    PageNumber = 1                          // Nomor halaman tertentu
};
```

Itu `AreaAnnotation` menyorot area persegi panjang pada dokumen. Sesuaikan posisinya (`Box`) dan warna latar belakang.

**Langkah 2: Buat Anotasi Elips**

```csharp
// Tentukan anotasi elips
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posisi dan ukuran
    BackgroundColor = 123456,                // Nilai warna ARGB untuk sorotan
    PageNumber = 1                           // Nomor halaman tertentu
};
```

Itu `EllipseAnnotation` memungkinkan menggambar bentuk oval pada dokumen. Sesuaikan posisi dan dimensi menggunakan `Box` milik.

**Langkah 3: Tambahkan Anotasi**

```csharp
// Menambahkan anotasi ke instance Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Menggunakan `Add` metode, termasuk beberapa jenis anotasi. Langkah ini menambahkan `AreaAnnotation` Dan `EllipseAnnotation`.

### Hanya Menyimpan Halaman yang Dianotasi

#### Ringkasan

Untuk hanya menyimpan halaman yang berisi anotasi, konfigurasikan opsi penyimpanan Anda sebagaimana mestinya.

**Langkah 4: Simpan Halaman yang Dianotasi**

```csharp
using GroupDocs.Annotation.Options;

// Siapkan opsi penyimpanan untuk hanya menyertakan halaman yang diberi anotasi
annotator.Save("path/to/output/document.pdf\