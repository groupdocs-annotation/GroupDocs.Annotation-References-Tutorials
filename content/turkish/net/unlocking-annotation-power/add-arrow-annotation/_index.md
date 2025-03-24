---
title: Belgeye Ok Açıklaması Ekle
linktitle: Belgeye Ok Açıklaması Ekle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation for .NET'i kullanarak belgelerinize ok açıklamalarını nasıl ekleyeceğinizi öğrenin. Belge netliğini ve etkileşimini zahmetsizce geliştirin.
weight: 11
url: /tr/net/unlocking-annotation-power/add-arrow-annotation/
---

# Belgeye Ok Açıklaması Ekle

## giriiş
Bu öğreticide, GroupDocs.Annotation for .NET'i kullanarak belgelerinize ok açıklamaları ekleme sürecinde size yol göstereceğiz. Ok açıklamaları, yönü belirtmek veya bir belgedeki belirli öğeleri belirtmek için kullanışlıdır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  .NET için GroupDocs.Annotation: .NET için GroupDocs.Annotation kitaplığını yükleyin. Şuradan indirebilirsiniz[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio veya tercih edilen herhangi bir IDE dahil, .NET geliştirme için ayarlanmış bir geliştirme ortamına sahip olduğunuzdan emin olun.

## Ad Alanlarını İçe Aktar
Öncelikle, açıklama için gerekli sınıflara ve yöntemlere erişmek için gerekli ad alanlarını içe aktarmanız gerekir.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. Adım: Annotator'ı Başlatın
Giriş belgesi dosya yolunu sağlayarak açıklayıcıyı başlatın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Adım 2: Ok Açıklaması Oluşturun
ArrowAnnotation sınıfının bir örneğini oluşturun ve konum, mesaj, opaklık, kalem rengi, stil, genişlik vb. gibi özelliklerini tanımlayın.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
		}
	};
```
## 3. Adım: Ek Açıklama Ekle
 Ok açıklamasını belgeye şunu kullanarak ekleyin:`Add` açıklamacının yöntemi.
```csharp
	annotator.Add(arrow);
```
## Adım 4: Belgeyi Kaydet
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
	annotator.Save(outputPath);
}
```
## Adım 5: Onayı Görüntüle
Belgenin başarıyla kaydedildiğini gösteren bir onay mesajı görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Artık GroupDocs.Annotation for .NET'i kullanarak belgenize başarıyla bir ok ek açıklaması eklediniz.

## Çözüm
Bu öğreticide, GroupDocs.Annotation for .NET kullanarak belgelere ok ek açıklamaları ekleme sürecini ele aldık. Bu adımları izleyerek belgelerinizi net yön göstergeleriyle geliştirebilir, onları daha bilgilendirici ve ilgi çekici hale getirebilirsiniz.
## SSS'ler
### Ok açıklamasının görünümünü özelleştirebilir miyim?
Evet, tercihlerinize ve belge gereksinimlerinize uyacak şekilde renk, stil, genişlik ve opaklık gibi çeşitli özellikleri özelleştirebilirsiniz.
### GroupDocs.Annotation tüm belge formatlarıyla uyumlu mu?
GroupDocs.Annotation, PDF, DOCX, PPTX, XLSX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs.Annotation'ı kullanarak programlı olarak ek açıklamalar ekleyebilir miyim?
Evet, GroupDocs.Annotation, belgelere ek açıklamaları programlı bir şekilde eklemenize, düzenlemenize ve kaldırmanıza olanak tanıyan API'ler sağlar.
### GroupDocs.Annotation ücretsiz deneme sunuyor mu?
 Evet, GroupDocs.Annotation'ı şu adresten indirerek ücretsiz deneyebilirsiniz:[Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için nereden teknik destek alabilirim?
Teknik destek ve yardım için GroupDocs.Annotation forumunu ziyaret edebilirsiniz.[Burada](https://forum.groupdocs.com/c/annotation/10).