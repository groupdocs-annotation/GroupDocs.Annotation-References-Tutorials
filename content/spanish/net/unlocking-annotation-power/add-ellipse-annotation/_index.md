---
"description": "Aprenda a agregar anotaciones de elipse a documentos en .NET con GroupDocs.Annotation. Mejore la colaboración y la comunicación sin esfuerzo."
"linktitle": "Agregar anotación de elipse al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de elipse al documento"
"url": "/es/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Agregar anotación de elipse al documento

## Introducción
En este tutorial, aprenderá a agregar una anotación de elipse a un documento con GroupDocs.Annotation para .NET. Esta guía paso a paso le guiará por el proceso, asegurándose de que comprenda cada paso con claridad.
## Prerrequisitos
Antes de comenzar, asegúrese de tener lo siguiente:
1. GroupDocs.Annotation para .NET: Asegúrese de haber descargado e instalado GroupDocs.Annotation para .NET. Puede descargarlo desde [aquí](https://releases.groupdocs.com/annotation/net/).
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
## Paso 1: Establecer la ruta de salida
Define la ruta de salida donde se guardará el documento anotado:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Inicialice el anotador proporcionando la ruta del documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: Crear una anotación de elipse
Crear una instancia de la `EllipseAnnotation` clase y establecer sus propiedades:
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
## Paso 4: Agregar anotación
Añade la anotación de elipse al documento:
```csharp
annotator.Add(ellipse);
```
## Paso 5: Guardar el documento
Guarde el documento anotado en la ruta de salida:
```csharp
annotator.Save(outputPath);
```

## Conclusión
¡Felicitaciones! Ha agregado correctamente una anotación de elipse a un documento con GroupDocs.Annotation para .NET. Ahora puede integrar esta funcionalidad en sus aplicaciones .NET para mejorar la colaboración y la comunicación en los documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación de elipse?
Sí, puede personalizar varias propiedades, como el color de fondo, el color del borde, la opacidad, etc., según sus requisitos.
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX, XLSX y más.
### ¿Puedo agregar múltiples anotaciones a un solo documento?
Sí, puedes agregar múltiples anotaciones, incluidas elipses, rectángulos, texto, etc., a un solo documento.
### ¿Existe una versión de prueba disponible para fines de prueba?
Sí, puedes descargar una versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/) para evaluar sus características.
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Annotation para .NET?
Puede obtener soporte técnico en el foro de la comunidad GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).