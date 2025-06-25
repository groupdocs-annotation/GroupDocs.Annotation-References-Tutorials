---
"description": "Aprenda a agregar fácilmente anotaciones de texto con líneas onduladas a documentos con Groupdocs.Annotation para .NET. Mejore la colaboración y la revisión de documentos."
"linktitle": "Agregar anotación de texto ondulado al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de texto ondulado al documento"
"url": "/es/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Agregar anotación de texto ondulado al documento

## Introducción

Groupdocs.Annotation para .NET es una biblioteca versátil que permite a los desarrolladores integrar fácilmente funciones de anotación robustas en sus aplicaciones .NET. Tanto si trabaja con archivos PDF, documentos de Word u otros formatos de archivo populares, Groupdocs.Annotation ofrece una solución integral para anotar y mejorar la colaboración en documentos.

## Prerrequisitos

Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:

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

Ahora que cubrimos los requisitos previos, dividamos el proceso de agregar anotaciones onduladas de texto en varios pasos.

## Paso 1: Definir la ruta de salida

Define la ruta donde se guardará el documento anotado.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Paso 2: Inicializar el anotador

Inicialice el objeto Anotador proporcionando la ruta del documento de entrada.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación va aquí
}
```

## Paso 3: Crear una anotación ondulada

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

## Paso 4: Agregar anotación

Añade la anotación ondulada creada al documento.

```csharp
annotator.Add(squiggly);
```

## Paso 5: Guardar el documento

Guarde el documento anotado en la ruta de salida especificada.

```csharp
annotator.Save(outputPath);
```

## Paso 6: Confirmación de visualización

Muestra un mensaje que confirma que el documento anotado se ha guardado correctamente.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión

En conclusión, Groupdocs.Annotation para .NET ofrece a los desarrolladores un conjunto completo de herramientas para integrar a la perfección las funciones de anotación de documentos en sus aplicaciones .NET. Siguiendo esta guía paso a paso, podrá añadir fácilmente anotaciones de texto con líneas onduladas a sus documentos, optimizando así la colaboración y la revisión de documentos.

## Preguntas frecuentes

### P: ¿Groupdocs.Annotation puede admitir anotaciones en varios formatos de archivos?

R: Sí, Groupdocs.Annotation admite anotaciones en una amplia gama de formatos de archivos, incluidos PDF, documentos de Word, hojas de Excel y más.

### P: ¿Groupdocs.Annotation es compatible con aplicaciones de escritorio y web?

R: ¡Por supuesto! Groupdocs.Annotation se integra perfectamente tanto en aplicaciones de escritorio como web, ofreciendo flexibilidad y versatilidad.

### P: ¿Hay opciones de licencia disponibles para Groupdocs.Annotation?

R: Sí, Groupdocs.Annotation ofrece opciones de licencia flexibles adaptadas a las necesidades individuales o empresariales, incluidas licencias temporales para fines de prueba.

### P: ¿Es posible personalizar las anotaciones creadas con Groupdocs.Annotation?

R: ¡Por supuesto! Groupdocs.Annotation ofrece amplias opciones de personalización para las anotaciones, lo que permite a los desarrolladores adaptarlas a sus necesidades específicas.

### P: ¿Groupdocs.Annotation ofrece soporte y documentación para desarrolladores?

R: ¡En efecto! Groupdocs.Annotation ofrece documentación completa y foros de soporte dedicados para ayudar a los desarrolladores a utilizar sus funciones eficazmente.