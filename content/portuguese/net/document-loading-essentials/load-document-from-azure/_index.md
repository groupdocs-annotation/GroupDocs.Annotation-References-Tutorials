---
title: Carregar documento do Azure
linktitle: Carregar documento do Azure
second_title: API GroupDocs.Annotation .NET
description: Aprenda como anotar documentos em .NET usando GroupDocs.Annotation. Tutorial passo a passo para integração perfeita com o Azure Blob Storage.
type: docs
weight: 11
url: /pt/net/document-loading-essentials/load-document-from-azure/
---
## Introdução
No domínio do gerenciamento e colaboração de documentos, o GroupDocs.Annotation for .NET surge como uma solução robusta, facilitando funcionalidades contínuas de anotação e marcação em aplicativos .NET. Este tutorial investiga as complexidades de aproveitar o GroupDocs.Annotation for .NET para anotar documentos, oferecendo orientação passo a passo, desde os pré-requisitos até o uso avançado.
## Pré-requisitos
Antes de mergulhar no GroupDocs.Annotation for .NET, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Instalação do .NET Framework: GroupDocs.Annotation for .NET requer um ambiente de tempo de execução .NET compatível. Certifique-se de ter o .NET Framework instalado em seu sistema.
2. Acesso à biblioteca GroupDocs.Annotation: Obtenha acesso à biblioteca GroupDocs.Annotation for .NET baixando-a do site ou por meio de gerenciadores de pacotes como NuGet.
3. Documento para anotar: Prepare o documento (por exemplo, PDF) que você pretende anotar. Certifique-se de que o documento esteja acessível localmente ou por meio de um serviço de armazenamento em nuvem como o Azure Blob Storage.

## Importar namespaces
Para começar a anotar documentos usando GroupDocs.Annotation for .NET, importe os namespaces necessários para o seu projeto. Esta etapa garante que você tenha acesso às classes e funcionalidades necessárias.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Carregar documento do Azure
Para anotar um documento armazenado no Armazenamento de Blobs do Azure, siga estas etapas:
### Etapa 1: definir caminho de saída
Defina o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Etapa 2: baixar o documento
 Recupere o documento do Azure Blob Storage invocando o`DownloadFile` método.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Lógica de anotação
    annotator.Save(outputPath);
}
```
## Baixar arquivo do armazenamento de Blobs do Azure
 Para baixar o documento do Azure Blob Storage, implemente o`DownloadFile` método.
### Etapa 1: recuperar o blob
Acesse o contêiner do Azure Blob Storage e recupere o blob desejado.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Etapa 2: baixar o conteúdo do blob
Baixe o conteúdo do blob em um fluxo de memória.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Obtenha o contêiner de armazenamento de blobs do Azure
 Para interagir com o Azure Blob Storage, implemente o`GetContainer` método.
### Etapa 1: inicializar credenciais de armazenamento
Forneça as credenciais de conta e informações de endpoint necessárias.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{nomedaconta}.blob.core.windows.net/";
```
### Etapa 2: criar cliente Blob
Crie um cliente para interagir com o Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Etapa 3: recuperar a referência do contêiner
Obtenha uma referência ao contêiner especificado.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Etapa 4: criar contêiner se não existir
Certifique-se de que o contêiner exista e, caso contrário, crie-o.
```csharp
container.CreateIfNotExists();
```

## Conclusão
GroupDocs.Annotation for .NET capacita os desenvolvedores com recursos robustos de anotação de documentos, integrando-se perfeitamente aos aplicativos .NET. Seguindo as etapas descritas neste tutorial, você pode aproveitar efetivamente as funcionalidades do GroupDocs.Annotation para anotar documentos armazenados no Azure Blob Storage.
#### Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
GroupDocs.Annotation oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, PPTX e muito mais.
### As anotações podem ser personalizadas de acordo com requisitos específicos?
Sim, GroupDocs.Annotation oferece amplas opções de personalização para anotações, permitindo aos usuários modificar a aparência, o comportamento e os metadados.
### O GroupDocs.Annotation é adequado para anotação colaborativa de documentos?
Absolutamente! GroupDocs.Annotation facilita a anotação colaborativa de documentos, permitindo que vários usuários adicionem, editem e revisem anotações simultaneamente.
### O GroupDocs.Annotation oferece compatibilidade entre plataformas?
Sim, GroupDocs.Annotation foi projetado para funcionar perfeitamente em várias plataformas, incluindo Windows, Linux e macOS.
### O suporte técnico está disponível para usuários do GroupDocs.Annotation?
Sim, o GroupDocs fornece suporte técnico abrangente por meio de fóruns e canais de suporte dedicados.