---
title: Generar vista previa sin comentarios
linktitle: Generar vista previa sin comentarios
second_title: API GroupDocs.Annotation .NET
description: Aprenda cómo integrar perfectamente las capacidades de anotación de documentos en sus aplicaciones .NET utilizando GroupDocs.Annotation para .NET.
type: docs
weight: 14
url: /es/net/advanced-usage/generate-preview-without-comments/
---
## Introducción
GroupDocs.Annotation para .NET es una poderosa herramienta que permite a los desarrolladores incorporar funciones de anotación en sus aplicaciones .NET sin problemas. Ya sea que esté trabajando en un sistema de gestión de documentos, una plataforma de colaboración o cualquier otra aplicación que requiera capacidades de anotación de documentos, GroupDocs.Annotation proporciona un conjunto completo de herramientas para mejorar la funcionalidad de su aplicación.
## Requisitos previos
Antes de sumergirse en el uso de GroupDocs.Annotation para .NET, asegúrese de tener configurados los siguientes requisitos previos:
### 1. Instale GroupDocs.Annotation para .NET
 Para comenzar, debe descargar e instalar GroupDocs.Annotation para .NET. Puedes encontrar el enlace de descarga.[aquí](https://releases.groupdocs.com/annotation/net/). Siga las instrucciones de instalación proporcionadas en la documentación para un proceso de instalación sin problemas.
### 2. Obtener licencia
 GroupDocs.Annotation para .NET requiere una licencia para uso comercial. Puede adquirir una licencia de[aquí](https://purchase.groupdocs.com/buy) u optar por una licencia temporal[aquí](https://purchase.groupdocs.com/temporary-license/) con fines de prueba.
### 3. Familiaridad con .NET Framework
El conocimiento básico de .NET Framework y el lenguaje de programación C# es esencial para utilizar eficazmente GroupDocs.Annotation para .NET.

## Importar espacios de nombres
Ahora que ha configurado los requisitos previos, importemos los espacios de nombres necesarios a su aplicación .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Siga estas instrucciones paso a paso para generar una vista previa sin comentarios usando GroupDocs.Annotation para .NET:
## Paso 1: inicializar el anotador
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Paso 2: configurar las opciones de vista previa
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Paso 3: especificar el formato de vista previa y los números de página
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Paso 4: deshabilite la representación de comentarios
```csharp
    previewOptions.RenderComments = false;
```
## Paso 5: Generar vista previa
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Una vez que haya seguido estos pasos, su aplicación .NET podrá generar una vista previa de las páginas especificadas del documento sin mostrar comentarios.

## Conclusión
Incorporar funciones de anotación en sus aplicaciones .NET nunca ha sido tan fácil gracias a GroupDocs.Annotation para .NET. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente las capacidades de anotación de documentos en sus aplicaciones, mejorando la colaboración y la gestión de documentos.
## Preguntas frecuentes
### ¿GroupDocs.Annotation para .NET es compatible con todos los formatos de documentos?
GroupDocs.Annotation para .NET admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, PPTX, XLSX y más.
### ¿Puedo personalizar la apariencia de las anotaciones generadas usando GroupDocs.Annotation para .NET?
Sí, GroupDocs.Annotation para .NET proporciona amplias opciones de personalización, lo que le permite personalizar la apariencia de las anotaciones para satisfacer las necesidades de su aplicación.
### ¿GroupDocs.Annotation para .NET admite la colaboración multiusuario?
Sí, GroupDocs.Annotation para .NET ofrece funciones de anotación colaborativa, lo que permite a varios usuarios anotar documentos simultáneamente.
### ¿Hay soporte técnico disponible para GroupDocs.Annotation para .NET?
 Sí, el soporte técnico para GroupDocs.Annotation para .NET está disponible a través de[Foro de soporte](https://forum.groupdocs.com/c/annotation/10).
### ¿Puedo probar GroupDocs.Annotation para .NET de forma gratuita antes de comprarlo?
 Sí, puede explorar las funciones de GroupDocs.Annotation para .NET descargando la versión de prueba gratuita.[aquí](https://releases.groupdocs.com/).