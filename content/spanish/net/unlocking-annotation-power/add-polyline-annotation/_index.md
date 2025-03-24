---
title: Agregar anotación de polilínea al documento
linktitle: Agregar anotación de polilínea al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de polilínea a documentos usando GroupDocs.Annotation para .NET. Mejore los procesos de colaboración y revisión de documentos sin esfuerzo.
weight: 18
url: /es/net/unlocking-annotation-power/add-polyline-annotation/
---
## Introducción
GroupDocs.Annotation para .NET es una poderosa herramienta que permite a los desarrolladores anotar documentos PDF y Microsoft Office mediante programación. Entre sus características se encuentra la capacidad de agregar anotaciones de polilíneas a los documentos, mejorando la colaboración y los procesos de revisión de documentos.
## Requisitos previos
Antes de continuar con este tutorial, asegúrese de tener lo siguiente:
- Visual Studio instalado en su sistema.
- Conocimientos básicos del lenguaje de programación C#.
-  GroupDocs.Annotation para la biblioteca .NET instalada. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/annotation/net/).

## Importar espacios de nombres
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: definir la ruta de salida
Primero, defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
Inicialice el anotador proporcionando el nombre del documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: crear un objeto de anotación de polilínea
Cree un objeto de anotación de polilínea y establezca sus propiedades, como posición, mensaje, opacidad, color de pluma, estilo de pluma y ancho de pluma.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Paso 4: agregar anotación de polilínea
Agregue la anotación de polilínea al documento usando el objeto anotador.
```csharp
annotator.Add(polyline);
```
## Paso 5: guardar el documento
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Muestra un mensaje confirmando el guardado exitoso del documento.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, hemos aprendido cómo agregar una anotación de polilínea a un documento usando GroupDocs.Annotation para .NET. Esta característica mejora los procesos de colaboración y revisión de documentos, facilitando a los usuarios comunicar comentarios y sugerencias de manera efectiva.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite formatos de documentos populares, como PDF y formatos de Microsoft Office, incluidos Word, Excel y PowerPoint.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, puede personalizar varias propiedades de las anotaciones, como color, opacidad, estilo y ancho, para adaptarlas a sus necesidades.
### ¿GroupDocs.Annotation para .NET ofrece una prueba gratuita?
 Sí, puede aprovechar una prueba gratuita de GroupDocs.Annotation para .NET visitando[este enlace](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar documentación para GroupDocs.Annotation para .NET?
 Puede encontrar la documentación de GroupDocs.Annotation para .NET[aquí](https://tutorials.groupdocs.com/annotation/net/).
### ¿Cómo puedo obtener soporte para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
 Puede obtener soporte visitando el foro GroupDocs.Annotation[aquí](https://forum.groupdocs.com/c/annotation/10).