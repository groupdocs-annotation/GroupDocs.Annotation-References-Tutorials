---
title: Agregar anotación de redacción de texto al documento
linktitle: Agregar anotación de redacción de texto al documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda a agregar anotaciones de redacción de texto a documentos PDF usando GroupDocs.Annotation para .NET. Proteja la información confidencial sin esfuerzo.
weight: 23
url: /es/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Introducción
Agregar una anotación de redacción de texto a un documento puede ser un paso crucial para administrar de forma segura información confidencial. GroupDocs.Annotation para .NET proporciona una solución sólida para lograr esto sin problemas. En este tutorial, lo guiaremos a través del proceso de agregar una anotación de redacción de texto a su documento paso a paso.
## Requisitos previos
Antes de comenzar, asegúrese de cumplir con los siguientes requisitos previos:
1.  GroupDocs.Annotation para .NET: asegúrese de haber instalado la biblioteca GroupDocs.Annotation para .NET. Puedes descargarlo desde el[sitio web](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo con un IDE compatible con .NET, como Visual Studio.

## Importando espacios de nombres
En primer lugar, importemos los espacios de nombres necesarios a nuestro proyecto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: definir la ruta de salida
Defina la ruta de salida donde desea guardar el documento anotado. Asegúrese de que sea accesible y grabable.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: inicializar el anotador
 Inicialice el anotador con la ruta del documento de entrada. Reemplazar`"input.pdf"` con la ruta a su documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí.
}
```
## Paso 3: crear una anotación de redacción de texto
 Crear un`TextRedactionAnnotation`objeto con las propiedades requeridas como`PageNumber`, `FontColor` , y`Points`. Personalice la anotación según sus requisitos.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Paso 4: agregue anotaciones y guarde
Agregue la anotación creada al documento usando el anotador y guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Paso 5: verificar la salida
Finalmente, confirme que el documento se haya guardado correctamente en la ruta de salida especificada.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, hemos recorrido el proceso de agregar una anotación de redacción de texto a un documento usando GroupDocs.Annotation para .NET. Con estos pasos, ahora puede administrar de forma segura la información confidencial dentro de sus documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación de redacción de texto?
Sí, puede personalizar varias propiedades, como el color de fuente, el color de relleno y la opacidad, para adaptarlas a sus necesidades.
### ¿Hay una versión de prueba disponible antes de comprar?
 Sí, puedes acceder a una versión de prueba gratuita desde[sitio web](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte si tengo algún problema?
 Puede obtener soporte en el foro de la comunidad GroupDocs.Annotation.[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Necesito una licencia temporal para realizar pruebas?
 Sí, puede obtener una licencia temporal de la[pagina de compra](https://purchase.groupdocs.com/temporary-license/)para las pruebas.
### ¿Puedo agregar varias anotaciones a un solo documento?
Por supuesto, GroupDocs.Annotation le permite agregar varios tipos de anotaciones y múltiples instancias a un solo documento.