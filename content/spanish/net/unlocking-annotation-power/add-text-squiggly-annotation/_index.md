---
title: Agregar anotaciones de texto ondulado al documento
linktitle: Agregar anotaciones de texto ondulado al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar sin esfuerzo anotaciones de texto ondulado a documentos usando Groupdocs.Annotation para .NET. Mejore los procesos de colaboración y revisión de documentos.
weight: 25
url: /es/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Introducción

Groupdocs.Annotation para .NET es una biblioteca versátil que permite a los desarrolladores integrar capacidades de anotación sólidas en sus aplicaciones .NET sin esfuerzo. Ya sea que esté trabajando con archivos PDF, documentos de Word u otros formatos de archivos populares, Groupdocs.Annotation proporciona una solución perfecta para anotar y mejorar la colaboración en documentos.

## Requisitos previos

Antes de sumergirse en el tutorial, asegúrese de cumplir con los siguientes requisitos previos:

## Importar espacios de nombres

Asegúrese de importar los espacios de nombres necesarios para acceder a las funcionalidades proporcionadas por Groupdocs.Annotation para .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ahora que tenemos cubiertos los requisitos previos, dividamos el proceso de agregar anotaciones de texto ondulado en varios pasos.

## Paso 1: definir la ruta de salida

Defina la ruta donde se guardará el documento anotado.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Paso 2: inicializar el anotador

Inicialice el objeto Annotator proporcionando la ruta del documento de entrada.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación va aquí.
}
```

## Paso 3: crear una anotación ondulada

Cree un objeto SquigglyAnnotation y especifique sus propiedades.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## Paso 4: agregar anotación

Agregue la anotación ondulada creada al documento.

```csharp
annotator.Add(squiggly);
```

## Paso 5: guardar el documento

Guarde el documento anotado en la ruta de salida especificada.

```csharp
annotator.Save(outputPath);
```

## Paso 6: Mostrar confirmación

Muestra un mensaje confirmando el guardado exitoso del documento anotado.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión

En conclusión, Groupdocs.Annotation para .NET proporciona a los desarrolladores un sólido conjunto de herramientas para integrar sin problemas funcionalidades de anotación de documentos en sus aplicaciones .NET. Si sigue esta guía paso a paso, podrá agregar sin esfuerzo anotaciones de texto ondulado a sus documentos, mejorando la colaboración y los procesos de revisión de documentos.

## Preguntas frecuentes

### P: ¿Grupodocs.Annotation puede admitir anotaciones en varios formatos de archivo?

R: Sí, Groupdocs.Annotation admite anotaciones en una amplia gama de formatos de archivos, incluidos PDF, documentos de Word, hojas de Excel y más.

### P: ¿Groupdocs.Annotation es compatible con aplicaciones web y de escritorio?

R: ¡Absolutamente! Groupdocs.Annotation se puede integrar perfectamente en aplicaciones web y de escritorio, ofreciendo flexibilidad y versatilidad.

### P: ¿Hay opciones de licencia disponibles para Groupdocs.Annotation?

R: Sí, Groupdocs.Annotation ofrece opciones de licencia flexibles adaptadas a las necesidades individuales o empresariales, incluidas licencias temporales para fines de prueba.

### P: ¿Se pueden personalizar las anotaciones creadas con Groupdocs.Annotation?

R: ¡Ciertamente! Groupdocs.Annotation proporciona amplias opciones de personalización para las anotaciones, lo que permite a los desarrolladores adaptar las anotaciones a sus requisitos específicos.

### P: ¿Groupdocs.Annotation ofrece soporte y documentación para desarrolladores?

R: ¡De hecho! Groupdocs.Annotation proporciona documentación completa y foros de soporte dedicados para ayudar a los desarrolladores a utilizar sus funciones de manera efectiva.