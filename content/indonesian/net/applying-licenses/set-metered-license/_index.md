---
"description": "Pelajari cara menyiapkan lisensi terukur untuk GroupDocs.Annotation .NET untuk penggunaan sumber daya dan kemampuan anotasi dokumen di aplikasi .NET Anda."
"linktitle": "Tetapkan Lisensi Terukur"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Tetapkan Lisensi Terukur"
"url": "/id/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Tetapkan Lisensi Terukur

## Perkenalan
GroupDocs.Annotation untuk .NET adalah pustaka canggih yang memungkinkan pengembang untuk menambahkan kemampuan anotasi dokumen ke aplikasi .NET mereka dengan mudah. Baik Anda sedang membangun sistem manajemen dokumen, platform kolaborasi, atau aplikasi apa pun yang melibatkan peninjauan dan penandaan dokumen, GroupDocs.Annotation untuk .NET menyediakan serangkaian alat yang lengkap untuk menyederhanakan proses.
Dalam tutorial ini, kita akan mendalami proses pengaturan lisensi terukur untuk GroupDocs.Annotation .NET. Lisensi terukur memungkinkan Anda membayar hanya untuk sumber daya yang Anda gunakan, menjadikannya solusi hemat biaya untuk proyek dalam skala apa pun. Dengan mengikuti langkah-langkah yang diuraikan di bawah ini, Anda akan dapat mengintegrasikan GroupDocs.Annotation ke dalam aplikasi .NET Anda dengan lancar sambil mengoptimalkan penggunaan sumber daya dan mempertahankan kontrol anggaran.
## Prasyarat
Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:
1. GroupDocs.Annotation untuk Pustaka .NET: Unduh pustaka dari [situs web](https://releases.groupdocs.com/annotation/net/).
2. Akses ke Akun GroupDocs: Anda memerlukan akun GroupDocs untuk mendapatkan kunci publik dan pribadi yang diperlukan untuk menyiapkan lisensi terukur. Jika Anda belum memiliki akun, Anda dapat mendaftar untuk uji coba gratis [Di Sini](https://releases.groupdocs.com/).
3. Pemahaman Dasar tentang C# dan .NET Framework: Keakraban dengan bahasa pemrograman C# dan .NET Framework akan bermanfaat dalam menerapkan langkah-langkah yang diuraikan dalam tutorial ini.

## Mengimpor Ruang Nama
Untuk memulai, pastikan untuk mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Namespace ini penting untuk berinteraksi dengan fungsionalitas GroupDocs.Annotation.
```csharp
using System;
```
## Langkah 1: Dapatkan Kunci Publik dan Pribadi
Sebelum menyiapkan lisensi terukur, Anda perlu memperoleh kunci publik dan privat dari dasbor akun GroupDocs Anda.
1. Masuk ke akun GroupDocs Anda.
2. Navigasi ke bagian manajemen lisensi.
3. Salin kunci publik dan privat Anda yang disediakan oleh GroupDocs.
## Langkah 2: Tetapkan Lisensi Terukur
Setelah Anda memperoleh kunci publik dan pribadi, Anda dapat mengatur lisensi terukur di aplikasi .NET Anda.
```csharp
string publicKey = "*****"; // Ganti ***** dengan kunci publik Anda
string privateKey = "*****"; // Ganti ***** dengan kunci pribadi Anda
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Kesimpulan
Kesimpulannya, menyiapkan lisensi terukur untuk GroupDocs.Annotation .NET adalah proses mudah yang memastikan pemanfaatan sumber daya yang efisien dan efektivitas biaya untuk proyek anotasi dokumen Anda. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat mengintegrasikan GroupDocs.Annotation ke dalam aplikasi .NET Anda dengan lancar dan meningkatkan kemampuan kolaborasi dan peninjauan dokumen.
## Pertanyaan yang Sering Diajukan
### Dapatkah saya menggunakan GroupDocs.Annotation untuk .NET dalam proyek komersial?
Ya, GroupDocs.Annotation untuk .NET dapat digunakan dalam proyek komersial dan nonkomersial. Namun, Anda perlu memperoleh lisensi yang sesuai berdasarkan persyaratan proyek Anda.
### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Annotation untuk .NET?
Ya, Anda dapat memanfaatkan uji coba gratis GroupDocs.Annotation untuk .NET dengan mengunjungi [tautan ini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Annotation untuk .NET?
Anda dapat mencari dukungan teknis dengan mengunjungi forum GroupDocs [Di Sini](https://forum.groupdocs.com/c/annotation/10).
### Apakah ada pilihan lisensi sementara yang tersedia?
Ya, Anda dapat memperoleh lisensi sementara dari GroupDocs untuk penggunaan jangka pendek atau tujuan evaluasi. Kunjungi [tautan ini](https://purchase.groupdocs.com/temporary-license/) untuk informasi lebih lanjut.
### Dapatkah saya menyesuaikan fitur anotasi menurut persyaratan proyek saya?
Ya, GroupDocs.Annotation untuk .NET menawarkan opsi penyesuaian yang luas, yang memungkinkan Anda menyesuaikan fitur anotasi agar sesuai dengan kebutuhan proyek spesifik Anda.