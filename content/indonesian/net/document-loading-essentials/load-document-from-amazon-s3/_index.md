---
categories:
- Document Management
date: '2026-07-06'
description: Pelajari cara mengkonfigurasi kredensial AWS dan mengintegrasikan GroupDocs
  Annotation dengan Amazon S3 menggunakan C#. Panduan langkah demi langkah untuk memuat,
  memberi anotasi, dan mengelola dokumen.
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: Muat Dokumen dari Amazon S3
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: Konfigurasi Kredensial AWS untuk Integrasi GroupDocs Annotation S3
type: docs
url: /id/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# Konfigurasikan Kredensial AWS untuk Integrasi GroupDocs Annotation S3

Dalam tutorial ini Anda akan belajar cara **mengonfigurasi kredensial AWS** dan mengintegrasikan GroupDocs.Annotation dengan Amazon S3 secara mulus menggunakan C#. Kami akan memandu Anda memuat dokumen dari bucket S3, menambahkan anotasi, dan menyimpan hasilnya kembali ke cloud, sambil membahas praktik keamanan dan kinerja terbaik.

## Jawaban Cepat
- **Bagaimana cara mengonfigurasi kredensial AWS?** Gunakan konstruktor `AmazonS3Client` dengan `BasicAWSCredentials` atau mengandalkan peran IAM untuk resolusi kredensial otomatis.  
- **Paket NuGet mana yang diperlukan?** `GroupDocs.Annotation` dan `AWSSDK.S3`.  
- **Apakah saya dapat memberi anotasi pada PDF yang lebih besar dari 100 MB?** Ya – gunakan streaming dan API async untuk menghindari memuat seluruh file ke memori.  
- **Apakah integrasi ini thread‑safe?** Buat instance `Annotator` terpisah per permintaan; SDK sendiri bersifat stateless.  
- **Apakah saya perlu mengenkripsi dokumen di S3?** Aktifkan enkripsi sisi server (SSE‑S3 atau SSE‑KMS) untuk kepatuhan dan perlindungan data.

## Mengapa Menggunakan S3 untuk Anotasi Dokumen?

Menggunakan S3 untuk anotasi dokumen memberi Anda solusi penyimpanan yang sangat skalabel, efisien biaya, dan dapat diakses secara global sambil menjaga keamanan file Anda.  
- **Skalabilitas**: S3 menangani hampir tak terbatas objek, mendukung hingga 5 TB per file dan jutaan permintaan per detik.  
- **Efisiensi Biaya**: Anda hanya membayar penyimpanan yang sebenarnya Anda gunakan, dengan tier otomatis ke kelas biaya lebih rendah.  
- **Akses Global**: Akses latensi rendah dari wilayah AWS mana pun memastikan dokumen beranotasi Anda selalu dapat dijangkau.  
- **Keamanan**: Enkripsi bawaan (SSE‑S3, SSE‑KMS) dan kebijakan IAM yang detail melindungi data sensitif.  
- **Integrasi**: Bekerja secara native dengan layanan AWS yang ada seperti CloudFront, Lambda, dan IAM.

## Prasyarat

1. **Lingkungan Pengembangan C#** – Visual Studio atau VS Code dengan dukungan .NET.  
2. **GroupDocs.Annotation untuk .NET** – Unduh dari [situs resmi](https://releases.groupdocs.com/annotation/net/).  
3. **Akses AWS S3** – Kredensial AWS yang valid dengan izin baca/tulis pada bucket target.  
4. **Pengetahuan Dasar C#** – Memahami kelas, async/await, dan stream.  
5. **Amazon S3 SDK** – Instal melalui NuGet (`AWSSDK.S3`).  

## Cara mengonfigurasi kredensial AWS untuk akses S3?

`BasicAWSCredentials` adalah kelas yang menyimpan ID kunci akses AWS dan kunci rahasia.  
`AmazonS3Client` adalah klien SDK AWS yang digunakan untuk berinteraksi dengan layanan S3.

Muat kunci AWS Anda sekali dan biarkan SDK menggunakan kembali untuk setiap permintaan. Cara paling sederhana adalah membuat objek `BasicAWSCredentials` dan melewatkannya ke konstruktor `AmazonS3Client`. Untuk beban kerja produksi, lebih baik menggunakan peran IAM atau variabel lingkungan untuk menghindari hard‑coding rahasia.

**Tip Pro:** Saat menjalankan di EC2, ECS, atau Lambda, hilangkan kredensial eksplisit dan biarkan SDK secara otomatis mengambil kredensial sementara dari profil instance.

## Impor Namespace

Mari mulai dengan mengimpor semua namespace yang diperlukan untuk integrasi S3 kami:

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

Impor ini memberi kami akses ke operasi AWS S3 dan fungsionalitas anotasi GroupDocs. Namespace `Amazon.S3` menangani interaksi penyimpanan cloud kami, sementara `GroupDocs.Annotation.Models` menyediakan kerangka kerja anotasi.

## Implementasi Langkah‑demi‑Langkah

Sekarang mari kita jalani proses lengkap memuat dokumen dari S3 dan menambahkan anotasi. Kami akan membagi ini menjadi langkah‑langkah yang dapat Anda ikuti.

### Langkah 1: Tentukan Jalur Output

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

Ini membuat jalur lokal tempat dokumen beranotasi Anda akan disimpan. Metode `Path.Combine` memastikan kompatibilitas lintas platform, dan kami mempertahankan ekstensi file asli untuk menjaga integritas tipe dokumen.

**Tip Pro**: Pertimbangkan menggunakan timestamp dalam nama file output Anda untuk menghindari menimpa anotasi sebelumnya: `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`.

### Langkah 2: Tentukan Kunci Dokumen

```csharp
string key = "sample.pdf";
```

Ini adalah pengidentifikasi unik dokumen Anda di bucket S3. Dalam skenario dunia nyata, Anda biasanya akan mendapatkan ini dari input pengguna, catatan basis data, atau parameter API. Pastikan kunci persis cocok dengan nama objek S3, termasuk prefiks folder apa pun (misalnya, `documents/2025/sample.pdf`).

### Langkah 3: Inisialisasi Annotator

`Annotator` adalah kelas inti di GroupDocs.Annotation yang mewakili sesi dokumen yang dapat diedit. Ia menyediakan metode untuk menambah, memodifikasi, dan menghapus anotasi.

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

Dengan membungkus stream unduhan S3 dalam blok `using`, kami memastikan pembuangan yang tepat baik untuk stream maupun instance annotator.

### Langkah 4: Buat Anotasi Area

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

Ini membuat anotasi persegi panjang pada dokumen Anda. Parameter `Rectangle(100, 100, 100, 100)` masing‑masing mewakili posisi X, posisi Y, lebar, dan tinggi. Nilai `BackgroundColor` `65535` menghasilkan sorotan kuning – Anda dapat menyesuaikannya menggunakan kode warna RGB standar.

**Kasus Penggunaan Umum untuk Anotasi Area**:
- Menyoroti bagian penting dalam kontrak  
- Menandai zona tinjauan dalam spesifikasi teknis  
- Menambahkan penjelasan visual pada slide presentasi  

### Langkah 5: Tambahkan Anotasi ke Dokumen

```csharp
annotator.Add(area);
```

Metode ini menambahkan anotasi area kami ke dokumen. Anda dapat memanggil `Add()` berkali‑kali untuk menyertakan tipe anotasi berbeda seperti komentar teks, panah, atau stempel. Anotasi berada di memori hingga Anda secara eksplisit menyimpan dokumen.

### Langkah 6: Simpan Dokumen Beranotasi

```csharp
annotator.Save(outputPath);
```

Sekarang kami menyimpan dokumen beranotasi ke jalur output yang telah ditentukan. Ini membuat file baru dengan semua anotasi tersemat. Jika Anda perlu menyimpan hasil kembali ke S3—skenario produksi umum—cukup unggah file menggunakan SDK S3 setelah langkah ini.

### Langkah 7: Tampilkan Pesan Sukses

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Pesan konfirmasi sederhana yang membantu debugging dan memberikan umpan balik kepada pengguna. Dalam aplikasi nyata Anda akan menggantinya dengan logging yang tepat atau notifikasi UI.

## Menerapkan Metode Unduh S3

Anda akan melihat kami merujuk ke metode `DownloadFile(key)` yang belum kami implementasikan. Berikut cara membuat helper penting ini:

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**Catatan Keamanan**: Jangan pernah menuliskan kredensial AWS secara keras dalam kode produksi. Gunakan peran IAM, variabel lingkungan, atau file kredensial bersama untuk menjaga rahasia tetap di luar kontrol sumber.

## Cara memuat dokumen dari Amazon S3?

`GetObjectAsync` adalah metode asinkron yang mengambil objek dari S3 dan mengembalikan respons berisi stream.  
`MemoryStream` adalah stream .NET yang menyimpan data di memori, memungkinkan baca/tulis cepat tanpa I/O disk.  
`Annotator` (seperti yang didefinisikan sebelumnya) adalah kelas yang memuat dokumen untuk anotasi.

Muat PDF langsung dari S3 menggunakan metode `GetObjectAsync`, bungkus stream respons dalam `MemoryStream`, dan berikan ke konstruktor `Annotator`. Pendekatan ini menghindari penulisan file asli ke disk, mengurangi overhead I/O, dan memungkinkan Anda bekerja dengan file besar secara efisien sambil menjaga penggunaan memori tetap terkendali.

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## Masalah Integrasi Umum & Solusinya

Berdasarkan pengalaman implementasi dunia nyata, berikut masalah paling sering yang akan Anda temui dan cara mengatasinya:

### Masalah 1: Kesalahan "Access Denied"

**Masalah**: Aplikasi Anda tidak dapat mengakses objek S3.  
**Solusi**: Pastikan pengguna IAM atau peran Anda memiliki izin `s3:GetObject` untuk bucket dan objek tertentu.

### Masalah 2: Timeout File Besar

**Masalah**: Dokumen lebih dari 50 MB menyebabkan kesalahan timeout.  
**Solusi**: Terapkan operasi async dan tingkatkan nilai timeout:

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### Masalah 3: Masalah Memori dengan Banyak Dokumen

**Masalah**: Memproses banyak dokumen menyebabkan pengecualian out‑of‑memory.  
**Solusi**: Segera dispose stream dan proses dokumen dalam batch.

### Masalah 4: Kesalahan Ketidaksesuaian Region

**Masalah**: Klien S3 tidak dapat menemukan bucket Anda.  
**Solusi**: Pastikan `RegionEndpoint` cocok dengan region sebenarnya dari bucket.

## Praktik Terbaik Kinerja & Keamanan

### Optimasi Kinerja
- **Gunakan Metode Async**: Pilih `GetObjectAsync()` daripada panggilan sinkron.  
- **Implementasikan Caching**: Simpan dokumen yang sering diakses secara lokal untuk periode singkat.  
- **Operasi Batch**: Proses beberapa file secara paralel bila sesuai.  
- **Pemrosesan Stream**: Hindari memuat seluruh dokumen besar ke memori; kerja dengan stream.

### Pertimbangan Keamanan
- **Gunakan Peran IAM**: Hilangkan kredensial yang dikodekan secara keras.  
- **Aktifkan Enkripsi S3**: Aktifkan enkripsi sisi server (SSE‑S3 atau SSE‑KMS).  
- **Implementasikan Logging Akses**: Lacak siapa yang mengakses dokumen mana.  
- **Validasi Tipe File**: Periksa ekstensi dan tipe MIME sebelum memproses.

## Kasus Penggunaan Dunia Nyata

Pola integrasi S3 ini bersinar di banyak industri:
1. **Peninjauan Dokumen Hukum** – Firma hukum memberi anotasi pada kontrak yang disimpan di S3.  
2. **Platform Pendidikan** – Guru menandai pengiriman siswa yang dihosting di cloud.  
3. **Manajemen Konstruksi** – Arsitek memberi anotasi pada cetak biru di berbagai region.  
4. **Rekam Medis** – Penyedia layanan kesehatan menambahkan catatan pada dokumen pasien secara aman.  
5. **Layanan Keuangan** – Auditor berkolaborasi pada dokumen kepatuhan yang disimpan di S3.

## Panduan Pemecahan Masalah

**Tidak Dapat Memuat Dokumen dari S3**  
- Verifikasi kredensial AWS dan izin bucket.  
- Periksa kembali ejaan nama bucket dan kunci objek.  
- Pastikan dokumen tidak rusak di S3.

**Anotasi Tidak Muncul**  
- Pastikan Anda memanggil `annotator.Save()` setelah menambahkan anotasi.  
- Periksa bahwa format dokumen mendukung tipe anotasi yang Anda gunakan.  
- Pastikan koordinat anotasi berada dalam batas halaman.

**Masalah Kinerja**  
- Pantau tingkat permintaan S3 dan terapkan exponential back‑off.  
- Gunakan CDN CloudFront untuk file yang sering diakses.  
- Pertimbangkan S3 Transfer Acceleration untuk aplikasi global.

## Pertanyaan yang Sering Diajukan

**Q: Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?**  
A: GroupDocs.Annotation mendukung lebih dari 50 format input dan output—termasuk PDF, DOCX, PPTX, dan HTML—meskipun tipe anotasi dapat bervariasi per format.

**Q: Bisakah saya mencoba GroupDocs.Annotation untuk .NET sebelum membeli?**  
A: Ya, Anda dapat menjelajahi fitur GroupDocs.Annotation untuk .NET dengan mengakses versi percobaan gratis yang tersedia [di sini](https://releases.groupdocs.com/). Ini memungkinkan Anda menguji integrasi S3 dan kemampuan anotasi tanpa risiko.

**Q: Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Annotation untuk .NET?**  
A: Dokumentasi lengkap untuk GroupDocs.Annotation untuk .NET tersedia [di sini](https://tutorials.groupdocs.com/annotation/net/). Dokumen tersebut mencakup referensi API, contoh lanjutan, dan panduan integrasi.

**Q: Apakah saya memerlukan lisensi sementara untuk mengevaluasi GroupDocs.Annotation untuk .NET?**  
A: Anda dapat memperoleh lisensi sementara untuk tujuan evaluasi dari [di sini](https://purchase.groupdocs.com/temporary-license/). Ini menghapus batasan percobaan dan memberi Anda akses penuh untuk menguji skenario produksi.

**Q: Di mana saya dapat mencari bantuan atau dukungan untuk GroupDocs.Annotation untuk .NET?**  
A: Untuk pertanyaan atau masalah terkait dukungan, Anda dapat mengunjungi forum GroupDocs.Annotation [di sini](https://forum.groupdocs.com/c/annotation/10). Komunitas dan tim dukungan aktif membantu memecahkan masalah integrasi.

**Q: Bisakah saya menyimpan dokumen beranotasi kembali ke S3 alih-alih penyimpanan lokal?**  
A: Tentu saja! Setelah memanggil `annotator.Save(localPath)`, Anda dapat mengunggah file beranotasi kembali ke S3 menggunakan metode `PutObjectAsync()`. Ini menciptakan alur kerja cloud‑to‑cloud lengkap yang ideal untuk aplikasi web.

**Q: Berapa ukuran file maksimum yang didukung untuk anotasi dokumen S3?**  
A: Meskipun GroupDocs.Annotation dapat menangani file besar, batas praktis tergantung pada memori server dan timeout transfer S3. Untuk file lebih dari 100 MB, terapkan streaming atau pemrosesan berbasis chunk untuk menghindari kehabisan memori.

---

**Terakhir Diperbarui:** 2026-07-06  
**Diuji dengan:** GroupDocs.Annotation 23.12 untuk .NET  
**Penulis:** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## Tutorial Terkait

- [GroupDocs.Annotation .NET Memuat Dokumen](/annotation/net/document-loading-essentials/)
- [Cara Memuat Dokumen dari FTP .NET - Panduan Lengkap GroupDocs](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [Tutorial Pratinjau Dokumen .NET - Panduan Lengkap GroupDocs.Annotation](/annotation/net/document-preview/)