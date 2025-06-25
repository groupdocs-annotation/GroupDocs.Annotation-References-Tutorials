---
"date": "2025-05-06"
"description": "Aprenda a guardar eficientemente solo las páginas anotadas de un PDF con GroupDocs.Annotation para .NET. Mejore la gestión de documentos y la colaboración con esta guía detallada."
"title": "Cómo guardar páginas anotadas en PDF con GroupDocs.Annotation para .NET"
"url": "/es/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# Cómo guardar páginas anotadas en PDF con GroupDocs.Annotation para .NET

## Introducción

¿Tiene dificultades para guardar páginas anotadas específicas de sus documentos PDF? Esta guía completa le muestra cómo hacerlo eficientemente con GroupDocs.Annotation para .NET. Al aprovechar las funciones de anotación, agilice la gestión de documentos y mejore la colaboración centrándose en el contenido relevante.

En este tutorial aprenderás:
- Configuración de su entorno de desarrollo con GroupDocs.Annotation
- Agregar varios tipos de anotaciones
- Guardar únicamente páginas anotadas de manera efectiva

¿Listo para empezar? Asegurémonos de tenerlo todo listo.

### Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:
- **Marco .NET** (versión 4.6 o posterior) o **.NET Core/5+**
- Un editor de código como Visual Studio
- Conocimientos básicos de configuración de proyectos C# y .NET

## Configuración de GroupDocs.Annotation para .NET

Para comenzar a utilizar GroupDocs.Annotation, instálelo a través de NuGet.

**Consola del administrador de paquetes NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\CLI de .NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Adquisición de licencias

GroupDocs ofrece una prueba gratuita para explorar su software a fondo. Para un uso prolongado, adquiera una licencia o solicite una temporal:
- **Prueba gratuita**:Explore las funciones sin limitaciones durante un período inicial.
- **Licencia temporal**:Utilice GroupDocs.Annotation en producción temporalmente.
- **Compra**Asegure sus necesidades a largo plazo con una licencia comercial.

Una vez instalada, inicialice la biblioteca de la siguiente manera:

```csharp
using GroupDocs.Annotation;

// Configuración básica para cargar y anotar documentos
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Guía de implementación

### Agregar anotaciones

#### Descripción general

Las anotaciones ayudan a resaltar áreas importantes dentro de tu documento. Exploremos cómo agregar una `AreaAnnotation` y un `EllipseAnnotation`.

**Paso 1: Crear una anotación de área**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definir la anotación del área
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posición y tamaño
    BackgroundColor = 65535,                // Valor de color ARGB para resaltar
    PageNumber = 1                          // Número de página específico
};
```

El `AreaAnnotation` Resalta un área rectangular en el documento. Personaliza su posición (`Box`) y color de fondo.

**Paso 2: Crear una anotación de elipse**

```csharp
// Definir la anotación de elipse
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posición y tamaño
    BackgroundColor = 123456,                // Valor de color ARGB para resaltar
    PageNumber = 1                           // Número de página específico
};
```

El `EllipseAnnotation` Permite dibujar una forma ovalada en el documento. Ajuste la posición y las dimensiones con el `Box` propiedad.

**Paso 3: Agregar anotaciones**

```csharp
// Agregar anotaciones a la instancia de Anotador
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Usando el `Add` método, incluye múltiples tipos de anotaciones. Este paso agrega tanto el `AreaAnnotation` y `EllipseAnnotation`.

### Guardar solo páginas anotadas

#### Descripción general

Para guardar únicamente las páginas que contienen anotaciones, configure sus opciones de guardado como corresponda.

**Paso 4: Guardar páginas anotadas**

```csharp
using GroupDocs.Annotation.Options;

// Configurar opciones de guardado para incluir solo páginas anotadas
annotator.Save("path/to/output/document.pdf\