---
date: '2026-10-16'
description: Aprende cómo guardar PDF sin anotaciones en Java, domina la gestión de
  memoria de PDF en Java y agrega anotaciones subrayadas con GroupDocs.Annotation.
  Guía paso a paso.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Anotación de documentos Java con GroupDocs
og_description: Aprende cómo guardar PDF sin anotaciones en Java, domina la gestión
  de memoria de PDF en Java y agrega anotaciones subrayadas con GroupDocs.Annotation.
  Guía paso a paso.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Cómo guardar PDF sin anotaciones en Java usando GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Cómo guardar PDF sin anotaciones en Java usando GroupDocs
type: docs
url: /es/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Cómo guardar PDF sin anotaciones en Java usando GroupDocs

Si necesita **guardar PDF sin anotaciones** y aún así poder añadir notas subrayadas colaborativas, está en el lugar correcto. Muchos desarrolladores Java tienen dificultades para mantener una versión limpia de un documento para la distribución final, especialmente cuando el mismo archivo se usa para revisiones iterativas. En este tutorial aprenderá a generar un PDF limpio, gestionar la memoria de forma eficiente y aplicar anotaciones de subrayado con comentarios usando GroupDocs.Annotation. Al final comprenderá el flujo de trabajo completo—desde cargar un PDF hasta producir una copia final sin marcas de agua—más consejos de mejores prácticas para construir un robusto **sistema de revisión de documentos java**.

## Respuestas rápidas
- **¿Cómo añado una anotación de subrayado?** Use `UnderlineAnnotation` con `annotator.add()` y luego guarde el documento.  
- **¿Cómo puedo guardar PDF sin anotaciones?** Cargue el archivo anotado, establezca `AnnotationType.NONE` en `SaveOptions` y guarde una nueva copia.  
- **¿Qué bibliotecas se requieren?** GroupDocs.Annotation v25.2 (o más reciente) y su repositorio Maven.  
- **¿Necesito una licencia para producción?** Sí—aplique una licencia válida de GroupDocs para evitar marcas de agua.  
- **¿Puedo procesar varios documentos de forma eficiente?** Envuelva cada `Annotator` en un bloque try‑with‑resources y disponga después de cada archivo.

## ¿Cómo guardo PDF sin anotaciones en Java?

Cargue el PDF fuente con un `Annotator`, configure `SaveOptions` para excluir todos los tipos de anotación y llame a `save()` para escribir una copia limpia. Esta operación no modifica el archivo original, por lo que conserva tanto la versión anotada para los revisores como una versión pristina para la distribución. El proceso usa streaming bajo el capó, lo que significa que el documento completo nunca reside en memoria—crucial para PDFs grandes.

## ¿Qué es guardar PDF sin anotaciones?

`save pdf without annotations` se refiere a exportar un documento PDF mientras se eliminan todos los objetos de anotación (resaltados, comentarios, sellos, subrayados, etc.). El archivo resultante contiene solo el contenido y el diseño original, lo que lo hace adecuado para presentación legal, publicación pública o almacenamiento de archivo.

## ¿Por qué crear PDFs limpios en un sistema de revisión de documentos Java?

Una versión limpia elimina marcas de revisores, comentarios y resaltados, dándole un documento pulido listo para clientes, reguladores o publicación pública. También reduce el tamaño del archivo hasta en un 30 % en promedio y previene la divulgación accidental de notas internas—crítico para flujos de trabajo legales y de cumplimiento. GroupDocs.Annotation puede eliminar todos los objetos de anotación en una sola pasada, soportando PDFs de hasta 500 MB sin cargar todo el archivo en memoria.

## Requisitos previos y configuración del entorno

### Requisitos antes de comenzar

**Requisitos del entorno de desarrollo**  
- Java Development Kit (JDK) 8 o superior (se recomienda JDK 11+)  
- Maven 3.6+ o Gradle 6.0+ para la gestión de dependencias  
- IDE como IntelliJ IDEA, Eclipse o VS Code con extensiones Java  
- Al menos 2 GB de RAM disponible (el procesamiento de documentos puede ser intensivo en memoria)

**Prerequisitos de conocimiento**  
Debe estar cómodo con conceptos básicos de Java—inicialización de objetos, llamadas a métodos y dependencias Maven. La experiencia previa con bibliotecas de terceros acelerará la adopción.

**Documentos de prueba**  
Tenga algunos PDFs de muestra listos. Los PDFs basados en texto funcionan mejor; las imágenes escaneadas pueden requerir OCR antes de la anotación.

### Configuración de Maven: obteniendo GroupDocs en su proyecto

Agregue la siguiente dependencia a su `pom.xml`. Este paso suele confundir a muchos desarrolladores en su primer intento porque el group ID y el artifact ID deben coincidir exactamente.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Importante:** La versión 25.2 es la última versión estable al momento de escribir. Revise el repositorio de GroupDocs regularmente para versiones más nuevas que incluyan correcciones de errores y mejoras de rendimiento.

### Configuración de licencia (no lo omita)

**Para desarrollo/pruebas** – Descargue la prueba gratuita desde el sitio web de GroupDocs. La prueba incluye todas las funciones pero agrega una marca de agua a los documentos procesados.

**Para producción** – Compre una licencia y aplíquela durante el inicio de la aplicación. Sin una licencia válida, las compilaciones de producción estarán limitadas y tendrán marcas de agua.

## Guía de implementación: añadiendo anotaciones de subrayado

### Comprendiendo el flujo de trabajo de anotación

Antes de sumergirnos en el código, revisemos el flujo de trabajo de cuatro pasos que ocurre cuando **anota PDF en Java**:

1. **Carga del documento** – `Annotator` lee el archivo en memoria.  
2. **Creación de anotación** – Defina propiedades como posición, estilo y comentarios.  
3. **Aplicación de anotación** – La biblioteca inyecta la anotación en la estructura del PDF.  
4. **Guardado del documento** – Persista el archivo modificado, opcionalmente preservando el original.

El proceso es no destructivo; el archivo fuente permanece intacto a menos que lo sobrescriba.

### Paso 1: inicializar el anotador y cargar su documento

`Annotator` es el punto de entrada principal en GroupDocs.Annotation para cargar y modificar documentos PDF. Abstrae el manejo del sistema de archivos, la gestión de streams y la asignación de recursos nativos.

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

**Consejo profesional:** Use rutas absolutas mientras desarrolla para evitar errores de “archivo no encontrado”. En producción, considere cargar recursos desde el classpath o un bucket de almacenamiento en la nube.

### Paso 2: crear comentarios y respuestas (la parte colaborativa)

Los objetos `Comment` representan discusiones en hilo adjuntas a una anotación. Cada comentario puede tener un autor, una marca de tiempo y respuestas opcionales, lo que permite una conversación completa alrededor de una marca específica.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Uso en el mundo real:** Los revisores pueden discutir una cláusula específica añadiendo respuestas en hilo, manteniendo la conversación vinculada a la anotación exacta.

### Paso 3: definir coordenadas de anotación (obtener la posición correcta)

`Point` define una única coordenada en el espacio PDF (medida en puntos, donde 72 puntos = 1 pulgada). Se requieren cuatro puntos para un subrayado: dos para la línea de inicio y dos para la línea de fin.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**Sistema de coordenadas:**  
- Los puntos 1 y 2 definen el borde superior del subrayado.  
- Los puntos 3 y 4 definen el borde inferior.  
- La diferencia Y (730 vs 650) controla el grosor.

### Paso 4: crear y configurar la anotación de subrayado

`UnderlineAnnotation` es la clase concreta que representa una marca de subrayado. Hereda de la clase base `Annotation` y agrega propiedades específicas de los subrayados, como el grosor de línea y el estilo.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**Consejos de color y opacidad:**  
- `FontColor` usa ARGB; `65535` (0x00FFFF) produce amarillo brillante.  
- Para rojo, use `16711680` (0xFF0000); para azul, `255` (0x0000FF).  
- Valores de opacidad entre 0.5 y 0.8 proporcionan buena legibilidad sin oscurecer el texto.

### Paso 5: guardar su documento anotado

`SaveOptions` le permite controlar el formato de salida, si se deben incrustar anotaciones y cómo manejar los metadatos. Establecer `AnnotationType.NONE` indica a la biblioteca que elimine todos los objetos de anotación, lo que es la clave para **guardar PDF sin anotaciones**.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Gestión de memoria:** La llamada `dispose()` libera recursos nativos y previene fugas de memoria—crítico al procesar muchos archivos en lote.

## Eliminar anotaciones: crear versiones limpias del documento

A veces necesita una versión del PDF **sin ninguna anotación**—por ejemplo, al entregar el contrato final aprobado. GroupDocs facilita esto.

### Comprendiendo las opciones de eliminación de anotaciones

Puede:  
- Eliminar **todas** las anotaciones (lo más común)  
- Eliminar tipos específicos (p.ej., solo resaltados)  
- Eliminar anotaciones por autor o página  

### Eliminación de anotaciones paso a paso

**Paso 1: cargar el documento previamente anotado**

`Annotator` vuelve a actuar como cargador; leerá el archivo que aún contiene objetos de anotación.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Paso 2: configurar opciones de guardado para una salida limpia**

`SaveOptions` ofrece una API fluida para especificar que no se escriban tipos de anotación en el archivo de salida.

```java
Annotator annotator = new Annotator(outputPath);
```

**Paso 3: guardar la versión limpia**

Llamar a `save()` con las opciones configuradas escribe un PDF que contiene solo el contenido original.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Esto produce un archivo **PDF limpio** que no contiene objetos de anotación, perfecto para la distribución final.

## Problemas comunes y soluciones

### Problema 1: errores “Documento no encontrado”

Asegúrese de que la ruta del archivo sea correcta y de que la aplicación tenga permisos de lectura. Usar `Path.of()` con rutas absolutas elimina la mayoría de las ambigüedades.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problema 2: Anotaciones aparecen en ubicaciones incorrectas

El origen de coordenadas del PDF está en la esquina inferior‑izquierda. Verifique que sus valores Y aumenten hacia arriba y que tenga en cuenta la rotación de la página.

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Problema 3: Problemas de memoria con documentos grandes

GroupDocs.Annotation procesa contenido en streaming y nunca carga el archivo completo en la memoria del heap. Sin embargo, aún debe llamar a `dispose()` y considerar aumentar el heap de JVM (`-Xmx`) para archivos mayores de 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problema 4: Problemas de licencia en producción

Si el archivo de licencia falta o la ruta es incorrecta, la biblioteca recurre al modo de prueba, añadiendo una marca de agua a cada página. Coloque el archivo de licencia en una ubicación que esté en el classpath y cárguelo temprano en el ciclo de vida de su aplicación.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Mejores prácticas de rendimiento para aplicaciones de producción

### Estrategias de gestión de memoria

GroupDocs.Annotation procesa PDFs de forma streaming, lo que permite manejar archivos de hasta 500 MB sin cargar todo el documento en memoria. Aún así, siga estas directrices:

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Consideraciones de subprocesamiento

GroupDocs.Annotation **no es thread‑safe** por defecto. Si su aplicación procesa documentos concurrentemente:

- **Nunca comparta** una instancia de `Annotator` entre hilos.  
- **Sincronice** el acceso a archivos o use un mecanismo de bloqueo.  
- Considere un **pool** de objetos `Annotator` si necesita alto rendimiento.

### Estrategias de caché

- Cachear plantillas de anotación usadas frecuentemente.  
- Reutilizar colecciones `Point` para conjuntos de coordenadas comunes.  
- Mantenga un **PDF plantilla** en memoria si anota repetidamente el mismo documento base.

## Mejores prácticas de gestión de memoria de PDF en Java

El uso eficiente de la memoria es esencial al manejar PDFs grandes o procesar muchos archivos en lote. Aquí hay algunas recomendaciones prácticas:

- **Use try‑with‑resources** para cada `Annotator` para garantizar la disposición.  
- **Aumente el heap de JVM** (`-Xmx`) solo según sea necesario; monitoree el uso con herramientas de perfilado.  
- **Procese documentos secuencialmente** cuando sea posible, liberando memoria después de cada archivo.  
- **Evite cargar el mismo PDF múltiples veces**; reutilice el mismo stream si necesita leerlo repetidamente.

Aplicar estas prácticas ayuda a que su aplicación sea receptiva y previene fallos por falta de memoria durante cargas intensas de anotación.

## Aplicaciones del mundo real y casos de uso

### Sistemas de revisión de documentos

- **Revisión legal:** Subraye cláusulas de contrato y añada comentarios sobre riesgos.  
- **Auditorías de cumplimiento:** Resalte secciones problemáticas en estados financieros.  
- **Revisión académica por pares:** Los profesores subrayan pasajes que necesitan aclaración.

### Plataformas educativas

- **Herramientas de anotación para estudiantes:** Permita a los alumnos subrayar conceptos clave en libros electrónicos.  
- **Retroalimentación del docente:** Proporcione comentarios en línea directamente en las tareas entregadas.

### Flujos de trabajo de aseguramiento de calidad

- **Revisión de documentación técnica:** Los ingenieros subrayan secciones que necesitan actualizaciones.  
- **Procedimientos operativos estándar:** Los oficiales de seguridad resaltan pasos críticos.

### Sistemas de gestión de contenido

- **Flujo editorial:** Los editores subrayan texto que requiere verificación de hechos.  
- **Control de versiones:** Rastrear el historial de anotaciones a través de revisiones de documentos.

## Consejos avanzados para una implementación profesional

### Estilos de anotación personalizados

Puede extender la apariencia visual de un subrayado configurando patrones de guiones personalizados, extremos de línea y niveles de opacidad. Esto es útil cuando necesita diferenciar roles de revisores (p.ej., legal vs. ingeniería).

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Metadatos de anotación para seguimiento

Cada anotación puede llevar un diccionario de metadatos definido por el usuario. Almacene IDs, marcas de tiempo o estado del flujo de trabajo para integrarse con sistemas de seguimiento externos.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integración con sistemas de gestión de usuarios

Mape la propiedad `author` de un `Comment` a los IDs de usuario de su aplicación. Esto permite estilos basados en roles y generación de auditorías.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Resolución de problemas en producción

### Monitoreo de rendimiento

Observe estas métricas en producción:  
- **Uso del heap** – asegúrese de que se llame a `dispose()`.  
- **Tiempo de procesamiento por documento** – registre marcas de tiempo antes/después de `annotator.save()`.  
- **Tasa de errores** – capture excepciones y categorícelas.

### Problemas comunes en producción

- **Bloqueo de archivos** – asegúrese de que los archivos subidos estén cerrados antes de la anotación.  
- **Ediciones concurrentes** – implemente bloqueo optimista o verificaciones de versión.  
- **Archivos grandes (> 50 MB)** – aumente el tiempo de espera de JVM y considere APIs de streaming.

### Mejores prácticas de manejo de errores

Envuelva todas las llamadas de anotación en bloques try‑catch, registre la traza completa y vuelva a lanzar una `AnnotationException` personalizada con un mensaje amigable para el usuario. Este patrón simplifica la depuración y brinda retroalimentación clara a los consumidores de la API.

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Preguntas frecuentes

**P: ¿Cómo anoto múltiples áreas de texto en una sola operación?**  
R: Cree varios objetos `UnderlineAnnotation` con diferentes coordenadas y añádalos secuencialmente usando `annotator.add()`.

**P: ¿Puedo anotar imágenes dentro de documentos PDF?**  
R: Sí. Use el mismo sistema de coordenadas, asegurándose de que los puntos estén dentro de los límites de la imagen.

**P: ¿Qué formatos de archivo, además de PDF, soporta GroupDocs.Annotation?**  
R: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) y formatos de imagen como JPEG, PNG, TIFF.

**P: ¿Cómo manejo documentos muy grandes sin quedarme sin memoria?**  
R: Procese los documentos uno a la vez, aumente el heap de JVM (`-Xmx`) y siempre disponga rápidamente de las instancias de `Annotator`.

**P: ¿Es posible extraer anotaciones existentes de un documento?**  
R: Sí. Use `annotator.get()` para obtener todas las anotaciones, luego filtre por tipo, autor o página según sea necesario.

---

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs  

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Tutoriales relacionados

- [Crear PDF limpio Java: anotaciones de subrayado con GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Editar anotaciones PDF Java - Tutorial completo de GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Anotar PDFs con GroupDocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)