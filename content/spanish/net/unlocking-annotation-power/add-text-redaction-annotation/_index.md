---
"description": "Aprenda a agregar anotaciones de redacción de texto a documentos PDF con GroupDocs.Annotation para .NET. Proteja su información confidencial fácilmente."
"linktitle": "Agregar anotación de redacción de texto al documento"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Agregar anotación de redacción de texto al documento"
"url": "/es/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Agregar anotación de redacción de texto al documento

## Introducción
Añadir una anotación de redacción de texto a un documento puede ser crucial para gestionar de forma segura información confidencial. GroupDocs.Annotation para .NET ofrece una solución robusta para lograrlo sin problemas. En este tutorial, le guiaremos paso a paso en el proceso de añadir una anotación de redacción de texto a su documento.
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. GroupDocs.Annotation para .NET: Asegúrese de tener instalada la biblioteca GroupDocs.Annotation para .NET. Puede descargarla desde [sitio web](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo con un IDE compatible con .NET como Visual Studio.

## Importación de espacios de nombres
En primer lugar, importemos los espacios de nombres necesarios a nuestro proyecto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Paso 1: Definir la ruta de salida
Define la ruta de salida donde quieres guardar el documento anotado. Asegúrate de que sea accesible y tenga permisos de escritura.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Paso 2: Inicializar el anotador
Inicialice el anotador con la ruta del documento de entrada. Reemplace `"input.pdf"` con la ruta a su documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // El código de anotación irá aquí
}
```
## Paso 3: Crear una anotación de redacción de texto
Crear una `TextRedactionAnnotation` objeto con las propiedades requeridas como `PageNumber`, `FontColor`, y `Points`Personalice la anotación según sus requisitos.
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
## Paso 4: Agregar anotación y guardar
Agregue la anotación creada al documento utilizando el anotador y guarde el documento anotado en la ruta de salida especificada.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Paso 5: Verificar la salida
Por último, confirme que el documento se haya guardado correctamente en la ruta de salida especificada.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, explicamos el proceso para agregar una anotación de redacción de texto a un documento con GroupDocs.Annotation para .NET. Con estos pasos, ahora puede administrar de forma segura la información confidencial de sus documentos.
## Preguntas frecuentes
### ¿Puedo personalizar la apariencia de la anotación de redacción de texto?
Sí, puede personalizar varias propiedades, como el color de fuente, el color de relleno y la opacidad, para adaptarlas a sus necesidades.
### ¿Hay una versión de prueba disponible antes de comprar?
Sí, puedes acceder a una versión de prueba gratuita desde [sitio web](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener ayuda si encuentro algún problema?
Puede obtener ayuda del foro de la comunidad GroupDocs.Annotation [aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Necesito una licencia temporal para realizar pruebas?
Sí, puede obtener una licencia temporal de la [página de compra](https://purchase.groupdocs.com/temporary-license/) para probar.
### ¿Puedo agregar múltiples anotaciones a un solo documento?
Por supuesto, GroupDocs.Annotation le permite agregar varios tipos de anotaciones y múltiples instancias a un solo documento.