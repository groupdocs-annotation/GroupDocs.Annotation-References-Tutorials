---
"date": "2025-05-06"
"description": "GroupDocs.Annotation for .NET kullanarak belirli çalışma sayfası sütunlarından özlü ve ilgili belge önizlemelerinin nasıl oluşturulacağını öğrenin. Veri analizi ve BT yönetiminde iş akışlarını kolaylaştırmak için mükemmeldir."
"title": "GroupDocs.Annotation .NET Kullanarak Hedeflenen Excel Sayfası Önizlemeleri Oluşturun"
"url": "/tr/net/document-preview/groupdocs-annotation-net-create-previews-worksheet-columns/"
"weight": 1
---

# GroupDocs.Annotation .NET Kullanarak Hedeflenen Excel Sayfası Önizlemeleri Oluşturun
## Belge Önizleme Kılavuzu
### giriiş
Belirli veri noktalarına odaklanarak belge işlemelerinizin netliğini artırmak mı istiyorsunuz? İster veri analizi araçları oluşturan bir geliştirici, ister belgeleri yöneten bir BT uzmanı veya iş akışlarını kolaylaştırmakla ilgilenen biri olun, hedeflenen belge önizlemeleri zamandan tasarruf sağlayabilir ve verimliliği artırabilir. Bu eğitim, seçili çalışma sayfası sütunlarından önizlemeler oluşturmak için GroupDocs.Annotation for .NET'i kullanma konusunda size rehberlik edecek ve çıktılarınızın özlü ve alakalı olmasını sağlayacaktır.

#### Ne Öğreneceksiniz:
- .NET için GroupDocs.Annotation nasıl kurulur
- Belirtilen çalışma sayfası sütunlarıyla önizlemeler oluşturuluyor
- En iyi çıktı için önizleme seçeneklerini yapılandırma
- Bu özelliğin gerçek dünya senaryolarındaki pratik uygulamaları

Bu çözümü uygulamaya başlamadan önce ihtiyaç duyduğunuz ön koşulları gözden geçirerek başlayalım.
## Ön koşullar
Uygulamaya başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

### Gerekli Kütüphaneler ve Sürümler:
- **GroupDocs.NET için Açıklama**: Sürüm 25.4.0 veya üzeri gereklidir.

### Çevre Kurulum Gereksinimleri:
- .NET Framework veya .NET Core yüklü bir geliştirme ortamı.

### Bilgi Ön Koşulları:
- C# programlamanın temel anlayışı
- .NET'te dosya G/Ç işlemlerine aşinalık
## .NET için GroupDocs.Annotation Kurulumu
Başlamak için GroupDocs.Annotation kütüphanesini yüklemeniz gerekir. Bunu farklı paket yöneticilerini kullanarak nasıl yapabileceğiniz aşağıda açıklanmıştır:

**NuGet Paket Yöneticisi Konsolu**
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET Komut Satırı Arayüzü**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Lisans Alma Adımları:
- **Ücretsiz Deneme**: Deneme sürümünü şu adresten indirin: [GroupDocs web sitesi](https://releases.groupdocs.com/annotation/net/) Özellikleri test etmek için.
- **Geçici Lisans**: Geliştirme sırasında tam erişim için geçici bir lisans edinin [Geçici Lisans Sayfası](https://purchase.groupdocs.com/temporary-license/).
- **Satın almak**: Üretim amaçlı kullanım için, lisans satın alın [GroupDocs Satın Alma Sayfası](https://purchase.groupdocs.com/buy).
### C# ile Temel Başlatma ve Kurulum:
GroupDocs.Annotation for .NET ile çalışmaya başlamak için ortamınızı nasıl ayarlayabileceğinizi aşağıda bulabilirsiniz.
```csharp
using System;
using GroupDocs.Annotation;
// Annotator nesnesini bir belge yolu ile başlatın.
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";
Annotator annotator = new Annotator(inputFilePath);
```
Artık kurulumunuz tamamlandığına göre, belirli çalışma sayfası sütunlarından önizleme oluşturmaya geçelim.
## Uygulama Kılavuzu
Bu kılavuz, belirtilen çalışma sayfası sütunlarıyla belge önizlemeleri oluşturma özelliğini uygulamada size yol gösterecektir. Her bölüm, uygulama sürecinin belirli bir yönüne odaklanır.
### Belirli Çalışma Sayfası Sütunlarından Belge Önizlemeleri Oluşturma
**Genel bakış**Bu özellik, geliştiricilerin yalnızca Excel çalışma sayfasındaki seçili sütunları içeren belge önizlemeleri oluşturmasına olanak tanır ve böylece hem performansı hem de alaka düzeyini artırır.
#### Adım 1: Önizleme Seçeneklerini Tanımlayın
Kurulumunuzu yaparak başlayın `PreviewOptions`. Bu, önizleme dosyalarınızın nasıl ve nereye kaydedileceğini belirler.
```csharp
using System.IO;
using GroupDocs.Annotation.Options;
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY";
PreviewOptions previewOptions = new PreviewOptions(pageNumber => 
    new FileStream(Path.Combine(outputDirectoryPath, $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose());
```
**Açıklama**: : `PreviewOptions` constructor iki temsilci alır. İlki her sayfanın önizleme görüntüsü için dosya yolunu belirtir. İkincisi akışların kullanımdan sonra düzgün bir şekilde atılmasını sağlar.
#### Adım 2: Çalışma Sayfası Sütunlarını Belirleyin
Çalışma sayfanızdan önizlemelere dahil etmek istediğiniz sütunları seçerek bunları ekleyin `WorksheetColumns`.
```csharp
// Sheet1'den belirli sütunları ekleyin.
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1\