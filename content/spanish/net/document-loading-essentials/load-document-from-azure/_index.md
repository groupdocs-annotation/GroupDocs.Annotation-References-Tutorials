---
title: Cargar documento desde Azure
linktitle: Cargar documento desde Azure
second_title: API GroupDocs.Annotation .NET
description: Aprenda a anotar documentos en .NET usando GroupDocs.Annotation. Tutorial paso a paso para una integración perfecta con Azure Blob Storage.
weight: 11
url: /es/net/document-loading-essentials/load-document-from-azure/
---

# Cargar documento desde Azure

## Introducción
En el ámbito de la gestión de documentos y la colaboración, GroupDocs.Annotation para .NET surge como una solución sólida, que facilita funciones perfectas de anotación y marcado dentro de las aplicaciones .NET. Este tutorial profundiza en las complejidades de aprovechar GroupDocs.Annotation para .NET para anotar documentos y ofrece orientación paso a paso desde los requisitos previos hasta el uso avanzado.
## Requisitos previos
Antes de sumergirse en GroupDocs.Annotation para .NET, asegúrese de tener implementados los siguientes requisitos previos:
1. Instalación de .NET Framework: GroupDocs.Annotation para .NET requiere un entorno de ejecución .NET compatible. Asegúrese de tener .NET Framework instalado en su sistema.
2. Acceso a la biblioteca GroupDocs.Annotation: obtenga acceso a la biblioteca GroupDocs.Annotation para .NET descargándola del sitio web o mediante administradores de paquetes como NuGet.
3. Documento para anotar: prepare el documento (por ejemplo, PDF) que desea anotar. Asegúrese de que se pueda acceder al documento localmente o mediante un servicio de almacenamiento en la nube como Azure Blob Storage.

## Importar espacios de nombres
Para comenzar a anotar documentos usando GroupDocs.Annotation para .NET, importe los espacios de nombres necesarios a su proyecto. Este paso garantiza que tenga acceso a las clases y funcionalidades requeridas.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Cargar documento desde Azure
Para anotar un documento almacenado en Azure Blob Storage, siga estos pasos:
### Paso 1: establecer la ruta de salida
Defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Paso 2: Descargar documento
 Recupere el documento de Azure Blob Storage invocando el`DownloadFile` método.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Lógica de anotación
    annotator.Save(outputPath);
}
```
## Descargar archivos desde Azure Blob Storage
 Para descargar el documento desde Azure Blob Storage, implemente el`DownloadFile` método.
### Paso 1: recuperar el blob
Acceda al contenedor de Azure Blob Storage y recupere el blob deseado.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Paso 2: descargar contenido Blob
Descargue el contenido del blob en un flujo de memoria.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Obtenga el contenedor de Azure Blob Storage
 Para interactuar con Azure Blob Storage, implemente el`GetContainer` método.
### Paso 1: inicializar las credenciales de almacenamiento
Proporcione las credenciales de cuenta necesarias y la información del punto final.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{nombre de cuenta}.blob.core.windows.net/";
```
### Paso 2: crear un cliente Blob
Cree un cliente para interactuar con Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Paso 3: recuperar la referencia del contenedor
Obtenga una referencia al contenedor especificado.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Paso 4: crear contenedor si no existe
Asegúrese de que el contenedor exista y créelo si no.
```csharp
container.CreateIfNotExists();
```

## Conclusión
GroupDocs.Annotation para .NET brinda a los desarrolladores capacidades sólidas de anotación de documentos, integrándose perfectamente en aplicaciones .NET. Si sigue los pasos descritos en este tutorial, podrá aprovechar eficazmente las funcionalidades de GroupDocs.Annotation para anotar documentos almacenados en Azure Blob Storage.
#### Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX y más.
### ¿Se pueden personalizar las anotaciones según requisitos específicos?
Sí, GroupDocs.Annotation ofrece amplias opciones de personalización para las anotaciones, lo que permite a los usuarios modificar la apariencia, el comportamiento y los metadatos.
### ¿GroupDocs.Annotation es adecuado para la anotación colaborativa de documentos?
¡Absolutamente! GroupDocs.Annotation facilita la anotación colaborativa de documentos al permitir que varios usuarios agreguen, editen y revisen anotaciones simultáneamente.
### ¿GroupDocs.Annotation ofrece compatibilidad multiplataforma?
Sí, GroupDocs.Annotation está diseñado para funcionar sin problemas en varias plataformas, incluidas Windows, Linux y macOS.
### ¿Hay soporte técnico disponible para los usuarios de GroupDocs.Annotation?
Sí, GroupDocs brinda soporte técnico integral a través de sus foros y canales de soporte dedicados.