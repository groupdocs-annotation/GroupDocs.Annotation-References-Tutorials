---
title: Azure'dan Belge Yükle
linktitle: Azure'dan Belge Yükle
second_title: GroupDocs.Annotation .NET API'si
description: GroupDocs.Annotation'ı kullanarak .NET'te belgelere nasıl açıklama ekleyeceğinizi öğrenin. Azure Blob Depolama ile sorunsuz entegrasyon için adım adım öğretici.
weight: 11
url: /tr/net/document-loading-essentials/load-document-from-azure/
---
## giriiş
Belge yönetimi ve işbirliği alanında, GroupDocs.Annotation for .NET, .NET uygulamaları içindeki kusursuz açıklama ve işaretleme işlevlerini kolaylaştıran sağlam bir çözüm olarak ortaya çıkıyor. Bu eğitimde, belgelere açıklama eklemek için GroupDocs.Annotation for .NET'ten yararlanmanın incelikleri ele alınmakta ve ön koşullardan ileri düzey kullanıma kadar adım adım rehberlik sunulmaktadır.
## Önkoşullar
GroupDocs.Annotation for .NET'e dalmadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
1. .NET Framework kurulumu: GroupDocs.Annotation for .NET, uyumlu bir .NET çalışma zamanı ortamı gerektirir. Sisteminizde .NET Framework'ün kurulu olduğundan emin olun.
2. GroupDocs.Annotation Kitaplığına Erişim: GroupDocs.Annotation for .NET kitaplığına web sitesinden indirerek veya NuGet gibi paket yöneticileri aracılığıyla erişim sağlayın.
3. Açıklama Eklenecek Belge: Açıklama eklemeyi düşündüğünüz belgeyi (örneğin, PDF) hazırlayın. Belgenin yerel olarak veya Azure Blob Depolama gibi bir bulut depolama hizmeti aracılığıyla erişilebilir olduğundan emin olun.

## Ad Alanlarını İçe Aktar
GroupDocs.Annotation for .NET'i kullanarak belgelere açıklama eklemeye başlamak için gerekli ad alanlarını projenize aktarın. Bu adım, gerekli sınıflara ve işlevlere erişmenizi sağlar.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Azure'dan Belge Yükle
Azure Blob Depolama'da depolanan bir belgeye açıklama eklemek için şu adımları izleyin:
### Adım 1: Çıkış Yolunu Ayarlayın
Açıklamalı belgenin kaydedileceği çıkış yolunu tanımlayın.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Adım 2: Belgeyi İndirin
 Çağırarak belgeyi Azure Blob Depolama'dan alın.`DownloadFile` yöntem.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Ek Açıklama Mantığı
    annotator.Save(outputPath);
}
```
## Azure Blob Depolamadan Dosya İndirin
 Belgeyi Azure Blob Depolama'dan indirmek için şunu uygulayın:`DownloadFile` yöntem.
### 1. Adım: Blob'u Alın
Azure Blob Depolama kapsayıcısına erişin ve istenen blobu alın.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 2. Adım: Blob İçeriğini İndirin
Blob içeriğini bir bellek akışına indirin.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Azure Blob Depolama Kapsayıcısını Alın
 Azure Blob Depolama ile etkileşimde bulunmak için şunları uygulayın:`GetContainer` yöntem.
### 1. Adım: Depolama Kimlik Bilgilerini Başlatın
Gerekli hesap kimlik bilgilerini ve uç nokta bilgilerini sağlayın.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### 2. Adım: Blob İstemcisi Oluşturun
Azure Blob Depolama ile etkileşim kurmak için bir istemci oluşturun.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 3. Adım: Kapsayıcı Referansını Alın
Belirtilen kapsayıcıya bir başvuru alın.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 4. Adım: Mevcut Değilse Kapsayıcı Oluşturun
Kapsayıcının mevcut olduğundan emin olun ve yoksa oluşturun.
```csharp
container.CreateIfNotExists();
```

## Çözüm
GroupDocs.Annotation for .NET, geliştiricilere, .NET uygulamalarına sorunsuz bir şekilde entegre olan güçlü belge açıklama yetenekleri sağlar. Bu öğreticide özetlenen adımları izleyerek, Azure Blob Depolama'da depolanan belgelere açıklama eklemek için GroupDocs.Annotation'ın işlevlerinden etkili bir şekilde yararlanabilirsiniz.
#### SSS'ler
### GroupDocs.Annotation for .NET tüm belge formatlarıyla uyumlu mu?
GroupDocs.Annotation, PDF, DOCX, PPTX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### Ek açıklamalar belirli gereksinimlere göre özelleştirilebilir mi?
Evet, GroupDocs.Annotation, ek açıklamalar için kapsamlı özelleştirme seçenekleri sunarak kullanıcıların görünümü, davranışı ve meta verileri değiştirmesine olanak tanır.
### GroupDocs.Annotation ortak belge açıklamasına uygun mu?
Kesinlikle! GroupDocs.Annotation, birden fazla kullanıcının aynı anda ek açıklamalar eklemesine, düzenlemesine ve incelemesine olanak tanıyarak belgeye ortak açıklama eklemeyi kolaylaştırır.
### GroupDocs.Annotation platformlar arası uyumluluk sunuyor mu?
Evet, GroupDocs.Annotation, Windows, Linux ve macOS dahil olmak üzere çeşitli platformlarda sorunsuz çalışacak şekilde tasarlanmıştır.
### GroupDocs.Annotation kullanıcıları için teknik destek mevcut mu?
Evet, GroupDocs, forumları ve özel destek kanalları aracılığıyla kapsamlı teknik destek sağlar.