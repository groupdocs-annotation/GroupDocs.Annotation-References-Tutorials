---
categories:
- Java Development
date: '2026-05-16'
description: Aprenda cómo crear respuestas de anotación en Java usando GroupDocs.Annotation.
  Domine la anotación PDF en Java con ejemplos prácticos, consejos de rendimiento
  y buenas prácticas.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Tutorial de Anotación PDF en Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Biblioteca Java de Anotación PDF: crear respuesta de anotación en Java'
type: docs
url: /es/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Biblioteca Java de Anotación PDF: crear respuesta de anotación java

Si necesitas **create annotation reply java** para PDFs—ya sea que estés construyendo un portal de revisión de contratos, un sistema de e‑learning o una canalización de procesamiento masivo—esta guía te muestra exactamente cómo hacerlo con GroupDocs.Annotation para Java. Recorreremos la configuración, la creación de anotaciones onduladas, el encadenamiento de respuestas y la optimización del rendimiento para que puedas entregar una solución fiable en días, no semanas.

## Respuestas rápidas
- **¿Cuál es el propósito principal de GroupDocs.Annotation?** Permite la creación, modificación y extracción programática de anotaciones PDF en Java.  
- **¿Cómo añado una anotación ondulada?** Instancia `SquigglyAnnotation`, establece su geometría y estilo, luego llama a `annotator.add(...)`.  
- **¿Puedo adjuntar respuestas a una anotación?** Sí—crea objetos `Reply`, establece el autor y el texto, y asócialos con la anotación principal.  
- **¿Necesito una licencia para producción?** Absolutamente; sin una licencia válida la salida contendrá marcas de agua.  
- **¿Es adecuada para procesamiento por lotes?** Sí—utiliza try‑with‑resources para abrir cada documento, anotarlo y cerrarlo, manteniendo bajo el uso de memoria.  

## Por qué los desarrolladores Java necesitan bibliotecas de anotación PDF

Marcar PDFs manualmente consume tiempo y es propenso a errores, especialmente cuando tienes que revisar cientos de contratos o exámenes. Una biblioteca Java de anotación PDF automatiza este trabajo, permitiéndote incrustar resaltados, subrayados ondulados y comentarios en hilo directamente en el archivo. El resultado es un documento portátil y buscable que conserva todas las marcas sin necesidad de un visor separado.

**Lo que dominarás en esta guía**
- Instalar y licenciar GroupDocs.Annotation en un proyecto Maven  
- Construir anotaciones onduladas que se asemejen a los subrayados nativos de Word  
- Añadir respuestas en hilo a cualquier anotación para revisión colaborativa  
- Optimizar el uso de memoria y CPU al procesar PDFs grandes  
- Desplegar la solución en Spring Boot, micro‑servicios o aplicaciones de escritorio  

Ya sea que estés construyendo un sistema de revisión de documentos legales, una herramienta de calificación educativa o una canalización automatizada de control de calidad, las técnicas a continuación te proporcionarán una base lista para producción.

## ¿Qué es create annotation reply java?

`create annotation reply java` es el proceso programático de adjuntar un hilo de comentarios (un Reply) a una anotación PDF existente usando Java. Las respuestas permiten que varios revisores discutan una marca específica sin salir del documento, habilitando una colaboración fluida y en el mismo lugar. Esta capacidad convierte un PDF estático en una plataforma de discusión interactiva, preservando el contexto y los registros de auditoría directamente dentro del archivo.

## Prerrequisitos: Preparando tu entorno

Antes de sumergirnos en el código, verifica que tu estación de desarrollo cumpla con estas especificaciones:

- **JDK** 8 o superior (se recomienda JDK 11 + para un mejor rendimiento de recolección de basura)  
- **Maven** o **Gradle** para la gestión de dependencias (los ejemplos usan Maven)  
- Un IDE con soporte Maven (IntelliJ IDEA, Eclipse o VS Code)  
- Al menos **2 GB** de RAM libre para el IDE y ejecuciones de prueba  
- Archivos PDF de muestra para experimentación (puedes generar PDFs simples con cualquier editor de PDF)

GroupDocs.Annotation se ejecuta completamente en proceso; no se requieren visores PDF externos ni bibliotecas nativas.

## Configuración de GroupDocs.Annotation para Java

Integrar la biblioteca es un proceso de varios pasos, pero un par de trampas ocultas pueden causar errores en tiempo de ejecución si las omites.

### Configuración de dependencia Maven

Agrega el repositorio y la dependencia a tu `pom.xml`. Coloca el elemento `<repositories>` **antes** de `<dependencies>` para asegurar que Maven pueda resolver el artefacto.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **Consejo profesional:** Consulta la página de lanzamientos de GroupDocs para obtener la última versión. Las nuevas versiones a menudo incluyen soporte para estándares PDF emergentes y mejoras de rendimiento.

### Configuración de licencia (¡No lo omitas!)

GroupDocs.Annotation requiere un archivo de licencia para uso en producción. Sin él, cada PDF generado llevará una marca de agua.

1. **Prueba gratuita** – Conjunto completo de funciones durante 30 días, ideal para evaluación.  
2. **Licencia temporal** – Buena para desarrollo y pruebas internas.  
3. **Licencia completa** – Requerida para cualquier despliegue comercial.

Coloca el archivo `GroupDocs.Annotation.lic` en tu carpeta de recursos y cárgalo al iniciar:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Error común:** Olvidar el paso de la licencia resulta en PDFs con marcas de agua y llamadas a la API que fallan silenciosamente. Siempre valida la licencia al inicio de tu rutina de arranque.

## Guía completa de implementación: Añadiendo anotaciones onduladas

A continuación se muestra una guía paso a paso que explica cómo **create annotation reply java** mientras construyes una anotación ondulada. Cada paso incluye una explicación concisa, para que comprendas el “por qué” detrás de cada línea.

### Paso 1: Importar todas las clases requeridas

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` es el punto de entrada para todas las operaciones a nivel de documento.  
- `Point` representa una coordenada en una página (X y Y medidos desde la esquina superior izquierda).  
- `SquigglyAnnotation` define el subrayado ondulado usado para resaltar errores.  
- `Reply` almacena comentarios en hilo adjuntos a una anotación.  
- `SaveOptions` te permite controlar el formato de salida y la compresión.  

### Paso 2: Crear y configurar tu anotación ondulada

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation es una clase que crea un subrayado ondulado usado para resaltar errores en un PDF.

- **Sistema de coordenadas**: Los puntos comienzan en la esquina superior izquierda. Los dos puntos anteriores dibujan una línea ondulada horizontal de (100, 200) a (300, 200).  
- **Opacidad** 0.7 significa que la anotación es 70 % opaca, permitiendo que el texto subyacente siga siendo legible.  

### Paso 3: Añadir respuestas interactivas (Opcional pero potente)

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

`Reply` es una clase que representa un hilo de comentarios adjunto a una anotación.

- Las respuestas crean una **discusión en hilo** directamente sobre la anotación, replicando la experiencia de los revisores de PDF modernos.  
- Cada respuesta almacena información del autor y una marca de tiempo, que puedes filtrar o mostrar posteriormente en una interfaz.  

### Paso 4: Aplicar la anotación y guardar el documento

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- La construcción **try‑with‑resources** cierra automáticamente el `Annotator`, liberando manejadores de archivo y buffers nativos.  
- `save` escribe el PDF modificado en `output.pdf`.  

> **Nota de memoria:** El `Annotator` carga solo las páginas que tocas. Para PDFs de varios cientos de páginas, este enfoque mantiene el uso del heap por debajo de 150 MB en un servidor típico.

## Opciones avanzadas de configuración

### Personalizando la apariencia de la anotación

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Ancho del borde** controla el grosor de la línea (en puntos).  
- El formato **ARGB** incluye un canal alfa para la transparencia.  

### Posicionamiento preciso de anotaciones

Obtener las coordenadas correctas puede ser complicado en PDFs con tamaños de página variables. Sigue este enfoque sistemático:

1. **Abre el PDF en un visor** (p. ej., Adobe Acrobat) y anota los valores de la regla para el área objetivo.  
2. **Convierte los valores de la regla** a puntos (1 punto = 1/72 pulgada).  
3. **Utiliza `annotator.getPageInfo(pageIndex)`** para obtener el ancho y alto de la página, luego calcula posiciones relativas.  

## Problemas comunes y soluciones

### Problema: Las anotaciones no aparecen

**Causas más probables**
- Los puntos están fuera de los límites de la página  
- Licencia no cargada (la marca de agua oculta la anotación)  
- Número de página incorrecto (las páginas son indexadas desde cero en la API)  

**Lista de verificación de solución**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Problema: Rendimiento deficiente con archivos grandes

Cargar un PDF de 500 páginas en memoria puede bloquear tu servicio. Mitíguelo mediante:

- **Procesar una página a la vez** – abre el documento, anota una sola página, guarda, luego pasa a la siguiente.  
- **Streaming** – usa la API de streaming de `Annotator` para evitar el almacenamiento completo del documento.  
- **Caching** – almacena PDFs de acceso frecuente en una caché rápida (p. ej., Redis) y anota la copia en caché.  

### Problema: Los valores de color no funcionan

GroupDocs espera **ARGB** (Alfa, Rojo, Verde, Azul) en lugar de RGB simple. Un valor ARGB de `0xFFFF0000` significa rojo totalmente opaco. Si proporcionas `0xFF0000` la biblioteca lo interpreta incorrectamente, resultando en una anotación negra.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Mejores prácticas de rendimiento

### Gestión de memoria

Al anotar decenas de PDFs en un trabajo por lotes, envuelve cada archivo en su propio bloque try‑with‑resources:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Este patrón garantiza que los buffers nativos se liberen después de cada iteración, evitando **OutOfMemoryError** en procesos de larga duración.

### Optimización del procesamiento por lotes

Para entornos de alto rendimiento, considera streams paralelos combinados con un pool de hilos limitado:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Pool limitado** evita la explosión de hilos, mientras que los streams paralelos mantienen ocupados los núcleos de CPU.

### Consideraciones sobre el tamaño de archivo

Los PDFs grandes (> 100 MB) pueden degradar el rendimiento. Aplica estas estrategias:

- **Pre‑comprimir** el PDF fuente con una herramienta como Ghostscript antes de la anotación.  
- **Anotar solo las páginas necesarias** – omite páginas que no requieran marcas.  
- **Dividir** el documento en secciones lógicas (p. ej., por capítulo) y procesar cada fragmento de forma independiente.  

## Aplicaciones del mundo real

### Sistemas de revisión de documentos

Los despachos legales a menudo necesitan marcar cláusulas problemáticas. Las anotaciones onduladas combinadas con respuestas en hilo permiten que varios abogados discutan un mismo párrafo sin salir del PDF:

- **Abogado A** añade una ondulación roja bajo una cláusula y escribe “Redacción ambigua”.  
- **Abogado B** responde “Agregar definición para ‘incumplimiento material’”.  
- Toda la discusión permanece incrustada, buscable y auditable.

### Integración con sistemas existentes

GroupDocs.Annotation funciona sin problemas con los frameworks Java populares:

- **Spring Boot** – expone un endpoint REST `/api/annotate` que acepta una carga multipart PDF, añade anotaciones y devuelve el resultado en streaming.  
- **JSF** – vincula acciones de anotación a componentes UI para marcar sobre la marcha en una vista web.  
- **Microservicios** – la pequeña huella de la biblioteca (< 15 MB) te permite contenerizarla con Docker y escalar horizontalmente.  

### Automatización de flujos de trabajo

Combina la anotación con otros productos GroupDocs (p. ej., GroupDocs.Signature) para construir pipelines de extremo a extremo:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Cuándo usar anotaciones onduladas vs. alternativas

| Caso de uso | Anotación recomendada |
|-------------|-----------------------|
| Marcar errores ortográficos o gramaticales | **Squiggly** – pista visual similar a los procesadores de texto |
| Resaltar secciones importantes sin implicar un error | **Highlight** – superposición translúcida |
| Proporcionar retroalimentación detallada | **Text** o **Comment** – cuadro de notas de forma libre |
| Aprobar o rechazar un documento | **Stamp** – insignia “Approved” o “Rejected” |

## Conclusión

Ahora tienes una receta completa y lista para producción de **create annotation reply java** usando GroupDocs.Annotation. Al dominar la API, gestionar la licencia y aplicar los consejos de rendimiento anteriores, puedes:

- Automatizar el marcado de errores en miles de PDFs  
- Habilitar discusiones colaborativas en hilo dentro del propio archivo  
- Mantener bajo el uso de memoria incluso al procesar documentos masivos  

**Próximos pasos**
1. Experimenta con otros tipos de anotación (resaltados, sellos, texto).  
2. Construye un servicio REST que reciba PDFs, los anote y devuelva el resultado.  
3. Explora la API de extracción (`annotator.get()`) para obtener comentarios existentes para análisis.  

El poder de la anotación PDF programática radica en su capacidad para reemplazar el tedioso marcado manual con código repetible y auditable. Ya sea que estés construyendo un producto legal‑tech de nicho o un motor de flujo de trabajo de documentos de propósito general, las técnicas de esta guía te brindan una base sólida para avanzar.

## Preguntas frecuentes

**Q: ¿Qué hace que GroupDocs.Annotation sea mejor que otras bibliotecas Java PDF?**  
A: GroupDocs.Annotation se centra exclusivamente en flujos de trabajo de anotación, ofreciendo más de 30 tipos de anotación, respuestas en hilo y soporte nativo para más de 50 formatos de archivo, manteniendo la huella de memoria bajo 200 MB para PDFs de 500 páginas.

**Q: ¿Puedo usar esta biblioteca con aplicaciones Spring Boot?**  
A: Absolutamente. Crea un `@RestController` que inyecte el servicio `Annotator`, procese cargas multipart y transmita el PDF anotado de vuelta al cliente. Recuerda configurar un pool de hilos para solicitudes concurrentes.

**Q: ¿Cómo manejo documentos con diferentes tamaños de página?**  
A: Consulta las dimensiones de cada página mediante `annotator.getPageInfo(pageIndex)` y calcula coordenadas relativas (p. ej., porcentajes) en lugar de codificar valores de puntos. Esto asegura que las anotaciones aparezcan correctamente en páginas A4, Letter y de tamaño personalizado.

**Q: ¿Hay una forma de extraer anotaciones existentes de PDFs?**  
A: Sí. Llama a `annotator.get()` para obtener una colección de todas las anotaciones, luego itera para leer propiedades como autor, comentario y geometría. Esto es útil para escenarios de migración o análisis.

**Q: ¿Cuál es el mejor enfoque para manejar permisos de anotación en sistemas multi‑usuario?**  
A: Implementa autenticación en la capa de aplicación, almacena el ID de usuario con cada `Reply` y aplica reglas de negocio (p. ej., solo el autor o un administrador pueden editar o eliminar una respuesta). La API en sí no impone permisos, dándote total flexibilidad.

**Q: ¿Cómo optimizo el uso de memoria al procesar cientos de PDFs?**  
A: Usa try‑with‑resources para cada documento, procesa páginas individualmente y considera un pool de hilos limitado para restringir el consumo de memoria concurrente. Monitorear el heap de JVM con herramientas como VisualVM te ayuda a ajustar finamente la configuración `-Xmx`.

---

**Última actualización:** 2026-05-16  
**Probado con:** GroupDocs.Annotation 25.2 para Java  
**Autor:** GroupDocs  

**Recursos adicionales**
- [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)
- [Complete API Reference](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## Tutoriales relacionados

- [Java PDF Annotation Library Tutorial](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Remove Annotation Replies Java - Manage Replies by ID with GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)