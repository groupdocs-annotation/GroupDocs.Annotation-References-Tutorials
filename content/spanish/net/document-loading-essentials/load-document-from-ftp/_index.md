---
"description": "Mejore sus aplicaciones .NET con GroupDocs.Annotation para una anotación de documentos fluida. Incluye tutorial paso a paso."
"linktitle": "Cargar documento desde FTP"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Cargar documento desde FTP"
"url": "/es/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# Cargar documento desde FTP

## Introducción
GroupDocs.Annotation para .NET es una biblioteca versátil diseñada para facilitar la anotación de documentos en aplicaciones .NET. Ya sea que trabaje con archivos PDF, documentos de Microsoft Office, imágenes u otros formatos, esta biblioteca ofrece una solución unificada para agregar anotaciones, como comentarios, resaltados y formas, para mejorar la colaboración y la gestión de documentos.
## Prerrequisitos
Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:
1. Conocimiento de C#: El dominio del lenguaje de programación C# es esencial para comprender e implementar los ejemplos de código proporcionados en este tutorial.
2. GroupDocs.Annotation para .NET: asegúrese de descargar e instalar GroupDocs.Annotation para .NET desde [enlace de descarga](https://releases.groupdocs.com/annotation/net/)Siga las instrucciones de instalación para integrar la biblioteca en su proyecto .NET con éxito.
## Importar espacios de nombres
Para utilizar GroupDocs.Annotation para las funcionalidades de .NET, debe importar los espacios de nombres necesarios a su proyecto de C#. Siga estos pasos:

Dentro de su proyecto C#, incluya los espacios de nombres necesarios al comienzo de su archivo de código:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Ahora, profundicemos en el proceso de cargar un documento desde FTP y agregarle anotaciones usando GroupDocs.Annotation para .NET.
## Paso 1: Definir la ruta de salida
Especifique la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Cargar documento desde FTP
Recupere el documento del servidor FTP utilizando la ruta de archivo proporcionada.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // El código de anotación se agregará aquí
}
```
## Paso 3: Agregar anotación
Defina y agregue la anotación deseada, como una anotación de área, al documento.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Paso 4: Guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Paso 5: Recuperar archivo del FTP
Implemente el método para obtener el archivo del servidor FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Paso 6: Crear solicitud FTP
Generar una solicitud FTP para descargar el archivo.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Paso 7: Obtener flujo de archivos
Recuperar el flujo de archivos de la respuesta FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Conclusión
En conclusión, GroupDocs.Annotation para .NET permite a los desarrolladores integrar fácilmente las funciones de anotación de documentos en sus aplicaciones .NET. Siguiendo la guía paso a paso de este tutorial, podrá cargar documentos desde FTP de forma eficiente y añadir anotaciones fácilmente, optimizando así la colaboración y la gestión de documentos en sus aplicaciones.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
Sí, GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, documentos de Microsoft Office, imágenes y más.
### ¿Puedo personalizar la apariencia de las anotaciones agregadas usando GroupDocs.Annotation para .NET?
Por supuesto, GroupDocs.Annotation para .NET ofrece amplias opciones de personalización para la apariencia de las anotaciones, incluidos colores, estilos y formas.
### ¿GroupDocs.Annotation para .NET proporciona soporte para servicios de almacenamiento en la nube?
Sí, GroupDocs.Annotation para .NET se integra perfectamente con los servicios de almacenamiento en la nube más populares, lo que le permite cargar y guardar documentos de servicios como Dropbox, Google Drive y OneDrive.
### ¿Hay una versión de prueba disponible para GroupDocs.Annotation para .NET?
Sí, puede explorar las características de GroupDocs.Annotation para .NET descargando la versión de prueba gratuita desde [página de lanzamiento](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener asistencia técnica o soporte para GroupDocs.Annotation para .NET?
Para asistencia técnica, resolución de problemas o consultas generales, puede visitar GroupDocs.Annotation para .NET [foro de soporte](https://forum.groupdocs.com/c/annotation/10).