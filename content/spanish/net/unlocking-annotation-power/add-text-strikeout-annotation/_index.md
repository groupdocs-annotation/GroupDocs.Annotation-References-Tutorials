---
title: Agregar anotación de tachado de texto al documento
linktitle: Agregar anotación de tachado de texto al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de texto tachado a documentos usando GroupDocs.Annotation para .NET. Mejore los procesos de colaboración y revisión de documentos de manera eficiente.
type: docs
weight: 26
url: /es/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Introducción
En este tutorial, exploraremos cómo agregar una anotación de texto tachado a un documento usando GroupDocs.Annotation para .NET. Esta biblioteca proporciona herramientas poderosas para anotar varios tipos de documentos, mejorando la colaboración y los procesos de revisión de documentos.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  GroupDocs.Annotation para .NET: instale la biblioteca. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo adecuado para el desarrollo .NET.
3. Documento: tenga un documento listo para realizar anotaciones, como un archivo PDF.

## Importando espacios de nombres
Primero, importe los espacios de nombres necesarios para acceder a las funcionalidades de GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ahora, dividamos el proceso de agregar una anotación de tachado de texto en varios pasos:
## Paso 1: definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Aquí, definimos la ruta de salida donde se guardará el documento anotado.
## Paso 2: inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicialice el objeto Annotator proporcionando la ruta al documento de entrada (archivo PDF en este caso).
## Paso 3: crear una anotación tachada
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Cree un objeto StrikeoutAnnotation con las propiedades deseadas, como mensaje, opacidad, número de página, color de fondo, puntos (coordenadas) y respuestas.
## Paso 4: agregar anotación
```csharp
annotator.Add(strikeout);
```
Agregue la anotación tachada creada al documento.
## Paso 5: guardar el documento
```csharp
annotator.Save(outputPath);
```
Guarde el documento anotado en la ruta de salida especificada.

## Conclusión
En este tutorial, aprendimos cómo agregar una anotación de texto tachado a un documento usando GroupDocs.Annotation para .NET. Esta poderosa biblioteca permite la anotación eficiente de documentos, mejorando la colaboración y los procesos de revisión de documentos.
## Preguntas frecuentes
### ¿GroupDocs.Annotation es compatible con varios formatos de documentos?
Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
Por supuesto, puede personalizar las propiedades de las anotaciones, como el color, la opacidad, el tamaño de fuente y más, según sus requisitos.
### ¿GroupDocs.Annotation proporciona funciones de colaboración?
Sí, GroupDocs.Annotation facilita la colaboración al permitir a los usuarios agregar comentarios, respuestas y anotaciones a los documentos.
### ¿Hay una prueba gratuita disponible?
 Sí, puedes aprovechar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte para GroupDocs.Annotation?
 Puede obtener apoyo del[Foro GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).