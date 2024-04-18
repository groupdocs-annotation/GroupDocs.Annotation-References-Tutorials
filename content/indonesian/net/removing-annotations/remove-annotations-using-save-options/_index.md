---
title: Hapus Anotasi Menggunakan Opsi Simpan di .NET
linktitle: Hapus Anotasi Menggunakan Opsi Simpan di .NET
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menghapus anotasi dari PDF dan dokumen lain di .NET menggunakan GroupDocs.Annotation. Panduan langkah demi langkah dengan contoh kode.
type: docs
weight: 14
url: /id/net/removing-annotations/remove-annotations-using-save-options/
---
## Perkenalan

GroupDocs.Annotation for .NET adalah alat canggih yang memungkinkan pengembang menambahkan fungsionalitas anotasi ke aplikasi .NET mereka dengan mudah. Baik Anda sedang mengerjakan sistem manajemen dokumen, platform kolaborasi, atau aplikasi lain apa pun yang melibatkan pemrosesan dokumen, GroupDocs.Annotation menyediakan serangkaian fitur lengkap untuk membuat anotasi PDF dan format dokumen lainnya dengan lancar.

## Prasyarat

Sebelum terjun ke dunia anotasi dokumen menggunakan GroupDocs.Annotation untuk .NET, pastikan Anda memiliki prasyarat berikut:

### 1. Instal GroupDocs.Annotation untuk .NET

 Mulailah dengan mengunduh dan menginstal GroupDocs.Annotation untuk .NET. Anda dapat mengunduh versi terbaru dari[download page](https://releases.groupdocs.com/annotation/net/).

## Mengimpor Namespace

Untuk mulai menggunakan GroupDocs.Annotation di proyek .NET Anda, Anda perlu mengimpor namespace yang diperlukan. Berikut adalah namespace yang biasa Anda gunakan:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Sekarang, mari kita telusuri proses menghapus anotasi dari dokumen menggunakan fitur Simpan Opsi di .NET:

## Langkah 1: Tentukan Jalur Keluaran

Pertama, tentukan jalur keluaran tempat dokumen dengan anotasi yang dihapus akan disimpan. Anda dapat menggunakan`Path.Combine` metode untuk menggabungkan jalur direktori dengan nama file keluaran.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Annotator

 Selanjutnya, inisialisasi sebuah instance dari`Annotator` kelas dengan menyediakan jalur ke dokumen yang berisi anotasi.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Kode penghapusan anotasi akan ditempatkan di sini
}
```

## Langkah 3: Simpan Dokumen dengan Penghapusan Anotasi

 Sekarang, gunakan`Save` metode`Annotator` kelas bersama dengan`SaveOptions` untuk menyimpan dokumen dengan anotasi yang dihapus. Dalam`SaveOptions` , mengatur`AnnotationTypes` properti ke`AnnotationType.None` untuk menghapus semua anotasi.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Langkah 4: Tampilkan Pesan Sukses

Terakhir, tampilkan pesan sukses yang menunjukkan bahwa dokumen telah berhasil disimpan dengan anotasi dihapus.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Kesimpulannya, GroupDocs.Annotation untuk .NET menyederhanakan proses menghapus anotasi dari dokumen. Dengan mengikuti panduan langkah demi langkah yang diuraikan di atas, pengembang dapat dengan lancar mengintegrasikan fungsi penghapusan anotasi ke dalam aplikasi .NET mereka.

## FAQ

### T: Bisakah GroupDocs.Annotation menghapus anotasi dari format dokumen lain selain PDF?

J: GroupDocs.Annotation mendukung berbagai format dokumen, termasuk PDF, Word, Excel, dan PowerPoint, memungkinkan Anda menghapus anotasi dari berbagai macam dokumen.

### T: Apakah GroupDocs.Annotation mudah diintegrasikan ke dalam proyek .NET yang sudah ada?

J: Ya, GroupDocs.Annotation menyediakan API sederhana dan dokumentasi komprehensif, sehingga memudahkan pengembang untuk mengintegrasikan fitur anotasi ke dalam aplikasi .NET mereka.

### T: Apakah GroupDocs.Annotation mendukung penghapusan anotasi secara selektif?

J: Ya, GroupDocs.Annotation memungkinkan pengembang menentukan jenis anotasi mana yang akan dihapus, sehingga memberi mereka fleksibilitas dalam mengelola anotasi dalam dokumen mereka.

### T: Dapatkah saya mencoba GroupDocs.Annotation secara gratis sebelum membeli?

 J: Ya, Anda dapat mengunduh GroupDocs.Annotation versi uji coba gratis dari[halaman rilis](https://releases.groupdocs.com/) untuk menjelajahi fitur-fiturnya sebelum membuat keputusan pembelian.

### T: Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?

 J: Untuk bantuan teknis dan dukungan komunitas, Anda dapat mengunjungi[GroupDocs.Forum anotasi](https://forum.groupdocs.com/c/annotation/10).