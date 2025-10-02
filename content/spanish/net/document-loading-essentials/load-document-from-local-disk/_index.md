---
"description": "Descubra el potencial de la anotación de documentos con GroupDocs.Annotation para .NET. Integre fácilmente las funciones de anotación en sus aplicaciones .NET."
"linktitle": "Cargar documento desde el disco local"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Cargar documento desde el disco local"
"url": "/es/net/document-loading-essentials/load-document-from-local-disk/"
type: docs
"weight": 13
---

# Cargar documento desde el disco local

## Introducción
Aprovechar el potencial de la anotación de documentos nunca ha sido tan fácil con GroupDocs.Annotation para .NET. Esta potente herramienta permite a los desarrolladores integrar fácilmente funciones de anotación robustas en sus aplicaciones .NET. En esta guía completa, le guiaremos paso a paso por el proceso de usar GroupDocs.Annotation para .NET para anotar documentos. Tanto si es un desarrollador experimentado como si está empezando, este tutorial le proporcionará los conocimientos necesarios para mejorar la colaboración en documentos y optimizar su flujo de trabajo.
## Prerrequisitos
Antes de sumergirse en la anotación de documentos con GroupDocs.Annotation para .NET, asegúrese de tener los siguientes requisitos previos:
1. Conocimientos básicos de C#: Es esencial estar familiarizado con los fundamentos del lenguaje de programación C#.
2. Instalación de GroupDocs.Annotation para .NET: Descargue e instale GroupDocs.Annotation para .NET desde [aquí](https://releases.groupdocs.com/annotation/net/).
3. Entorno de desarrollo: configure un entorno de desarrollo con Visual Studio o cualquier IDE compatible.

## Importar espacios de nombres
Para comenzar a anotar documentos con GroupDocs.Annotation para .NET, importe los espacios de nombres necesarios en su proyecto:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Paso 1: Cargar documento desde el disco local
Primero, debe cargar el documento desde su disco local. Use el siguiente fragmento de código:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Paso 2: Definir el área de anotación
A continuación, defina el área de anotación. En este ejemplo, crearemos una Anotación de Área:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Paso 3: Guardar el documento con anotaciones
Después de anotar el documento, guárdelo con las anotaciones:
```csharp
    annotator.Save(outputPath);
}
```
## Paso 4: Mostrar mensaje de éxito
Finalmente, muestra un mensaje de éxito con la ruta de salida:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusión
En conclusión, GroupDocs.Annotation para .NET ofrece una solución robusta para integrar funciones de anotación de documentos en sus aplicaciones .NET. Siguiendo esta guía paso a paso, podrá anotar documentos fácilmente y mejorar la colaboración en sus proyectos.
## Preguntas frecuentes
### ¿Puedo probar GroupDocs.Annotation para .NET antes de comprarlo?
Sí, puedes descargar una versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar documentación de GroupDocs.Annotation para .NET?
Puedes acceder a la documentación [aquí](https://tutorials.groupdocs.com/annotation/net/).
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Annotation para .NET?
Puede obtener una licencia temporal en [aquí](https://purchase.groupdocs.com/temporary-license/).
### ¿Hay soporte disponible para GroupDocs.Annotation para .NET?
Sí, puedes encontrar ayuda en el foro de GroupDocs [aquí](https://forum.groupdocs.com/c/annotation/10).
### ¿Dónde puedo comprar GroupDocs.Annotation para .NET?
Puedes adquirir GroupDocs.Annotation para .NET [aquí](https://purchase.groupdocs.com/buy).