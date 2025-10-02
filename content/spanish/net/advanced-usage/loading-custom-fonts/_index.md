---
"description": "Aprenda a cargar fuentes personalizadas sin problemas en GroupDocs.Annotation para .NET y optimizar la anotación de documentos. Siga nuestra guía paso a paso para una integración sencilla."
"linktitle": "Cargando fuentes personalizadas"
"second_title": "API .NET de GroupDocs.Annotation"
"title": "Cargando fuentes personalizadas"
"url": "/es/net/advanced-usage/loading-custom-fonts/"
type: docs
"weight": 20
---

# Cargando fuentes personalizadas

## Introducción
GroupDocs.Annotation para .NET es una potente biblioteca que permite a los desarrolladores añadir funciones de anotación a sus aplicaciones .NET sin esfuerzo. Una de sus principales funciones es la posibilidad de cargar fuentes personalizadas, lo que permite una mayor personalización y flexibilidad en la anotación de documentos.
## Prerrequisitos
Antes de continuar con el tutorial, asegúrese de tener los siguientes requisitos previos:
1. GroupDocs.Annotation para la biblioteca .NET: Descargue e instale la biblioteca desde [aquí](https://releases.groupdocs.com/annotation/net/).
2. Entorno de desarrollo .NET: asegúrese de tener un entorno de trabajo configurado para el desarrollo .NET.
3. Acceso a fuentes personalizadas: prepare las fuentes personalizadas que desea cargar en su aplicación.

## Importar espacios de nombres
En su proyecto .NET, importe los espacios de nombres necesarios para utilizar GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Paso 1: Crear una instancia del objeto anotador
Crear una instancia de la `Annotator` clase proporcionando la ruta al documento PDF de entrada junto con los directorios de fuentes personalizados:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Su código para futuras operaciones irá aquí
}
```
## Paso 2: Configurar las opciones de vista previa
Defina las opciones de vista previa para especificar cómo se generarán las vistas previas del documento. Puede configurar opciones como el formato de vista previa, la numeración de páginas, etc.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Paso 3: Generar vistas previas del documento
Utilice el `GeneratePreview` método de la `Document` propiedad para generar vistas previas con fuentes personalizadas:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Paso 4: Mostrar la ruta de salida
Por último, muestra un mensaje indicando la generación exitosa de las vistas previas del documento junto con la ruta del directorio de salida:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Conclusión
En conclusión, cargar fuentes personalizadas en GroupDocs.Annotation para .NET ofrece a los desarrolladores la flexibilidad de personalizar las anotaciones de los documentos según sus necesidades. Siguiendo los pasos descritos en este tutorial, podrá integrar fácilmente fuentes personalizadas en sus aplicaciones .NET y mejorar la experiencia de anotación para los usuarios.
## Preguntas frecuentes
### ¿Puedo cargar varias fuentes personalizadas simultáneamente?
Sí, puede especificar varios directorios de fuentes al crear una instancia de `Annotator` objeto.
### ¿Existen limitaciones en los tipos de fuentes compatibles?
GroupDocs.Annotation para .NET admite una amplia gama de tipos de fuentes, incluidas las fuentes TrueType (.ttf) y OpenType (.otf).
### ¿Puedo cambiar dinámicamente las fuentes cargadas durante el tiempo de ejecución?
Sí, puede modificar dinámicamente los directorios de fuentes y recargar las anotaciones del documento según sea necesario.
### ¿GroupDocs.Annotation admite la incrustación de fuentes en los documentos de salida?
Sí, puedes incorporar fuentes personalizadas en los documentos de salida para garantizar una representación uniforme en distintas plataformas.
### ¿Hay alguna forma de gestionar las licencias de fuentes dentro de la aplicación?
GroupDocs.Annotation proporciona opciones para administrar las licencias de fuentes, incluidas licencias temporales para fines de evaluación.