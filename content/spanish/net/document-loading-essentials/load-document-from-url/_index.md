---
"description": "Aprenda a anotar documentos PDF mediante programación con GroupDocs.Annotation para .NET. Tutorial paso a paso con ejemplos de código."
"linktitle": "Cargar documento desde URL"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Cargar documento desde URL"
"url": "/es/net/document-loading-essentials/load-document-from-url/"
type: docs
"weight": 15
---

# Cargar documento desde URL

## Introducción
GroupDocs.Annotation para .NET es una biblioteca repleta de funciones que permite a los desarrolladores añadir funciones de anotación a sus aplicaciones .NET sin esfuerzo. Con GroupDocs.Annotation, puede anotar documentos PDF mediante programación, lo que permite a los usuarios resaltar texto, añadir comentarios, dibujar formas y mucho más. Este tutorial le guiará por los pasos para cargar un documento desde una URL, añadir anotaciones y guardar el documento anotado con GroupDocs.Annotation para .NET.
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Visual Studio: asegúrese de tener Visual Studio instalado en su equipo de desarrollo.
2. GroupDocs.Annotation para .NET: Descargue e instale GroupDocs.Annotation para .NET desde [sitio web](https://releases.groupdocs.com/annotation/net/).
3. Conocimientos básicos de C#: Familiarícese con el lenguaje de programación C#.
4. Conexión a Internet: Necesitará una conexión a Internet para acceder a recursos externos y descargar archivos de muestra.

## Importar espacios de nombres
Primero, importemos los espacios de nombres necesarios en su proyecto C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Paso 1: Cargar documento desde la URL
Para anotar un documento PDF desde una URL, siga estos pasos:
### Paso 1.1: Definir la ruta de salida
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Paso 1.2: Especificar URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Paso 1.3: Cargar documento
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Añade anotaciones aquí
    annotator.Save(outputPath);
}
```
## Paso 2: Agregar anotaciones
Ahora, agreguemos anotaciones al documento cargado. En este ejemplo, agregaremos una anotación de área:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Paso 3: Guardar el documento anotado
Por último, guarde el documento anotado en la ruta de salida especificada:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En este tutorial, aprendimos a anotar documentos PDF con GroupDocs.Annotation para .NET. Siguiendo la guía paso a paso, podrá integrar fácilmente la función de anotación en sus aplicaciones .NET, lo que permitirá a los usuarios colaborar eficazmente en archivos PDF.

## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los marcos .NET?
Sí, GroupDocs.Annotation para .NET es compatible con varios marcos .NET, incluidos .NET Framework, .NET Core y .NET Standard.
### ¿Puedo personalizar la apariencia de las anotaciones?
¡Por supuesto! GroupDocs.Annotation para .NET ofrece amplias opciones de personalización, lo que le permite modificar la apariencia y el comportamiento de las anotaciones según sus necesidades.
### ¿Hay una prueba gratuita disponible para GroupDocs.Annotation para .NET?
Sí, puede descargar una versión de prueba gratuita de GroupDocs.Annotation para .NET desde [sitio web](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Annotation para .NET?
Si tiene algún problema técnico o preguntas sobre GroupDocs.Annotation para .NET, puede buscar ayuda en el [foro de soporte](https://forum.groupdocs.com/c/annotation/10).
### ¿Dónde puedo comprar una licencia para GroupDocs.Annotation para .NET?
Puede comprar una licencia para GroupDocs.Annotation para .NET en [página de compra](https://purchase.groupdocs.com/buy).