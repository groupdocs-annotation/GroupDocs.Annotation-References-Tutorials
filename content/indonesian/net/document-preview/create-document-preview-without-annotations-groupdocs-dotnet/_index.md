---
categories:
- Document Processing
date: '2026-10-05'
description: Pelajari cara menyembunyikan anotasi saat menghasilkan pratinjau dokumen
  bersih di C# menggunakan GroupDocs.Annotation .NET. Panduan langkah demi langkah
  dengan contoh kode, tips kinerja, dan pemecahan masalah.
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: Pratinjau Dokumen Tanpa Anotasi
og_description: Pelajari cara menyembunyikan anotasi saat menghasilkan pratinjau dokumen
  bersih di C#. Panduan ini mencakup pengaturan, kode, tips kinerja, dan pemecahan
  masalah.
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: Cara menyembunyikan anotasi saat menghasilkan pratinjau dokumen di C#
schemas:
- author: GroupDocs
  dateModified: '2026-10-05'
  description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  headline: How to hide annotations when generating document preview in C#
  type: TechArticle
- description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  name: How to hide annotations when generating document preview in C#
  steps:
  - name: initialize your annotator (the foundation)
    text: The `Annotator` class loads a document and provides methods for rendering
      and annotation manipulation. csharp using (Annotator annotator = new Annotator("path/to/your/document"))
      { // All your preview generation happens within this scope }
  - name: configure your preview options (this is where the magic happens)
    text: The `PreviewOptions` class defines rendering parameters such as format,
      resolution, and whether annotations are included. csharp // Define how each
      page should be handled during preview generation PreviewOptions previewOptions
      = new PreviewOptions(pageNumber => { var pagePath = $"output_directory\\r
  - name: generate the preview (the payoff)
    text: The `GeneratePreview` method processes the document according to the supplied
      options and returns file paths for the created images. csharp annotator.Document.GeneratePreview(previewOptions);
  type: HowTo
- questions:
  - answer: Absolutely! GroupDocs.Annotation supports over 50 formats—including PDF,
      PPTX, XLSX, and common image types. See the [documentation](https://docs.groupdocs.com/annotation/net/)
      for the full list.
    question: Can I preview documents other than DOCX files?
  - answer: Initialise the `Annotator` with a `LoadOptions` object that includes the
      password. The `LoadOptions` class lets you specify the document password and
      other loading parameters.
    question: How do I handle password‑protected documents?
  - answer: Yes. The same code works in ASP.NET, but store generated images in a temporary
      folder and clean them up after the response to avoid disk bloat.
    question: Can I generate previews in a web application?
  - answer: PNG offers the highest quality, JPEG loads faster, and WebP provides the
      best compression if your target browsers support it. PNG is the safest default.
    question: What’s the best output format for web display?
  - answer: Process pages in batches of 5‑10, monitor memory usage, and optionally
      show a progress bar to improve the user experience.
    question: How do I handle very large documents efficiently?
  type: FAQPage
tags:
- groupdocs
- document-preview
- annotations
- dotnet
- csharp
title: Cara menyembunyikan anotasi saat menghasilkan pratinjau dokumen di C#
type: docs
url: /id/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# Cara menyembunyikan anotasi saat menghasilkan pratinjau dokumen di C#

Jika Anda perlu membagikan pratinjau dokumen tetapi ingin **menyembunyikan anotasi**, Anda berada di tempat yang tepat. Tutorial ini menunjukkan cara menghasilkan pratinjau bersih tanpa anotasi di C# dengan GroupDocs.Annotation untuk .NET, mencakup semua hal mulai dari instalasi hingga optimalisasi kinerja.

## Jawaban Cepat
- **Kelas utama apa yang membuat pratinjau?** The `Annotator` class.
- **Opsi mana yang menonaktifkan anotasi?** Set `RenderAnnotations = false` in `PreviewOptions`.
- **Versi .NET minimum?** .NET 6 is recommended; .NET Core 3.1 also works.
- **Apakah saya dapat meninjau PDF dan file Word?** Yes – over 50 formats are supported.
- **Apakah saya memerlukan lisensi untuk pengujian?** A temporary license is available for free trials.

## Apa itu cara menyembunyikan anotasi?
*Cara menyembunyikan anotasi* adalah proses menghasilkan gambar pratinjau dokumen sambil menekan setiap komentar, sorotan, atau markup yang ada dalam file sumber. Teknik ini memastikan output visual hanya berisi konten asli, sehingga cocok untuk distribusi publik, presentasi klien, atau skenario apa pun di mana catatan internal harus tetap tersembunyi.

## Mengapa Anda membutuhkan pratinjau dokumen bersih (dan cara mendapatkannya)
Saat Anda membagikan pratinjau kepada klien, mitra, atau publik, komentar internal dapat terlihat tidak profesional atau bahkan mengungkap strategi rahasia. Pratinjau bersih menjaga fokus pada konten dan melindungi alur kerja Anda. GroupDocs.Annotation memungkinkan Anda mengaktifkan atau menonaktifkan rendering anotasi, sehingga Anda dapat menghasilkan versi beranotasi maupun bersih dari file sumber yang sama.

## Apa yang Anda perlukan sebelum memulai

### Apa saja prasyaratnya?
Untuk memulai, Anda memerlukan komponen berikut terpasang di mesin pengembangan Anda. Menyiapkan item-item ini memastikan kode berjalan tanpa kesalahan runtime dan Anda dapat menguji seluruh alur pratinjau secara lokal.

- GroupDocs.Annotation untuk .NET 25.4.0 atau lebih baru (rilis terbaru menambahkan pembuatan pratinjau yang dioptimalkan memori).
- Visual Studio 2022 atau IDE apa pun yang kompatibel dengan .NET.
- Lisensi GroupDocs yang valid (lisensi sementara gratis untuk evaluasi).

## Penyiapan Cepat: Menambahkan GroupDocs.Annotation ke proyek Anda

### Opsi 1: Konsol Pengelola Paket NuGet
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Opsi 2: .NET CLI (preferensi pribadi saya)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Tip pro:** Jaga versi paket tetap konsisten di semua anggota tim untuk menghindari perbedaan rendering yang halus.

Verifikasi instalasi dengan pemeriksaan singkat:

```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## Bagaimana cara menghasilkan pratinjau tanpa anotasi?
Muat dokumen dengan `Annotator`, konfigurasikan `PreviewOptions`, dan panggil `GeneratePreview`. Menetapkan `RenderAnnotations = false` memberi tahu mesin untuk menghilangkan setiap komentar, sorotan, dan stempel dari gambar output.

### Langkah 1: inisialisasi annotator Anda (dasar)
The `Annotator` class loads a document and provides methods for rendering and annotation manipulation.  
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### Langkah 2: konfigurasikan opsi pratinjau Anda (di sinilah keajaiban terjadi)
The `PreviewOptions` class defines rendering parameters such as format, resolution, and whether annotations are included.  
```csharp
```csharp
// Define how each page should be handled during preview generation
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = $"output_directory\\result{pageNumber}.png";
    return File.Create(pagePath);
});

// Set the output format for the preview as PNG
previewOptions.PreviewFormat = PreviewFormats.PNG;

// Specify which pages to include in the preview generation
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};

// The key setting: disable rendering of annotations
previewOptions.RenderAnnotations = false;
```
```

### Langkah 3: hasilkan pratinjau (hasilnya)
The `GeneratePreview` method processes the document according to the supplied options and returns file paths for the created images.  
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## Masalah Umum (dan cara memperbaikinya)

### Masalah 1: kesalahan “File not found”
**Gejala:** Sebuah pengecualian dilemparkan saat `Annotator` dibuat.  
**Solusi:** Gunakan jalur absolut atau verifikasi bahwa jalur relatif Anda benar. Pemeriksaan singkat terlihat seperti ini:

```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### Masalah 2: Kualitas pratinjau buruk
**Gejala:** Gambar output tampak buram atau berpixel.  
**Solusi:** Tingkatkan pengaturan DPI di `PreviewOptions` untuk meningkatkan kejelasan:

```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### Masalah 3: Masalah memori dengan dokumen besar
**Gejala:** `OutOfMemoryException` atau pemrosesan yang jelas lambat.  
**Solusi:** Proses halaman dalam batch alih-alih memuat seluruh file sekaligus:

```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## Kasus penggunaan dunia nyata (di mana ini benar-benar penting)

### Berbagi dokumen hukum
Firma hukum dapat mendistribusikan pratinjau kontrak yang menyembunyikan catatan negosiasi internal, menjaga komunikasi dengan klien tetap profesional.

### Penerbitan akademik
Peneliti dapat membagikan draf manuskrip bersih setelah satu putaran tinjauan sejawat, menghapus komentar reviewer sebelum pengajuan ke jurnal.

### Pelaporan bisnis
Pemangku kepentingan menerima laporan yang dipoles tanpa catatan “verifikasi angka ini” atau “perbarui sebelum rapat dewan”, yang sebaliknya dapat merusak kepercayaan.

### Pengarsipan dokumen
Tim kepatuhan menyimpan salinan tanpa anotasi untuk memenuhi standar regulasi sambil mempertahankan versi beranotasi asli untuk referensi internal.

## Praktik Terbaik Kinerja

### Bagaimana sebaiknya Anda mengelola memori untuk file besar?
Proses halaman dalam batch kecil dan segera dispose `Annotator`. Pendekatan ini mengurangi penggunaan memori puncak hingga 60 % pada dokumen yang lebih besar dari 200 halaman.

```csharp
// Good: Dispose properly
using (Annotator annotator = new Annotator(documentPath))
{
    // Generate preview
} // Automatically disposed here

// Avoid: Manual disposal (easy to forget)
Annotator annotator = new Annotator(documentPath);
// ... use annotator
annotator.Dispose(); // Easy to forget or skip due to exceptions
```

### Bagaimana Anda dapat mempercepat pemrosesan batch?
Bagi dokumen 100‑halaman menjadi grup berisi 10 halaman, hasilkan tiap grup secara berurutan, dan tulis hasilnya ke folder sementara. Teknik ini memotong total waktu pemrosesan sekitar 30 % pada perangkat keras server tipikal.

```csharp
// Process in batches of 10 pages
for (int startPage = 1; startPage <= totalPages; startPage += 10)
{
    int endPage = Math.Min(startPage + 9, totalPages);
    var pageRange = Enumerable.Range(startPage, endPage - startPage + 1).ToArray();
    
    previewOptions.PageNumbers = pageRange;
    annotator.Document.GeneratePreview(previewOptions);
}
```

### Bagaimana Anda memilih format output yang optimal?
- **PNG:** Kualitas visual terbaik; ideal untuk skema detail.  
- **JPEG:** Ukuran file lebih kecil; cocok untuk dokumen dengan banyak teks di mana artefak kompresi ringan dapat diterima.  
- **WebP:** Format modern dengan kompresi luar biasa; periksa dukungan browser sebelum mengadopsi.

## Opsi Konfigurasi Lanjutan

### Bagaimana Anda dapat menyesuaikan penamaan file?
Lambda `PreviewOptions` memungkinkan Anda menyisipkan nomor halaman, cap waktu, atau pengidentifikasi khusus ke dalam setiap nama file.

```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### Bagaimana Anda mengontrol kualitas gambar?
Sesuaikan properti `Width`, `Height`, dan `Resolution` di `PreviewOptions`. Dimensi yang lebih besar menghasilkan kualitas lebih tinggi dengan biaya ukuran file yang lebih besar.

```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### Bagaimana Anda dapat memproses hanya halaman tertentu?
Setel koleksi `PageNumbers` ke halaman yang tepat yang Anda butuhkan, yang mengurangi I/O dan mempercepat pembuatan untuk dokumen ratusan halaman.

```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## Panduan Pemecahan Masalah

### Mengapa pembuatan pratinjau gagal tanpa pesan?
Penyebab umum meliputi:
1. Direktori output tidak ada atau tidak memiliki izin menulis.  
2. Dokumen sumber yang dilindungi kata sandi.  
3. Format file tidak didukung.  
4. Memori sistem tidak cukup.

### Mengapa anotasi masih muncul?
Pastikan `RenderAnnotations = false` sudah diatur pada instance `PreviewOptions` sebelum memanggil `GeneratePreview`. Properti `RenderAnnotations` mengontrol apakah lapisan anotasi digambar selama rendering pratinjau.

```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### Mengapa kinerja lambat?
- Kurangi resolusi saat pengujian.  
- Proses lebih sedikit halaman per batch.  
- Verifikasi bahwa Anda menggunakan versi GroupDocs.Annotation terbaru (25.4.0 atau lebih baru) yang mencakup perbaikan kinerja.

## Kapan TIDAK menggunakan pendekatan ini
- **Pratinjau waktu nyata:** Untuk pratinjau instan, rendering sisi klien mungkin lebih cepat.  
- **Dokumen interaktif:** Formulir atau skrip tersemat dapat kehilangan fungsionalitas saat dirender sebagai gambar statis.  
- **Grafik skalabel:** Jika Anda membutuhkan output berbasis vektor (mis., SVG), pertimbangkan menghasilkan halaman PDF alih-alih gambar raster.

## Kesimpulan
Menghasilkan pratinjau dokumen bersih tanpa anotasi sangat mudah dengan GroupDocs.Annotation untuk .NET. Ingatlah untuk:

1. Dispose `Annotator` dengan benar.  
2. Set `RenderAnnotations = false` di `PreviewOptions`.  
3. Proses file besar secara batch untuk menjaga penggunaan memori tetap rendah.  
4. Uji dengan dokumen dunia nyata untuk menyesuaikan DPI dan pilihan format.

Mulailah dengan file uji sederhana, bereksperimen dengan opsi di atas, dan Anda akan memiliki pratinjau tingkat profesional tanpa anotasi yang siap untuk audiens mana pun.

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya meninjau dokumen selain file DOCX?**  
A: Tentu saja! GroupDocs.Annotation mendukung lebih dari 50 format—termasuk PDF, PPTX, XLSX, dan tipe gambar umum. Lihat [documentation](https://docs.groupdocs.com/annotation/net/) untuk daftar lengkap.

**Q: Bagaimana saya menangani dokumen yang dilindungi kata sandi?**  
A: Inisialisasi `Annotator` dengan objek `LoadOptions` yang mencakup kata sandi. Kelas `LoadOptions` memungkinkan Anda menentukan kata sandi dokumen dan parameter pemuatan lainnya.

```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: Bisakah saya menghasilkan pratinjau dalam aplikasi web?**  
A: Ya. Kode yang sama berfungsi di ASP.NET, tetapi simpan gambar yang dihasilkan di folder sementara dan bersihkan setelah respons untuk menghindari penumpukan disk.

**Q: Apa format output terbaik untuk tampilan web?**  
A: PNG menawarkan kualitas tertinggi, JPEG lebih cepat dimuat, dan WebP memberikan kompresi terbaik jika browser target Anda mendukungnya. PNG adalah pilihan default yang paling aman.

**Q: Bagaimana saya menangani dokumen sangat besar secara efisien?**  
A: Proses halaman dalam batch 5‑10, pantau penggunaan memori, dan opsional tampilkan bilah kemajuan untuk meningkatkan pengalaman pengguna.

**Q: Bisakah saya menyesuaikan kualitas gambar output?**  
A: Ya—sesuaikan `Width`, `Height`, dan `Resolution` di `PreviewOptions`. Nilai yang lebih besar meningkatkan kualitas tetapi juga ukuran file.

**Q: Bagaimana jika saya membutuhkan versi beranotasi dan bersih?**  
A: Jalankan pratinjau dua kali—sekali dengan `RenderAnnotations = true` dan sekali dengan `false`. Simpan masing‑masing set di direktori terpisah untuk memudahkan pengambilan.

## Sumber Daya
- [Dokumentasi GroupDocs.Annotation .NET](https://docs.groupdocs.com/annotation/net/)  
- [Referensi API GroupDocs Annotation](https://reference.groupdocs.com/annotation/net/)  
- [Rilis GroupDocs untuk .NET](https://releases.groupdocs.com/annotation/net/)  
- [Beli Lisensi GroupDocs](https://purchase.groupdocs.com/buy)  
- [Uji Coba Gratis GroupDocs](https://releases.groupdocs.com/annotation/net/)  
- [Minta Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)  
- [Forum GroupDocs](https://forum.groupdocs.com/c/annotation/)  

**Terakhir Diperbarui:** 2026-10-05  
**Diuji Dengan:** GroupDocs.Annotation 25.4.0 for .NET  
**Penulis:** GroupDocs

## Tutorial Terkait
- [Cara Menghapus Anotasi PDF C# – Panduan GroupDocs.Annotation](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [Hasilkan Pratinjau Dokumen Tanpa Komentar di .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [Muat Font Kustom .NET - Panduan Integrasi GroupDocs.Annotation](/annotation/net/advanced-usage/loading-custom-fonts/)