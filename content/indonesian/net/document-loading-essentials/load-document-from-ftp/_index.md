---
title: Muat Dokumen dari FTP
linktitle: Muat Dokumen dari FTP
second_title: GroupDocs.Annotasi .NET API
description: Tingkatkan aplikasi .NET Anda dengan GroupDocs.Annotation untuk anotasi dokumen yang lancar. Tutorial langkah demi langkah disertakan.
weight: 12
url: /id/net/document-loading-essentials/load-document-from-ftp/
---

# Muat Dokumen dari FTP

## Perkenalan
GroupDocs.Annotation for .NET adalah perpustakaan serbaguna yang dirancang untuk memfasilitasi kemampuan anotasi dokumen dalam aplikasi .NET dengan mudah. Baik Anda menangani PDF, dokumen Microsoft Office, gambar, atau format lainnya, pustaka ini menyediakan solusi terpadu untuk menambahkan anotasi, seperti komentar, sorotan, dan bentuk, untuk meningkatkan kolaborasi dan manajemen dokumen.
## Prasyarat
Sebelum masuk ke tutorial, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan tentang C#: Kemahiran dalam bahasa pemrograman C# sangat penting untuk memahami dan mengimplementasikan contoh kode yang disediakan dalam tutorial ini.
2.  GroupDocs.Annotation untuk .NET: Pastikan untuk mengunduh dan menginstal GroupDocs.Annotation untuk .NET dari[tautan unduhan](https://releases.groupdocs.com/annotation/net/). Ikuti petunjuk instalasi untuk mengintegrasikan perpustakaan ke dalam proyek .NET Anda dengan sukses.
## Impor Namespace
Untuk memanfaatkan fungsionalitas GroupDocs.Annotation untuk .NET, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda. Ikuti langkah ini:

Dalam proyek C# Anda, sertakan namespace yang diperlukan di awal file kode Anda:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Sekarang, mari selami proses memuat dokumen dari FTP dan menambahkan anotasi ke dalamnya menggunakan GroupDocs.Annotation untuk .NET.
## Langkah 1: Tentukan Jalur Keluaran
Tentukan jalur keluaran tempat dokumen beranotasi akan disimpan.
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
Tentukan dan tambahkan anotasi yang diinginkan, misalnya anotasi area, ke dokumen.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Langkah 4: Simpan Dokumen Beranotasi
Simpan dokumen beranotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Langkah 5: Ambil File dari FTP
Terapkan metode untuk mengambil file dari server FTP.
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
Hasilkan permintaan FTP untuk mengunduh file.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Langkah 7: Dapatkan File Stream
Ambil aliran file dari respons FTP.
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
Kesimpulannya, GroupDocs.Annotation for .NET memberdayakan pengembang untuk mengintegrasikan fungsi anotasi dokumen ke dalam aplikasi .NET mereka dengan lancar. Dengan mengikuti panduan langkah demi langkah yang diuraikan dalam tutorial ini, Anda dapat memuat dokumen dari FTP secara efisien dan menambahkan anotasi dengan mudah, sehingga meningkatkan kolaborasi dan manajemen dokumen dalam aplikasi Anda.
## FAQ
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
Ya, GroupDocs.Annotation untuk .NET mendukung berbagai format dokumen, termasuk PDF, dokumen Microsoft Office, gambar, dan banyak lagi.
### Bisakah saya menyesuaikan tampilan anotasi yang ditambahkan menggunakan GroupDocs.Annotation untuk .NET?
Tentu saja, GroupDocs.Annotation untuk .NET menawarkan opsi penyesuaian yang luas untuk tampilan anotasi, termasuk warna, gaya, dan bentuk.
### Apakah GroupDocs.Annotation untuk .NET menyediakan dukungan untuk layanan penyimpanan cloud?
Ya, GroupDocs.Annotation untuk .NET terintegrasi secara mulus dengan layanan penyimpanan cloud populer, memungkinkan Anda memuat dan menyimpan dokumen dari layanan seperti Dropbox, Google Drive, dan OneDrive.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?
 Ya, Anda dapat menjelajahi fitur GroupDocs.Annotation untuk .NET dengan mengunduh versi uji coba gratis dari[halaman rilis](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan bantuan teknis atau dukungan untuk GroupDocs.Annotation untuk .NET?
 Untuk bantuan teknis, pemecahan masalah, atau pertanyaan umum, Anda dapat mengunjungi GroupDocs.Annotation untuk .NET[forum dukungan](https://forum.groupdocs.com/c/annotation/10).