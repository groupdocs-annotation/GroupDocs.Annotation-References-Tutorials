---
"description": "Aprenda a rotar documentos PDF fácilmente con Groupdocs.Annotation para .NET. Mejore la eficiencia de la gestión de documentos."
"linktitle": "Rotación de documentos PDF"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Rotación de documentos PDF"
"url": "/es/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Rotación de documentos PDF

## Introducción
Rotar documentos PDF puede ser crucial al trabajar con archivos que requieren una visualización o procesamiento diferente. En este tutorial, exploraremos cómo rotar documentos PDF paso a paso con Groupdocs.Annotation para .NET.
## Prerrequisitos
Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:
1. Biblioteca Groupdocs.Annotation para .NET: Asegúrese de haber descargado e instalado la biblioteca Groupdocs.Annotation para .NET. Puede descargarla desde [aquí](https://releases.groupdocs.com/annotation/net/).
2. Conocimientos básicos de programación en C#: este tutorial asume que tienes un conocimiento básico del lenguaje de programación C# y cómo trabajar con bibliotecas .NET.

## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios en su proyecto C# para acceder a la funcionalidad proporcionada por la biblioteca Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Paso 1: Cargue el documento PDF
Comience cargando el documento PDF que desea rotar utilizando el `Annotator` clase.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Paso 2: Establecer la rotación y procesar páginas
Especifique el ángulo de rotación y las páginas que desea rotar. En este ejemplo, rotaremos la primera página 90 grados en el sentido de las agujas del reloj.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Paso 3: Guardar el documento rotado
Guarde el documento PDF girado con los cambios especificados.
```csharp
annotator.Save("result.pdf");
```
## Paso 4: Confirmación de visualización
Informar al usuario que el documento se ha girado correctamente.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusión
Rotar documentos PDF es una operación fundamental, y con Groupdocs.Annotation para .NET, es más sencillo y eficiente. Siguiendo los pasos de este tutorial, podrá rotar fácilmente sus archivos PDF según sus necesidades.
## Preguntas frecuentes
### ¿Puedo rotar varias páginas en un documento PDF usando Groupdocs.Annotation para .NET?
Sí, puedes especificar varias páginas para rotar ajustando el `ProcessPages` propiedad en consecuencia.
### ¿Groupdocs.Annotation para .NET es compatible con todas las versiones de .NET Framework?
Groupdocs.Annotation for .NET admite una amplia gama de versiones de .NET Framework, lo que garantiza la compatibilidad con la mayoría de los entornos de desarrollo.
### ¿Groupdocs.Annotation para .NET proporciona opciones para rotar documentos PDF en diferentes direcciones?
Sí, puede rotar documentos PDF en sentido horario, antihorario o en ángulos personalizados según sus necesidades.
### ¿Puedo integrar Groupdocs.Annotation for .NET en mi sistema de gestión de documentos existente?
Por supuesto, Groupdocs.Annotation para .NET ofrece opciones de integración perfectas, lo que le permite mejorar las capacidades de gestión de documentos sin esfuerzo.
### ¿Hay una versión de prueba disponible para Groupdocs.Annotation para .NET?
Sí, puedes obtener una versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/).