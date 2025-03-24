---
title: Agregar anotación de imagen al documento (ruta remota)
linktitle: Agregar anotación de imagen al documento (ruta remota)
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de imágenes a documentos usando GroupDocs.Annotation para .NET. Mejore la gestión de documentos con potentes capacidades de anotación.
weight: 15
url: /es/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Introducción
En este tutorial, recorreremos el proceso de agregar anotaciones de imágenes a un documento usando GroupDocs.Annotation para .NET. Esta biblioteca proporciona herramientas poderosas para anotar varios tipos de documentos mediante programación.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Annotation para .NET: descargue e instale la biblioteca desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: asegúrese de tener un entorno de desarrollo funcional configurado para el desarrollo .NET.
3.  Documento: Prepare el documento que desea anotar. Para este tutorial, asumiremos que tiene un documento PDF llamado`input.pdf`.
4. Imagen para anotaciones: elija la imagen que desea utilizar para anotaciones. Asegúrese de tener lista la URL de la imagen o la ruta local.

## Importar espacios de nombres
Antes de comenzar a codificar, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Paso 1: establecer la ruta de salida
Primero, defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
 Crear una instancia del`Annotator` clase y especifique el documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí.
}
```
## Paso 3: agregar anotaciones de imagen
Ahora, agreguemos la anotación de la imagen al documento. Especificaremos las propiedades de la anotación de la imagen, como posición, opacidad, número de página y ruta de la imagen.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Especificar la posición de la anotación.
    CreatedOn = DateTime.Now, // Establecer la fecha de creación
    Opacity = 0.7, // Establecer opacidad (0 a 1)
    PageNumber = 0, // Especifique el número de página
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Proporciona la URL de la imagen
};
annotator.Add(image); // Agregar la anotación de la imagen.
```
## Paso 4: guardar el documento
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
```
## Paso 5: Mostrar ruta de salida
Informe al usuario sobre la operación exitosa de guardar el documento y muestre la ruta de salida.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, aprendimos cómo agregar anotaciones de imágenes a un documento usando GroupDocs.Annotation para .NET. Si sigue estos pasos, podrá mejorar sus aplicaciones de gestión de documentos con potentes capacidades de anotación.
## Preguntas frecuentes
### ¿Se puede utilizar GroupDocs.Annotation con otros formatos de documentos además de PDF?
Sí, GroupDocs.Annotation admite varios formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿GroupDocs.Annotation es compatible con .NET Core?
Sí, GroupDocs.Annotation es compatible tanto con .NET Framework como con .NET Core.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, puedes personalizar la apariencia de las anotaciones, como el color, la opacidad y el tamaño.
### ¿GroupDocs.Annotation admite funciones de anotación colaborativa?
Sí, GroupDocs.Annotation ofrece funciones de anotación colaborativa para la colaboración en tiempo real en documentos.
### ¿Existe una versión de prueba disponible para probar?
 Sí, puede obtener una prueba gratuita de GroupDocs.Annotation desde[aquí](https://releases.groupdocs.com/).