---
"description": "Aprenda a anotar documentos en .NET con GroupDocs.Annotation. Tutorial paso a paso para una integración perfecta con Azure Blob Storage."
"linktitle": "Cargar documento desde Azure"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Cargar documento desde Azure"
"url": "/es/net/document-loading-essentials/load-document-from-azure/"
type: docs
"weight": 11
---

# Cargar documento desde Azure

## Introducción
En el ámbito de la gestión y colaboración documental, GroupDocs.Annotation para .NET se presenta como una solución robusta que facilita la anotación y el marcado sin interrupciones en aplicaciones .NET. Este tutorial profundiza en los detalles del uso de GroupDocs.Annotation para .NET para anotar documentos, ofreciendo una guía paso a paso, desde los requisitos previos hasta el uso avanzado.
## Prerrequisitos
Antes de sumergirse en GroupDocs.Annotation para .NET, asegúrese de tener los siguientes requisitos previos:
1. Instalación de .NET Framework: GroupDocs.Annotation para .NET requiere un entorno de ejecución .NET compatible. Asegúrese de tener .NET Framework instalado en su sistema.
2. Acceso a la biblioteca GroupDocs.Annotation: obtenga acceso a la biblioteca GroupDocs.Annotation para .NET descargándola del sitio web o a través de administradores de paquetes como NuGet.
3. Documento para anotar: Prepare el documento (p. ej., PDF) que desea anotar. Asegúrese de que sea accesible localmente o mediante un servicio de almacenamiento en la nube como Azure Blob Storage.

## Importar espacios de nombres
Para empezar a anotar documentos con GroupDocs.Annotation para .NET, importe los espacios de nombres necesarios a su proyecto. Este paso garantiza el acceso a las clases y funcionalidades necesarias.
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
### Paso 1: Establecer la ruta de salida
Define la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Paso 2: Descargar documento
Recupere el documento de Azure Blob Storage invocando el comando `DownloadFile` método.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Lógica de anotación
    annotator.Save(outputPath);
}
```
## Descargar archivo desde Azure Blob Storage
Para descargar el documento desde Azure Blob Storage, implemente el `DownloadFile` método.
### Paso 1: Recuperar Blob
Acceda al contenedor de Azure Blob Storage y recupere el blob deseado.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Paso 2: Descargar el contenido del blob
Descargue el contenido del blob en un flujo de memoria.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Obtener un contenedor de almacenamiento de blobs de Azure
Para interactuar con Azure Blob Storage, implemente el `GetContainer` método.
### Paso 1: Inicializar las credenciales de almacenamiento
Proporcione las credenciales de cuenta y la información del punto final necesarias.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{nombreDeCuenta}.blob.core.windows.net/";
```
### Paso 2: Crear un cliente Blob
Cree un cliente para interactuar con Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Paso 3: Recuperar la referencia del contenedor
Obtenga tutoriales para el contenedor especificado.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Paso 4: Crear contenedor si no existe
Asegúrese de que el contenedor exista y créelo si no es así.
```csharp
container.CreateIfNotExists();
```

## Conclusión
GroupDocs.Annotation para .NET ofrece a los desarrolladores sólidas funciones de anotación de documentos, integrándose a la perfección en aplicaciones .NET. Siguiendo los pasos descritos en este tutorial, podrá aprovechar eficazmente las funcionalidades de GroupDocs.Annotation para anotar documentos almacenados en Azure Blob Storage.
#### Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX y más.
### ¿Se pueden personalizar las anotaciones según requisitos específicos?
Sí, GroupDocs.Annotation ofrece amplias opciones de personalización para las anotaciones, lo que permite a los usuarios modificar la apariencia, el comportamiento y los metadatos.
### ¿GroupDocs.Annotation es adecuado para la anotación colaborativa de documentos?
¡Por supuesto! GroupDocs.Annotation facilita la anotación colaborativa de documentos, permitiendo que varios usuarios agreguen, editen y revisen anotaciones simultáneamente.
### ¿GroupDocs.Annotation ofrece compatibilidad entre plataformas?
Sí, GroupDocs.Annotation está diseñado para funcionar sin problemas en varias plataformas, incluidas Windows, Linux y macOS.
### ¿Hay soporte técnico disponible para los usuarios de GroupDocs.Annotation?
Sí, GroupDocs proporciona soporte técnico integral a través de sus foros y canales de soporte dedicados.