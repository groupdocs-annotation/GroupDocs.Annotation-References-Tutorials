---
"description": "Aprenda a agregar anotaciones de resaltado de texto a documentos con GroupDocs.Annotation para .NET. Mejore la colaboración y la productividad con esta completa herramienta."
"linktitle": "Agregar anotación de resaltado de texto al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de resaltado de texto al documento"
"url": "/es/net/unlocking-annotation-power/add-text-highlight-annotation/"
type: docs
"weight": 22
---

# Agregar anotación de resaltado de texto al documento

## Introducción
En el ámbito de la gestión y colaboración documental, GroupDocs.Annotation para .NET se perfila como una solución robusta que permite a los desarrolladores integrar a la perfección las anotaciones de resaltado de texto en sus aplicaciones. Este tutorial es una guía completa para añadir anotaciones de resaltado de texto a documentos con GroupDocs.Annotation para .NET. Mediante instrucciones paso a paso y explicaciones detalladas, adquirirá experiencia en el uso de las capacidades de esta potente biblioteca.
## Prerrequisitos
Antes de profundizar en la implementación de anotaciones de resaltado de texto, asegúrese de tener los siguientes requisitos previos:
1. Configuración del entorno: tenga un entorno de desarrollo adecuado configurado para el desarrollo .NET.
2. Instalación de GroupDocs.Annotation para .NET: Descargue e instale GroupDocs.Annotation para .NET desde el sitio web proporcionado. [enlace de descarga](https://releases.groupdocs.com/annotation/net/).
3. Familiaridad con C#: comprensión básica del lenguaje de programación C#.
4. Documento para anotar: prepare un documento (por ejemplo, PDF) que desee anotar.

## Importar espacios de nombres
Para comenzar, importe los espacios de nombres necesarios en su código C# para utilizar las funcionalidades de GroupDocs.Annotation para .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Ahora, desglosemos el proceso de agregar anotaciones de resaltado de texto en varios pasos:
## Paso 1: Definir la ruta de salida
Especifique la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Crear una instancia de la `Annotator` clase, pasando el nombre del archivo del documento como parámetro:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Paso 3: Crear una anotación destacada
Instanciar una `HighlightAnnotation` objeto y configurar sus propiedades:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
Agregue la anotación resaltada creada al documento:
```csharp
annotator.Add(highlight);
```
## Paso 5: Guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada:
```csharp
annotator.Save(outputPath);
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET ofrece un enfoque simplificado para incorporar anotaciones de resaltado de texto en los documentos. Siguiendo los pasos descritos en este tutorial, los desarrolladores pueden mejorar la colaboración y la productividad en sus aplicaciones.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite varios formatos de documentos, como PDF, Word, Excel y más. Consulte la documentación para ver la lista completa.
### ¿Se pueden personalizar las anotaciones según requisitos específicos?
Sí, los desarrolladores tienen control total sobre las propiedades y la apariencia de las anotaciones, lo que permite la personalización para satisfacer diversas necesidades.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation para .NET?
Sí, puede explorar las características de GroupDocs.Annotation para .NET accediendo a la prueba gratuita desde el sitio web proporcionado. [enlace](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener ayuda para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
Para obtener ayuda y asistencia, puede visitar el foro GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Qué opciones de licencia están disponibles para GroupDocs.Annotation para .NET?
GroupDocs.Annotation para .NET ofrece diversas opciones de licencia, incluyendo licencias temporales para pruebas y licencias comerciales para entornos de producción. Visite la página de compra. [aquí](https://purchase.groupdocs.com/buy) Para más detalles.