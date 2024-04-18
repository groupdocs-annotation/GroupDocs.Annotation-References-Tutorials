---
title: Agregar anotación de subrayado de texto al documento
linktitle: Agregar anotación de subrayado de texto al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de subrayado de texto a documentos usando GroupDocs.Annotation para .NET. Mejore la colaboración y la comunicación sin esfuerzo.
type: docs
weight: 27
url: /es/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Introducción
En este tutorial, recorreremos el proceso de agregar una anotación de subrayado de texto a un documento usando GroupDocs.Annotation para .NET. Las anotaciones de subrayado de texto pueden resultar útiles para enfatizar partes específicas de un documento, como pasajes importantes o puntos clave.
## Requisitos previos
Antes de comenzar, asegúrese de tener instalados los siguientes requisitos previos:
1.  GroupDocs.Annotation para .NET: descargue e instale GroupDocs.Annotation para .NET desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: asegúrese de tener .NET Framework instalado en su sistema.

## Importando espacios de nombres
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
## Paso 1: definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
En este paso, definimos la ruta de salida donde se guardará el documento anotado.
## Paso 2: inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Aquí, inicializamos una instancia del`Annotator` clase proporcionando la ruta del documento de entrada.
## Paso 3: crear una anotación subrayada
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // funciona solo con documentos Word y PDF
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
 Este paso implica crear un`UnderlineAnnotation`objeto con varias propiedades como color de fuente, mensaje, opacidad, número de página, color de fondo, color de subrayado, puntos y respuestas.
## Paso 4: agregar una anotación al documento
```csharp
annotator.Add(underline);
```
Aquí, agregamos la anotación subrayada al documento.
## Paso 5: guardar el documento anotado
```csharp
annotator.Save(outputPath);
```
Finalmente, guardamos el documento anotado en la ruta de salida especificada.

## Conclusión
En este tutorial, aprendimos cómo agregar una anotación de subrayado de texto a un documento usando GroupDocs.Annotation para .NET. Esta poderosa biblioteca proporciona varias opciones de anotaciones para mejorar la colaboración y la comunicación en documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación subrayada?
Sí, puede personalizar propiedades como el color, la opacidad y la posición según sus requisitos.
### ¿GroupDocs.Annotation es compatible con diferentes formatos de documentos?
Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos Word y PDF.
### ¿Puedo agregar varias anotaciones a un solo documento?
Por supuesto, GroupDocs.Annotation le permite agregar múltiples anotaciones de diferentes tipos a un documento.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?
 Sí, puedes acceder a la versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte para GroupDocs.Annotation?
 Puede obtener soporte en el foro de la comunidad GroupDocs.Annotation.[aquí](https://forum.groupdocs.com/c/annotation/10).