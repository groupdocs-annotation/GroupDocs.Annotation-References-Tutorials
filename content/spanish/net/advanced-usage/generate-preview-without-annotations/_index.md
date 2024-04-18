---
title: Generar vista previa sin anotaciones
linktitle: Generar vista previa sin anotaciones
second_title: API GroupDocs.Annotation .NET
description: Mejore la colaboración y la anotación de documentos dentro de aplicaciones .NET utilizando GroupDocs.Annotation para .NET. Anota, marca y revisa documentos fácilmente con esta potente biblioteca.
type: docs
weight: 13
url: /es/net/advanced-usage/generate-preview-without-annotations/
---
## Introducción
En la era digital actual, la colaboración eficiente en documentos es clave para la productividad y el éxito. Ya sea que esté trabajando en un proyecto con miembros del equipo repartidos por todo el mundo o colaborando con clientes en contratos importantes, la capacidad de anotar y revisar documentos sin problemas es crucial. Con GroupDocs.Annotation para .NET, puede llevar la colaboración de sus documentos al siguiente nivel, permitiendo realizar anotaciones, marcas y revisiones fácilmente directamente dentro de sus aplicaciones .NET.
## Requisitos previos
Antes de sumergirse en el mundo de la anotación de documentos con GroupDocs.Annotation para .NET, existen algunos requisitos previos que deberá cumplir:
### 1. Instale GroupDocs.Annotation para .NET
 En primer lugar, deberá descargar e instalar GroupDocs.Annotation para .NET. Puedes encontrar el enlace de descarga.[aquí](https://releases.groupdocs.com/annotation/net/). Siga las instrucciones de instalación proporcionadas para configurar la biblioteca en su entorno .NET.
### 2. Obtener una licencia (opcional)
Si bien GroupDocs.Annotation para .NET ofrece una prueba gratuita, es posible que desee considerar obtener una licencia para tener acceso completo a sus funciones. Puedes comprar una licencia[aquí](https://purchase.groupdocs.com/buy) o solicitar una licencia temporal[aquí](https://purchase.groupdocs.com/temporary-license/) con fines de prueba.
### 3. Familiaridad con C# y desarrollo .NET
Para aprovechar al máximo GroupDocs.Annotation para .NET, resulta útil tener un conocimiento básico del desarrollo de C# y .NET. Esto le permitirá integrar la biblioteca sin problemas en sus aplicaciones y flujos de trabajo existentes.
### 4. Instale un visor de PDF
Dado que GroupDocs.Annotation para .NET funciona con documentos PDF, necesitará un visor de PDF instalado en su sistema para obtener una vista previa de los documentos anotados. Adobe Acrobat Reader o cualquier otro visor de PDF será suficiente.

## Importar espacios de nombres
Antes de poder comenzar a anotar documentos, deberá importar los espacios de nombres necesarios a su proyecto .NET. Esto le permite acceder a las clases y métodos proporcionados por GroupDocs.Annotation para .NET.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Ahora que tiene todo configurado, generemos una vista previa de un documento sin anotaciones. Siga estos pasos para lograr esto:
## Paso 1: inicializar el anotador
 Primero, cree una instancia del`Annotator` clase, pasando la ruta al documento que desea anotar.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Paso 2: configurar las opciones de vista previa
A continuación, configure las opciones de vista previa según sus requisitos. Puede especificar los números de página que desea incluir en la vista previa, el formato de vista previa (por ejemplo, PNG) y si desea representar anotaciones.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## Paso 3: generar vista previa
 Finalmente, genere la vista previa usando el`GeneratePreview` método de la`Document` clase, pasando las opciones de vista previa configuradas.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Siguiendo estos sencillos pasos, puede generar una vista previa de un documento sin anotaciones utilizando GroupDocs.Annotation para .NET.

## Conclusión
En conclusión, GroupDocs.Annotation para .NET proporciona una potente solución para la colaboración y anotación de documentos dentro de aplicaciones .NET. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente las capacidades de anotación de documentos en sus proyectos, mejorando la colaboración y la productividad.
## Preguntas frecuentes
### P: ¿Puedo utilizar GroupDocs.Annotation para .NET con otros formatos de documentos además de PDF?
Sí, GroupDocs.Annotation para .NET admite una variedad de formatos de documentos, incluidos DOCX, XLSX, PPTX y más.
### P: ¿GroupDocs.Annotation para .NET es compatible con .NET Core?
Sí, GroupDocs.Annotation para .NET es compatible con los entornos .NET Framework y .NET Core.
### P: ¿GroupDocs.Annotation para .NET ofrece herramientas de anotación personalizables?
Sí, GroupDocs.Annotation para .NET proporciona una variedad de herramientas de anotación que se pueden personalizar para satisfacer sus requisitos específicos.
### P: ¿Puedo integrar GroupDocs.Annotation para .NET en mis aplicaciones web?
Sí, GroupDocs.Annotation para .NET se puede integrar en aplicaciones web y de escritorio, lo que proporciona capacidades de colaboración de documentos perfectas.
### P: ¿Existe un foro comunitario donde pueda obtener soporte y asistencia con GroupDocs.Annotation para .NET?
 Sí, puede encontrar soporte y asistencia en el foro GroupDocs.Annotation[aquí](https://forum.groupdocs.com/c/annotation/10).