---
"description": "Tingkatkan kolaborasi & tinjauan dokumen dengan GroupDocs.Annotation untuk .NET. Beri anotasi pada PDF & lebih mudah di aplikasi .NET Anda."
"linktitle": "Muat Dokumen yang Dilindungi Kata Sandi"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Muat Dokumen yang Dilindungi Kata Sandi"
"url": "/id/net/document-loading-essentials/load-password-protected-documents/"
"weight": 17
---

# Muat Dokumen yang Dilindungi Kata Sandi

## Perkenalan
Dalam dunia yang serba cepat saat ini, kolaborasi adalah kunci keberhasilan. Baik Anda mengerjakan proyek dengan kolega, klien, atau mitra, kemampuan untuk membuat anotasi dan berbagi dokumen secara efisien dapat meningkatkan produktivitas dan menyederhanakan alur kerja secara signifikan. GroupDocs.Annotation untuk .NET menawarkan solusi hebat untuk membuat anotasi PDF dan format dokumen lainnya langsung dalam aplikasi .NET Anda, yang memungkinkan kolaborasi dan proses peninjauan dokumen yang lancar.
## Prasyarat
Sebelum menyelami dunia anotasi dokumen dengan GroupDocs.Annotation untuk .NET, ada beberapa prasyarat yang perlu Anda pastikan terpenuhi:
### 1. Instal GroupDocs.Annotation untuk .NET
Untuk memulai, Anda perlu mengunduh dan menginstal pustaka GroupDocs.Annotation for .NET. Anda dapat menemukan tautan unduhannya [Di Sini](https://releases.groupdocs.com/annotation/net/)Ikuti petunjuk instalasi yang diberikan untuk menyiapkan pustaka di lingkungan .NET Anda.
### 2. Memperoleh Lisensi atau Menggunakan Lisensi Sementara
GroupDocs.Annotation untuk .NET memerlukan lisensi yang valid untuk membuka fungsionalitas penuhnya. Anda dapat membeli lisensi dari situs web GroupDocs [Di Sini](https://purchase.groupdocs.com/buy), atau Anda dapat meminta lisensi sementara untuk tujuan evaluasi [Di Sini](https://purchase.groupdocs.com/temporary-license/).
### 3. Keakraban dengan Pengembangan C# dan .NET
Pemahaman dasar tentang bahasa pemrograman C# dan pengembangan .NET sangat penting untuk memanfaatkan GroupDocs.Annotation for .NET secara efektif. Jika Anda baru mengenal C# atau .NET, pertimbangkan untuk membiasakan diri dengan bahasa dan kerangka kerja tersebut melalui tutorial dan sumber daya daring.

## Impor Ruang Nama yang Diperlukan
Sebelum Anda mulai membuat anotasi pada dokumen, pastikan untuk mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Ini memungkinkan Anda untuk mengakses kelas dan metode yang disediakan oleh GroupDocs.Annotation untuk .NET dengan mudah.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Sekarang setelah Anda memiliki prasyarat dan namespace yang diperlukan telah diimpor, mari kita mulai membuat anotasi pada dokumen yang dilindungi kata sandi menggunakan GroupDocs.Annotation untuk .NET. Berikut adalah panduan langkah demi langkah untuk membantu Anda menyelesaikan tugas ini:
## Langkah 1: Muat Dokumen
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
```
Pada langkah ini, kami menentukan jalur keluaran untuk dokumen yang dianotasi dan menentukan opsi pemuatan, termasuk kata sandi yang diperlukan untuk membuka dokumen yang dilindungi kata sandi.
## Langkah 2: Inisialisasi Anotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
```
Di sini, kita membuat sebuah instance dari `Annotator` kelas, melewati jalur ke dokumen input dan opsi muat sebagai parameter. `using` pernyataan tersebut memastikan bahwa `Annotator` Benda tersebut dibuang dengan benar setelah digunakan.
## Langkah 3: Tambahkan Anotasi
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
Pada langkah ini, kita membuat yang baru `AreaAnnotation` objek, menentukan lokasi dan ukuran kotak anotasi, serta warna latar belakangnya. Kami kemudian menambahkan anotasi ke dokumen menggunakan `Add` metode dari `Annotator` obyek.
## Langkah 4: Simpan Dokumen Beranotasi
```csharp
annotator.Save(outputPath);
```
Terakhir, kami menyimpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan menggunakan `Save` metode dari `Annotator` obyek.
## Langkah 5: Menampilkan Pesan Konfirmasi
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Untuk memberikan umpan balik kepada pengguna, kami menampilkan pesan konfirmasi yang menunjukkan bahwa dokumen telah berhasil disimpan dan menentukan lokasi berkas keluaran.

## Kesimpulan
Sebagai kesimpulan, GroupDocs.Annotation untuk .NET menawarkan solusi yang tangguh dan kaya fitur untuk membuat anotasi dokumen dalam aplikasi .NET. Dengan mengikuti panduan langkah demi langkah yang disediakan dalam artikel ini, Anda dapat dengan mudah mengintegrasikan kemampuan anotasi dokumen ke dalam proyek Anda, yang memungkinkan kolaborasi dan proses peninjauan dokumen yang lebih baik.
## Pertanyaan yang Sering Diajukan
### T: Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, Microsoft Word, Excel, PowerPoint, dan banyak lagi.
### T: Dapatkah saya menyesuaikan tampilan anotasi yang dibuat dengan GroupDocs.Annotation untuk .NET?
Tentu saja! GroupDocs.Annotation untuk .NET menyediakan opsi penyesuaian yang luas untuk anotasi, yang memungkinkan Anda mengontrol berbagai aspek seperti warna, ukuran, opasitas, dan banyak lagi.
### T: Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat mengunduh versi uji coba gratis GroupDocs.Annotation untuk .NET dari [Di Sini](https://releases.groupdocs.com/)Versi uji coba memungkinkan Anda mengevaluasi produk sebelum melakukan pembelian.
### T: Bagaimana saya bisa mendapatkan dukungan untuk GroupDocs.Annotation untuk .NET?
Jika Anda memiliki pertanyaan atau mengalami masalah saat menggunakan GroupDocs.Annotation untuk .NET, Anda dapat mengunjungi forum dukungan [Di Sini](https://forum.groupdocs.com/c/annotation/10) untuk mencari bantuan dari komunitas dan tim dukungan GroupDocs.
### T: Dapatkah saya mengintegrasikan GroupDocs.Annotation untuk .NET ke dalam aplikasi web dan desktop?
Ya, GroupDocs.Annotation untuk .NET dirancang agar kompatibel dengan aplikasi web dan desktop, memberikan fleksibilitas dalam cara Anda menggabungkan fungsionalitas anotasi dokumen ke dalam proyek Anda.