---
title: Poner anotación de imagen sobre texto
linktitle: Poner anotación de imagen sobre texto
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de imágenes sobre texto en .NET usando GroupDocs.Annotation para una gestión de documentos y colaboración eficientes.
weight: 21
url: /es/net/advanced-usage/put-image-annotation-over-text/
---

# Poner anotación de imagen sobre texto

## Introducción
En el mundo del desarrollo .NET, GroupDocs.Annotation ofrece una poderosa solución para agregar anotaciones a documentos, haciendo que la colaboración y la gestión de documentos sean más eficientes. Un requisito común es colocar anotaciones de imágenes sobre texto, lo que se puede lograr sin problemas utilizando GroupDocs.Annotation para .NET.
## Requisitos previos
Antes de sumergirse en el proceso de colocar anotaciones de imágenes sobre texto usando GroupDocs.Annotation para .NET, asegúrese de tener lo siguiente:
1.  GroupDocs.Annotation para la biblioteca .NET: descargue e instale la biblioteca desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo adecuado, como Visual Studio o cualquier otro IDE .NET.
3. Archivos de documentos e imágenes: prepare el archivo del documento (PDF, DOCX, etc.) y el archivo de imagen que desea utilizar para las anotaciones.
4. Comprensión básica de C#: es necesario estar familiarizado con el lenguaje de programación C# para implementar los fragmentos de código proporcionados en este tutorial.

## Importar espacios de nombres
Antes de continuar con el proceso de anotación, asegúrese de importar los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Paso 1: definir la ruta de salida
Primero, defina la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Paso 2: inicializar el anotador
 Inicializar el`Annotator` objeto proporcionando la ruta del documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí.
}
```
## Paso 3: crear anotaciones de imagen
 Crear un`ImageAnnotation` objeto con las propiedades deseadas, como dimensiones del cuadro, opacidad, número de página, ruta de la imagen e índice z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Paso 4: agregar anotación
 Agregue la anotación de imagen al documento usando el`Add` método de la`Annotator` objeto:
```csharp
annotator.Add(image);
```
## Paso 5: guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada:
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Muestra un mensaje de éxito con la ruta al documento anotado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, agregar anotaciones de imágenes sobre texto en aplicaciones .NET usando GroupDocs.Annotation es un proceso sencillo. Si sigue la guía paso a paso proporcionada en este tutorial, podrá anotar documentos de manera eficiente y mejorar las capacidades de colaboración y gestión de documentos en sus proyectos .NET.
## Preguntas frecuentes
### ¿Puedo anotar documentos que no sean PDF?
Sí, GroupDocs.Annotation admite varios formatos de documentos, como DOCX, XLSX, PPTX y más.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte para GroupDocs.Annotation?
 Puede obtener soporte en el foro de la comunidad GroupDocs.Annotation.[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Necesito una licencia temporal para realizar pruebas?
 Sí, puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/) con fines de prueba.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, GroupDocs.Annotation proporciona varias opciones para personalizar la apariencia de las anotaciones, como el color, la opacidad, el tamaño de fuente, etc.