---
title: Cargar documento desde el disco local
linktitle: Cargar documento desde el disco local
second_title: API GroupDocs.Annotation .NET
description: Desbloquee el poder de la anotación de documentos con GroupDocs.Annotation para .NET. Integre perfectamente funciones de anotación en sus aplicaciones .NET.
weight: 13
url: /es/net/document-loading-essentials/load-document-from-local-disk/
---

# Cargar documento desde el disco local

## Introducción
Liberar el potencial de la anotación de documentos nunca ha sido tan fácil con GroupDocs.Annotation para .NET. Esta potente herramienta permite a los desarrolladores integrar funciones de anotación sólidas sin problemas en sus aplicaciones .NET. En esta guía completa, lo guiaremos a través del proceso de aprovechar GroupDocs.Annotation para .NET para anotar documentos paso a paso. Ya sea que sea un desarrollador experimentado o recién esté comenzando, este tutorial le brindará el conocimiento para mejorar la colaboración en documentos y optimizar su flujo de trabajo.
## Requisitos previos
Antes de profundizar en la anotación de documentos con GroupDocs.Annotation para .NET, asegúrese de tener los siguientes requisitos previos:
1. Conocimientos básicos de C#: la familiaridad con los fundamentos del lenguaje de programación C# es esencial.
2. Instalación de GroupDocs.Annotation para .NET: Descargue e instale GroupDocs.Annotation para .NET desde[aquí](https://releases.groupdocs.com/annotation/net/).
3. Entorno de desarrollo: configure un entorno de desarrollo con Visual Studio o cualquier IDE compatible.

## Importar espacios de nombres
Para comenzar a anotar documentos con GroupDocs.Annotation para .NET, importe los espacios de nombres necesarios a su proyecto:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Paso 1: cargar el documento desde el disco local
Primero, debe cargar el documento desde su disco local. Utilice el siguiente fragmento de código:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 2: definir el área de anotación
A continuación, defina el área de anotación. En este ejemplo, crearemos una AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Paso 3: guardar el documento con anotaciones
Después de anotar el documento, guárdelo con las anotaciones:
```csharp
    annotator.Save(outputPath);
}
```
## Paso 4: Mostrar mensaje de éxito
Finalmente, muestre un mensaje de éxito con la ruta de salida:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET proporciona una solución sólida para integrar capacidades de anotación de documentos en sus aplicaciones .NET. Si sigue esta guía paso a paso, podrá anotar documentos sin esfuerzo y mejorar la colaboración en sus proyectos.
## Preguntas frecuentes
### ¿Puedo probar GroupDocs.Annotation para .NET antes de comprarlo?
 Sí, puedes descargar una prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar documentación para GroupDocs.Annotation para .NET?
 Puedes acceder a la documentación[aquí](https://tutorials.groupdocs.com/annotation/net/).
### ¿Cómo puedo obtener una licencia temporal de GroupDocs.Annotation para .NET?
 Puede obtener una licencia temporal de[aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Hay soporte disponible para GroupDocs.Annotation para .NET?
 Sí, puedes encontrar soporte en el foro de GroupDocs.[aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Dónde puedo comprar GroupDocs.Annotation para .NET?
 Puede comprar GroupDocs.Annotation para .NET[aquí](https://purchase.groupdocs.com/buy).