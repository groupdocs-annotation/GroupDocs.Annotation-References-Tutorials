---
title: Rotar documentos PDF
linktitle: Rotar documentos PDF
second_title: API GroupDocs.Annotation .NET
description: Aprenda a rotar documentos PDF sin esfuerzo usando Groupdocs.Annotation para .NET. Mejorar la eficiencia de la gestión documental.
type: docs
weight: 22
url: /es/net/advanced-usage/rotating-pdf-documents/
---
## Introducción
Rotar documentos PDF puede ser una tarea crucial cuando se trata de archivos que deben verse o procesarse de manera diferente. En este tutorial, exploraremos cómo rotar documentos PDF paso a paso usando Groupdocs.Annotation para .NET.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:
1.  Groupdocs.Annotation para la biblioteca .NET: asegúrese de haber descargado e instalado la biblioteca Groupdocs.Annotation para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/annotation/net/).
2. Conocimientos básicos de programación C#: este tutorial asume que tiene conocimientos básicos del lenguaje de programación C# y de cómo trabajar con bibliotecas .NET.

## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios a su proyecto C# para acceder a la funcionalidad proporcionada por la biblioteca Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Paso 1: cargue el documento PDF
 Comience cargando el documento PDF que desea rotar usando el`Annotator` clase.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Paso 2: Establecer rotación y páginas de proceso
Especifique el ángulo de rotación y las páginas que desea rotar. En este ejemplo, rotaremos la primera página 90 grados en el sentido de las agujas del reloj.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Paso 3: guarde el documento rotado
Guarde el documento PDF rotado con los cambios especificados.
```csharp
annotator.Save("result.pdf");
```
## Paso 4: Mostrar confirmación
Informe al usuario que el documento se ha rotado correctamente.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusión
Rotar documentos PDF es una operación fundamental y con Groupdocs.Annotation para .NET se vuelve simple y eficiente. Si sigue los pasos descritos en este tutorial, podrá rotar fácilmente archivos PDF según sus necesidades.
## Preguntas frecuentes
### ¿Puedo rotar varias páginas en un documento PDF usando Groupdocs.Annotation para .NET?
 Sí, puede especificar varias páginas para rotar ajustando el`ProcessPages` propiedad en consecuencia.
### ¿Groupdocs.Annotation para .NET es compatible con todas las versiones de .NET framework?
Groupdocs.Annotation para .NET admite una amplia gama de versiones de .NET framework, lo que garantiza la compatibilidad con la mayoría de los entornos de desarrollo.
### ¿Groupdocs.Annotation para .NET ofrece opciones para rotar documentos PDF en diferentes direcciones?
Sí, puede rotar documentos PDF en el sentido de las agujas del reloj, en el sentido contrario a las agujas del reloj o en ángulos personalizados según sus requisitos.
### ¿Puedo integrar Groupdocs.Annotation para .NET en mi sistema de gestión de documentos existente?
Por supuesto, Groupdocs.Annotation para .NET ofrece opciones de integración perfectas, lo que le permite mejorar las capacidades de gestión de documentos sin esfuerzo.
### ¿Existe una versión de prueba disponible para Groupdocs.Annotation para .NET?
 Sí, puedes obtener una versión de prueba gratuita en[aquí](https://releases.groupdocs.com/).