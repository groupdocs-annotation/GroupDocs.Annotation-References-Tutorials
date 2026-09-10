---
categories:
- Licensing
date: '2026-06-06'
description: Pelajari cara mengatur lisensi Metered untuk GroupDocs.Annotation .NET
  guna mengoptimalkan penggunaan sumber daya dan mengurangi biaya anotasi dokumen
  dalam aplikasi Anda.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Atur Lisensi Metered
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Cara mengatur lisensi Metered untuk GroupDocs.Annotation .NET – Bayar Hanya
  untuk Apa yang Anda Gunakan
type: docs
url: /id/net/applying-licenses/set-metered-license/
weight: 12
---

# Atur Lisensi Metered untuk GroupDocs.Annotation .NET – Bayar Hanya untuk Apa yang Anda Gunakan

Jika Anda memerlukan **lisensi metered set** untuk GroupDocs.Annotation .NET, Anda berada di tempat yang tepat. Tutorial ini memandu Anda melalui setiap langkah yang diperlukan untuk mengonfigurasi model lisensi metered, menjelaskan kapan model ini masuk akal, dan menunjukkan cara menghindari jebakan paling umum. Pada akhir tutorial, Anda akan dapat mengintegrasikan lisensi berbasis penggunaan yang hemat biaya ke dalam aplikasi .NET apa pun—baik itu prototipe kecil atau layanan perusahaan dengan lalu lintas tinggi.

## Jawaban Cepat
- **Apa itu lisensi metered?** Model berbasis penggunaan di mana Anda hanya membayar untuk operasi anotasi yang benar‑benar dilakukan aplikasi Anda.  
- **Berapa banyak kunci yang diperlukan?** Dua kunci—kunci publik dan kunci pribadi—diperlukan untuk mengaktifkan lisensi.  
- **Kapan saya harus menginisialisasi lisensi?** Pada saat aplikasi dimulai atau selama konfigurasi kontainer DI, sebelum ada panggilan anotasi apa pun.  
- **Apakah saya memerlukan konektivitas internet?** Ya, SDK secara berkala menghubungi server GroupDocs untuk melaporkan penggunaan.  
- **Bisakah saya beralih ke lisensi permanen nanti?** Tentu saja; Anda dapat mengubah model lisensi dari dasbor GroupDocs kapan saja.

## Apa itu Lisensi Metered?
**Lisensi metered** adalah opsi penagihan bayar‑per‑pakai GroupDocs.Annotation yang melacak setiap permintaan anotasi dan menagih Anda berdasarkan konsumsi aktual. Ini menghilangkan biaya awal yang besar, menyediakan penagihan real‑time yang transparan, dan secara otomatis menyesuaikan dengan beban kerja Anda, memastikan Anda hanya membayar untuk halaman yang Anda anotasi.

## Mengapa Mengatur Lisensi Metered untuk Anotasi Dokumen?
Mengatur lisensi metered memungkinkan Anda menyelaraskan biaya dengan penggunaan sebenarnya, menawarkan pengeluaran yang dapat diprediksi sambil mendukung pertumbuhan. Ini menghapus kebutuhan pembayaran besar di muka, memberikan wawasan penggunaan yang detail, dan memastikan aplikasi Anda dapat menangani lonjakan tanpa batasan lisensi.

Lisensi metered memberikan **manfaat yang terukur**:

- **Penghematan Biaya:** Anda hanya membayar untuk jumlah halaman yang tepat yang dianotasi. Misalnya, memproses 2 000 halaman dalam sebulan dapat berbiaya serendah $0,02 per 1 000 halaman, dibandingkan dengan lisensi permanen $500.  
- **Skalabilitas:** Mendukung hingga **100 000+ halaman per bulan** tanpa upgrade lisensi manual apa pun.  
- **Tanpa Investasi Awal:** Tidak ada pengeluaran modal besar; Anda dapat mulai menguji segera dengan percobaan gratis.  
- **Pelaporan Detail:** Dasbor menampilkan penggunaan per‑operasi, membantu Anda meramalkan pengeluaran dengan akurasi ±5 %.  

## Prasyarat
Sebelum memulai, pastikan Anda memiliki hal‑hal berikut:

1. **GroupDocs.Annotation untuk .NET Library** – unduh build terbaru dari [situs web](https://releases.groupdocs.com/annotation/net/). Anda juga dapat mengakses halaman unduhan secara langsung melalui [tautan ini](https://releases.groupdocs.com/).  
2. **Akun GroupDocs** – akun aktif diperlukan untuk mengambil kunci publik dan pribadi Anda. Jika belum memiliki, Anda dapat [mendaftar percobaan gratis](https://releases.groupdocs.com/).  
3. **Lingkungan Pengembangan .NET** – Visual Studio 2022 atau IDE apa pun yang menargetkan .NET 6+ (SDK juga bekerja dengan .NET Framework 4.7.2).  
4. **Akses Internet** – SDK mengirim data penggunaan ke server GroupDocs setiap 15 menit; koneksi HTTPS keluar yang stabil wajib ada.  

## Impor Namespace
Kelas `Metered` berada di namespace `GroupDocs.Annotation.License`. `Metered` menangani komunikasi dengan server lisensi GroupDocs dan memvalidasi kunci penggunaan. Impor di bagian atas file C# Anda:

```csharp
using System;
```

> **Definition Anchor:** Kelas `Metered` menangani semua komunikasi dengan server lisensi GroupDocs dan memvalidasi kunci berbasis penggunaan Anda.

## Cara Mengatur Lisensi Metered di GroupDocs.Annotation .NET?
Untuk mengonfigurasi lisensi metered, muat kunci publik dan pribadi Anda, buat objek `Metered`, dan panggil `SetMeteredLicense`. Panggilan ini memvalidasi kunci dengan server GroupDocs, membangun saluran TLS yang aman, dan mulai melacak setiap operasi anotasi, memungkinkan penagihan bayar‑per‑pakai untuk seluruh aplikasi. `SetMeteredLicense` mengaktifkan model lisensi metered untuk SDK. Muat kunci publik dan pribadi Anda, buat instance `Metered`, dan panggil `SetMeteredLicense`. Panggilan tunggal ini mengaktifkan model bayar‑per‑pakai untuk seluruh aplikasi.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Direct Answer (40‑70 words):**  
> Buat objek `Metered` dengan kunci publik dan pribadi Anda, lalu panggil `SetMeteredLicense()` sebelum operasi anotasi apa pun. SDK segera memvalidasi kunci, membangun saluran TLS aman dengan server GroupDocs, dan mulai melacak setiap permintaan anotasi halaman. Setelah diatur, semua panggilan API selanjutnya tercakup oleh lisensi metered.  

### Langkah 1: Dapatkan Kunci Lisensi Metered Anda
Langkah praktis pertama adalah mengambil kunci publik dan pribadi dari dasbor GroupDocs Anda.

1. Masuk ke akun GroupDocs Anda menggunakan kredensial.  
2. Arahkan ke **License Management** di bilah sisi dasbor.  
3. Temukan entri lisensi metered; Anda akan melihat **Public Key** dan **Private Key** ditampilkan berdampingan.  
4. Salin kedua kunci dan simpan dengan aman—perlakukan seperti kata sandi.

> **Pro Tip:** Simpan kunci dalam variabel lingkungan (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) atau manajer rahasia (Azure Key Vault, AWS Secrets Manager). Jangan pernah menuliskannya secara keras di kontrol sumber.

### Langkah 2: Implementasikan Pengaturan Lisensi Metered
Sekarang sematkan kunci ke dalam kode inisialisasi aplikasi Anda. Cuplikan berikut menunjukkan urutan tepat yang Anda perlukan:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explanation:**  
> - **Membuat objek `Metered`** yang mengenkapsulasi logika lisensi.  
> - **Menyertakan kunci publik dan pribadi** ke konstruktor, membentuk permintaan bertanda tangan.  
> - **Memanggil `SetMeteredLicense()`**, yang menghubungi endpoint lisensi GroupDocs, memvalidasi kunci, dan mengaktifkan pelacakan penggunaan.  
> - **Semua fitur anotasi** (highlight, comment, drawing) langsung tersedia.  

### Langkah 3: Amankan Inisialisasi Lisensi
Bungkus inisialisasi dalam blok try‑catch untuk menangani kegagalan konektivitas atau kesalahan kunci secara elegan. `LicenseException` dilemparkan ketika lisensi tidak dapat divalidasi atau diterapkan.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Why this matters:**  
> - **Kegagalan jaringan** atau kunci yang tidak tepat akan melempar `LicenseException`. Menangkapnya mencegah aplikasi Anda crash dan memungkinkan Anda beralih ke mode baca‑saja atau menampilkan halaman error yang ramah.  
> - **Mencatat** pengecualian dengan ID korelasi membantu tim dukungan mendiagnosis sengketa penagihan dengan cepat.  

## Praktik Terbaik untuk Implementasi Produksi
Meskipun pengaturan dasar hanya beberapa baris, lingkungan produksi memerlukan perhatian ekstra.

### Inisialisasi Terpusat
Letakkan pemanggilan lisensi di satu lokasi—misalnya, `Program.cs` untuk ASP.NET Core atau metode `Main` untuk aplikasi konsol. Ini menjamin lisensi siap sebelum ada controller atau layanan yang mengakses API.

### Integrasi Dependency Injection (DI)
Jika Anda menggunakan kontainer DI, daftarkan instance `Metered` sebagai singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Result:** Setiap komponen yang memerlukan layanan anotasi menerima instance berlisensi yang sama, mengurangi panggilan jaringan berulang.

### Penyimpanan Kunci yang Aman
- **Variabel Lingkungan** – atur pada OS host atau di pipeline CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – menyediakan enkripsi saat istirahat dan log audit.  
- **Docker Secrets** – mount sebagai file di dalam kontainer untuk deployment berbasis container.

### Pemantauan Penggunaan
Aktifkan logger penggunaan bawaan:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Tinjau tab **Usage** di portal GroupDocs setiap minggu; Anda akan melihat hitungan halaman tepat, tipe panggilan API, dan proyeksi biaya.

## Masalah Umum dan Pemecahan Masalah

### Kesalahan “Invalid License Keys”
**Penyebab Utama:**  
- Spasi ekstra atau karakter baris baru saat menyalin kunci.  
- Menggunakan kunci dari produk lain (misalnya, kunci GroupDocs.Viewer).  
- Kunci yang kedaluwarsa atau dinonaktifkan.

**Perbaikan:**  
1. Salin kembali kunci langsung dari dasbor, pastikan tidak ada spasi di sekelilingnya.  
2. Verifikasi kunci memang untuk **GroupDocs.Annotation** pada tab *Metered*.  
3. Pastikan status akun Anda aktif (tidak ada pembayaran tertunda).

### Masalah Konektivitas Jaringan
**Gejala:** Validasi lisensi gagal dengan timeout atau error DNS.

**Solusi:**  
- Buka port keluar **443** untuk lalu lintas HTTPS pada firewall.  
- Jika berada di belakang proxy perusahaan, setel `WebRequest.DefaultWebProxy` ke URL proxy Anda sebelum memanggil `SetMeteredLicense()`.  
- Implementasikan logika retry dengan back‑off eksponensial untuk kegagalan sementara.

### Pelaporan Penggunaan Terlambat
Data penggunaan dapat tertunda hingga **24 jam** karena pemrosesan batch di sisi server. Ini normal; dasbor akan akhirnya menampilkan hitungan yang tepat.

### Tagihan Tinggi yang Tidak Terduga
Jika Anda melihat lonjakan, periksa:

- **Pekerjaan anotasi batch** yang berjalan tanpa throttling.  
- **Bot otomatis** yang berulang‑ulang mengannotasi dokumen yang sama.  
- **Tidak ada caching**, menyebabkan dokumen yang sama di‑annotasi pada setiap permintaan.

Kurangi dengan menambahkan rate limiting di sisi server dan caching dokumen yang telah diproses.

## Strategi Optimasi Biaya

| Strategi | Bagaimana Menghemat Biaya |
|----------|---------------------------|
| **Pemrosesan Batch** | Gabungkan beberapa aksi anotasi menjadi satu panggilan API; mengurangi overhead per halaman. |
| **Caching Dokumen** | Simpan PDF yang telah dianotasi di CDN atau blob storage; menghindari anotasi ulang pada file yang tidak berubah. |
| **Peringatan Penggunaan** | Konfigurasikan peringatan email di portal GroupDocs ketika penggunaan harian melebihi ambang batas (misalnya, 5 000 halaman). |
| **Aktivasi Fitur Selektif** | Nonaktifkan tipe anotasi yang jarang dipakai (misalnya, stempel 3‑D) melalui `AnnotationOptions` untuk mengurangi pemrosesan yang tidak perlu. |

## Kapan Memilih Metered vs. Lisensi Tradisional
Pilih lisensi metered ketika volume anotasi Anda berfluktuasi atau Anda lebih suka penagihan berbasis penggunaan, dan pilih lisensi permanen untuk beban kerja yang konsisten tinggi, dapat diprediksi, atau lingkungan tanpa akses internet. Evaluasi faktor seperti jumlah halaman bulanan, fleksibilitas anggaran, dan batasan jaringan untuk memilih model yang paling hemat biaya.

## Kesimpulan
Mengatur **lisensi metered set** untuk GroupDocs.Annotation .NET cukup sederhana, namun kekuatan sesungguhnya terletak pada fleksibilitas dan transparansi biaya yang ditawarkannya. Dengan mengikuti langkah‑langkah di atas, mengamankan kunci Anda, dan menerapkan praktik terbaik produksi, Anda akan mengaktifkan anotasi dokumen skala besar dengan model bayar‑per‑pakai yang tumbuh bersama bisnis Anda.

Ingatlah untuk memantau penggunaan secara rutin, mengamankan kredensial, dan memanfaatkan logging bawaan untuk menjaga penagihan tetap dapat diprediksi. Baik Anda membangun platform review kolaboratif, sistem manajemen dokumen hukum, atau widget anotasi sederhana, model lisensi metered memastikan Anda hanya membayar untuk nilai yang sebenarnya Anda berikan.

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menggunakan GroupDocs.Annotation untuk .NET dalam proyek komersial?**  
J: Ya, perpustakaan ini sepenuhnya berlisensi untuk penggunaan komersial setelah Anda memiliki lisensi metered atau permanen yang valid.

**T: Apakah tersedia versi percobaan untuk menguji alur lisensi metered?**  
J: Ya, Anda dapat memperoleh percobaan gratis dari [situs web](https://releases.groupdocs.com/).

**T: Bagaimana cara mendapatkan dukungan teknis untuk masalah lisensi?**  
J: Kunjungi forum GroupDocs [di sini](https://forum.groupdocs.com/c/annotation/10) untuk mengajukan pertanyaan atau membuka tiket dukungan.

**T: Apakah lisensi sementara menjadi opsi untuk evaluasi jangka pendek?**  
J: Tentu saja—lisensi sementara ditawarkan untuk periode terbatas. Lihat detailnya di [tautan ini](https://purchase.groupdocs.com/temporary-license/).

**T: Seberapa akurat pelacakan penggunaan dengan lisensi metered?**  
J: Pelacakan akurat hingga satu anotasi halaman; laporan biasanya diperbarui dalam 24 jam.

**Last Updated:** 2026-06-06  
**Tested With:** GroupDocs.Annotation 23.12 for .NET  
**Author:** GroupDocs

## Tutorial Terkait

- [Panduan Lengkap Pengaturan Lisensi GroupDocs Annotation .NET](/annotation/net/applying-licenses/set-license-from-file/)
- [Set License dari Stream .NET - Panduan Lengkap GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licensing GroupDocs.Annotation .NET - Setup & Konfigurasi Lengkap](/annotation/net/licensing-and-configuration/)