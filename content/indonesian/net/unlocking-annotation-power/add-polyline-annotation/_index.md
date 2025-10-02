---
"description": "Pelajari cara menambahkan anotasi polyline ke dokumen menggunakan GroupDocs.Annotation for .NET. Tingkatkan kolaborasi dan proses peninjauan dokumen dengan mudah."
"linktitle": "Tambahkan Anotasi Polyline ke Dokumen"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tambahkan Anotasi Polyline ke Dokumen"
"url": "/id/net/unlocking-annotation-power/add-polyline-annotation/"
type: docs
"weight": 18
---

# Tambahkan Anotasi Polyline ke Dokumen

## Perkenalan
GroupDocs.Annotation untuk .NET adalah alat canggih yang memungkinkan pengembang untuk membuat anotasi dokumen PDF dan Microsoft Office secara terprogram. Di antara fitur-fiturnya adalah kemampuan untuk menambahkan anotasi polyline ke dokumen, yang meningkatkan kolaborasi dan proses peninjauan dokumen.
## Prasyarat
Sebelum melanjutkan tutorial ini, pastikan Anda memiliki hal berikut:
- Visual Studio terinstal di sistem Anda.
- Pengetahuan dasar tentang bahasa pemrograman C#.
- GroupDocs.Annotation untuk pustaka .NET telah terpasang. Anda dapat mengunduhnya dari [Di Sini](https://releases.groupdocs.com/annotation/net/).

## Mengimpor Ruang Nama
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Langkah 1: Tentukan Jalur Output
Pertama, tentukan jalur keluaran tempat dokumen yang diberi anotasi akan disimpan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Langkah 2: Inisialisasi Anotator
Inisialisasi anotator dengan memberikan nama dokumen masukan.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Langkah 3: Buat Objek Anotasi Polyline
Buat objek anotasi polyline dan atur propertinya seperti posisi, pesan, opasitas, warna pena, gaya pena, dan lebar pena.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Langkah 4: Tambahkan Anotasi Polyline
Tambahkan anotasi polyline ke dokumen menggunakan objek anotator.
```csharp
annotator.Add(polyline);
```
## Langkah 5: Simpan Dokumen
Simpan dokumen yang diberi anotasi ke jalur keluaran yang ditentukan.
```csharp
annotator.Save(outputPath);
```
## Langkah 6: Menampilkan Pesan Sukses
Menampilkan pesan yang mengonfirmasi keberhasilan penyimpanan dokumen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menambahkan anotasi polyline ke dokumen menggunakan GroupDocs.Annotation for .NET. Fitur ini meningkatkan kolaborasi dan proses peninjauan dokumen, sehingga memudahkan pengguna untuk mengomunikasikan umpan balik dan saran secara efektif.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua format dokumen?
GroupDocs.Annotation untuk .NET mendukung format dokumen populer seperti PDF dan format Microsoft Office termasuk Word, Excel, dan PowerPoint.
### Bisakah saya menyesuaikan tampilan anotasi?
Ya, Anda dapat menyesuaikan berbagai properti anotasi seperti warna, opasitas, gaya, dan lebar agar sesuai dengan kebutuhan Anda.
### Apakah GroupDocs.Annotation untuk .NET menawarkan uji coba gratis?
Ya, Anda dapat memanfaatkan uji coba gratis GroupDocs.Annotation untuk .NET dengan mengunjungi [tautan ini](https://releases.groupdocs.com/).
### Di mana saya dapat menemukan dokumentasi untuk GroupDocs.Annotation untuk .NET?
Anda dapat menemukan dokumentasi untuk GroupDocs.Annotation untuk .NET [Di Sini](https://tutorials.groupdocs.com/annotation/net/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan GroupDocs.Annotation untuk .NET?
Anda bisa mendapatkan dukungan dengan mengunjungi forum GroupDocs.Annotation [Di Sini](https://forum.groupdocs.com/c/annotation/10).