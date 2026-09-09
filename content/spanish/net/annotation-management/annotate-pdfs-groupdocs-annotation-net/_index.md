---
categories:
- PDF Processing
date: '2026-05-26'
description: Aprenda cómo crear un sistema de revisión de documentos usando GroupDocs
  Annotation para .NET. El tutorial paso a paso cubre la configuración, los tipos
  de anotación, la optimización del rendimiento y la solución de problemas para desarrolladores
  C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Crear sistema de revisión de documentos: PDF Annotation .NET Guide'
type: docs
url: /es/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Crear sistema de revisión de documentos: Guía de anotación PDF .NET

Si necesitas **crear un sistema de revisión de documentos** que permita a los usuarios agregar comentarios, resaltados y formas a PDFs directamente desde una aplicación .NET, has llegado al lugar correcto. GroupDocs.Annotation para .NET elimina el dolor de cabeza del manejo de PDF de bajo nivel mientras te brinda un control granular sobre cada tipo de anotación. En esta guía verás cómo configurar la biblioteca, agregar anotaciones de área, elipse y texto, filtrar lo que se guarda y mantener un rendimiento ágil incluso con archivos de cientos de páginas.

## Respuestas rápidas
- **¿Qué biblioteca maneja la anotación de PDF en .NET?** GroupDocs.Annotation for .NET.
- **¿Puedo agregar resaltados, círculos y comentarios programáticamente?** Sí – usa objetos AreaAnnotation, EllipseAnnotation y TextAnnotation.
- **¿Se requiere una licencia para producción?** Una licencia válida de GroupDocs es obligatoria para cualquier despliegue en producción.
- **¿Qué tamaño de PDF se puede procesar?** Hasta 500 MB pueden manejarse sin cargar todo el archivo en memoria.
- **¿Esto me ayudará a crear un sistema de revisión de documentos?** Absolutamente – puedes guardar por lotes, filtrar y versionar anotaciones para los revisores.

## ¿Qué es un sistema de revisión de documentos?
Un **sistema de revisión de documentos** es una solución de software que permite a múltiples partes interesadas anotar, comentar y aprobar archivos PDF en un flujo de trabajo coordinado. Centraliza la retroalimentación, rastrea los cambios y a menudo exporta una versión limpia para la aprobación final.

## ¿Por qué usar GroupDocs Annotation para .NET para crear un sistema de revisión de documentos?
GroupDocs Annotation soporta **más de 30 tipos de anotación**, procesa PDFs de hasta **500 MB** de tamaño, y funciona en **.NET Framework 4.6.1+**, **.NET Core 2.0+**, y **.NET 6+**. Su API te permite agregar, eliminar y filtrar anotaciones sin tocar nunca la estructura interna del PDF, lo que acelera el desarrollo y reduce errores.

## Requisitos previos y configuración del entorno
Antes de escribir cualquier código, asegúrate de que tu entorno de desarrollo cumpla con los siguientes criterios:

- **IDE:** Visual Studio 2019 o posterior, o VS Code con la extensión C#.
- **Framework objetivo:** .NET Framework 4.6.1 + o .NET Core 2.0 + ( recomendamos .NET 6 para nuevos proyectos).
- **Acceso a NuGet:** Capacidad para instalar paquetes desde nuget.org.
- **PDFs de muestra:** Al menos un PDF multipágina para probar la colocación de anotaciones.
- **Memoria y disco:** Mínimo 4 GB de RAM y suficiente espacio libre en disco para archivos temporales (el procesamiento de anotaciones puede generar flujos temporales).

### Prácticas de desarrollo recomendadas
- Mantén tu solución bajo control de versiones (Git) para que puedas revertir cambios relacionados con anotaciones.
- Usa una carpeta dedicada **Annotations** en tu proyecto para almacenar archivos de configuración y claves de licencia.
- Habilita **nullable reference types** (`<Nullable>enable</Nullable>`) para detectar posibles errores de referencia nula temprano.

## Comenzando: Instalación de GroupDocs.Annotation

### Métodos de instalación

**Opción 1: Consola del Administrador de paquetes NuGet**  
Ejecuta el siguiente comando en la Consola del Administrador de paquetes:  

`Install-Package GroupDocs.Annotation`

**Opción 2: .NET CLI (recomendado para desarrollo multiplataforma)**  
Ejecuta en una terminal:  

`dotnet add package GroupDocs.Annotation`

**Opción 3: Interfaz de usuario del Administrador de paquetes de Visual Studio**  
- Haz clic derecho en el proyecto → **Manage NuGet Packages**  
- Busca **GroupDocs.Annotation**  
- Haz clic en **Install** en la última versión estable  

Los tres métodos instalan el mismo binario; elige el que se ajuste a tu flujo de trabajo.

### Configuración de la licencia
GroupDocs requiere una licencia válida para cualquier uso en producción. Tienes tres opciones:

- **Prueba gratuita:** evaluación de 30 días con el conjunto completo de funciones.  
- **Licencia temporal:** evaluación extendida para desarrollo y pruebas.  
- **Licencia comercial:** uso ilimitado en entornos de producción.  

La clase `License` carga y aplica un archivo de licencia de GroupDocs para habilitar la funcionalidad completa. Puedes obtener una licencia desde la [Página de compra de GroupDocs](https://purchase.groupdocs.com/buy). Después de recibir el archivo `.lic`, colócalo en una carpeta que tu aplicación pueda leer y apunta la clase `License` a él al iniciar.

### Verificación de la configuración inicial
Crea un pequeño programa de consola que cargue un PDF y escriba el número de páginas en la consola. Si el programa se ejecuta sin lanzar una excepción, la biblioteca está correctamente instalada y licenciada.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Nota:** El código anterior es solo para ilustración; **no** necesitas agregar un bloque de código con fences en el artículo final, pero el fragmento en línea muestra el uso exacto de la API.

Si ves el recuento de páginas impreso, estás listo para comenzar a agregar anotaciones reales.

## Implementación central: Agregar anotaciones a PDFs

### Ancla de definición – Annotator
La clase `Annotator` es el punto de entrada para todas las operaciones de anotación de PDF en GroupDocs.Annotation para .NET. Carga un PDF en memoria, expone métodos para agregar, editar y recuperar anotaciones, y maneja el guardado del documento modificado.

### ¿Cómo agregar anotaciones de área y elipse?
Carga el PDF con `new Annotator(...)`, crea objetos `AreaAnnotation` y `EllipseAnnotation`, establece sus coordenadas y añádelos a la colección del annotator. Finalmente, llama a `Save` para persistir los cambios. Este flujo de trabajo te permite resaltar secciones (área) o rodear gráficos importantes de forma programática en una única operación atómica.

#### Paso 1: Inicializar el Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Paso 2: Crear un AreaAnnotation
`AreaAnnotation` representa un área rectangular de resaltado en una página PDF.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Paso 3: Crear un EllipseAnnotation
`EllipseAnnotation` representa una anotación de forma elíptica en una página PDF.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Paso 4: Agregar anotaciones en bloque
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Consejo profesional:** Agregar anotaciones en una lista y llamar a `Add` una sola vez reduce la sobrecarga de I/O, especialmente cuando necesitas insertar decenas de marcas en muchas páginas.

### ¿Cómo guardar anotaciones selectivas?
`SaveOptions` configura cómo se guarda el PDF anotado, incluyendo qué tipos de anotación incluir. GroupDocs.Annotation te permite filtrar qué tipos de anotación se escriben en el archivo de salida. Crea una instancia de `SaveOptions`, establece la colección `AnnotationTypes` con los tipos que deseas conservar y pasa las opciones a `Save`. Esto es perfecto para generar PDFs solo para revisores o eliminar notas temporales antes de archivar.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Escenarios de implementación del mundo real

### Escenario 1: Flujo de trabajo de revisión de documentos
Múltiples revisores agregan anotaciones **Area**, **Ellipse** y **Text**. Después de la ronda de revisión, generas tres PDFs:
1. Versión completa con todos los comentarios.  
2. Versión solo para revisores (filtra notas internas).  
3. Versión limpia para la aprobación final (mantiene solo los resaltados).  

### Escenario 2: Generación automática de informes
Tu backend procesa informes de ventas diarios, resaltando automáticamente métricas clave con anotaciones de área y rodeando gráficos atípicos con anotaciones de elipse. Los PDFs generados se envían por correo electrónico a los interesados sin intervención manual.

### Escenario 3: Documentos legales colaborativos
Los despachos de abogados a menudo necesitan separar los comentarios de los socios de las notas de los asociados junior. Al etiquetar anotaciones con metadatos personalizados y usar guardado selectivo, puedes producir un PDF de revisión de socios que oculta los comentarios junior, simplificando el control de versiones.

## Optimización de rendimiento para uso en producción

### ¿Cómo gestionar la memoria al anotar PDFs grandes?
`LoadOptions` te permite especificar cómo se carga un PDF, como rangos de páginas o contraseñas. Cuando un PDF supera los 100 MB, evita cargar el archivo completo usando el constructor de `LoadOptions` que acepta un rango de páginas. Procesa las páginas en lotes, elimina cada instancia de `Annotator` con un bloque `using` y limpia los archivos temporales después de cada lote. Este enfoque mantiene el uso máximo de memoria por debajo de 200 MB incluso para documentos de 500 páginas.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Mejores prácticas de gestión de memoria
- **Siempre envuelve `Annotator` en una declaración `using`** para garantizar la liberación de recursos no administrados.  
- **Procesa anotaciones por lotes**: recopila todas las anotaciones de un documento y luego llama a `Add` una sola vez.  
- **Evita cargar PDFs completos** cuando solo necesitas modificar un subconjunto de páginas; usa `LoadOptions.PageNumbers`.  

### Estrategias para manejar archivos grandes
1. **Procesamiento por página** – Carga, anota y guarda una página a la vez.  
2. **Salida en streaming** – Dirige el método `Save` a un `MemoryStream` para evitar escrituras intermedias en disco.  
3. **Limpieza de archivos temporales** – Elimina cualquier archivo temporal creado por el annotator después de cada operación.  

### Consideraciones para procesamiento concurrente
- **Seguridad de subprocesos:** Las instancias de `Annotator` no son seguras para subprocesos. Crea una instancia separada por subproceso.  
- **Limitación de recursos:** Limita los trabajos concurrentes al número de núcleos de CPU para evitar la saturación.  
- **API asíncrona:** `SaveAsync` guarda el documento anotado de forma asíncrona, devolviendo una Task, lo cual es útil en entornos ASP.NET Core.  

## Solución de problemas comunes

### Problema 1: errores “File Not Found”
**Respuesta directa:** Verifica que la ruta de archivo que pasas a `new Annotator(...)` sea absoluta o relativa correctamente al ensamblado en ejecución, y asegura que el proceso de la aplicación tenga permisos de lectura para esa ubicación. Si el archivo está en un recurso de red, asigna la unidad o usa rutas UNC.  

**Correcciones típicas:**  
- Usa `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Concede a la identidad del pool de aplicaciones IIS permisos de lectura/escritura en la carpeta.  

### Problema 2: Las anotaciones aparecen en ubicaciones incorrectas
**Respuesta directa:** Asegúrate de usar el mismo sistema de coordenadas (origen superior‑izquierda) y que el DPI de la página coincida con los valores que proporcionas. Obtén el tamaño de la página mediante `annotator.GetPageInfo(pageNumber)` y calcula las coordenadas en relación con ese tamaño.  

**Correcciones típicas:**  
- Multiplica las coordenadas por el factor de escala de la página si el PDF se creó con un DPI no estándar.  
- Verifica que no estés mezclando puntos (1/72 pulgada) con píxeles.  

### Problema 3: Problemas de rendimiento con archivos grandes
**Respuesta directa:** Cambia a carga por rangos de página, procesa anotaciones en lotes y elimina rápidamente cada instancia de `Annotator`. También habilita la opción `MemoryCache` en `LoadOptions` para reutilizar buffers entre operaciones.  

**Correcciones típicas:**  
- Establece `LoadOptions.UseMemoryCache = true`.  
- Procesa archivos de forma asíncrona con `await annotator.SaveAsync(...)`.  

### Problema 4: Errores relacionados con la licencia
**Respuesta directa:** Coloca el archivo `.lic` en una carpeta que la aplicación pueda leer y llama a `License license = new License(); license.SetLicense("path/to/license.lic");` antes de cualquier otra llamada a GroupDocs. Verifica que la versión de la licencia coincida con la versión de la biblioteca que estás usando.  

**Correcciones típicas:**  
- Verifica que el archivo de licencia no esté corrupto (compara el tamaño del archivo).  
- Asegúrate de no mezclar una licencia de prueba con una comercial en el mismo entorno.  

## Consejos avanzados y mejores prácticas

### Gestión de color
Los colores consistentes mejoran la legibilidad para los revisores. Define una paleta (p. ej., amarillo para resaltados, rojo para problemas críticos) y guárdala en una clase auxiliar estática. Recuerda usar colores de alto contraste para accesibilidad y agregar una página de leyenda en el PDF como referencia.

### Patrones de manejo de errores
Envuelve todas las llamadas de anotación en bloques try‑catch que capturen específicamente `GroupDocs.Annotation.Exceptions.AnnotationException`. Registra el mensaje de la excepción, la traza de pila y el nombre del PDF para ayudar en la depuración.

### Estrategias de pruebas
- **Pruebas unitarias:** Usa un PDF pequeño con dimensiones conocidas, agrega una anotación y verifica que `GetAnnotations()` devuelva las coordenadas esperadas.  
- **Pruebas de integración:** Ejecuta el flujo completo en PDFs de 1 a 200 páginas y verifica que el tiempo de procesamiento se mantenga bajo 5 segundos para archivos menores a 50 MB.  
- **Pruebas de carga:** Simula 50 solicitudes de anotación concurrentes usando una herramienta como k6 o Apache JMeter y monitorea CPU/memoria.  

## Preguntas frecuentes

**P: ¿Cómo manejo PDFs con diferentes tamaños de página?**  
R: GroupDocs lee automáticamente las dimensiones de cada página. Al posicionar anotaciones, siempre consulta `annotator.GetPageInfo(pageNumber)` y calcula las coordenadas basándote en el ancho y alto de esa página.  

**P: ¿Puedo anotar PDFs protegidos con contraseña?**  
R: Sí. Usa el constructor de `LoadOptions` que acepta una cadena de contraseña, por ejemplo `new LoadOptions { Password = "secret" }`, y pásalo al constructor de `Annotator`.  

**P: ¿Cuál es el número máximo de anotaciones que puedo agregar a un solo PDF?**  
R: No hay un límite estricto, pero el rendimiento disminuye después de unas pocas mil anotaciones. Para conjuntos de anotaciones muy grandes, agrúpalas en secciones lógicas y procesa cada sección por separado.  

**P: ¿Cómo elimino anotaciones específicas programáticamente?**  
R: Obtén el `Id` de la anotación mediante `GetAnnotations()`, luego llama a `Delete(id)` o crea una instancia de `SaveOptions` que excluya el `AnnotationType` no deseado.  

**P: ¿Puedo personalizar la apariencia de la anotación más allá de los colores?**  
R: Absolutamente. Puedes establecer opacidad, grosor del borde, estilo de guiones e incluso incrustar íconos SVG personalizados para anotaciones de sello.  

**P: ¿Qué ocurre si intento anotar un PDF escaneado (basado en imágenes)?**  
R: Las anotaciones se renderizarán como objetos superpuestos sobre la imagen de la página. No modifican los datos raster subyacentes, por lo que el PDF sigue siendo buscable si existen capas OCR.  

**P: ¿Cómo manejo PDFs muy grandes sin quedarme sin memoria?**  
R: Procesa el documento página por página usando `LoadOptions.PageNumbers`, elimina cada instancia de `Annotator` inmediatamente después de usarla y habilita guardados en streaming a un `MemoryStream` para evitar picos de disco.  

## Integración con aplicaciones ASP.NET

Cuando expones la funcionalidad de anotación a través de una API web, sigue el siguiente patrón:

1. **El controlador recibe el flujo PDF** del cliente.  
2. **Validar el tamaño del archivo** (rechazar > 200 MB a menos que tengas un manejo especial).  
3. **Instanciar `Annotator` dentro de un bloque `using`** para garantizar la liberación.  
4. **Aplicar anotaciones** basadas en la carga JSON que describe el tipo de anotación, coordenadas y texto.  
5. **Guardar en una ubicación temporal**, luego transmitir el resultado al cliente con el encabezado `Content‑Disposition` apropiado.  

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Recursos adicionales
- [Página de compra de GroupDocs](https://purchase.groupdocs.com/buy)  
- [Comprar GroupDocs](https://purchase.groupdocs.com/buy)  
- [Documentación de GroupDocs Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Referencia de la API de GroupDocs](https://reference.groupdocs.com/annotation/net/)  
- [Últimas versiones](https://releases.groupdocs.com/annotation/net/)  
- [Probar GroupDocs gratis](https://releases.groupdocs.com/annotation/net/)  
- [Solicitar una licencia temporal](https://purchase.groupdocs.com/temporary-license/)  
- [Foro de GroupDocs](https://forum.groupdocs.com/c/annotation/)  

## Conclusión y próximos pasos
Ahora tienes una **hoja de ruta completa y lista para producción** para construir un **sistema de revisión de documentos** impulsado por GroupDocs.Annotation para .NET. Has aprendido cómo configurar la biblioteca, agregar anotaciones de área, elipse y texto, filtrar guardados y mantener bajo el uso de memoria incluso con PDFs masivos.

**Próximas acciones que puedes realizar hoy:**  

1. **Experimenta** con tipos de anotación adicionales como `ArrowAnnotation` y `StampAnnotation`.  
2. **Integra** el flujo de trabajo en tu API ASP.NET Core existente o aplicación de escritorio WPF.  
3. **Explora** la referencia completa de la API para descubrir funciones avanzadas como versionado de anotaciones y metadatos personalizados.  
4. **Únete** a los foros de la comunidad GroupDocs para obtener soporte de pares y mantenerte actualizado sobre nuevas versiones.  

---

**Última actualización:** 2026-05-26  
**Probado con:** GroupDocs.Annotation 23.11 for .NET  
**Autor:** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```
```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```
```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```
```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```
```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```
```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```
```csharp
annotator.Save(outputPath, saveOptions);
```
```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```
```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```
```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```
```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```
```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```
```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```
```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Tutoriales relacionados
- [Tutorial de GroupDocs Annotation .NET - Guía completa para gestión de documentos](/annotation/net/annotation-management/)
- [Tutoriales de vista previa de documentos .NET - Guía completa de GroupDocs.Annotation](/annotation/net/document-preview/)
- [Tutorial de licencia medida de GroupDocs Annotation - Guía completa de configuración .NET](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)