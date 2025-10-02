---
"description": "Explore el poder de GroupDocs.Annotation para .NET y agregue sin esfuerzo capacidades de anotación de documentos a sus aplicaciones."
"linktitle": "Agregar anotación de fragmento de texto de búsqueda al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de fragmento de texto de búsqueda al documento"
"url": "/es/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Agregar anotación de fragmento de texto de búsqueda al documento

## Introducción
En el ámbito del desarrollo .NET, GroupDocs.Annotation destaca como una potente herramienta para anotar documentos sin problemas. Tanto si eres un desarrollador experimentado como si te estás iniciando en el mundo de .NET, este completo tutorial te guiará por los fundamentos del uso de GroupDocs.Annotation para .NET, desde la importación de espacios de nombres hasta el dominio de las complejidades de añadir anotaciones de fragmentos de texto de búsqueda a tus documentos.
## Introducción
GroupDocs.Annotation para .NET permite a los desarrolladores incorporar funciones de anotación de documentos en sus aplicaciones sin esfuerzo. Gracias a su API intuitiva y sus robustas funciones, los desarrolladores pueden anotar en diversos formatos de documentos, como PDF, documentos de Microsoft Office, imágenes y más.
## Prerrequisitos
Antes de sumergirse en GroupDocs.Annotation para .NET, asegúrese de tener los siguientes requisitos previos:

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
## Paso 1: Definir la ruta de salida
Comience por definir la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
A continuación, inicialice una instancia de `Annotator` clase proporcionando la ruta al documento que desea anotar:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: Crear una anotación de fragmento de texto de búsqueda
Crear una `SearchTextFragment` objeto con las propiedades deseadas, como texto a buscar, tamaño de fuente, familia de fuentes, color de fuente y color de fondo:
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
## Paso 4: Agregar anotación
Agregue la anotación del fragmento de texto de búsqueda creado al documento usando el `Add` método del anotador:
```csharp
annotator.Add(searchText);
```
## Paso 5: Guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada:
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Informar al usuario que el documento se ha guardado correctamente:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET simplifica la adición de anotaciones a los documentos, mejorando la colaboración y la revisión de documentos. Siguiendo los pasos descritos en esta guía, podrá integrar fácilmente las funciones de anotación de documentos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Annotation es compatible con todos los formatos de documentos?
Sí, GroupDocs.Annotation admite una amplia gama de formatos de documentos, incluidos PDF, documentos de Microsoft Office, imágenes y más.
### ¿Puedo personalizar la apariencia de las anotaciones?
¡Por supuesto! GroupDocs.Annotation ofrece amplias opciones de personalización para las anotaciones, permitiéndole ajustar propiedades como el tamaño de fuente, el color y el estilo.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation?
Sí, puedes acceder a una prueba gratuita de GroupDocs.Annotation para explorar sus características y capacidades antes de realizar una compra. [aquí](https://releases.groupdocs.com/)..
### ¿Dónde puedo encontrar soporte para GroupDocs.Annotation?
Para obtener soporte y asistencia con GroupDocs.Annotation, puede visitar GroupDocs. [foro](https://forum.groupdocs.com/c/annotation/10) Dedicado a consultas y discusiones relacionadas con anotaciones.
### ¿Cómo obtengo una licencia temporal para GroupDocs.Annotation?
Puede adquirir una licencia temporal para GroupDocs.Annotation a través de GroupDocs [sitio web](https://purchase.groupdocs.com/temporary-license/), permitiéndole evaluar el producto en su totalidad.