---
"description": "Aprenda a agregar anotaciones de imagen a documentos con GroupDocs.Annotation para .NET. Mejore sus capacidades de procesamiento de documentos fácilmente."
"linktitle": "Agregar anotación de imagen al documento (ruta local)"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de imagen al documento (ruta local)"
"url": "/es/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Agregar anotación de imagen al documento (ruta local)

## Introducción
GroupDocs.Annotation para .NET es una potente biblioteca que permite a los desarrolladores añadir diversos tipos de anotaciones a documentos mediante programación. En este tutorial, aprenderemos a añadir anotaciones de imagen a un documento mediante una ruta local.
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Conocimientos básicos del lenguaje de programación C#.
2. Visual Studio instalado en su sistema.
3. GroupDocs.Annotation para la biblioteca .NET instalada o tutorialsd en su proyecto.
4. Un documento de entrada (por ejemplo, PDF) y un archivo de imagen para anotación.
## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios a su archivo de C#. Estos espacios de nombres proporcionan acceso a las clases y métodos necesarios para trabajar con GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Paso 1: Definir la ruta de salida
Define la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Inicialice el anotador proporcionando la ruta al documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación va aquí
}
```
## Paso 3: Crear anotación de imagen
Crear una instancia de la `ImageAnnotation` clase y especifique sus propiedades como posición, opacidad, número de página y ruta de la imagen.
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
## Paso 4: Agregar anotación
Agregue la anotación de imagen creada al documento usando el `Add` método del anotador.
```csharp
annotator.Add(image);
```
## Paso 5: Guardar el documento
Guarde el documento anotado en la ruta de salida.
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar la ruta de salida
Muestra un mensaje indicando que el documento se ha guardado correctamente y la ubicación del archivo de salida.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, aprendimos a agregar anotaciones de imagen a un documento con GroupDocs.Annotation para .NET. Siguiendo estos sencillos pasos, podrá optimizar su capacidad de procesamiento de documentos con potentes funciones de anotación.
## Preguntas frecuentes
### ¿Puedo anotar documentos que no sean PDF?
Sí, GroupDocs.Annotation admite varios formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿GroupDocs.Annotation es compatible con .NET Core?
Sí, GroupDocs.Annotation es compatible con .NET Framework y .NET Core.
### ¿Puedo personalizar la apariencia de las anotaciones?
Por supuesto, puede personalizar la apariencia, el tamaño, el color y otras propiedades de las anotaciones según sus requisitos.
### ¿GroupDocs.Annotation proporciona soporte para anotación colaborativa?
Sí, GroupDocs.Annotation ofrece funciones de anotación colaborativa que permiten que varios usuarios anoten documentos simultáneamente.
### ¿Dónde puedo encontrar ayuda o soporte adicional?
Puede visitar el foro GroupDocs.Annotation para obtener asistencia y soporte de la comunidad.