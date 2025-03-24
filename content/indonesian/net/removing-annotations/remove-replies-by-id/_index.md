---
title: Hapus Balasan berdasarkan ID di .NET
linktitle: Hapus Balasan berdasarkan ID di .NET
second_title: GroupDocs.Annotasi .NET API
description: Pelajari cara menghapus balasan berdasarkan ID di .NET menggunakan GroupDocs.Annotation. Ikuti tutorial langkah demi langkah kami untuk manajemen anotasi dokumen yang efisien.
weight: 16
url: /id/net/removing-annotations/remove-replies-by-id/
---
## Perkenalan
Dalam bidang pengembangan .NET, kemampuan mengelola anotasi dalam dokumen sangat penting untuk berbagai aplikasi. Baik Anda bekerja dengan PDF, dokumen Word, atau format lainnya, memiliki kemampuan untuk memanipulasi anotasi secara terprogram akan membuka banyak kemungkinan. Salah satu alat canggih untuk menangani anotasi di .NET adalah GroupDocs.Annotation.
## Prasyarat
Sebelum mendalami tutorial tentang menghapus balasan berdasarkan ID di .NET menggunakan GroupDocs.Annotation, pastikan Anda memiliki prasyarat berikut:
### 1. Instalasi GroupDocs.Annotation
 Pertama, Anda perlu menginstal GroupDocs.Annotation untuk .NET. Anda dapat mengunduh perpustakaan dari[Di Sini](https://releases.groupdocs.com/annotation/net/) dan ikuti petunjuk instalasi yang disediakan dalam dokumentasi[Di Sini](https://tutorials.groupdocs.com/annotation/net/).
### 2. Pemahaman Dasar C# dan .NET
Keakraban dengan bahasa pemrograman C# dan kerangka .NET diperlukan untuk mengikuti contoh dalam tutorial ini.
### 3. Dokumen Beranotasi dengan Balasan
Siapkan dokumen yang berisi anotasi dengan balasan. Dokumen ini akan berfungsi sebagai masukan untuk proses penghapusan.

## Impor Namespace
Di proyek .NET Anda, impor namespace yang diperlukan untuk mengakses fungsi GroupDocs.Annotation.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## Langkah 1: Tentukan Jalur Keluaran
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tentukan jalur tempat Anda ingin menyimpan dokumen yang dimodifikasi setelah menghapus balasan.
## Langkah 2: Muat Dokumen dan Anotasi
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    List<AnnotationBase> annotations = annotator.Get();
```
 Muat dokumen yang berisi anotasi dengan balasan menggunakan`Annotator` kelas dan mengambil koleksi anotasi.
## Langkah 3: Hapus Balasan berdasarkan ID
```csharp
annotations[0].Replies.RemoveAll(x => x.Id == 4);
```
Identifikasi balasan yang ingin Anda hapus berdasarkan ID-nya dan hapus dari kumpulan balasan anotasi yang sesuai.
## Langkah 4: Simpan Perubahan
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
Perbarui anotasi dengan balasan yang dihapus dan simpan dokumen yang dimodifikasi ke jalur keluaran yang ditentukan.
## Langkah 5: Konfirmasikan Keberhasilan
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Menampilkan pesan konfirmasi yang menunjukkan bahwa dokumen telah berhasil disimpan dan balasannya dihapus.

## Kesimpulan
Kesimpulannya, GroupDocs.Annotation untuk .NET memberikan solusi langsung untuk mengelola anotasi dalam dokumen. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat dengan mudah menghapus balasan berdasarkan ID, sehingga memberdayakan Anda untuk menyesuaikan anotasi dokumen dengan kebutuhan spesifik Anda dengan mudah dan efisien.
## FAQ
### Bisakah GroupDocs.Annotation digunakan dengan format dokumen lain selain PDF?
Ya, GroupDocs.Annotation mendukung berbagai format dokumen termasuk Word, Excel, PowerPoint, dan lainnya.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Annotation?
 Ya, Anda dapat mengakses uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dukungan untuk GroupDocs.Annotation?
 Anda dapat menemukan dukungan dan terlibat dengan komunitas[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Annotation?
 Anda dapat memperoleh lisensi sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Di mana saya dapat membeli GroupDocs.Annotation untuk .NET?
 Anda dapat membeli GroupDocs.Annotation[Di Sini](https://purchase.groupdocs.com/buy).