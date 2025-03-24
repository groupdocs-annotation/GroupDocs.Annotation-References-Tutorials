---
title: Agregar anotación de elipse al documento
linktitle: Agregar anotación de elipse al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de elipse a documentos en .NET usando GroupDocs.Annotation. Mejore la colaboración y la comunicación sin esfuerzo.
weight: 13
url: /es/net/unlocking-annotation-power/add-ellipse-annotation/
---

# Agregar anotación de elipse al documento

## Introducción
En este tutorial, aprenderá cómo agregar una anotación de elipse a un documento usando GroupDocs.Annotation para .NET. Esta guía paso a paso lo guiará a través del proceso, asegurándose de que comprenda cada paso con claridad.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Annotation para .NET: asegúrese de haber descargado e instalado GroupDocs.Annotation para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. IDE (entorno de desarrollo integrado): necesitará un IDE instalado en su sistema, como Visual Studio, para escribir y ejecutar el código.

## Importar espacios de nombres
Primero, importe los espacios de nombres necesarios a su proyecto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: establecer la ruta de salida
Defina la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
Inicialice el anotador proporcionando la ruta del documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: crear una anotación de elipse
 Crear una instancia del`EllipseAnnotation` clase y establece sus propiedades:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
Agregue la anotación de elipse al documento:
```csharp
annotator.Add(ellipse);
```
## Paso 5: guardar el documento
Guarde el documento anotado en la ruta de salida:
```csharp
annotator.Save(outputPath);
```

## Conclusión
¡Felicidades! Ha agregado con éxito una anotación de elipse a un documento usando GroupDocs.Annotation para .NET. Ahora puede integrar esta funcionalidad en sus aplicaciones .NET para mejorar la colaboración y la comunicación en documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación de elipse?
Sí, puede personalizar varias propiedades, como color de fondo, color de borde, opacidad, etc., según sus requisitos.
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX, XLSX y más.
### ¿Puedo agregar varias anotaciones a un solo documento?
Sí, puedes agregar múltiples anotaciones, incluidas elipses, rectángulos, texto, etc., a un solo documento.
### ¿Existe una versión de prueba disponible para fines de prueba?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/) para evaluar sus características.
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Annotation para .NET?
 Puede obtener soporte técnico en el foro de la comunidad GroupDocs.Annotation.[aquí](https://forum.groupdocs.com/c/annotation/10).