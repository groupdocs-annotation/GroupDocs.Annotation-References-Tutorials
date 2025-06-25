---
"description": "Pelajari cara menghapus anotasi dari PDF dan dokumen lain dalam .NET menggunakan GroupDocs.Annotation. Panduan langkah demi langkah dengan contoh kode."
"linktitle": "Hapus Anotasi Menggunakan Opsi Simpan di .NET"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Hapus Anotasi Menggunakan Opsi Simpan di .NET"
"url": "/id/net/removing-annotations/remove-annotations-using-save-options/"
"weight": 14
---

# Hapus Anotasi Menggunakan Opsi Simpan di .NET

## Perkenalan

GroupDocs.Annotation untuk .NET adalah alat canggih yang memungkinkan pengembang untuk menambahkan fungsi anotasi ke aplikasi .NET mereka dengan mudah. Baik Anda bekerja pada sistem manajemen dokumen, platform kolaborasi, atau aplikasi lain yang melibatkan pemrosesan dokumen, GroupDocs.Annotation menyediakan serangkaian fitur lengkap untuk membuat anotasi PDF dan format dokumen lainnya dengan mudah.

## Prasyarat

Sebelum terjun ke dunia anotasi dokumen menggunakan GroupDocs.Annotation untuk .NET, pastikan Anda memiliki prasyarat berikut:

### 1. Instal GroupDocs.Annotation untuk .NET

Mulailah dengan mengunduh dan menginstal GroupDocs.Annotation untuk .NET. Anda dapat mengunduh versi terbaru dari [halaman unduhan](https://releases.groupdocs.com/annotation/net/).

## Mengimpor Ruang Nama

Untuk mulai menggunakan GroupDocs.Annotation di proyek .NET Anda, Anda perlu mengimpor namespace yang diperlukan. Berikut ini adalah namespace yang umum digunakan:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Sekarang, mari kita telusuri proses menghapus anotasi dari dokumen menggunakan fitur Opsi Simpan di .NET:

## Langkah 1: Tentukan Jalur Output

Pertama, tentukan jalur keluaran tempat dokumen dengan anotasi yang dihapus akan disimpan. Anda dapat menggunakan `Path.Combine` metode untuk menggabungkan jalur direktori dengan nama file keluaran.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 2: Inisialisasi Anotator

Selanjutnya, inisialisasikan instance dari `Annotator` kelas dengan menyediakan jalur ke dokumen yang berisi anotasi.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Kode penghapusan anotasi akan ada di sini
}
```

## Langkah 3: Simpan Dokumen dengan Penghapusan Anotasi

Sekarang, gunakan `Save` metode dari `Annotator` kelas bersama dengan `SaveOptions` untuk menyimpan dokumen dengan anotasi yang dihapus. Di `SaveOptions`, mengatur `AnnotationTypes` properti untuk `AnnotationType.None` untuk menghapus semua anotasi.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Langkah 4: Menampilkan Pesan Sukses

Terakhir, tampilkan pesan sukses yang menunjukkan bahwa dokumen telah berhasil disimpan dan anotasi dihapus.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Sebagai kesimpulan, GroupDocs.Annotation untuk .NET menyederhanakan proses penghapusan anotasi dari dokumen. Dengan mengikuti panduan langkah demi langkah yang diuraikan di atas, pengembang dapat dengan mudah mengintegrasikan fungsionalitas penghapusan anotasi ke dalam aplikasi .NET mereka.

## Pertanyaan yang Sering Diajukan

### T: Bisakah GroupDocs.Annotation menghapus anotasi dari format dokumen lain selain PDF?

A: GroupDocs.Annotation mendukung berbagai format dokumen, termasuk PDF, Word, Excel, dan PowerPoint, yang memungkinkan Anda menghapus anotasi dari berbagai dokumen.

### T: Apakah GroupDocs.Annotation mudah diintegrasikan ke proyek .NET yang ada?

A: Ya, GroupDocs.Annotation menyediakan API sederhana dan dokumentasi yang komprehensif, sehingga memudahkan pengembang untuk mengintegrasikan fitur anotasi ke dalam aplikasi .NET mereka.

### T: Apakah GroupDocs.Annotation mendukung penghapusan anotasi secara selektif?

A: Ya, GroupDocs.Annotation memungkinkan pengembang menentukan jenis anotasi yang akan dihapus, memberi mereka fleksibilitas dalam mengelola anotasi dalam dokumen mereka.

### T: Dapatkah saya mencoba GroupDocs.Annotation secara gratis sebelum membeli?

A: Ya, Anda dapat mengunduh versi uji coba gratis GroupDocs.Annotation dari [halaman rilis](https://releases.groupdocs.com/) untuk menjelajahi fitur-fiturnya sebelum membuat keputusan pembelian.

### T: Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation?

A: Untuk bantuan teknis dan dukungan komunitas, Anda dapat mengunjungi [Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).