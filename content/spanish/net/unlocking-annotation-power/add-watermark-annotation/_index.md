---
"description": "Aprenda a agregar fácilmente anotaciones de marca de agua a sus documentos con GroupDocs.Annotation para .NET. Mejore la claridad y la seguridad de sus documentos."
"linktitle": "Agregar anotación de marca de agua al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de marca de agua al documento"
"url": "/es/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# Agregar anotación de marca de agua al documento

## Introducción
En este tutorial, explicaremos el proceso para agregar una anotación de marca de agua a un documento con GroupDocs.Annotation para .NET. Las anotaciones de marca de agua son útiles para indicar el estado de un documento, marcarlo como confidencial o añadir cualquier otra información relevante.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1. GroupDocs.Annotation para .NET: Puede descargarlo desde [aquí](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: asegúrese de tener Visual Studio instalado en su sistema.
3. Conocimientos básicos de C#: Es necesario estar familiarizado con el lenguaje de programación C# para comprender e implementar los ejemplos de código.

## Importar espacios de nombres

Antes de comenzar a codificar, importemos los espacios de nombres necesarios:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Ahora, desglosemos el proceso de agregar una anotación de marca de agua en varios pasos:

## Paso 1: Definir la ruta de salida

Primero, necesitamos definir la ruta de salida donde se guardará el documento anotado. Usaremos el `Path` clase de `System.IO` espacio de nombres para combinar la ruta del directorio de salida con el nombre del archivo.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Paso 2: Inicializar el anotador

A continuación, inicializaremos el anotador proporcionando la ruta del documento de entrada. Esto nos permitirá añadir anotaciones al documento.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí
}
```

## Paso 3: Crear una anotación de marca de agua

Ahora, creemos un objeto de anotación de marca de agua con las propiedades deseadas, como ángulo, posición, texto, color de fuente, opacidad, etc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Paso 4: Agregar anotación de marca de agua

Ahora, agregaremos la anotación de marca de agua al documento usando el `Add` método del objeto anotador.

```csharp
annotator.Add(watermark);
```

## Paso 5: Guardar el documento

Finalmente, guardaremos el documento anotado en la ruta de salida especificada.

```csharp
annotator.Save(outputPath);
```

## Conclusión

En este tutorial, aprendimos a agregar una anotación de marca de agua a un documento con GroupDocs.Annotation para .NET. Las anotaciones de marca de agua son una herramienta valiosa para marcar documentos con información relevante o indicar su estado.

## Preguntas frecuentes

### P: ¿Puedo personalizar la apariencia de la anotación de la marca de agua?

R: Sí, puede personalizar varias propiedades como texto, tamaño de fuente, color, opacidad, posición, etc., para adaptar la marca de agua según sus requisitos.

### P: ¿GroupDocs.Annotation para .NET es compatible con diferentes formatos de documentos?

R: Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, Microsoft Word, Excel, PowerPoint y formatos de imagen.

### P: ¿Puedo agregar varias anotaciones a un solo documento?

R: Por supuesto. GroupDocs.Annotation le permite agregar múltiples anotaciones de diferentes tipos a un solo documento, lo que permite un marcado completo del documento.

### P: ¿GroupDocs.Annotation proporciona soporte para anotación colaborativa?

R: Sí, GroupDocs.Annotation facilita la anotación colaborativa al permitir que los usuarios agreguen comentarios, respuestas y anotaciones, lo que fomenta la colaboración efectiva entre los miembros del equipo.

### P: ¿Hay una versión de prueba disponible de GroupDocs.Annotation para .NET?

R: Sí, puedes descargar una versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/).