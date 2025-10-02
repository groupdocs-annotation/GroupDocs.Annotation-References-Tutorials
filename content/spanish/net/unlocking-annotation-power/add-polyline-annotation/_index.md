---
"description": "Aprenda a agregar anotaciones de polilínea a documentos con GroupDocs.Annotation para .NET. Mejore la colaboración y la revisión de documentos sin esfuerzo."
"linktitle": "Agregar anotación de polilínea al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de polilínea al documento"
"url": "/es/net/unlocking-annotation-power/add-polyline-annotation/"
type: docs
"weight": 18
---

# Agregar anotación de polilínea al documento

## Introducción
GroupDocs.Annotation para .NET es una potente herramienta que permite a los desarrolladores anotar documentos PDF y de Microsoft Office mediante programación. Entre sus funciones se encuentra la posibilidad de añadir anotaciones de polilínea a los documentos, lo que mejora la colaboración y la revisión de documentos.
## Prerrequisitos
Antes de continuar con este tutorial, asegúrese de tener lo siguiente:
- Visual Studio instalado en su sistema.
- Conocimientos básicos del lenguaje de programación C#.
- La biblioteca GroupDocs.Annotation para .NET está instalada. Puede descargarla desde [aquí](https://releases.groupdocs.com/annotation/net/).

## Importar espacios de nombres
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: Definir la ruta de salida
Primero, defina la ruta de salida donde se guardará el documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Inicialice el anotador proporcionando el nombre del documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 3: Crear un objeto de anotación de polilínea
Cree un objeto de anotación de polilínea y configure sus propiedades, como posición, mensaje, opacidad, color de pluma, estilo de pluma y ancho de pluma.
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
## Paso 4: Agregar anotación de polilínea
Agregue la anotación de polilínea al documento utilizando el objeto anotador.
```csharp
annotator.Add(polyline);
```
## Paso 5: Guardar el documento
Guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Save(outputPath);
```
## Paso 6: Mostrar mensaje de éxito
Muestra un mensaje confirmando que el documento se ha guardado correctamente.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, aprendimos a agregar una anotación de polilínea a un documento con GroupDocs.Annotation para .NET. Esta función mejora la colaboración y la revisión de documentos, facilitando a los usuarios la comunicación eficaz de comentarios y sugerencias.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation for .NET admite formatos de documentos populares como PDF y formatos de Microsoft Office, incluidos Word, Excel y PowerPoint.
### ¿Puedo personalizar la apariencia de las anotaciones?
Sí, puede personalizar varias propiedades de las anotaciones, como el color, la opacidad, el estilo y el ancho, para adaptarlas a sus necesidades.
### ¿GroupDocs.Annotation para .NET ofrece una prueba gratuita?
Sí, puede obtener una prueba gratuita de GroupDocs.Annotation para .NET visitando [este enlace](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar documentación de GroupDocs.Annotation para .NET?
Puede encontrar la documentación de GroupDocs.Annotation para .NET [aquí](https://tutorials.groupdocs.com/annotation/net/).
### ¿Cómo puedo obtener ayuda para cualquier problema o consulta relacionada con GroupDocs.Annotation para .NET?
Puede obtener ayuda visitando el foro GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).