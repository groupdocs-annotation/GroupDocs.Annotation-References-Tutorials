---
"description": "Tingkatkan aplikasi .NET Anda dengan GroupDocs.Annotation untuk anotasi dokumen yang lancar. Tutorial langkah demi langkah disertakan."
"linktitle": "Muat Dokumen dari FTP"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Muat Dokumen dari FTP"
"url": "/id/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Muat Dokumen dari FTP

## Perkenalan
GroupDocs.Annotation untuk .NET adalah pustaka serbaguna yang dirancang untuk memfasilitasi kemampuan anotasi dokumen dalam aplikasi .NET dengan mudah. Baik Anda menangani PDF, dokumen Microsoft Office, gambar, atau format lain, pustaka ini menyediakan solusi terpadu untuk menambahkan anotasi, seperti komentar, sorotan, dan bentuk, guna meningkatkan kolaborasi dan manajemen dokumen.
## Prasyarat
Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan tentang C#: Kemampuan dalam bahasa pemrograman C# sangat penting untuk memahami dan menerapkan contoh kode yang disediakan dalam tutorial ini.
2. GroupDocs.Annotation untuk .NET: Pastikan untuk mengunduh dan menginstal GroupDocs.Annotation untuk .NET dari [tautan unduhan](https://releases.groupdocs.com/annotation/net/)Ikuti petunjuk instalasi untuk mengintegrasikan pustaka ke dalam proyek .NET Anda dengan sukses.
## Mengimpor Ruang Nama
Untuk memanfaatkan GroupDocs.Annotation untuk fungsi .NET, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Ikuti langkah-langkah berikut:

Dalam proyek C# Anda, sertakan namespace yang diperlukan di awal file kode Anda:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Sekarang, mari kita bahas proses memuat dokumen dari FTP dan menambahkan anotasi ke dalamnya menggunakan GroupDocs.Annotation untuk .NET.
## Langkah 1: Tentukan Jalur Output
Tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Muat Dokumen dari FTP
Ambil dokumen dari server FTP menggunakan jalur file yang disediakan.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Kode anotasi akan ditambahkan di sini
}
```
## Langkah 3: Tambahkan Anotasi
Tentukan dan tambahkan anotasi yang diinginkan, seperti anotasi area, ke dokumen.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Langkah 4: Simpan Dokumen Beranotasi
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Langkah 5: Ambil File dari FTP
Terapkan metode untuk mengambil berkas dari server FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Langkah 6: Buat Permintaan FTP
Buat permintaan FTP untuk mengunduh berkas.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Langkah 7: Dapatkan Aliran File
Ambil aliran berkas dari respons FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Kesimpulan
Sebagai kesimpulan, GroupDocs.Annotation untuk .NET memberdayakan para pengembang untuk mengintegrasikan fungsionalitas anotasi dokumen ke dalam aplikasi .NET mereka dengan lancar. Dengan mengikuti panduan langkah demi langkah yang diuraikan dalam tutorial ini, Anda dapat memuat dokumen dari FTP secara efisien dan menambahkan anotasi dengan mudah, meningkatkan kolaborasi dan manajemen dokumen dalam aplikasi Anda.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, dokumen Microsoft Office, gambar, dan banyak lagi.
### Dapatkah saya menyesuaikan tampilan anotasi yang ditambahkan menggunakan GroupDocs.Annotation untuk .NET?
Tentu saja, GroupDocs.Annotation untuk .NET menawarkan opsi penyesuaian yang luas untuk tampilan anotasi, termasuk warna, gaya, dan bentuk.
### Apakah GroupDocs.Annotation untuk .NET menyediakan dukungan untuk layanan penyimpanan cloud?
Ya, GroupDocs.Annotation untuk .NET terintegrasi secara mulus dengan layanan penyimpanan cloud populer, memungkinkan Anda memuat dan menyimpan dokumen dari layanan seperti Dropbox, Google Drive, dan OneDrive.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat menjelajahi fitur GroupDocs.Annotation untuk .NET dengan mengunduh versi uji coba gratis dari [halaman rilis](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan bantuan teknis atau dukungan untuk GroupDocs.Annotation untuk .NET?
Untuk bantuan teknis, pemecahan masalah, atau pertanyaan umum, Anda dapat mengunjungi GroupDocs.Annotation untuk .NET [forum dukungan](https://forum.groupdocs.com/c/annotation/10).