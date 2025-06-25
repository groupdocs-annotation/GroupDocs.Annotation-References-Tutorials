---
"description": "Aprenda a agregar anotaciones de imagen a documentos con GroupDocs.Annotation para .NET. Mejore la gestión de documentos con potentes funciones de anotación."
"linktitle": "Agregar anotación de imagen al documento (ruta remota)"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de imagen al documento (ruta remota)"
"url": "/es/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Agregar anotación de imagen al documento (ruta remota)

## Introducción
En este tutorial, explicaremos el proceso de agregar anotaciones de imagen a un documento con GroupDocs.Annotation para .NET. Esta biblioteca proporciona potentes herramientas para anotar diversos tipos de documentos mediante programación.
## Prerrequisitos
Antes de comenzar, asegúrese de tener lo siguiente:
1. GroupDocs.Annotation para .NET: Descargue e instale la biblioteca desde [aquí](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: asegúrese de tener un entorno de desarrollo funcional configurado para el desarrollo .NET.
3. Documento: Prepare el documento que desea anotar. Para este tutorial, asumiremos que tiene un documento PDF llamado `input.pdf`.
4. Imagen para anotación: Elija la imagen que desea usar para la anotación. Asegúrese de tener lista la URL o la ruta local de la imagen.

## Importar espacios de nombres
Antes de comenzar a codificar, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Paso 1: Establecer la ruta de salida
Primero, defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Crear una instancia de la `Annotator` clase y especifique el documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí
}
```
## Paso 3: Agregar anotación de imagen
Ahora, agreguemos la anotación de imagen al documento. Especificaremos sus propiedades, como la posición, la opacidad, el número de página y la ruta de la imagen.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Especifique la posición de la anotación
    CreatedOn = DateTime.Now, // Establecer la fecha de creación
    Opacity = 0.7, // Establecer opacidad (de 0 a 1)
    PageNumber = 0, // Especifique el número de página
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Proporcione la URL de la imagen
};
annotator.Add(image); // Añadir la anotación de la imagen
```
## Paso 4: Guardar el documento
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
```
## Paso 5: Mostrar la ruta de salida
Informar al usuario sobre la operación de guardado exitosa del documento y mostrar la ruta de salida.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, aprendimos a agregar anotaciones de imagen a un documento con GroupDocs.Annotation para .NET. Siguiendo estos pasos, podrá mejorar sus aplicaciones de gestión documental con potentes funciones de anotación.
## Preguntas frecuentes
### ¿Se puede utilizar GroupDocs.Annotation con otros formatos de documentos además de PDF?
Sí, GroupDocs.Annotation admite varios formatos de documentos, incluidos Word, Excel, PowerPoint y más.
### ¿GroupDocs.Annotation es compatible con .NET Core?
Sí, GroupDocs.Annotation es compatible con .NET Framework y .NET Core.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, puedes personalizar la apariencia de las anotaciones, como el color, la opacidad y el tamaño.
### ¿GroupDocs.Annotation admite funciones de anotación colaborativa?
Sí, GroupDocs.Annotation ofrece funciones de anotación colaborativa para la colaboración en tiempo real en documentos.
### ¿Hay una versión de prueba disponible para probar?
Sí, puedes obtener una prueba gratuita de GroupDocs.Annotation desde [aquí](https://releases.groupdocs.com/).