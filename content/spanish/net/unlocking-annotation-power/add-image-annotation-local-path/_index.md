---
title: Agregar anotación de imagen al documento (ruta local)
linktitle: Agregar anotación de imagen al documento (ruta local)
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de imágenes a documentos usando GroupDocs.Annotation para .NET. Mejore las capacidades de procesamiento de documentos con facilidad.
weight: 14
url: /es/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Introducción
GroupDocs.Annotation para .NET es una poderosa biblioteca que permite a los desarrolladores agregar varios tipos de anotaciones a documentos mediante programación. En este tutorial, aprenderemos cómo agregar anotaciones de imágenes a un documento usando una ruta local.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Conocimientos básicos del lenguaje de programación C#.
2. Visual Studio instalado en su sistema.
3. GroupDocs.Annotation para la biblioteca .NET instalada o a la que se hace referencia en su proyecto.
4. Un documento de entrada (por ejemplo, PDF) y un archivo de imagen para realizar anotaciones.
## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios a su archivo C#. Estos espacios de nombres brindan acceso a las clases y métodos necesarios para trabajar con GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Paso 1: definir la ruta de salida
Defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
Inicialice el anotador proporcionando la ruta al documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación va aquí.
}
```
## Paso 3: crear anotaciones de imagen
 Crear una instancia del`ImageAnnotation`clase y especifique sus propiedades como posición, opacidad, número de página y ruta de la imagen.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Paso 4: agregar anotación
 Agregue la anotación de imagen creada al documento usando el`Add` método del anotador.
```csharp
annotator.Add(image);
```
## Paso 5: guardar el documento
Guarde el documento anotado en la ruta de salida.
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar ruta de salida
Muestra un mensaje que indica que el documento se guardó correctamente y la ubicación del archivo de salida.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, hemos aprendido cómo agregar anotaciones de imágenes a un documento usando GroupDocs.Annotation para .NET. Si sigue estos sencillos pasos, podrá mejorar sus capacidades de procesamiento de documentos con potentes funciones de anotación.
## Preguntas frecuentes
### ¿Puedo anotar documentos que no sean PDF?
Sí, GroupDocs.Annotation admite varios formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿GroupDocs.Annotation es compatible con .NET Core?
Sí, GroupDocs.Annotation es compatible tanto con .NET Framework como con .NET Core.
### ¿Puedo personalizar la apariencia de las anotaciones?
Por supuesto, puedes personalizar la apariencia, el tamaño, el color y otras propiedades de las anotaciones según tus necesidades.
### ¿GroupDocs.Annotation proporciona soporte para la anotación colaborativa?
Sí, GroupDocs.Annotation ofrece funciones de anotación colaborativa que permiten a varios usuarios anotar documentos simultáneamente.
### ¿Dónde puedo encontrar ayuda o soporte adicional?
Puede visitar el foro GroupDocs.Annotation para obtener ayuda y apoyo de la comunidad.