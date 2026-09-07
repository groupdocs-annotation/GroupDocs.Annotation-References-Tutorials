---
categories:
- Document Processing
date: '2026-04-01'
description: Pelajari cara membuat thumbnail PDF dan menghasilkan pratinjau PDF bersih
  tanpa anotasi di .NET. Panduan langkah demi langkah dengan kode untuk pembuatan
  thumbnail PDF menggunakan GroupDocs.Annotation.
keywords:
- create pdf thumbnails
- generate pdf preview
- remove annotations preview
- render pdf without markup
- pdf thumbnail generation
lastmod: '2025-01-02'
linktitle: Buat Pratinjau tanpa Anotasi
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-preview
- document-collaboration
- annotations
- net-development
title: Buat Thumbnail PDF di .NET – Pratinjau Bersih Tanpa Anotasi
type: docs
url: /id/net/advanced-usage/generate-preview-without-annotations/
weight: 13
---

# Buat Thumbnail PDF di .NET – Pratinjau Bersih Tanpa Anotasi

Membuat pratinjau dokumen yang bersih adalah kebutuhan umum ketika Anda **create pdf thumbnails** untuk galeri, alur kerja persetujuan, atau berbagi publik. Dalam tutorial ini Anda akan belajar cara **create pdf thumbnails** yang menghilangkan semua anotasi, memberikan pengguna Anda tampilan bersih dari konten PDF asli.

## Jawaban Cepat
- **Apa yang dilakukan “RenderAnnotations = false”?** Ini memberi tahu GroupDocs.Annotation untuk melewatkan semua markup saat merender pratinjau.  
- **Format gambar mana yang direkomendasikan untuk thumbnail berkualitas tinggi?** PNG menyediakan kualitas lossless; JPEG lebih kecil tetapi lossy.  
- **Apakah saya dapat memilih halaman tertentu untuk set thumbnail?** Ya – atur `PreviewOptions.PageNumbers` ke halaman yang Anda butuhkan.  
- **Apakah saya memerlukan lisensi untuk penggunaan produksi?** Lisensi direkomendasikan untuk fitur tak terbatas dan dukungan.  
- **Apakah pendekatan ini kompatibel dengan .NET Core?** Tentu – GroupDocs.Annotation bekerja dengan .NET Framework dan .NET Core.

## Apa itu “create pdf thumbnails”?
Membuat thumbnail PDF berarti merender setiap halaman PDF menjadi gambar (PNG/JPEG) yang dapat ditampilkan di UI. Thumbnail berguna untuk pratinjau cepat, penjelajah dokumen, dan menghasilkan grid pratinjau tanpa harus memuat PDF secara penuh.

## Mengapa menghasilkan pratinjau tanpa anotasi?
Menghapus anotasi dari pratinjau menjaga fokus pada konten dokumen asli. Ini penting untuk:

- **Document approval workflows** – bandingkan versi bersih dengan versi beranotasi.  
- **Thumbnail galleries** – hindari kekacauan visual dari komentar atau sorotan.  
- **Public sharing** – lindungi markup sensitif sambil tetap menampilkan dokumen.  
- **Print preparation** – hasilkan PDF bersih untuk pencetakan sambil memisahkan catatan digital.

## Prasyarat
- **GroupDocs.Annotation for .NET** – instal dari [halaman rilis](https://releases.groupdocs.com/annotation/net/) resmi.  
- **License (optional but recommended)** – beli lisensi penuh melalui [halaman pembelian](https://purchase.groupdocs.com/buy) atau minta [lisensi sementara](https://purchase.groupdocs.com/temporary-license/).  
- Pengetahuan dasar tentang C#/.NET.  
- Penampil PDF (misalnya Adobe Acrobat Reader) untuk memverifikasi thumbnail yang dihasilkan.

## Impor Namespace
Tambahkan pernyataan `using` yang diperlukan agar Anda dapat bekerja dengan API anotasi:

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

## Cara Membuat Thumbnail PDF Tanpa Anotasi

Berikut adalah panduan langkah demi langkah yang menunjukkan secara tepat cara **generate pdf preview** gambar sambil **removing annotations preview** dari output.

### Langkah 1: Inisialisasi Annotator
Buat instance `Annotator` yang menunjuk ke PDF sumber. Blok `using` memastikan sumber daya dilepaskan secara otomatis.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```

> **Pro Tip:** Validasi jalur file dan terapkan pemeriksaan keamanan yang tepat saat menangani PDF yang diunggah pengguna.

### Langkah 2: Konfigurasi Opsi Pratinjau
Siapkan `PreviewOptions` untuk menentukan format output, rentang halaman, dan yang paling penting, menonaktifkan rendering anotasi.

```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```

**Poin penting**

- **File naming** – lambda membuat file PNG unik untuk setiap halaman.  
- **Format choice** – PNG untuk thumbnail berkualitas tinggi; beralih ke JPEG untuk file yang lebih kecil.  
- **Page selection** – tentukan secara tepat halaman mana yang Anda inginkan untuk **pdf thumbnail generation**.  
- **`RenderAnnotations = false`** – ini menonaktifkan semua markup dan merupakan inti dari **disable annotations preview**.

### Langkah 3: Hasilkan Pratinjau Bersih
Panggil metode `GeneratePreview` untuk merender gambar berdasarkan opsi yang Anda tetapkan.

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

File thumbnail bersih Anda (`result1.png`, `result2.png`, …) kini siap digunakan.

## Kasus Penggunaan Umum dalam Aplikasi Nyata
- **Document Management Systems** – thumbnail bersih untuk penjelajah file sambil mempertahankan versi beranotasi terpisah.  
- **Legal Review Platforms** – tunjukkan kontrak asli kepada klien tanpa komentar internal.  
- **E‑learning Portals** – tampilkan tugas asli sementara guru menyimpan catatan penilaian secara pribadi.  
- **Publishing Workflows** – buat gambar pratinjau untuk materi pemasaran tanpa markup editorial.

## Pertimbangan Kinerja
- **Batch processing** – tangani banyak PDF dalam satu pekerjaan latar belakang untuk mengurangi beban.  
- **Caching** – simpan thumbnail yang dihasilkan setelah unggahan pertama untuk menghindari perenderan ulang pada setiap permintaan.  
- **Page limits** – untuk PDF yang sangat besar, batasi pratinjau ke beberapa halaman pertama agar waktu pemrosesan tetap rendah.  
- **File format trade‑offs** – PNG menghasilkan thumbnail tajam; JPEG mengurangi penyimpanan ketika bandwidth menjadi masalah.

## Memecahkan Masalah Umum
- **Thumbnails not created** – verifikasi izin menulis untuk folder output dan pastikan PDF sumber tidak rusak.  
- **Low image quality** – beralih ke PNG atau sesuaikan pengaturan DPI jika versi GroupDocs.Annotation Anda mendukungnya.  
- **High memory usage** – proses halaman dalam batch lebih kecil atau streaming PDF alih-alih memuat seluruhnya ke memori.  
- **Path problems** – selalu bangun jalur file dengan `Path.Combine()` untuk keamanan lintas‑platform.

## Praktik Terbaik untuk Produksi
- Bungkus pembuatan pratinjau dalam blok `try‑catch` untuk menangani kesalahan I/O secara elegan.  
- Gunakan pernyataan `using` (seperti yang ditunjukkan) untuk menjamin pembuangan penangan file yang tepat.  
- Validasi PDF yang masuk (ukuran, format, perlindungan kata sandi) sebelum diproses.  
- Catat setiap peristiwa pembuatan pratinjau untuk pemantauan dan debugging.

## Opsi Konfigurasi Lanjutan
- **Custom DPI** – beberapa versi memungkinkan Anda mengatur resolusi lebih tinggi untuk thumbnail yang lebih tajam.  
- **Watermarking** – tambahkan watermark “Preview Only” untuk menunjukkan gambar bukan dokumen final.  
- **Smart page selection** – secara otomatis pilih halaman paling relevan (mis., halaman pertama, daftar isi) berdasarkan metadata dokumen.

## Kesimpulan
Anda kini memiliki resep lengkap yang siap produksi untuk **create pdf thumbnails** dan **generate pdf preview** gambar tanpa markup apa pun. Dengan mengatur `RenderAnnotations = false`, Anda **remove annotations preview** dan menyajikan thumbnail bersih serta profesional yang terintegrasi mulus ke dalam aplikasi berpusat dokumen apa pun.

## Pertanyaan yang Sering Diajukan

**Q: Dapatkah saya menggunakan GroupDocs.Annotation untuk .NET dengan format selain PDF?**  
A: Ya. Perpustakaan mendukung DOCX, XLSX, PPTX, dan banyak lagi. Alur kerja pratinjau yang sama berlaku terlepas dari format sumber.

**Q: Apakah GroupDocs.Annotation untuk .NET kompatibel dengan .NET Core?**  
A: Tentu. Ia bekerja dengan .NET Framework, .NET Core, dan .NET 5/6+, sehingga Anda dapat menargetkan aplikasi lintas‑platform modern.

**Q: Apakah perpustakaan menyediakan alat anotasi yang dapat disesuaikan?**  
A: Ya, tetapi ketika Anda mengatur `RenderAnnotations = false` alat tersebut diabaikan untuk pembuatan pratinjau.

**Q: Dapatkah saya mengintegrasikan ini ke dalam aplikasi web?**  
A: Ya. Pastikan server web memiliki izin I/O file yang tepat dan pertimbangkan streaming output langsung ke klien untuk menghindari file sementara.

**Q: Format gambar mana yang harus saya pilih untuk galeri thumbnail?**  
A: PNG menawarkan kualitas terbaik, sementara JPEG mengurangi ukuran file. Pilih berdasarkan keakuratan visual yang Anda butuhkan versus keterbatasan bandwidth.

**Q: Di mana saya dapat mendapatkan dukungan komunitas?**  
A: Anda dapat menemukan bantuan di forum GroupDocs.Annotation [di sini](https://forum.groupdocs.com/c/annotation/10). Komunitasnya aktif dan responsif.

**Terakhir Diperbarui:** 2026-04-01  
**Diuji Dengan:** GroupDocs.Annotation for .NET 23.12  
**Penulis:** GroupDocs