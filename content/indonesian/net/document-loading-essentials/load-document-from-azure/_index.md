---
"description": "Pelajari cara membuat anotasi pada dokumen dalam .NET menggunakan GroupDocs.Annotation. Tutorial langkah demi langkah untuk integrasi yang lancar dengan Azure Blob Storage."
"linktitle": "Muat Dokumen dari Azure"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Muat Dokumen dari Azure"
"url": "/id/net/document-loading-essentials/load-document-from-azure/"
type: docs
"weight": 11
---

# Muat Dokumen dari Azure

## Perkenalan
Dalam bidang manajemen dan kolaborasi dokumen, GroupDocs.Annotation for .NET muncul sebagai solusi yang tangguh, yang memfasilitasi fungsionalitas anotasi dan markup yang lancar dalam aplikasi .NET. Tutorial ini membahas seluk-beluk pemanfaatan GroupDocs.Annotation for .NET untuk membuat anotasi dokumen, dengan menawarkan panduan langkah demi langkah mulai dari prasyarat hingga penggunaan tingkat lanjut.
## Prasyarat
Sebelum menyelami GroupDocs.Annotation untuk .NET, pastikan Anda memiliki prasyarat berikut:
1. Pemasangan .NET Framework: GroupDocs.Annotation untuk .NET memerlukan lingkungan runtime .NET yang kompatibel. Pastikan Anda telah memasang .NET Framework di sistem Anda.
2. Akses ke Pustaka GroupDocs.Annotation: Dapatkan akses ke pustaka GroupDocs.Annotation untuk .NET baik dengan mengunduhnya dari situs web atau melalui pengelola paket seperti NuGet.
3. Dokumen yang Akan Dianotasi: Siapkan dokumen (misalnya, PDF) yang ingin Anda anotasi. Pastikan dokumen tersebut dapat diakses secara lokal atau melalui layanan penyimpanan cloud seperti Azure Blob Storage.

## Mengimpor Ruang Nama
Untuk mulai membuat anotasi dokumen menggunakan GroupDocs.Annotation for .NET, impor namespace yang diperlukan ke dalam proyek Anda. Langkah ini memastikan bahwa Anda memiliki akses ke kelas dan fungsi yang diperlukan.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Muat Dokumen dari Azure
Untuk memberi anotasi pada dokumen yang disimpan di Azure Blob Storage, ikuti langkah-langkah berikut:
### Langkah 1: Tetapkan Jalur Output
Tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Langkah 2: Unduh Dokumen
Ambil dokumen dari Azure Blob Storage dengan memanggil perintah `DownloadFile` metode.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logika Anotasi
    annotator.Save(outputPath);
}
```
## Unduh File dari Azure Blob Storage
Untuk mengunduh dokumen dari Azure Blob Storage, terapkan `DownloadFile` metode.
### Langkah 1: Ambil Blob
Akses kontainer Azure Blob Storage dan ambil blob yang diinginkan.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Langkah 2: Unduh Konten Blob
Mengunduh konten blob ke dalam aliran memori.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Dapatkan Kontainer Penyimpanan Blob Azure
Untuk berinteraksi dengan Azure Blob Storage, terapkan `GetContainer` metode.
### Langkah 1: Inisialisasi Kredensial Penyimpanan
Berikan kredensial akun dan informasi titik akhir yang diperlukan.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{namaakun}.blob.core.windows.net/";
```
### Langkah 2: Buat Klien Blob
Buat klien untuk berinteraksi dengan Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Langkah 3: Ambil Referensi Kontainer
Dapatkan tutorial untuk kontainer yang ditentukan.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Langkah 4: Buat Kontainer jika Tidak Ada
Pastikan wadah tersebut ada, dan buatlah jika belum ada.
```csharp
container.CreateIfNotExists();
```

## Kesimpulan
GroupDocs.Annotation untuk .NET memberdayakan pengembang dengan kemampuan anotasi dokumen yang tangguh, terintegrasi dengan lancar ke dalam aplikasi .NET. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat secara efektif memanfaatkan fungsionalitas GroupDocs.Annotation untuk membuat anotasi pada dokumen yang disimpan di Azure Blob Storage.
#### Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Annotation mendukung berbagai format dokumen, termasuk PDF, DOCX, PPTX, dan banyak lagi.
### Bisakah anotasi disesuaikan menurut persyaratan tertentu?
Ya, GroupDocs.Annotation menawarkan opsi penyesuaian yang luas untuk anotasi, yang memungkinkan pengguna untuk mengubah tampilan, perilaku, dan metadata.
### Apakah GroupDocs.Annotation cocok untuk anotasi dokumen kolaboratif?
Tentu saja! GroupDocs.Annotation memfasilitasi anotasi dokumen secara kolaboratif dengan memungkinkan beberapa pengguna untuk menambahkan, mengedit, dan meninjau anotasi secara bersamaan.
### Apakah GroupDocs.Annotation menawarkan kompatibilitas lintas platform?
Ya, GroupDocs.Annotation dirancang untuk bekerja dengan lancar di berbagai platform, termasuk Windows, Linux, dan macOS.
### Apakah dukungan teknis tersedia untuk pengguna GroupDocs.Annotation?
Ya, GroupDocs menyediakan dukungan teknis yang komprehensif melalui forum dan saluran dukungan khusus.