---
"date": "2025-05-06"
"description": "Pelajari cara membuat anotasi pada file PDF secara online menggunakan GroupDocs.Annotation for .NET. Sederhanakan proses peninjauan dokumen Anda dengan teknik anotasi yang efisien."
"title": "Cara Membuat Anotasi pada PDF dari URL Menggunakan GroupDocs.Annotation untuk .NET"
"url": "/id/net/annotation-management/annotate-pdfs-online-groupdocs-annotation-net/"
"weight": 1
---

# Cara Membuat Anotasi pada PDF dari URL Menggunakan GroupDocs.Annotation untuk .NET

## Perkenalan

Dalam lanskap digital saat ini, kemampuan untuk membuat anotasi dokumen secara daring sangat penting untuk kolaborasi dan manajemen alur kerja yang efektif. Baik Anda seorang pengembang atau organisasi yang ingin meningkatkan proses peninjauan dokumen, membuat anotasi PDF langsung dari URL dapat menghemat waktu dan sumber daya. Tutorial ini memandu Anda menggunakan GroupDocs.Annotation untuk .NET—pustaka canggih yang dirancang untuk membuat anotasi berbagai jenis file, termasuk PDF, secara lancar.

**Apa yang Akan Anda Pelajari:**
- Memuat dokumen dari URL jarak jauh
- Beri anotasi pada file PDF dengan anotasi tertentu seperti anotasi area
- Siapkan GroupDocs.Annotation di lingkungan .NET

Mari kita bahas prasyarat yang dibutuhkan untuk memulai perjalanan ini!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

### Pustaka dan Ketergantungan yang Diperlukan
- **GroupDocs.Annotation untuk .NET**Pastikan proyek Anda menyertakan versi 25.4.0 atau yang lebih baru.
  

### Persyaratan Pengaturan Lingkungan
- Lingkungan pengembangan yang mendukung .NET (seperti Visual Studio).
- Akses internet untuk mengunduh paket yang diperlukan.

### Prasyarat Pengetahuan
- Pemahaman dasar tentang pemrograman C# dan .NET.
- Kemampuan menggunakan NuGet untuk manajemen paket bermanfaat namun tidak diwajibkan.

## Menyiapkan GroupDocs.Annotation untuk .NET

Untuk mulai membuat anotasi pada PDF dari URL, pertama-tama Anda perlu menyiapkan GroupDocs.Annotation di lingkungan pengembangan Anda. Berikut caranya:

**Konsol Pengelola Paket NuGet**

```bash
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.KLIK NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Akuisisi Lisensi

GroupDocs menawarkan uji coba gratis untuk memulai. Anda juga dapat meminta lisensi sementara atau membeli lisensi untuk penggunaan jangka panjang.

- **Uji Coba Gratis**:Ideal untuk pengujian awal.
- **Lisensi Sementara**: Untuk evaluasi lebih lanjut tanpa batasan.
- **Pembelian**: Dapatkan akses dan dukungan penuh.

### Inisialisasi Dasar

Berikut ini cara Anda dapat menginisialisasi GroupDocs.Annotation di aplikasi C# Anda:

```csharp
using GroupDocs.Annotation;

// Inisialisasi anotator dengan aliran atau jalur file
Annotator annotator = new Annotator("input.pdf");
```

Pengaturan sederhana ini memungkinkan Anda mulai menggunakan fungsionalitas GroupDocs.Annotation.

## Panduan Implementasi

### Memuat Dokumen dari URL

#### Ringkasan

Langkah pertama adalah memuat dokumen dari URL jarak jauh. Kemampuan ini memungkinkan pemrosesan file secara langsung tanpa memerlukan penyimpanan lokal, sehingga memudahkan aplikasi dan kolaborasi berbasis cloud.

#### Langkah-langkah Implementasi

**1. Buat Permintaan Web**

```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
WebRequest request = WebRequest.Create(url);
```

Baris ini membuat permintaan HTTP untuk mengakses URL yang ditentukan.

**2. Dapatkan dan Konversi Aliran Respons**

```csharp
private static Stream GetRemoteFile(string url)
{
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}

private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream); // Salin data ke aliran memori
    fileStream.Position = 0; // Atur ulang untuk membaca
    return fileStream;
}
```

Proses ini mengubah respons web menjadi aliran file lokal yang dapat digunakan oleh GroupDocs.Annotation.

### Menambahkan Anotasi ke Dokumen

#### Ringkasan

Sekarang dokumen Anda telah dimuat, Anda dapat menambahkan anotasi seperti anotasi area untuk menyorot bagian atau catatan tertentu.

#### Langkah-langkah Implementasi

**1. Muat Dokumen**

```csharp
using (Annotator annotator = new Annotator(GetRemoteFile("YOUR_DOCUMENT_DIRECTORY/input.pdf")))
{
    // Lanjutkan dengan langkah anotasi
}
```

**2. Membuat dan Menambahkan Anotasi Area**

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Tentukan dimensi persegi panjang
    BackgroundColor = 65535, // Mengatur warna latar belakang
};

annotator.Add(area); // Tambahkan anotasi ke dokumen
```

**3. Simpan Dokumen Beranotasi**

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY\