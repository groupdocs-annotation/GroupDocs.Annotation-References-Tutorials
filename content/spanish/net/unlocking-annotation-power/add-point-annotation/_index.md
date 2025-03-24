---
title: Agregar anotación de puntos al documento
linktitle: Agregar anotación de puntos al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de puntos a archivos PDF usando GroupDocs.Annotation para .NET. Guía paso a paso para una integración perfecta.
weight: 17
url: /es/net/unlocking-annotation-power/add-point-annotation/
---

# Agregar anotación de puntos al documento

## Introducción
GroupDocs.Annotation para .NET es una poderosa herramienta que permite a los desarrolladores agregar varios tipos de anotaciones a documentos mediante programación. En este tutorial, nos centraremos en agregar una anotación de punto a un documento usando C#.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1. Conocimientos básicos del lenguaje de programación C#.
2. Visual Studio instalado en su sistema.
3.  GroupDocs.Annotation para la biblioteca .NET instalada. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/annotation/net/).

## Importación de espacios de nombres necesarios
Para comenzar, necesita importar los espacios de nombres requeridos a su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
En este paso, definimos la ruta de salida donde se guardará el documento anotado.
## Paso 2: inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Aquí inicializamos el`Annotator` objeto con el documento de entrada ("input.pdf").
## Paso 3: crear anotación de puntos
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 En este paso, creamos un`PointAnnotation` objeto y especificar sus propiedades como posición, mensaje, número de página y respuestas.
## Paso 4: agregar anotación
```csharp
annotator.Add(point);
```
Aquí, agregamos la anotación de punto creada al documento.
## Paso 5: guardar el documento
```csharp
annotator.Save(outputPath);
```
Finalmente, guardamos el documento anotado en la ruta de salida especificada.

## Conclusión
En este tutorial, aprendimos cómo agregar una anotación de punto a un documento usando GroupDocs.Annotation para .NET. Con esta potente biblioteca, puede mejorar sus aplicaciones de gestión de documentos incorporando funcionalidades de anotación.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
Sí, GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, Microsoft Word, Excel, PowerPoint y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
¡Absolutamente! GroupDocs.Annotation para .NET proporciona amplias opciones para personalizar la apariencia de las anotaciones para satisfacer las necesidades de su aplicación.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation para .NET?
 Sí, puedes aprovechar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
 Puede obtener soporte en el foro GroupDocs.Annotation[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Puedo obtener una licencia temporal para realizar pruebas?
 Sí, puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/).