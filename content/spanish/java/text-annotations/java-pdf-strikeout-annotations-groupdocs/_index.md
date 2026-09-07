---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Aprenda cómo agregar anotaciones de tachado a PDFs en Java usando GroupDocs.
  Este tutorial paso a paso cubre la configuración, el código, la solución de problemas
  y consejos de rendimiento.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Guía de tachado de texto PDF en Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Cómo agregar anotaciones de tachado a PDFs en Java – Guía completa de GroupDocs
type: docs
url: /es/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Cómo agregar anotaciones de tachado a PDFs en Java

¿Alguna vez necesitaste tachar texto en un PDF de forma programática? Ya sea que estés construyendo un sistema de revisión de documentos, creando un flujo de trabajo de edición, o simplemente necesites marcar texto para eliminarlo, **how to add strikeout** annotations in Java es una habilidad práctica que ahorra tiempo y reduce el esfuerzo manual. En esta guía completa descubrirás todo lo que necesitas saber para implementar anotaciones de tachado con GroupDocs.Annotation para Java, desde la configuración del proyecto hasta la optimización del rendimiento.

## Respuestas rápidas
- **¿Cuál es el primer paso?** Agrega la dependencia Maven de GroupDocs.Annotation a tu `pom.xml`.  
- **¿Cómo creo un tachado?** Instancia `Annotator`, define `StrikeoutAnnotation` con puntos, establece color/opacidad, luego llama a `addAnnotation`.  
- **¿Puedo agregar comentarios?** Sí, adjunta un objeto `Comment` a la anotación para colaboración.  
- **¿Qué pasa si la anotación está mal ubicada?** Ajusta los puntos de coordenadas; PDF usa un sistema de origen en la esquina inferior‑izquierda.  
- **¿Existe un límite de tamaño del documento?** GroupDocs procesa PDFs de cientos de páginas sin cargar todo el archivo en memoria.

## ¿Qué significa “how to add strikeout” en la anotación de PDF?
La frase “how to add strikeout” se refiere al proceso de dibujar programáticamente una línea a través del texto seleccionado dentro de un documento PDF usando una API de anotaciones. En Java, GroupDocs.Annotation proporciona una clase dedicada `StrikeoutAnnotation` que maneja el renderizado, estilo y persistencia de las marcas de tachado.

## ¿Por qué usar GroupDocs para Java PDF Strikeout?
GroupDocs.Annotation soporta **más de 50 formatos de entrada y salida**—incluidos PDF, DOCX, XLSX, PPTX, HTML y tipos de imagen comunes—por lo que no estás limitado a un solo tipo de archivo. Proporciona una API de alto nivel que abstrae la estructura de bajo nivel del PDF, manejando automáticamente la incrustación de fuentes, renderizado de páginas y persistencia de anotaciones, lo que permite a los desarrolladores centrarse en la lógica de negocio en lugar de los internals del PDF.

## Requisitos previos y requisitos de configuración

### Requisitos esenciales
- **Java Development Kit (JDK):** Versión 8 o posterior (JDK 11+ recomendado para una recolección de basura óptima).  
- **GroupDocs.Annotation for Java:** Integrado vía Maven (ver el fragmento Maven a continuación).  
- **IDE:** IntelliJ IDEA, Eclipse o cualquier editor compatible con Java.

### Configuración de dependencias Maven
Agrega el siguiente bloque de dependencia a tu `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/annotation/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

**Consejo profesional:** Siempre verifica la última versión en la página de lanzamientos de GroupDocs; las versiones más recientes añaden funcionalidades y corrigen errores que pueden afectar el renderizado de anotaciones.

### Obtención de tu licencia
GroupDocs.Annotation requiere una licencia válida para uso en producción. Tienes tres opciones:

- **Prueba gratuita:** Descarga desde [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Licencia temporal:** Solicita una clave de desarrollo en [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Licencia completa:** Compra para producción en [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

La prueba agrega una marca de agua sutil, así que planifica tus pruebas en consecuencia.

## Guía paso a paso de implementación

### Comprendiendo los componentes principales
Las siguientes definiciones te dan un modelo mental rápido:

- **Annotator:** El objeto API principal que carga un PDF y expone métodos de anotación.  
- **StrikeoutAnnotation:** Representa la línea visual de tachado y sus opciones de estilo.  
- **Point:** Un par de coordenadas (X, Y) que indica a la biblioteca dónde comienza y termina la línea.  
- **Comment:** Texto opcional adjunto a una anotación para colaboración.

### Paso 1: Configuración de rutas de archivo
Define las ubicaciones de tu PDF de origen y del archivo de destino. Las rutas incorrectas son una fuente común de errores “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Alerta de error común:** Asegúrate de que el directorio de salida exista y tenga permisos de escritura; GroupDocs no crea carpetas faltantes automáticamente.

### Paso 2: Inicializar el Annotator
Crea una instancia de `Annotator` que cargue el PDF en memoria.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**¿Qué ocurre aquí?** La biblioteca analiza la estructura del PDF, construye una representación interna y prepara un lienzo de anotación por página. Para archivos de cientos de páginas este paso puede tardar unos segundos.

### Paso 3: Agregar comentarios (Opcional pero recomendado)
`Comment` es una clase que representa una nota textual adjunta a una anotación, permitiendo a los colaboradores explicar la razón del tachado.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Consejo del mundo real:** Usa comentarios para explicar por qué se elimina el texto—esto es especialmente útil en flujos de revisión legal o editorial.

### Paso 4: Definir coordenadas de anotación
Los objetos `Point` almacenan pares de coordenadas X‑Y que definen la ubicación exacta de una anotación en una página PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Sistema de coordenadas explicado:** Las coordenadas PDF comienzan en la esquina inferior‑izquierda (0,0). El ejemplo crea una línea horizontal de (80,730) a (240,730) en la página objetivo.

**Encontrar las coordenadas correctas:** Muchos desarrolladores crean un helper que convierte porcentajes del ancho/alto de página en puntos absolutos, haciendo el código resistente a diferentes tamaños de página.

### Paso 5: Crear la anotación de tachado
`StrikeoutAnnotation` encapsula la línea visual, sus propiedades de estilo como color y opacidad, y cualquier metadato asociado para una marca de tachado.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Valores de color:** `fontColor` usa valores RGB decimales (p. ej., 65535 para amarillo brillante). Usa un convertidor en línea si necesitas tonos específicos de marca.

**Recomendación de opacidad:** Una opacidad de `0.7` (70 %) ofrece una pista visual clara mientras mantiene legible el texto subyacente.

### Paso 6: Aplicar la anotación
`addAnnotation` es un método de `Annotator` que registra la anotación preparada con el documento para que sea renderizada y guardada.

```java
annotator.add(strikeout);
```

### Paso 7: Guardar y limpiar
`dispose()` libera los recursos nativos mantenidos por la instancia de `Annotator`, evitando fugas de memoria después de que el procesamiento haya finalizado.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Nota sobre gestión de memoria:** Llamar a `dispose()` libera recursos nativos y previene fugas de memoria al procesar lotes de PDFs.

## Problemas comunes y cómo solucionarlos

### Problema 1: Errores “File Not Found”
**Síntomas:** Excepción lanzada durante la construcción de `Annotator`.  
**Solución:** Verifica tanto las rutas de entrada como de salida, y confirma que la aplicación tenga permisos de lectura/escritura.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problema 2: El tachado aparece en la ubicación incorrecta
**Síntomas:** La línea no se alinea con el texto deseado.  
**Solución:** Recuerda que las coordenadas Y del PDF aumentan hacia arriba. Usa una herramienta de depuración visual o imprime las dimensiones de la página para afinar los puntos.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problema 3: La anotación no es visible
**Síntomas:** No aparece ningún tachado después de guardar.  
**Posibles causas y soluciones:**
- **Opacidad demasiado baja:** Temporalmente establece la opacidad a `1.0` para verificar la visibilidad.  
- **Mezcla de colores:** Usa un color de alto contraste como rojo (`255`).  
- **Índice de página incorrecto:** Los números de página son base cero; asegúrate de apuntar a la página correcta.

### Problema 4: Problemas de memoria con archivos grandes
**Síntomas:** `OutOfMemoryError` o rendimiento lento.  
**Soluciones:**  
- Procesa los documentos en lotes más pequeños.  
- Usa la API de streaming si está disponible.  
- Siempre invoca `dispose()` después de cada documento.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Aplicaciones del mundo real y casos de uso

### Revisión de documentos legales
Los despachos de abogados anotan contratos con tachados para indicar cláusulas eliminadas mientras preservan una pista de auditoría.

### Edición de artículos académicos
Los profesores usan tachados para sugerir eliminaciones durante la revisión por pares, manteniendo el texto original visible para contexto.

### Sistemas de gestión de contenido
Plataformas de publicación marcan automáticamente secciones que violan políticas con tachados antes de la moderación manual.

### Control de versiones para documentos
Las empresas tratan las anotaciones de tachado como “marcadores de eliminación” en un flujo de trabajo de control de versiones centrado en documentos, similar a los diffs de código.

## Consejos para optimizar el rendimiento

### Estrategia de procesamiento por lotes
Al manejar muchos PDFs, reutiliza una única instancia de `Annotator` cuando sea posible y procesa los archivos en hilos paralelos.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Mejores prácticas de gestión de memoria
- Llama a `dispose()` en cada `Annotator`.  
- Limita las cargas concurrentes de documentos para evitar presión en el heap.  
- Monitorea el uso de memoria de la JVM con herramientas como VisualVM.

### Caché de coordenadas
Si aplicas el mismo diseño de anotación en varios archivos, almacena en caché los objetos `Point` para evitar recomputaciones.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Opciones de personalización avanzada

### Selección dinámica de color
Elige colores en tiempo de ejecución según reglas de negocio (p. ej., rojo para eliminaciones críticas, amarillo para tentativas).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Tachados de varias líneas
Crea una serie de pares `Point` para dibujar una línea en zig‑zag que cruce varias líneas de texto.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Lista de verificación de solución de problemas
1. **Permisos de archivo:** Verifica el acceso de lectura/escritura.  
2. **Versión de la biblioteca:** Asegúrate de usar una versión compatible de GroupDocs.Annotation.  
3. **Estado de la licencia:** Confirma que el archivo de licencia está referenciado correctamente.  
4. **Compatibilidad del PDF:** Comprueba que el PDF no esté corrupto y esté dentro de los límites de tamaño soportados.  
5. **Validación de coordenadas:** Asegúrate de que todos los puntos estén dentro de los límites de la página.  
6. **Espacio de heap:** Incrementa `-Xmx` de la JVM si procesas archivos muy grandes.

## Preguntas frecuentes

**P: ¿Puedo tachar texto que abarca varias líneas?**  
R: Sí. Crea varios objetos `Point` que tracen la ruta deseada; la anotación seguirá la polilínea suministrada.

**P: ¿Qué ocurre si especifico coordenadas fuera de los límites de la página?**  
R: La anotación será recortada y puede volverse invisible. Siempre valida las coordenadas contra el ancho y alto de la página.

**P: ¿Puedo eliminar anotaciones de tachado después de agregarlas?**  
R: Absolutamente. Usa el método `removeAnnotation` con el ID de la anotación o filtra por tipo para eliminarlas programáticamente.

**P: ¿Existe un límite de cuántas anotaciones puedo agregar a un solo PDF?**  
R: GroupDocs no impone un límite estricto, pero el rendimiento puede degradarse después de miles de anotaciones. Considera paginación o resumir anotaciones para conjuntos muy grandes.

**P: ¿Cómo trabajo con PDFs protegidos con contraseña?**  
R: Pasa la contraseña al constructor de `Annotator`. La biblioteca descifrará el documento en memoria antes de aplicar cualquier anotación.

**P: ¿Cómo manejo PDFs con diferentes tamaños y orientaciones de página?**  
R: Obtén las dimensiones de cada página mediante `annotator.getPageInfo(pageNumber)` y calcula las coordenadas relativas a esas dimensiones para asegurar una colocación consistente.

## Conclusión
Ahora tienes una solución completa y lista para producción para **how to add strikeout** annotations to PDFs in Java usando GroupDocs.Annotation. Al dominar el manejo de rutas de archivo, cálculo de coordenadas y gestión de recursos, puedes integrar esta capacidad en herramientas de revisión de documentos, pipelines de contenido o cualquier aplicación basada en Java que necesite retroalimentación visual precisa.

**Próximos pasos**
1. Clona el proyecto de ejemplo y ejecútalo contra un PDF de muestra.  
2. Experimenta con diferentes colores, opacidades y textos de comentario.  
3. Integra el flujo de trabajo de anotación en tu servicio de procesamiento de documentos existente.  
4. Explora tipos de anotación relacionados—resaltados, notas adhesivas y anotaciones de forma—para ampliar tu caja de herramientas de manipulación de PDFs.

¿Listo para más? Sumérgete en la documentación oficial para obtener conocimientos más profundos de la API.

## Recursos adicionales

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Documentación general de las bibliotecas GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Referencia completa de la API  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Detalles método por método  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Mantén tu biblioteca actualizada  
- [Purchase License](https://purchase.groupdocs.com/buy) - Licenciamiento listo para producción  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Evalúa antes de comprar  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Pruebas de desarrollo  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Ayuda de la comunidad y soporte oficial  

---

**Última actualización:** 2026-05-21  
**Probado con:** GroupDocs.Annotation 23.12 for Java  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)