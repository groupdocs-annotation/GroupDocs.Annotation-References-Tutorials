---
"description": "Aprenda a agregar anotaciones de distancia a documentos con GroupDocs.Annotation para .NET. Mejore la colaboración y la comunicación sin esfuerzo."
"linktitle": "Agregar anotación de distancia al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de distancia al documento"
"url": "/es/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Agregar anotación de distancia al documento

## Introducción
En este tutorial, aprenderá a agregar una anotación de distancia a un documento usando GroupDocs.Annotation para .NET. Siga estos pasos para realizar la tarea:
## Prerrequisitos

Asegúrese de tener los siguientes requisitos previos antes de continuar:

- Biblioteca GroupDocs.Annotation para .NET: Descargue e instale la biblioteca GroupDocs.Annotation para .NET desde [este enlace](https://releases.groupdocs.com/annotation/net/).
- Documento a anotar: prepare el documento (por ejemplo, PDF) al que desea agregar la anotación de distancia.
- Entorno de desarrollo: configure su entorno de desarrollo con Visual Studio o cualquier otro IDE de su elección.

## Importar espacios de nombres

Antes de comenzar, asegúrese de incluir los espacios de nombres necesarios en su código. Estos espacios de nombres son esenciales para acceder a las clases y métodos requeridos.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Paso 1: Inicializar el anotador

Comience por inicializar el `Annotator` objeto con la ruta al documento que desea anotar.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí
}
```

## Paso 2: Crear anotación de distancia

Ahora, crea un `DistanceAnnotation` objeto y configurar sus propiedades como dimensiones del cuadro, mensaje, opacidad, color del lápiz, etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Paso 3: Agregar anotación

Agregue la anotación de distancia creada al documento usando el `Add` método del objeto anotador.

```csharp
annotator.Add(distance);
```

## Paso 4: Guardar el documento

Guarde el documento anotado en la ubicación deseada en su sistema.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Paso 5: Confirmación de visualización

Por último, muestra un mensaje confirmando que el documento anotado se ha guardado correctamente.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión

Añadir anotaciones de distancia a documentos con GroupDocs.Annotation para .NET es un proceso sencillo. Siguiendo los pasos de este tutorial, podrá enriquecer sus documentos con valiosas anotaciones, lo que facilitará la colaboración y la comunicación.

## Preguntas frecuentes

### P: ¿Puedo personalizar la apariencia de la anotación de distancia?

R: Sí, puede personalizar varias propiedades como el color, la opacidad, el estilo de línea, etc., para adaptarlas a sus necesidades.

### P: ¿GroupDocs.Annotation admite anotaciones en diferentes tipos de documentos?

R: Sí, GroupDocs.Annotation admite anotaciones en una amplia gama de formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y más.

### P: ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?

R: Sí, puede acceder a una prueba gratuita de GroupDocs.Annotation desde [este enlace](https://releases.groupdocs.com/).

### P: ¿Dónde puedo encontrar la documentación de GroupDocs.Annotation para .NET?

A: Puede consultar la documentación detallada disponible [aquí](https://tutorials.groupdocs.com/annotation/net/).

### P: ¿Cómo puedo obtener soporte o asistencia con GroupDocs.Annotation?

R: Puede buscar soporte y asistencia en el foro de la comunidad GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).