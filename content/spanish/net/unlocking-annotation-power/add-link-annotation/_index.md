---
title: Agregar anotación de enlace al documento
linktitle: Agregar anotación de enlace al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de enlaces a documentos usando Groupdocs.Annotation para .NET. Mejore la colaboración y la interactividad sin esfuerzo.
weight: 16
url: /es/net/unlocking-annotation-power/add-link-annotation/
---

# Agregar anotación de enlace al documento

## Introducción
Groupdocs.Annotation para .NET es una poderosa biblioteca que permite a los desarrolladores integrar funciones integrales de anotación en sus aplicaciones .NET sin esfuerzo. Una de las características clave que ofrece es la capacidad de agregar anotaciones de enlaces a documentos, mejorando la colaboración y la interactividad.
## Requisitos previos
Antes de sumergirse en el proceso de agregar anotaciones de enlaces, asegúrese de tener los siguientes requisitos previos:
- Conocimientos básicos del lenguaje de programación C#.
- Se instaló Groupdocs.Annotation para la biblioteca .NET.
- Accede a un documento que deseas anotar.

## Importar espacios de nombres
En primer lugar, debe importar los espacios de nombres necesarios para utilizar Groupdocs.Annotation para las funcionalidades .NET. Esto permite que su aplicación acceda a las clases y métodos necesarios para anotar documentos.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: establecer la ruta de salida
Defina la ruta donde desea guardar el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
 Crear una instancia del`Annotator` clase proporcionando la ruta del documento que desea anotar.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí.
}
```
## Paso 3: crear una anotación de enlace
 Definir un`LinkAnnotation` objeto y especifique sus propiedades como mensaje, opacidad, número de página, color de fondo, puntos, respuestas y URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## Paso 4: agregar anotación
 Agregue la anotación del enlace creado al documento usando el`Add` método de la instancia del anotador.
```csharp
annotator.Add(link);
```
## Paso 5: guardar el documento
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Informar al usuario sobre el guardado exitoso del documento anotado.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, siguiendo los pasos anteriores, puede agregar sin problemas anotaciones de enlaces a documentos utilizando Groupdocs.Annotation para .NET. Esto mejora la colaboración en documentos y proporciona a los usuarios funciones interactivas.
## Preguntas frecuentes
### ¿Groupdocs.Annotation para .NET es compatible con todo tipo de documentos?
Groupdocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, Word, Excel y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, puede personalizar varias propiedades de las anotaciones, como el color, la opacidad y el tamaño, para adaptarlas a sus necesidades.
### ¿Groupdocs.Annotation para .NET ofrece funciones de colaboración en tiempo real?
Sí, Groupdocs.Annotation para .NET proporciona funciones de colaboración en tiempo real que permiten a varios usuarios anotar documentos simultáneamente.
### ¿Hay soporte técnico disponible para los productos Groupdocs?
 Sí, el soporte técnico para los productos Groupdocs está disponible a través del foro y soporte[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Puedo probar Groupdocs.Annotation para .NET antes de comprarlo?
Sí, puede aprovechar una prueba gratuita de Groupdocs.Annotation para .NET para explorar sus funciones antes de realizar una compra.[aquí](https://purchase.groupdocs.com/temporary-license/).