---
title: Agregar anotación de resaltado de texto al documento
linktitle: Agregar anotación de resaltado de texto al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de resaltado de texto a documentos usando GroupDocs.Annotation para .NET. Mejore la colaboración y la productividad con este completo.
weight: 22
url: /es/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# Agregar anotación de resaltado de texto al documento

## Introducción
En el ámbito de la gestión de documentos y la colaboración, GroupDocs.Annotation para .NET surge como una solución sólida que permite a los desarrolladores integrar sin problemas anotaciones de resaltado de texto en sus aplicaciones. Este tutorial sirve como una guía completa para agregar anotaciones de resaltado de texto a documentos usando GroupDocs.Annotation para .NET. A través de instrucciones paso a paso y explicaciones detalladas, adquirirá competencia para aprovechar las capacidades de esta poderosa biblioteca.
## Requisitos previos
Antes de profundizar en la implementación de anotaciones de resaltado de texto, asegúrese de tener implementados los siguientes requisitos previos:
1. Configuración del entorno: tenga configurado un entorno de desarrollo adecuado para el desarrollo .NET.
2.  Instalación de GroupDocs.Annotation para .NET: descargue e instale GroupDocs.Annotation para .NET desde el archivo proporcionado[enlace de descarga](https://releases.groupdocs.com/annotation/net/).
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
#Ahora, dividamos el proceso de agregar anotaciones de resaltado de texto en varios pasos:
## Paso 1: definir la ruta de salida
Especifique la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
 Crear una instancia del`Annotator` clase, pasando el nombre del archivo del documento como parámetro:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Paso 3: crear una anotación resaltada
 Crear una instancia de`HighlightAnnotation` objeto y configurar sus propiedades:
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
## Paso 4: agregar anotación
Agregue la anotación resaltada creada al documento:
```csharp
annotator.Add(highlight);
```
## Paso 5: guardar el documento anotado
Guarde el documento anotado en la ruta de salida especificada:
```csharp
annotator.Save(outputPath);
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET ofrece un enfoque simplificado para incorporar anotaciones de resaltado de texto en documentos. Siguiendo los pasos descritos en este tutorial, los desarrolladores pueden mejorar sin problemas la colaboración de documentos y la productividad dentro de sus aplicaciones.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite varios formatos de documentos, incluidos PDF, Word, Excel y más. Consulte la documentación para obtener la lista completa.
### ¿Se pueden personalizar las anotaciones según requisitos específicos?
Sí, los desarrolladores tienen control total sobre las propiedades y la apariencia de las anotaciones, lo que permite la personalización para satisfacer diversas necesidades.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation para .NET?
 Sí, puede explorar las funciones de GroupDocs.Annotation para .NET accediendo a la prueba gratuita desde el sitio web proporcionado.[enlace](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
 Para obtener soporte y asistencia, puede visitar el foro GroupDocs.Annotation[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Qué opciones de licencia están disponibles para GroupDocs.Annotation para .NET?
 GroupDocs.Annotation para .NET ofrece varias opciones de licencia, incluidas licencias temporales para fines de prueba y licencias comerciales para entornos de producción. Visita la página de compra[aquí](https://purchase.groupdocs.com/buy) para más detalles.