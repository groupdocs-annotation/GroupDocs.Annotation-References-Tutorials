---
"description": "Aprenda a añadir anotaciones de puntos a archivos PDF con GroupDocs.Annotation para .NET. Guía paso a paso para una integración perfecta."
"linktitle": "Agregar anotación de puntos al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de puntos al documento"
"url": "/es/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Agregar anotación de puntos al documento

## Introducción
GroupDocs.Annotation para .NET es una potente herramienta que permite a los desarrolladores añadir diversos tipos de anotaciones a documentos mediante programación. En este tutorial, nos centraremos en añadir una anotación de punto a un documento con C#.
## Prerrequisitos
Antes de comenzar, asegúrese de tener lo siguiente:
1. Comprensión básica del lenguaje de programación C#.
2. Visual Studio instalado en su sistema.
3. La biblioteca GroupDocs.Annotation para .NET está instalada. Puede descargarla desde [aquí](https://releases.groupdocs.com/annotation/net/).

## Importación de espacios de nombres necesarios
Para comenzar, debe importar los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: Definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
En este paso, definimos la ruta de salida donde se guardará el documento anotado.
## Paso 2: Inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Aquí, inicializamos el `Annotator` objeto con el documento de entrada ("input.pdf").
## Paso 3: Crear anotación de puntos
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
En este paso, creamos un `PointAnnotation` objeto y especificar sus propiedades como posición, mensaje, número de página y respuestas.
## Paso 4: Agregar anotación
```csharp
annotator.Add(point);
```
Aquí, agregamos la anotación del punto creado al documento.
## Paso 5: Guardar el documento
```csharp
annotator.Save(outputPath);
```
Finalmente, guardamos el documento anotado en la ruta de salida especificada.

## Conclusión
En este tutorial, aprendimos a agregar una anotación de punto a un documento usando GroupDocs.Annotation para .NET. Con esta potente biblioteca, puede mejorar sus aplicaciones de gestión documental incorporando funciones de anotación.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
Sí, GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, Microsoft Word, Excel, PowerPoint y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
¡Por supuesto! GroupDocs.Annotation para .NET ofrece amplias opciones para personalizar la apariencia de las anotaciones según las necesidades de su aplicación.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation para .NET?
Sí, puedes aprovechar una prueba gratuita desde [aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener ayuda para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
Puede obtener ayuda en el foro GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Puedo obtener una licencia temporal para fines de prueba?
Sí, puede obtener una licencia temporal de [aquí](https://purchase.groupdocs.com/temporary-license/).