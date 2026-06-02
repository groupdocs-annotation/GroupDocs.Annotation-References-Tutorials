---
categories:
- PDF Processing
date: '2026-05-26'
description: Pelajari cara membuat sistem review dokumen menggunakan GroupDocs Annotation
  untuk .NET. Tutorial langkah demi langkah mencakup pengaturan, jenis anotasi, penyetelan
  kinerja, dan pemecahan masalah untuk pengembang C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: Panduan PDF Annotation .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Buat Sistem Review Dokumen: Panduan PDF Annotation .NET'
type: docs
url: /id/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Buat Sistem Review Dokumen: Panduan PDF Annotation .NET

Jika Anda perlu **membuat sistem review dokumen** yang memungkinkan pengguna menambahkan komentar, sorotan, dan bentuk ke PDF langsung dari aplikasi .NET, Anda berada di tempat yang tepat. GroupDocs.Annotation untuk .NET menghilangkan kerumitan penanganan PDF tingkat rendah sambil memberi Anda kontrol detail atas setiap tipe anotasi. Dalam panduan ini Anda akan melihat cara menyiapkan pustaka, menambahkan anotasi area, elips, dan teks, memfilter apa yang disimpan, dan menjaga kinerja tetap cepat bahkan dengan file berisi ratusan halaman.

## Jawaban Cepat
- **Perpustakaan apa yang menangani PDF annotation di .NET?** GroupDocs.Annotation untuk .NET.  
- **Apakah saya dapat menambahkan sorotan, lingkaran, dan komentar secara programatis?** Ya – gunakan objek AreaAnnotation, EllipseAnnotation, dan TextAnnotation.  
- **Apakah lisensi diperlukan untuk produksi?** Lisensi GroupDocs yang valid wajib untuk setiap penerapan produksi.  
- **Seberapa besar PDF yang dapat diproses?** Hingga 500 MB dapat ditangani tanpa memuat seluruh file ke memori.  
- **Apakah ini akan membantu saya membuat sistem review dokumen?** Tentu – Anda dapat menyimpan secara batch, memfilter, dan memberi versi anotasi untuk reviewer.  

## Apa itu sistem review dokumen?
Sebuah **sistem review dokumen** adalah solusi perangkat lunak yang memungkinkan banyak pemangku kepentingan untuk memberi anotasi, komentar, dan menyetujui file PDF dalam alur kerja terkoordinasi. Sistem ini memusatkan umpan balik, melacak perubahan, dan sering mengekspor versi bersih untuk persetujuan akhir.

## Mengapa menggunakan GroupDocs Annotation untuk .NET dalam membuat sistem review dokumen?
GroupDocs Annotation mendukung **lebih dari 30 tipe anotasi**, memproses PDF hingga **500 MB**, dan berjalan pada **.NET Framework 4.6.1+**, **.NET Core 2.0+**, serta **.NET 6+**. API-nya memungkinkan Anda menambah, menghapus, dan memfilter anotasi tanpa pernah menyentuh struktur internal PDF, yang mempercepat pengembangan dan mengurangi bug.

## Prasyarat dan Penyiapan Lingkungan
Sebelum menulis kode apa pun, pastikan lingkungan pengembangan Anda memenuhi kriteria berikut:

- **IDE:** Visual Studio 2019 atau yang lebih baru, atau VS Code dengan ekstensi C#.  
- **Target Framework:** .NET Framework 4.6.1 + atau .NET Core 2.0 + (kami merekomendasikan .NET 6 untuk proyek baru).  
- **Akses NuGet:** Kemampuan menginstal paket dari nuget.org.  
- **PDF Contoh:** Setidaknya satu PDF multi‑halaman untuk menguji penempatan anotasi.  
- **Memori & Disk:** Minimum 4 GB RAM dan ruang disk bebas yang cukup untuk file sementara (pemrosesan anotasi dapat menghasilkan aliran sementara).  

### Praktik Pengembangan yang Direkomendasikan
- Simpan solusi Anda di bawah kontrol sumber (Git) sehingga Anda dapat mengembalikan perubahan terkait anotasi.  
- Gunakan folder **Annotations** khusus dalam proyek Anda untuk menyimpan file konfigurasi dan kunci lisensi.  
- Aktifkan **nullable reference types** (`<Nullable>enable</Nullable>`) untuk menangkap potensi bug referensi null lebih awal.  

## Memulai: Instalasi GroupDocs.Annotation
### Metode Instalasi
**Opsi 1: NuGet Package Manager Console**  
Jalankan perintah berikut di Package Manager Console:  

`Install-Package GroupDocs.Annotation`

**Opsi 2: .NET CLI (direkomendasikan untuk pengembangan lintas‑platform)**  
Jalankan di terminal:  

`dotnet add package GroupDocs.Annotation`

**Opsi 3: UI Package Manager Visual Studio**  
- Klik kanan proyek → **Manage NuGet Packages**  
- Cari **GroupDocs.Annotation**  
- Klik **Install** pada rilis stabil terbaru  

Ketiga metode tersebut menginstal binary yang sama; pilih yang sesuai dengan alur kerja Anda.

### Konfigurasi Lisensi
GroupDocs memerlukan lisensi yang valid untuk penggunaan produksi apa pun. Anda memiliki tiga pilihan:

- **Uji Coba Gratis:** Evaluasi 30‑hari dengan semua fitur.  
- **Lisensi Sementara:** Evaluasi diperpanjang untuk pengembangan dan pengujian.  
- **Lisensi Komersial:** Penggunaan tak terbatas di lingkungan produksi.  

Kelas `License` memuat dan menerapkan file lisensi GroupDocs untuk mengaktifkan fungsionalitas penuh. Anda dapat memperoleh lisensi dari [halaman pembelian GroupDocs](https://purchase.groupdocs.com/buy). Setelah menerima file `.lic`, letakkan di folder yang dapat dibaca aplikasi Anda dan arahkan kelas `License` ke file tersebut saat startup.

### Verifikasi Penyiapan Awal
Buat program konsol kecil yang memuat PDF dan menulis jumlah halaman ke konsol. Jika program berjalan tanpa melempar pengecualian, pustaka telah terinstal dan berlisensi dengan benar.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Catatan:** Kode di atas hanya untuk ilustrasi; Anda **tidak** perlu menambahkan blok kode berbingkai dalam artikel akhir, tetapi potongan kode inline menunjukkan penggunaan API yang tepat.

Jika Anda melihat jumlah halaman tercetak, Anda siap mulai menambahkan anotasi nyata.

## Implementasi Inti: Menambahkan Annotations ke PDF
### Definisi Anchor – Annotator
Kelas `Annotator` adalah titik masuk untuk semua operasi anotasi PDF di GroupDocs.Annotation untuk .NET. Ia memuat PDF ke memori, menyediakan metode untuk menambah, mengedit, dan mengambil anotasi, serta menangani penyimpanan dokumen yang telah dimodifikasi.

### Bagaimana cara menambahkan anotasi area dan elips?
Muat PDF dengan `new Annotator(...)`, buat objek `AreaAnnotation` dan `EllipseAnnotation`, atur koordinatnya, dan tambahkan ke koleksi annotator. Akhirnya, panggil `Save` untuk menyimpan perubahan. Alur kerja ini memungkinkan Anda secara programatis menyorot bagian (area) atau melingkari grafik penting dengan satu operasi atomik.

#### Langkah 1: Inisialisasi Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Langkah 2: Buat AreaAnnotation
`AreaAnnotation` represents a rectangular highlight area on a PDF page.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Langkah 3: Buat EllipseAnnotation
`EllipseAnnotation` represents an elliptical shape annotation on a PDF page.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Langkah 4: Tambahkan Anotasi secara Massal
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Tips Pro:** Menambahkan anotasi dalam daftar dan memanggil `Add` sekali mengurangi beban I/O, terutama ketika Anda perlu menyisipkan puluhan tanda di banyak halaman.

### Bagaimana cara menyimpan anotasi selektif?
`SaveOptions` mengonfigurasi cara PDF beranotasi disimpan, termasuk tipe anotasi mana yang disertakan. GroupDocs.Annotation memungkinkan Anda memfilter tipe anotasi yang ditulis ke file output. Buat instance `SaveOptions`, atur koleksi `AnnotationTypes` ke tipe yang ingin Anda pertahankan, dan berikan opsi tersebut ke `Save`. Ini sempurna untuk menghasilkan PDF hanya untuk reviewer atau menghapus catatan sementara sebelum pengarsipan.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Skenario Implementasi Dunia Nyata
### Skenario 1: Alur Kerja Review Dokumen
Beberapa reviewer menambahkan anotasi **Area**, **Ellipse**, dan **Text**. Setelah putaran review, Anda menghasilkan tiga PDF:
1. Versi lengkap dengan semua komentar.  
2. Versi hanya reviewer (menyaring catatan internal).  
3. Versi bersih untuk persetujuan akhir (hanya menyimpan sorotan).

### Skenario 2: Pembuatan Laporan Otomatis
Backend Anda memproses laporan penjualan harian, secara otomatis menyorot metrik kunci dengan anotasi area dan melingkari grafik outlier dengan anotasi elips. PDF yang dihasilkan kemudian dikirim via email ke pemangku kepentingan tanpa intervensi manual.

### Skenario 3: Dokumen Hukum Kolaboratif
Firma hukum sering perlu memisahkan komentar partner dari catatan associate junior. Dengan menandai anotasi dengan metadata khusus dan menggunakan penyimpanan selektif, Anda dapat menghasilkan PDF review partner yang menyembunyikan catatan junior, menyederhanakan kontrol versi.

## Optimasi Kinerja untuk Penggunaan Produksi
### Bagaimana cara mengelola memori saat memberi anotasi pada PDF besar?
`LoadOptions` memungkinkan Anda menentukan cara PDF dimuat, seperti rentang halaman atau kata sandi. Ketika PDF melebihi 100 MB, hindari memuat seluruh file dengan menggunakan konstruktor `LoadOptions` yang menerima rentang halaman. Proses halaman secara batch, buang setiap instance `Annotator` dengan blok `using`, dan bersihkan file sementara setelah setiap batch. Pendekatan ini menjaga penggunaan memori puncak di bawah 200 MB bahkan untuk dokumen 500 halaman.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Praktik Terbaik Manajemen Memori
- **Selalu bungkus `Annotator` dalam pernyataan `using`** untuk menjamin pembuangan sumber daya yang tidak dikelola.  
- **Proses anotasi secara batch**: kumpulkan semua anotasi untuk sebuah dokumen, lalu panggil `Add` sekali.  
- **Hindari memuat PDF penuh** ketika Anda hanya perlu memodifikasi subset halaman; gunakan `LoadOptions.PageNumbers`.  

### Strategi Penanganan File Besar
1. **Pemrosesan per halaman** – Muat, beri anotasi, dan simpan satu halaman pada satu waktu.  
2. **Output streaming** – Arahkan metode `Save` ke `MemoryStream` untuk menghindari penulisan disk menengah.  
3. **Pembersihan file sementara** – Hapus semua file sementara yang dibuat oleh annotator setelah setiap operasi.  

### Pertimbangan Pemrosesan Konkuren
- **Keamanan thread:** Instance `Annotator` tidak thread‑safe. Buat instance terpisah per thread.  
- **Pembatasan sumber daya:** Batasi pekerjaan bersamaan sesuai jumlah core CPU untuk mencegah saturasi CPU.  
- **API Async:** `SaveAsync` menyimpan dokumen beranotasi secara asynchronous, mengembalikan Task, yang berguna di lingkungan ASP.NET Core.  

## Memecahkan Masalah Umum
### Masalah 1: Kesalahan “File Not Found”
**Jawaban langsung:** Verifikasi bahwa jalur file yang Anda berikan ke `new Annotator(...)` bersifat absolut atau relatif dengan benar terhadap assembly yang dijalankan, dan pastikan proses aplikasi memiliki izin baca untuk lokasi tersebut. Jika file berada di share jaringan, map share tersebut atau gunakan jalur UNC.

**Perbaikan umum:**  
- Gunakan `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Berikan identitas application pool IIS hak baca/tulis pada folder.  

### Masalah 2: Anotasi muncul di lokasi yang salah
**Jawaban langsung:** Pastikan Anda menggunakan sistem koordinat yang sama (origin kiri‑atas) dan DPI halaman cocok dengan nilai yang Anda berikan. Dapatkan ukuran halaman melalui `annotator.GetPageInfo(pageNumber)` dan hitung koordinat relatif terhadap ukuran tersebut.

**Perbaikan umum:**  
- Kalikan koordinat dengan faktor skala halaman jika PDF dibuat dengan DPI non‑standar.  
- Periksa kembali bahwa Anda tidak mencampur poin (1/72 inci) dengan piksel.  

### Masalah 3: Masalah kinerja dengan file besar
**Jawaban langsung:** Beralih ke pemuatan rentang halaman, proses anotasi secara batch, dan buang setiap instance `Annotator` dengan cepat. Juga aktifkan opsi `MemoryCache` di `LoadOptions` untuk menggunakan kembali buffer antar operasi.

**Perbaikan umum:**  
- Setel `LoadOptions.UseMemoryCache = true`.  
- Proses file secara asynchronous dengan `await annotator.SaveAsync(...)`.  

### Masalah 4: Kesalahan terkait Lisensi
**Jawaban langsung:** Letakkan file `.lic` di folder yang dapat dibaca aplikasi, dan panggil `License license = new License(); license.SetLicense("path/to/license.lic");` sebelum panggilan GroupDocs lainnya. Verifikasi versi lisensi cocok dengan versi pustaka yang Anda gunakan.

**Perbaikan umum:**  
- Periksa bahwa file lisensi tidak rusak (bandingkan ukuran file).  
- Pastikan Anda tidak mencampur lisensi percobaan dengan lisensi komersial dalam lingkungan yang sama.  

## Tips Lanjutan dan Praktik Terbaik
### Manajemen Warna
Warna yang konsisten meningkatkan keterbacaan bagi reviewer. Definisikan palet (mis., Kuning untuk sorotan, Merah untuk masalah kritis) dan simpan dalam kelas helper statis. Ingatlah untuk menggunakan warna kontras tinggi untuk aksesibilitas dan tambahkan halaman legenda dalam PDF sebagai referensi.

### Pola Penanganan Kesalahan
Bungkus semua panggilan anotasi dalam blok try‑catch yang secara khusus menangkap `GroupDocs.Annotation.Exceptions.AnnotationException`. Catat pesan pengecualian, jejak stack, dan nama PDF untuk membantu debugging.

### Strategi Pengujian
- **Unit Tests:** Gunakan PDF kecil dengan dimensi yang diketahui, tambahkan anotasi, dan pastikan `GetAnnotations()` mengembalikan koordinat yang diharapkan.  
- **Integration Tests:** Jalankan alur kerja penuh pada PDF dengan rentang 1 halaman hingga 200 halaman, dan verifikasi bahwa waktu pemrosesan tetap di bawah 5 detik untuk file di bawah 50 MB.  
- **Load Tests:** Simulasikan 50 permintaan anotasi bersamaan menggunakan alat seperti k6 atau Apache JMeter dan pantau CPU/memori.  

## Pertanyaan yang Sering Diajukan
**T: Bagaimana cara menangani PDF dengan ukuran halaman yang berbeda?**  
J: GroupDocs secara otomatis membaca dimensi setiap halaman. Saat menempatkan anotasi, selalu query `annotator.GetPageInfo(pageNumber)` dan hitung koordinat berdasarkan lebar dan tinggi halaman tersebut.

**T: Bisakah saya memberi anotasi pada PDF yang dilindungi kata sandi?**  
J: Ya. Gunakan konstruktor `LoadOptions` yang menerima string kata sandi, mis., `new LoadOptions { Password = "secret" }`, dan berikan ke konstruktor `Annotator`.

**T: Berapa jumlah maksimum anotasi yang dapat saya tambahkan ke satu PDF?**  
J: Tidak ada batas keras, tetapi kinerja menurun setelah beberapa ribu anotasi. Untuk set anotasi yang sangat besar, kelompokkan menjadi bagian logis dan proses setiap bagian secara terpisah.

**T: Bagaimana cara menghapus anotasi tertentu secara programatis?**  
J: Dapatkan `Id` anotasi melalui `GetAnnotations()`, lalu panggil `Delete(id)` atau buat instance `SaveOptions` yang mengecualikan `AnnotationType` yang tidak diinginkan.

**T: Bisakah saya menyesuaikan tampilan anotasi selain warna?**  
J: Tentu. Anda dapat mengatur opacity, ketebalan border, gaya dash, dan bahkan menyematkan ikon SVG khusus untuk anotasi stempel.

**T: Apa yang terjadi jika saya mencoba memberi anotasi pada PDF yang dipindai (berbasis gambar)?**  
J: Anotasi akan dirender sebagai objek overlay di atas gambar halaman. Mereka tidak mengubah data raster yang mendasarinya, sehingga PDF tetap dapat dicari jika lapisan OCR ada.

**T: Bagaimana cara menangani PDF yang sangat besar tanpa kehabisan memori?**  
J: Proses dokumen halaman‑per‑halaman menggunakan `LoadOptions.PageNumbers`, buang setiap instance `Annotator` segera setelah digunakan, dan aktifkan penyimpanan streaming ke `MemoryStream` untuk menghindari lonjakan disk.  

## Integrasi dengan Aplikasi ASP.NET
Ketika Anda mengekspos fungsionalitas anotasi melalui web API, ikuti pola berikut:

1. **Controller menerima aliran PDF** dari klien.  
2. **Validasi ukuran file** (tolak > 200 MB kecuali Anda memiliki penanganan khusus).  
3. **Instansiasi `Annotator` dalam blok `using`** untuk menjamin pembuangan.  
4. **Terapkan anotasi** berdasarkan payload JSON yang mendeskripsikan tipe anotasi, koordinat, dan teks.  
5. **Simpan ke lokasi sementara**, lalu streaming hasil kembali ke klien dengan header `Content‑Disposition` yang sesuai.  

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Sumber Daya Tambahan
- [halaman pembelian GroupDocs](https://purchase.groupdocs.com/buy)  
- [Beli GroupDocs](https://purchase.groupdocs.com/buy)  
- [Dokumentasi GroupDocs Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Referensi API GroupDocs](https://reference.groupdocs.com/annotation/net/)  
- [Rilis Terbaru](https://releases.groupdocs.com/annotation/net/)  
- [Coba GroupDocs Gratis](https://releases.groupdocs.com/annotation/net/)  
- [Minta Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)  
- [Forum GroupDocs](https://forum.groupdocs.com/c/annotation/)  

## Kesimpulan dan Langkah Selanjutnya
Anda kini memiliki **peta jalan lengkap, siap produksi** untuk membangun **sistem review dokumen** yang didukung oleh GroupDocs.Annotation untuk .NET. Anda telah mempelajari cara menyiapkan pustaka, menambahkan anotasi area, elips, dan teks, memfilter penyimpanan, serta menjaga penggunaan memori rendah bahkan dengan PDF besar.

1. **Bereksperimen** dengan tipe anotasi tambahan seperti `ArrowAnnotation` dan `StampAnnotation`.  
2. **Integrasikan** alur kerja ke dalam API ASP.NET Core atau aplikasi desktop WPF Anda yang sudah ada.  
3. **Jelajahi** referensi API lengkap untuk menemukan fitur lanjutan seperti versioning anotasi dan metadata khusus.  
4. **Bergabung** dengan forum komunitas GroupDocs untuk dukungan sesama dan tetap terbarui tentang rilis baru.  

---

**Terakhir Diperbarui:** 2026-05-26  
**Diuji Dengan:** GroupDocs.Annotation 23.11 untuk .NET  
**Penulis:** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```
```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```
```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```
```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```
```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```
```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```
```csharp
annotator.Save(outputPath, saveOptions);
```
```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```
```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```
```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```
```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```
```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```
```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```
```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Tutorial Terkait
- [Tutorial GroupDocs Annotation .NET - Panduan Lengkap untuk Manajemen Dokumen](/annotation/net/annotation-management/)  
- [Tutorial Pratinjau Dokumen .NET - Panduan Lengkap GroupDocs.Annotation](/annotation/net/document-preview/)  
- [Tutorial Lisensi Metered GroupDocs Annotation - Panduan Lengkap Penyiapan .NET](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)