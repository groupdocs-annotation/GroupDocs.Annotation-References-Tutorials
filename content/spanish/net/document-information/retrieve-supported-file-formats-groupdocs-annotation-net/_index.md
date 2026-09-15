---
categories:
- .NET Development
date: '2026-06-26'
description: Aprenda cómo recuperar formatos con GroupDocs.Annotation para .NET, solucione
  problemas de formatos de archivo no compatibles y aplique validación de mejores
  prácticas.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Recuperar formatos de archivo compatibles .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Cómo recuperar formatos en .NET usando GroupDocs.Annotation – Guía completa
type: docs
url: /es/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Cómo recuperar formatos en .NET usando GroupDocs.Annotation

## Introducción

¿Alguna vez te has preguntado qué formatos de archivo puede manejar realmente tu aplicación .NET para la anotación de documentos? **Cómo recuperar formatos** es una pregunta que muchos desarrolladores se hacen cuando necesitan validar las cargas de usuarios o crear filtros de UI dinámicos. Saber exactamente qué formatos de archivo admite tu implementación de GroupDocs.Annotation no solo es útil, es esencial para construir aplicaciones robustas que nunca se bloqueen por un tipo de archivo inesperado.

En esta guía aprenderás a recuperar y validar programáticamente los formatos de archivo compatibles usando GroupDocs.Annotation para .NET. Recorreremos la implementación básica, te mostraremos cómo convertir la lista cruda en un menú desplegable limpio para los usuarios finales y cubriremos consejos de solución de problemas del mundo real para que puedas manejar cualquier escenario de formato de documento con confianza.

**Lo que obtendrás**

- Una comprensión clara de las capacidades de formatos de archivo de GroupDocs.Annotation  
- Código listo para ejecutar que recupera y muestra cada formato compatible  
- Estrategias probadas para el almacenamiento en caché, manejo de errores y casos límite de licenciamiento  
- Recomendaciones de mejores prácticas para la validación de tipos de archivo en producción  

Vamos a sumergirnos y resolver este rompecabezas de formatos de archivo de una vez por todas.

## Respuestas rápidas
- **¿Qué significa “cómo recuperar formatos”?** Es la forma programática de preguntar a GroupDocs.Annotation qué extensiones puede anotar.  
- **¿Qué formatos principales se admiten de fábrica?** Más de 50, incluidos PDF, DOCX, XLSX, PPTX, JPEG, PNG y TIFF.  
- **¿Necesito una licencia para obtener la lista completa?** Sí, una licencia comercial activa o de prueba desbloquea el catálogo completo.  
- **¿Se recomienda almacenar en caché la lista de formatos?** Absolutamente; el caché evita llamadas innecesarias y mejora el tiempo de respuesta.  
- **¿Cómo validar una carga contra la lista?** Compara la extensión del archivo con la colección en caché de extensiones compatibles.

## ¿Qué es “cómo recuperar formatos”?
**Cómo recuperar formatos** se refiere al proceso de llamar a la API de GroupDocs.Annotation para obtener una colección de todos los tipos de archivo que la biblioteca puede anotar. Esta operación devuelve una lista de solo lectura de objetos `FileType` que incluyen tanto la extensión del archivo como una descripción amigable.

## ¿Por qué usar GroupDocs.Annotation para la detección de formatos?
GroupDocs.Annotation soporta **más de 50 formatos de entrada y salida** —incluidos PDF, Microsoft Office (Word, Excel, PowerPoint) y tipos de imagen comunes— mientras procesa documentos de cientos de páginas sin cargar todo el archivo en memoria. Esta capacidad cuantificada lo convierte en una opción confiable para pipelines de anotación a escala empresarial.

## Requisitos previos y configuración del entorno

### Lo que necesitarás
- **IDE:** Visual Studio 2019 o posterior (la edición Community funciona bien)  
- **Framework objetivo:** .NET Framework 4.6.1 + o .NET Core 2.0 +   
- **Conceptos básicos de C#:** Si puedes escribir una aplicación “Hello World”, estás listo  

### Instalación de GroupDocs.Annotation
La forma más sencilla es vía NuGet. Elige el método que coincida con tu flujo de trabajo:

**Opción 1: Consola del Administrador de paquetes**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Opción 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Consejo profesional:** En entornos corporativos restringidos, descarga el paquete manualmente desde [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) y referencia el DLL localmente.

### Licenciamiento simplificado
- **Desarrollo y pruebas:** Comienza con la prueba gratuita para obtener la funcionalidad completa.  
- **Evaluación extendida:** Obtén una [licencia temporal](https://purchase.groupdocs.com/temporary-license/) (emitida en ~5 minutos).  
- **Producción:** Compra una licencia comercial en [GroupDocs Purchase](https://purchase.groupdocs.com/buy); una licencia cubre todos los escenarios de despliegue.

## Cómo recuperar programáticamente los formatos de archivo compatibles

Carga los formatos compatibles con una única llamada a `FileType.GetSupportedFileTypes()` y luego transforma el resultado en una lista amigable para el usuario que pueda mostrarse en controles UI o usarse para validación. El método devuelve una colección de solo lectura de objetos `FileType`, cada uno con una extensión y descripción, lo que facilita su manipulación.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

El código anterior consulta los metadatos internos de GroupDocs.Annotation, ordena las extensiones alfabéticamente y devuelve una colección ligera que puedes enlazar a controles UI o usar para validación.

### Ancla de definición: clase FileType
La clase `FileType` es la representación de GroupDocs.Annotation de un solo formato de documento, exponiendo propiedades como `Extension` y `Description`.  

### Recorrido paso a paso
1. **Agregar el espacio de nombres** – `using GroupDocs.Annotation;` al inicio de tu archivo.  
2. **Llamar al método estático** – `FileType.GetSupportedFileTypes()` devuelve un `IEnumerable<FileType>`.  
3. **Ordenar y proyectar** – Usa `OrderBy` y `Select` de LINQ para dar forma a los datos para la visualización.  
4. **Renderizar** – Recorre la lista en una consola, vista MVC o menú desplegable de WinForms.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Cómo almacenar en caché la lista de formatos para uso en producción

El caché elimina búsquedas repetidas de metadatos y garantiza tiempos de respuesta submilisegundos para cada solicitud, lo cual es crítico en aplicaciones de alto tráfico. Al guardar la lista de formatos en un campo estático y cargarla perezosamente en el primer uso, aseguras que los datos se recuperen solo una vez y luego se reutilicen eficientemente durante todo el ciclo de vida de la aplicación.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**¿Por qué almacenar en caché?** El conjunto de formatos compatibles nunca cambia en tiempo de ejecución, por lo que una única carga al iniciar la aplicación ahorra ciclos de CPU y evita verificaciones de licencia en cada llamada.

## Problemas comunes y soluciones

### Problema 1: error de compilación “GroupDocs.Annotation not found”
**Respuesta directa:** Verifica que el paquete NuGet esté instalado correctamente, limpia y recompila la solución, y asegura que tu framework objetivo coincida con las versiones compatibles del paquete.  

**Análisis de causa raíz** – Referencia faltante, framework incompatible o restricciones del origen de paquetes corporativo.

### Problema 2: lista de formatos vacía o incompleta
**Respuesta directa:** Una licencia caducada o mal configurada a menudo trunca la lista; vuelve a aplicar un archivo de licencia válido y reinicia la aplicación.  

**Posibles causas:**  
- Archivo de licencia no cargado (`License.SetLicense("license.json")` ausente)  
- Paquete NuGet dañado  
- Dependencias nativas faltantes  

**Solución rápida:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Problema 3: impactos de rendimiento por llamadas frecuentes
**Respuesta directa:** Almacena en caché el resultado como se muestra en la sección “Cómo almacenar en caché”; las llamadas subsecuentes se vuelven O(1).  

**Consejo de implementación:** Guarda la lista en `MemoryCache` o en un campo estático, y actualízala solo cuando actualices la biblioteca.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Aplicaciones del mundo real y casos de uso

### ¿Cómo validar cargas de archivo usando la lista en caché?
Cuando un usuario envía un documento, extrae la extensión del archivo y compárala con la colección en caché:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### ¿Cómo generar un filtro de archivo dinámico para un OpenFileDialog?
Puebla la cadena de filtro del diálogo con las extensiones en caché, asegurando que la UI siempre refleje las capacidades de la biblioteca:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### ¿Cómo omitir archivos no compatibles en un escaneo por lotes de carpetas?
Itera sobre un directorio, verifica cada archivo con `IsSupported` y procesa solo los válidos:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Consideraciones de rendimiento y mejores prácticas

- **Cachear una vez, reutilizar en todas partes** – Inicializa `FormatCache` al iniciar la aplicación (p. ej., en `Program.cs` o `Startup.cs`).  
- **Carga perezosa** – La propiedad estática garantiza que la lista se cargue solo cuando se necesite por primera vez, evitando sobrecarga de inicio innecesaria.  
- **Seguridad en hilos** – El operador de coalescencia nula (`??=`) es seguro para la mayoría de escenarios monohilo; para aplicaciones de alta concurrencia, envuelve el caché en un `Lazy<IReadOnlyList<FileType>>`.  
- **Liberar objetos de anotación** – Aunque la lista de formatos no requiere disposición, cualquier instancia de `Annotation` que crees debe envolver en sentencias `using` para liberar recursos nativos.  

### Patrón de manejo de errores para problemas de licenciamiento
Envuelve la recuperación de formatos en un bloque try‑catch que detecte específicamente `LicenseException` y registre un mensaje claro:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Guía de solución de problemas

### Paso 1: Verificar la instalación
Ejecuta `dotnet list package` o revisa la salida de la consola de NuGet para detectar advertencias.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Paso 2: Comprobar el estado de la licencia
Asegúrate de que `License.SetLicense("path/to/license.json")` se ejecute antes de cualquier llamada a la API.  

### Paso 3: Diagnosticar restricciones del entorno
- Confirma que la versión del runtime .NET coincida con los requisitos de la biblioteca.  
- Verifica que el proceso tenga permisos de lectura/escritura para la carpeta temporal usada por GroupDocs.Annotation.  

## Preguntas frecuentes

**P: ¿Qué formatos de archivo admite realmente GroupDocs.Annotation?**  
R: La biblioteca soporta **más de 50 formatos**, incluidos PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF y muchos otros. Ejecuta el código de ejemplo para obtener la lista exacta para tu licencia.

**P: ¿Por qué obtengo menos formatos compatibles de los esperados?**  
R: Esto suele deberse a un problema de licencia—una prueba caducada o un archivo de licencia cargado incorrectamente. Vuelve a aplicar una licencia válida y reinicia la aplicación.

**P: ¿Puedo comprobar un solo formato sin obtener toda la lista?**  
R: No existe un método directo “IsSupported”; el enfoque recomendado es almacenar en caché la lista completa una vez y consultarla localmente para búsquedas rápidas.

**P: ¿Cómo debo manejar la verificación de formatos en una aplicación web de alto tráfico?**  
R: Inicializa el caché de formatos al iniciar la aplicación (p. ej., en `ConfigureServices`) y guárdalo en un servicio estático o singleton. Esto elimina la sobrecarga por solicitud.

**P: ¿Qué ocurre si GetSupportedFileTypes() lanza una excepción?**  
R: Las excepciones normalmente provienen de problemas de licenciamiento o instalaciones corruptas. Verifica la integridad del paquete, reinstálalo si es necesario y asegura que el archivo de licencia sea accesible.

## Conclusión

Ahora dispones de una estrategia completa y lista para producción sobre **cómo recuperar formatos** con GroupDocs.Annotation en .NET. Desde la llamada de una sola línea a la API hasta el caché robusto, manejo de errores e integración UI, puedes validar cargas con confianza, generar filtros de archivo dinámicos y construir pipelines de anotación escalables.

**Próximos pasos:**  
- Explora la [Referencia API de GroupDocs.Annotation](https://reference.groupdocs.com/annotation/net/) para profundizar en funciones de anotación.  
- Únete a la comunidad en el [Foro de soporte](https://forum.groupdocs.com/c/annotation/) si encuentras escenarios límite.  
- Experimenta combinando la validación de formatos con reglas de negocio personalizadas (p. ej., límites de tamaño, escaneos de seguridad) para reforzar aún más tu flujo de trabajo de documentos.

## Recursos
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

---

**Última actualización:** 2026-06-26  
**Probado con:** GroupDocs.Annotation 25.4.0 for .NET  
**Autor:** GroupDocs  

---

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Tutoriales relacionados

- [Extracción de metadatos de documentos .NET - Guía completa de GroupDocs.Annotation](/annotation/net/document-information/)
- [Cargar PDF desde URL .NET - Guía completa con GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Vista previa de documentos .NET - Guía completa de GroupDocs.Annotation](/annotation/net/document-preview/)