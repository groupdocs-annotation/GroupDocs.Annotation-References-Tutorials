---
title: Belgeyi Yerel Diskten Yükle
linktitle: Belgeyi Yerel Diskten Yükle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET ile belgeye açıklama eklemenin gücünün kilidini açın. Ek açıklama özelliklerini .NET uygulamalarınıza sorunsuz bir şekilde entegre edin.
type: docs
weight: 13
url: /tr/net/document-loading-essentials/load-document-from-local-disk/
---
## giriiş
GroupDocs.Annotation for .NET ile belgeye açıklama eklemenin potansiyelini açığa çıkarmak hiç bu kadar kolay olmamıştı. Bu güçlü araç, geliştiricilerin sağlam açıklama özelliklerini .NET uygulamalarına sorunsuz bir şekilde entegre etmelerine olanak tanır. Bu kapsamlı kılavuzda, belgelere adım adım açıklama eklemek için GroupDocs.Annotation for .NET'ten yararlanma sürecinde size yol göstereceğiz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu eğitim sizi belgelerde işbirliğini geliştirecek ve iş akışınızı kolaylaştıracak bilgilerle donatacaktır.
## Önkoşullar
GroupDocs.Annotation for .NET ile belge açıklamalarına dalmadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Temel C# Bilgisi: C# programlama dilinin temellerine aşina olmak çok önemlidir.
2. GroupDocs.Annotation for .NET kurulumu: GroupDocs.Annotation for .NET'i şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/annotation/net/).
3. Geliştirme Ortamı: Visual Studio veya uyumlu herhangi bir IDE ile bir geliştirme ortamı kurun.

## Ad Alanlarını İçe Aktar
GroupDocs.Annotation for .NET ile belgelere açıklama eklemeye başlamak için gerekli ad alanlarını projenize aktarın:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 1. Adım: Belgeyi Yerel Diskten Yükleyin
Öncelikle belgeyi yerel diskinizden yüklemeniz gerekir. Aşağıdaki kod parçacığını kullanın:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Adım 2: Ek Açıklama Alanını Tanımlayın
Daha sonra ek açıklama alanını tanımlayın. Bu örnekte bir Alan Açıklaması oluşturacağız:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## 3. Adım: Belgeyi Ek Açıklamalarla Kaydetme
Belgeye açıklama ekledikten sonra onu ek açıklamalarla birlikte kaydedin:
```csharp
    annotator.Save(outputPath);
}
```
## Adım 4: Başarı Mesajını Görüntüleyin
Son olarak, çıktı yolunu içeren bir başarı mesajı görüntüleyin:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm
Sonuç olarak, GroupDocs.Annotation for .NET, belge açıklama yeteneklerini .NET uygulamalarınıza entegre etmek için güçlü bir çözüm sağlar. Bu adım adım kılavuzu izleyerek belgelere zahmetsizce açıklama ekleyebilir ve projelerinizde işbirliğini geliştirebilirsiniz.
## SSS'ler
### Satın almadan önce GroupDocs.Annotation for .NET'i deneyebilir miyim?
 Evet, ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET belgelerini nerede bulabilirim?
 Dokümantasyona ulaşabilirsiniz[Burada](https://reference.groupdocs.com/annotation/net/).
### GroupDocs.Annotation for .NET için nasıl geçici lisans alabilirim?
 adresinden geçici lisans alabilirsiniz.[Burada](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Annotation for .NET için destek mevcut mu?
 Evet, GroupDocs forumunda destek bulabilirsiniz[Burada](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET'i nereden satın alabilirim?
 .NET için GroupDocs.Annotation'ı satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy).