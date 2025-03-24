---
title: Muat Dokumen dari Disk Lokal
linktitle: Muat Dokumen dari Disk Lokal
second_title: GroupDocs.Annotasi .NET API
description: Buka kekuatan anotasi dokumen dengan GroupDocs.Annotation untuk .NET. Integrasikan fitur anotasi dengan mulus ke dalam aplikasi .NET Anda.
weight: 13
url: /id/net/document-loading-essentials/load-document-from-local-disk/
---

# Muat Dokumen dari Disk Lokal

## Perkenalan
Membuka potensi anotasi dokumen tidak pernah semudah ini dengan GroupDocs.Annotation untuk .NET. Alat canggih ini memberdayakan pengembang untuk mengintegrasikan fitur anotasi yang kuat dengan lancar ke dalam aplikasi .NET mereka. Dalam panduan komprehensif ini, kami akan memandu Anda melalui proses memanfaatkan GroupDocs.Annotation untuk .NET untuk membuat anotasi dokumen langkah demi langkah. Baik Anda seorang pengembang berpengalaman atau baru memulai, tutorial ini akan membekali Anda dengan pengetahuan untuk meningkatkan kolaborasi dokumen dan menyederhanakan alur kerja Anda.
## Prasyarat
Sebelum mendalami anotasi dokumen dengan GroupDocs.Annotation untuk .NET, pastikan Anda memiliki prasyarat berikut:
1. Pengetahuan Dasar C#: Keakraban dengan dasar-dasar bahasa pemrograman C# sangat penting.
2. Instalasi GroupDocs.Annotation untuk .NET: Unduh dan instal GroupDocs.Annotation untuk .NET dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
3. Lingkungan Pengembangan: Siapkan lingkungan pengembangan dengan Visual Studio atau IDE apa pun yang kompatibel.

## Impor Namespace
Untuk mulai membuat anotasi dokumen dengan GroupDocs.Annotation untuk .NET, impor namespace yang diperlukan ke dalam proyek Anda:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Langkah 1: Muat Dokumen dari Disk Lokal
Pertama, Anda perlu memuat dokumen dari disk lokal Anda. Gunakan cuplikan kode berikut:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Langkah 2: Tentukan Area Anotasi
Selanjutnya, tentukan area anotasi. Dalam contoh ini, kita akan membuat AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Langkah 3: Simpan Dokumen dengan Anotasi
Setelah memberi anotasi pada dokumen, simpan dengan anotasi:
```csharp
    annotator.Save(outputPath);
}
```
## Langkah 4: Tampilkan Pesan Sukses
Terakhir, tampilkan pesan sukses dengan jalur keluaran:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Kesimpulannya, GroupDocs.Annotation untuk .NET memberikan solusi kuat untuk mengintegrasikan kemampuan anotasi dokumen ke dalam aplikasi .NET Anda. Dengan mengikuti panduan langkah demi langkah ini, Anda dapat dengan mudah membuat anotasi pada dokumen dan meningkatkan kolaborasi dalam proyek Anda.
## FAQ
### Bisakah saya mencoba GroupDocs.Annotation untuk .NET sebelum membeli?
 Ya, Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Annotation untuk .NET?
 Anda dapat mengakses dokumentasinya[Di Sini](https://tutorials.groupdocs.com/annotation/net/).
### Bagaimana saya bisa mendapatkan lisensi sementara untuk GroupDocs.Annotation untuk .NET?
 Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Apakah dukungan tersedia untuk GroupDocs.Annotation untuk .NET?
 Ya, Anda dapat menemukan dukungan di forum GroupDocs[Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Di mana saya dapat membeli GroupDocs.Annotation untuk .NET?
 Anda dapat membeli GroupDocs.Annotation untuk .NET[Di Sini](https://purchase.groupdocs.com/buy).