---
"description": "GroupDocs.Annotation for .NET'i kullanarak belgelerinize ok açıklamaları eklemeyi öğrenin. Belge netliğini ve etkileşimini zahmetsizce artırın."
"linktitle": "Belgeye Ok Açıklaması Ekle"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Belgeye Ok Açıklaması Ekle"
"url": "/tr/net/unlocking-annotation-power/add-arrow-annotation/"
"weight": 11
---

# Belgeye Ok Açıklaması Ekle

## giriiş
Bu eğitimde, .NET için GroupDocs.Annotation'ı kullanarak belgelerinize ok ek açıklamaları ekleme sürecinde size rehberlik edeceğiz. Ok ek açıklamaları, bir belgedeki yönü belirtmek veya belirli öğeleri işaret etmek için kullanışlıdır.
## Ön koşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation kütüphanesini .NET için yükleyin. Bunu şu adresten indirebilirsiniz: [Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Visual Studio veya tercih ettiğiniz herhangi bir IDE dahil olmak üzere .NET geliştirme için bir geliştirme ortamı kurduğunuzdan emin olun.

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
## Adım 1: Annotator'ı Başlatın
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
## Adım 3: Açıklama Ekle
Belgeye ok açıklamasını eklemek için şunu kullanın: `Add` açıklayıcının yöntemi.
```csharp
	annotator.Add(arrow);
```
## Adım 4: Belgeyi Kaydedin
Açıklamalı belgeyi belirtilen çıktı yoluna kaydedin.
```csharp
	annotator.Save(outputPath);
}
```
## Adım 5: Onay Ekranı
Belgenin başarıyla kaydedildiğini belirten bir onay mesajı görüntüleyin.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Artık GroupDocs.Annotation for .NET'i kullanarak belgenize başarıyla bir ok ek açıklaması eklediniz.

## Çözüm
Bu eğitimde, GroupDocs.Annotation for .NET kullanarak belgelere ok açıklamaları ekleme sürecini ele aldık. Bu adımları izleyerek, belgelerinizi net yön göstergeleriyle geliştirebilir, onları daha bilgilendirici ve ilgi çekici hale getirebilirsiniz.
## SSS
### Ok açıklamasının görünümünü özelleştirebilir miyim?
Evet, renk, stil, genişlik ve opaklık gibi çeşitli özellikleri kendi öğreticilerinize ve belge gereksinimlerinize uyacak şekilde özelleştirebilirsiniz.
### GroupDocs.Annotation tüm belge formatlarıyla uyumlu mudur?
GroupDocs.Annotation, PDF, DOCX, PPTX, XLSX ve daha fazlası dahil olmak üzere çok çeşitli belge biçimlerini destekler.
### GroupDocs.Annotation'ı kullanarak program aracılığıyla ek açıklamalar ekleyebilir miyim?
Evet, GroupDocs.Annotation, belgelere programlı olarak açıklama eklemenize, düzenlemenize ve kaldırmanıza olanak tanıyan API'ler sağlar.
### GroupDocs.Annotation ücretsiz deneme sunuyor mu?
Evet, GroupDocs.Annotation'ı şu adresten indirerek ücretsiz deneyebilirsiniz: [Burada](https://releases.groupdocs.com/).
### GroupDocs.Annotation için teknik desteği nereden alabilirim?
Teknik destek ve yardım için GroupDocs.Annotation forumunu ziyaret edebilirsiniz [Burada](https://forum.groupdocs.com/c/annotation/10).