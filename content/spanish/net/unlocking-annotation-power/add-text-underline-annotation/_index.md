---
"description": "Aprenda a añadir anotaciones de subrayado de texto a documentos con GroupDocs.Annotation para .NET. Mejore la colaboración y la comunicación sin esfuerzo."
"linktitle": "Agregar anotación de subrayado de texto al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de subrayado de texto al documento"
"url": "/es/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# Agregar anotación de subrayado de texto al documento

## Introducción
En este tutorial, explicaremos el proceso de agregar una anotación de subrayado de texto a un documento con GroupDocs.Annotation para .NET. Las anotaciones de subrayado de texto pueden ser útiles para destacar partes específicas de un documento, como pasajes importantes o puntos clave.
## Prerrequisitos
Antes de comenzar, asegúrese de tener instalados los siguientes requisitos previos:
1. GroupDocs.Annotation para .NET: Descargue e instale GroupDocs.Annotation para .NET desde [aquí](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: asegúrese de tener .NET Framework instalado en su sistema.

## Importación de espacios de nombres
Primero, importemos los espacios de nombres necesarios a nuestro proyecto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ahora, dividamos el ejemplo en varios pasos:
## Paso 1: Definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
En este paso, definimos la ruta de salida donde se guardará el documento anotado.
## Paso 2: Inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Aquí, inicializamos una instancia de `Annotator` clase proporcionando la ruta del documento de entrada.
## Paso 3: Crear una anotación subrayada
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // Obras compatibles únicamente con documentos Word y PDF
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Este paso implica crear un `UnderlineAnnotation` objeto con varias propiedades como color de fuente, mensaje, opacidad, número de página, color de fondo, color de subrayado, puntos y respuestas.
## Paso 4: Agregar anotación al documento
```csharp
annotator.Add(underline);
```
Aquí, agregamos la anotación subrayada al documento.
## Paso 5: Guardar el documento anotado
```csharp
annotator.Save(outputPath);
```
Finalmente, guardamos el documento anotado en la ruta de salida especificada.

## Conclusión
En este tutorial, aprendimos a añadir una anotación de subrayado de texto a un documento con GroupDocs.Annotation para .NET. Esta potente biblioteca ofrece diversas opciones de anotación para mejorar la colaboración y la comunicación en los documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación subrayada?
Sí, puede personalizar propiedades como el color, la opacidad y la posición según sus requisitos.
### ¿GroupDocs.Annotation es compatible con diferentes formatos de documentos?
Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos Word y PDF.
### ¿Puedo agregar múltiples anotaciones a un solo documento?
Por supuesto, GroupDocs.Annotation le permite agregar múltiples anotaciones de diferentes tipos a un documento.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?
Sí, puedes acceder a la versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte para GroupDocs.Annotation?
Puede obtener ayuda del foro de la comunidad GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).