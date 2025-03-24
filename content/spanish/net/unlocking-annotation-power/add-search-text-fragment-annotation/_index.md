---
title: Agregar anotación de fragmento de texto de búsqueda al documento
linktitle: Agregar anotación de fragmento de texto de búsqueda al documento
second_title: API GroupDocs.Annotation .NET
description: Explore el poder de GroupDocs.Annotation para .NET y agregue fácilmente capacidades de anotación de documentos a sus aplicaciones.
weight: 20
url: /es/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Introducción
En el ámbito del desarrollo .NET, GroupDocs.Annotation se destaca como una poderosa herramienta para anotar documentos sin problemas. Ya sea que sea un desarrollador experimentado o simplemente esté ingresando al mundo de .NET, este completo tutorial lo guiará a través de los conceptos básicos del uso de GroupDocs.Annotation para .NET, desde la importación de espacios de nombres hasta el dominio de las complejidades de agregar anotaciones de fragmentos de texto de búsqueda a su documentos.
## Introducción
GroupDocs.Annotation para .NET permite a los desarrolladores incorporar capacidades de anotación de documentos en sus aplicaciones sin esfuerzo. Con su API intuitiva y funciones sólidas, los desarrolladores pueden anotar varios formatos de documentos, incluidos PDF, documentos de Microsoft Office, imágenes y más.
## Requisitos previos
Antes de sumergirse en GroupDocs.Annotation para .NET, asegúrese de tener implementados los siguientes requisitos previos:

## Importar espacios de nombres
En primer lugar, importe los espacios de nombres necesarios para acceder a las clases y métodos de GroupDocs.Annotation en su proyecto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: definir la ruta de salida
Comience definiendo la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
 A continuación, inicialice una instancia del`Annotator` clase proporcionando la ruta al documento que desea anotar:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: crear una anotación de fragmento de texto de búsqueda
 Crear un`SearchTextFragment` objeto con las propiedades deseadas, como texto a buscar, tamaño de fuente, familia de fuentes, color de fuente y color de fondo:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Paso 4: agregar anotación
 Agregue la anotación del fragmento de texto de búsqueda creado al documento usando el`Add` método del anotador:
```csharp
annotator.Add(searchText);
```
## Paso 5: guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada:
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Informar al usuario que el documento se ha guardado exitosamente:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET simplifica el proceso de agregar anotaciones a documentos, mejorando la colaboración y los procesos de revisión de documentos. Si sigue los pasos descritos en esta guía, podrá integrar perfectamente las capacidades de anotación de documentos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Annotation es compatible con todos los formatos de documentos?
Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, documentos de Microsoft Office, imágenes y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
¡Absolutamente! GroupDocs.Annotation proporciona amplias opciones de personalización para anotaciones, lo que le permite ajustar propiedades como el tamaño, el color y el estilo de la fuente.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?
 Sí, puede acceder a una prueba gratuita de GroupDocs.Annotation para explorar sus características y capacidades antes de realizar una compra.[aquí](https://releases.groupdocs.com/)..
### ¿Dónde puedo encontrar soporte para GroupDocs.Annotation?
 Para obtener soporte y asistencia con GroupDocs.Annotation, puede visitar GroupDocs[foro](https://forum.groupdocs.com/c/annotation/10) dedicado a consultas y debates relacionados con las anotaciones.
### ¿Cómo obtengo una licencia temporal para GroupDocs.Annotation?
 Puede adquirir una licencia temporal para GroupDocs.Annotation a través de GroupDocs[sitio web](https://purchase.groupdocs.com/temporary-license/), permitiéndole evaluar el producto en su totalidad.