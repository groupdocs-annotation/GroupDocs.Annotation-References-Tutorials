---
title: Muat Dokumen yang Dilindungi Kata Sandi
linktitle: Muat Dokumen yang Dilindungi Kata Sandi
second_title: GroupDocs.Annotasi .NET API
description: Tingkatkan kolaborasi & tinjauan dokumen dengan GroupDocs.Annotation untuk .NET. Beri anotasi pada PDF & lebih lancar di aplikasi .NET Anda.
weight: 17
url: /id/net/document-loading-essentials/load-password-protected-documents/
---
## Perkenalan
Di dunia yang serba cepat saat ini, kolaborasi adalah kunci kesuksesan. Baik Anda mengerjakan proyek bersama kolega, klien, atau mitra, kemampuan untuk membuat anotasi dan berbagi dokumen secara efisien dapat meningkatkan produktivitas dan menyederhanakan alur kerja secara signifikan. GroupDocs.Annotation for .NET menawarkan solusi canggih untuk membuat anotasi PDF dan format dokumen lainnya langsung dalam aplikasi .NET Anda, memungkinkan proses kolaborasi dan peninjauan dokumen yang lancar.
## Prasyarat
Sebelum terjun ke dunia anotasi dokumen dengan GroupDocs.Annotation untuk .NET, ada beberapa prasyarat yang perlu Anda pastikan sudah ada:
### 1. Instal GroupDocs.Annotation untuk .NET
 Untuk memulai, Anda harus mengunduh dan menginstal pustaka GroupDocs.Annotation untuk .NET. Anda dapat menemukan tautan unduhan[Di Sini](https://releases.groupdocs.com/annotation/net/). Ikuti petunjuk instalasi yang disediakan untuk menyiapkan perpustakaan di lingkungan .NET Anda.
### 2. Mendapatkan Lisensi atau Menggunakan Lisensi Sementara
 GroupDocs.Annotation untuk .NET memerlukan lisensi yang valid untuk membuka fungsionalitas penuhnya. Anda dapat membeli lisensi dari situs web GroupDocs[Di Sini](https://purchase.groupdocs.com/buy) atau Anda dapat meminta lisensi sementara untuk tujuan evaluasi[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### 3. Keakraban dengan Pengembangan C# dan .NET
Pemahaman dasar tentang bahasa pemrograman C# dan pengembangan .NET sangat penting untuk memanfaatkan GroupDocs.Annotation untuk .NET secara efektif. Jika Anda baru mengenal C# atau .NET, pertimbangkan untuk membiasakan diri dengan bahasa dan kerangka kerja melalui tutorial dan sumber daya online.

## Impor Namespace yang Diperlukan
Sebelum Anda mulai membuat anotasi pada dokumen, pastikan untuk mengimpor namespace yang diperlukan ke proyek C# Anda. Ini memungkinkan Anda mengakses kelas dan metode yang disediakan oleh GroupDocs.Annotation untuk .NET dengan lancar.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang setelah Anda memiliki prasyarat dan namespace yang diperlukan telah diimpor, mari selami pembuatan anotasi pada dokumen yang dilindungi kata sandi menggunakan GroupDocs.Annotation untuk .NET. Di bawah ini adalah panduan langkah demi langkah untuk membantu Anda menyelesaikan tugas ini:
## Langkah 1: Muat Dokumen
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
```
Pada langkah ini, kami menentukan jalur keluaran untuk dokumen beranotasi dan menentukan opsi pemuatan, termasuk kata sandi yang diperlukan untuk membuka dokumen yang dilindungi kata sandi.
## Langkah 2: Inisialisasi Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
```
 Di sini, kita membuat sebuah instance dari`Annotator` kelas, meneruskan jalur ke dokumen masukan dan opsi pemuatan sebagai parameter. Itu`using` pernyataan memastikan bahwa`Annotator` benda dibuang dengan benar setelah digunakan.
## Langkah 3: Tambahkan Anotasi
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
 Pada langkah ini, kami membuat yang baru`AreaAnnotation` objek, menentukan lokasi dan ukuran kotak anotasi, serta warna latar belakangnya. Kami kemudian menambahkan anotasi ke dokumen menggunakan`Add` metode`Annotator` obyek.
## Langkah 4: Simpan Dokumen Beranotasi
```csharp
annotator.Save(outputPath);
```
 Terakhir, kami menyimpan dokumen beranotasi ke jalur keluaran yang ditentukan menggunakan`Save` metode`Annotator` obyek.
## Langkah 5: Tampilkan Pesan Konfirmasi
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Untuk memberikan umpan balik kepada pengguna, kami menampilkan pesan konfirmasi yang menunjukkan bahwa dokumen telah berhasil disimpan dan menentukan lokasi file keluaran.

## Kesimpulan
Kesimpulannya, GroupDocs.Annotation untuk .NET menawarkan solusi yang kuat dan kaya fitur untuk membuat anotasi dokumen dalam aplikasi .NET. Dengan mengikuti panduan langkah demi langkah yang disediakan dalam artikel ini, Anda dapat dengan mudah mengintegrasikan kemampuan anotasi dokumen ke dalam proyek Anda, sehingga memungkinkan peningkatan kolaborasi dan proses peninjauan dokumen.
## FAQ
### T: Apakah GroupDocs.Annotation for .NET kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi.
### T: Dapatkah saya menyesuaikan tampilan anotasi yang dibuat dengan GroupDocs.Annotation untuk .NET?
Sangat! GroupDocs.Annotation untuk .NET menyediakan opsi penyesuaian ekstensif untuk anotasi, memungkinkan Anda mengontrol berbagai aspek seperti warna, ukuran, opacity, dan banyak lagi.
### T: Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?
 Ya, Anda dapat mengunduh GroupDocs.Annotation versi uji coba gratis untuk .NET dari[Di Sini](https://releases.groupdocs.com/)Versi uji coba memungkinkan Anda mengevaluasi produk sebelum melakukan pembelian.
### T: Bagaimana cara mendapatkan dukungan untuk GroupDocs.Annotation untuk .NET?
 Jika Anda memiliki pertanyaan atau mengalami masalah apa pun saat menggunakan GroupDocs.Annotation untuk .NET, Anda dapat mengunjungi forum dukungan[Di Sini](https://forum.groupdocs.com/c/annotation/10) untuk mencari bantuan dari komunitas dan tim dukungan GroupDocs.
### T: Dapatkah saya mengintegrasikan GroupDocs.Annotation untuk .NET ke dalam aplikasi web dan desktop?
Ya, GroupDocs.Annotation untuk .NET dirancang agar kompatibel dengan aplikasi web dan desktop, memberikan fleksibilitas dalam cara Anda memasukkan fungsionalitas anotasi dokumen ke dalam proyek Anda.