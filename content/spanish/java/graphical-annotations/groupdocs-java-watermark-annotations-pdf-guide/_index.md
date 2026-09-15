---
categories:
- Java PDF Processing
date: '2026-07-30'
description: Aprende cómo aplicar una marca de agua en todas las páginas de PDFs en
  Java usando GroupDocs.Annotation. Este tutorial paso a paso muestra cómo añadir
  una marca de agua en PDF a múltiples páginas, con ejemplos de código, consejos de
  solución de problemas y buenas prácticas.
keywords:
- apply watermark all pages
- pdf watermark multiple pages
- java add watermark pdf
- add pdf watermark java
lastmod: '2026-07-30'
linktitle: Guía de Marca de Agua en PDF con Java
og_description: Aplica una marca de agua en todas las páginas de PDFs usando GroupDocs.Annotation
  para Java. Esta guía cubre la marca de agua en PDF en múltiples páginas, configuración,
  código y solución de problemas en un tutorial conciso.
og_image_alt: 'Guide: Apply watermark to all pages of a PDF using GroupDocs.Annotation
  Java'
og_title: Aplicar Marca de Agua en Todas las Páginas – Guía de Marca de Agua en PDF
  con Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  headline: Apply Watermark All Pages – Java PDF Watermark Guide
  type: TechArticle
- description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  name: Apply Watermark All Pages – Java PDF Watermark Guide
  steps:
  - name: Import the Required Classes
    text: Before you can use the API, import the essential classes. **Definition:**
      Import statements bring the needed GroupDocs.Annotation classes into the current
      Java file, allowing you to reference them without fully qualified names.
  - name: Load the PDF Document
    text: Create the `Annotator` instance that points to your source PDF. **Definition:**
      The `Annotator` constructor loads the PDF file into a manageable object, preparing
      it for annotation operations. > **Pro tip:** For PDFs larger than 50 MB, consider
      increasing the JVM heap (`-Xmx4g`) and processing files
  - name: (Optional) Prepare Reply Metadata
    text: If you need to attach comments or approval notes to the watermark, create
      a `Reply` object. **Definition:** `Reply` stores user‑generated comments that
      accompany an annotation, useful for audit trails.
  - name: Configure the Watermark Appearance
    text: Set the visual properties such as text, color, rotation, size, and opacity.
      **Definition:** The following setters customize the watermark’s look and placement
      on each page.
  - name: Loop Through All Pages and Apply the Watermark
    text: To **apply watermark all pages**, iterate over the document’s page count
      and assign the annotation to each page. **Definition:** `annotator.getPageCount()`
      returns the total number of pages, enabling a loop that creates a separate `WatermarkAnnotation`
      per page.
  - name: Save the Watermarked PDF
    text: Finally, write the changes to a new file. The original PDF remains untouched.
      **Definition:** `annotator.save("output.pdf")` persists all added annotations
      into a new PDF file. That’s the complete flow for **apply watermark all pages**
      using GroupDocs.Annotation for Java.
  type: HowTo
- questions:
  - answer: Loop over the document’s page count, clone a configured `WatermarkAnnotation`
      for each page, set `setPageNumber(i)`, and add it with `annotator.add()`.
    question: How do I add watermarks to multiple pages in a PDF?
  - answer: GroupDocs.Annotation uses fonts installed on the host OS. Specify a font
      family that exists on the server; the library falls back to a default if the
      font isn’t found.
    question: Can I use custom fonts for my watermarks?
  - answer: Between **0.3** and **0.7** provides a balance—visible enough to be noticed
      but still allows underlying content to be read.
    question: What opacity setting works best for professional watermarks?
  - answer: Increase the JVM heap (`-Xmx4g` or more), process files one at a time,
      and always call `dispose()` after each document to free native resources.
    question: How should I handle very large PDF files?
  - answer: 'Yes—retrieve annotations with `annotator.get()`, filter for `WatermarkAnnotation`,
      then edit or delete as needed:'
    question: Is it possible to remove or modify existing watermarks?
  type: FAQPage
tags:
- java pdf watermark
- groupdocs annotation
- document security
- apply watermark all pages
- pdf processing
title: Aplicar Marca de Agua en Todas las Páginas – Guía de Marca de Agua en PDF con
  Java
type: docs
url: /es/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/
weight: 1
---

# Aplicar marca de agua a todas las páginas – Guía de marca de agua PDF en Java

En este tutorial completo aprenderás **cómo aplicar marca de agua a todas las páginas** a un documento PDF usando Java y GroupDocs.Annotation. Ya sea que necesites proteger informes confidenciales, marcar PDFs de marketing con la marca de la empresa, o agregar un sello “CONFIDENTIAL” en todo el archivo, los pasos a continuación te guiarán a través de todo—desde la configuración de Maven hasta la personalización avanzada—para que puedas implementar una solución fiable en minutos.

## Respuestas rápidas
- **¿Qué biblioteca puede agregar marca de agua PDF a múltiples páginas en Java?** GroupDocs.Annotation for Java.  
- **¿Necesito una licencia?** Sí, una prueba gratuita funciona para desarrollo; se requiere una licencia completa para producción.  
- **¿Puedo aplicar marca de agua a todas las páginas a la vez?** Sí – crea una anotación de marca de agua para cada página en un bucle.  
- **¿Qué versión de Java se requiere?** JDK 8+ (se recomienda JDK 11+).  
- **¿Cómo controlo la opacidad?** Usa `setOpacity(double)` donde 0.0 es totalmente transparente y 1.0 es totalmente opaco.

## Por qué necesitas marcas de agua PDF (y cómo Java lo facilita)

¿Alguna vez te has preocupado de que un PDF confidencial sea compartido sin tu permiso? ¿O necesitaste una forma rápida de marcar cada página de un folleto de ventas? Añadir marcas de agua programáticamente elimina el esfuerzo manual, garantiza la consistencia y refuerza la seguridad del documento. Con Java y GroupDocs.Annotation—una de las bibliotecas **java add watermark pdf** más robustas—obtienes un control granular sobre la posición, rotación, color y opacidad, todo mientras manejas archivos grandes de manera eficiente.

**Lo que dominarás al final de esta guía:**
- Configurar GroupDocs.Annotation para marcas de agua en Java  
- Crear anotaciones de marca de agua personalizadas que se apliquen a **todas las páginas**  
- Manejar PDFs grandes sin agotar la memoria  
- Solucionar problemas comunes y optimizar el rendimiento  

## Qué es una marca de agua PDF y por qué usarla en múltiples páginas?

Una marca de agua PDF es una superposición que aparece sobre el contenido del documento sin alterar el texto o imágenes subyacentes. Aplicar una marca de agua a **todas las páginas** garantiza que cada página lleve la misma marca o aviso de confidencialidad, evitando la distribución accidental de páginas sin marcar.

## Requisitos previos

### Requisitos esenciales
- **Entorno Java:** JDK 8 o superior (se recomienda JDK 11+), Maven 3.6+, cualquier IDE (IntelliJ, Eclipse, VS Code).  
- **Prerequisitos de conocimiento:** Sintaxis básica de Java, I/O de archivos, gestión de dependencias Maven.  
- **Permisos del proyecto:** Acceso de escritura al directorio de salida y suficiente RAM para PDFs grandes (≥ 4 GB recomendado para archivos de > 200 páginas).

## Configurando tu entorno de marca de agua PDF en Java

### Añadiendo GroupDocs.Annotation a tu proyecto

Primero, agrega el artefacto Maven de GroupDocs.Annotation. Esta dependencia trae todos los binarios requeridos y las bibliotecas transitivas.

**Definición:** El elemento Maven `<dependency>` declara la biblioteca GroupDocs.Annotation para tu proyecto, permitiendo al compilador localizar los archivos JAR durante el tiempo de compilación.  

```xml
<!-- Maven dependency for GroupDocs.Annotation -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```
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

**Consejo profesional:** Siempre usa la última versión publicada (el ejemplo muestra 25.2, la más reciente a partir de 2025) para beneficiarte de correcciones de errores y mejoras de rendimiento.

### Obtén tu licencia

Necesitas una licencia válida para implementaciones en producción. Elige la opción que se ajuste a tu cronograma:

1. **Prueba gratuita:** Ideal para desarrollo y pruebas. Descarga desde [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
2. **Licencia temporal:** Conjunto completo de funciones para evaluación. Obtén una en la [Temporary License Page](https://purchase.groupdocs.com/temporary-license/)  
3. **Licencia completa:** Requerida para uso comercial. Compra a través de la [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

### Configuración básica que realmente funciona

Después de agregar la dependencia y obtener un archivo de licencia, inicializa el objeto `Annotator`. Este objeto carga el PDF en memoria y proporciona la API para crear anotaciones.

**Definición:** `Annotator` es el punto de entrada principal de GroupDocs.Annotation; gestiona la carga del PDF, la creación de anotaciones y el guardado.  

```java
// Initialize Annotator with a license and input PDF
Annotator annotator = new Annotator("input.pdf", "GroupDocs.Annotation.lic");
```
```java
import com.groupdocs.annotation.Annotator;

public class WatermarkSetup {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
        Annotator annotator = new Annotator(inputFilePath);
        
        // Your watermark code goes here...
        // Always remember to dispose!
        annotator.dispose();
    }
}
```

**Error común a evitar:** Olvidar llamar a `annotator.dispose()` después del procesamiento; esto puede causar fugas de memoria, especialmente al manejar muchos documentos en lote.

## Cómo aplicar marca de agua a todas las páginas en Java

Para aplicar una marca de agua a cada página, creas un `WatermarkAnnotation`, estableces sus propiedades visuales y luego añades una instancia separada de esta anotación a cada página en un bucle. El bucle usa el recuento de páginas del documento, asigna el número de página correcto y finalmente guarda el PDF modificado.

### Entendiendo las anotaciones de marca de agua

Un `WatermarkAnnotation` representa una capa superpuesta que puede contener texto, colores personalizados, rotación y opacidad. A diferencia de una simple adición de texto, se almacena como una anotación, lo que la hace removible o editable posteriormente.

**Definición:** `WatermarkAnnotation` es una clase en GroupDocs.Annotation que encapsula todas las propiedades visuales de una superposición de marca de agua.  

```java
WatermarkAnnotation watermark = new WatermarkAnnotation();
```
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.WatermarkAnnotation;
import java.util.ArrayList;
import java.util.Calendar;
```

### Paso 1: Importar las clases requeridas

Antes de poder usar la API, importa las clases esenciales.

**Definición:** Las declaraciones de importación traen las clases necesarias de GroupDocs.Annotation al archivo Java actual, permitiéndote referenciarlas sin nombres totalmente calificados.  

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.annotation.WatermarkAnnotation;
import com.groupdocs.annotation.models.common.Rectangle;
import com.groupdocs.annotation.models.annotation.Reply;
```
```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/AddWatermarkAnnotation.pdf";

final Annotator annotator = new Annotator(inputFilePath);
```

### Paso 2: Cargar el documento PDF

Crea la instancia `Annotator` que apunta a tu PDF de origen.

**Definición:** El constructor `Annotator` carga el archivo PDF en un objeto manejable, preparándolo para operaciones de anotación.  

```java
Annotator annotator = new Annotator("sample.pdf");
```
```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```

> **Consejo profesional:** Para PDFs mayores de 50 MB, considera aumentar el heap de JVM (`-Xmx4g`) y procesar los archivos secuencialmente para mantener bajo el uso de memoria.

### Paso 3: (Opcional) Preparar metadatos de respuesta

Si necesitas adjuntar comentarios o notas de aprobación a la marca de agua, crea un objeto `Reply`.

**Definición:** `Reply` almacena comentarios generados por el usuario que acompañan a una anotación, útil para auditorías.  

```java
Reply reply = new Reply();
reply.setComment("Confidential – Internal Use Only");
```
```java
ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

WatermarkAnnotation watermark = new WatermarkAnnotation();
watermark.setAngle(75.0); // Set the angle of the watermark.
watermark.setBox(new Rectangle(200, 200, 100, 50)); // Define position and size with a rectangle.
watermark.setCreatedOn(Calendar.getInstance().getTime());
watermark.setText("Watermark");
watermark.setFontColor(65535); // Yellow color in ARGB format
watermark.setFontSize(12.0);
watermark.setMessage("This is a watermark annotation");
watermark.setOpacity(0.7);
watermark.setPageNumber(0);
watermark.setReplies(replies);
```

### Paso 4: Configurar la apariencia de la marca de agua

Establece las propiedades visuales como texto, color, rotación, tamaño y opacidad.

**Definición:** Los siguientes setters personalizan el aspecto y la posición de la marca de agua en cada página.  

```java
watermark.setText("CONFIDENTIAL");
watermark.setAngle(75.0);                     // Diagonal orientation
watermark.setBox(new Rectangle(200, 200, 300, 100)); // Position & size
watermark.setFontColor(65535);               // Yellow (ARGB)
watermark.setOpacity(0.7);                   // 70% opacity
watermark.setReply(reply);                   // Attach the optional reply
```
```java
annotator.add(watermark);
annotator.save(outputPath);
annotator.dispose();
```

### Paso 5: Recorrer todas las páginas y aplicar la marca de agua

Para **aplicar marca de agua a todas las páginas**, itera sobre el recuento de páginas del documento y asigna la anotación a cada página.

**Definición:** `annotator.getPageCount()` devuelve el número total de páginas, habilitando un bucle que crea un `WatermarkAnnotation` separado por página.  

```java
int pageCount = annotator.getPageCount();
for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation pageWatermark = watermark.clone(); // Duplicate settings
    pageWatermark.setPageNumber(i);                       // Zero‑based index
    annotator.add(pageWatermark);                         // Add to current page
}
```
```java
// Get total page count first
int pageCount = annotator.getDocument().getPages().size();

for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation watermark = new WatermarkAnnotation();
    // Reuse the same configuration or customize per page
    watermark.setAngle(45.0);
    watermark.setText("CONFIDENTIAL");
    watermark.setFontColor(16711680); // Red
    watermark.setOpacity(0.3);
    watermark.setFontSize(24.0);
    watermark.setBox(new Rectangle(100, 300, 400, 100));
    watermark.setPageNumber(i);
    annotator.add(watermark);
}
annotator.save(outputPath);
annotator.dispose();
```

### Paso 6: Guardar el PDF con marca de agua

Finalmente, escribe los cambios en un nuevo archivo. El PDF original permanece intacto.

**Definición:** `annotator.save("output.pdf")` persiste todas las anotaciones añadidas en un nuevo archivo PDF.  

```java
annotator.save("output_watermarked.pdf");
annotator.dispose(); // Release resources
```
```java
// Better error handling approach
try {
    File inputFile = new File(inputFilePath);
    if (!inputFile.exists()) {
        throw new FileNotFoundException("Input PDF not found: " + inputFilePath);
    }
    
    Annotator annotator = new Annotator(inputFilePath);
    // ... your watermark code
} catch (Exception e) {
    System.err.println("Error processing PDF: " + e.getMessage());
}
```

Ese es el flujo completo para **aplicar marca de agua a todas las páginas** usando GroupDocs.Annotation para Java.

## Problemas comunes y cómo solucionarlos

### Errores “File Not Found”

```java
// Example of handling missing file paths
File inputFile = new File("nonexistent.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Input PDF not found at: " + inputFile.getAbsolutePath());
}
```
```java
WatermarkAnnotation confidentialWatermark = new WatermarkAnnotation();
confidentialWatermark.setAngle(45.0);
confidentialWatermark.setText("CONFIDENTIAL");
confidentialWatermark.setFontColor(16711680); // Red
confidentialWatermark.setOpacity(0.3); // Subtle but visible
confidentialWatermark.setFontSize(24.0);
confidentialWatermark.setBox(new Rectangle(100, 300, 400, 100));
```

- Verifica rutas absolutas y asegura que el archivo exista.  
- Revisa los permisos de lectura/escritura en los directorios de entrada y salida.  
- Crea la carpeta de salida previamente si no existe.

### Problemas de memoria con PDFs grandes

- Siempre invoca `annotator.dispose()` después del procesamiento.  
- Procesa PDFs uno a la vez; evita flujos paralelos a menos que la biblioteca haya demostrado ser segura para hilos.  
- Aumenta el heap de JVM (`-Xmx4g` o superior) para archivos que superen las 200 páginas.

### La posición de la marca de agua no es la esperada

- El origen de coordenadas del PDF es **abajo‑izquierda**; ajusta los valores de `Rectangle` en consecuencia.  
- Prueba con diferentes tamaños de página (A4 vs. Letter) porque las dimensiones afectan la posición.  
- Usa `setOpacity(0.5)` si la marca de agua aparece demasiado tenue en fondos de alto contraste.

### Problemas de color de fuente

GroupDocs.Annotation espera valores enteros ARGB. Colores comunes:
- Rojo: `16711680`  
- Azul: `255`  
- Verde: `65280`  
- Negro: `0`  
- Blanco: `16777215`  
- Amarillo: `65535` (usado en el ejemplo)

## Casos de uso reales para marcas de agua PDF en Java

### Protección de documentos empresariales

```java
// Apply a corporate logo watermark across all pages of a contract
watermark.setText("© Acme Corp – Confidential");
```
```java
WatermarkAnnotation brandWatermark = new WatermarkAnnotation();
brandWatermark.setText("© YourCompany 2025");
brandWatermark.setFontColor(0); // Black
brandWatermark.setOpacity(0.6);
brandWatermark.setFontSize(10.0);
brandWatermark.setBox(new Rectangle(400, 50, 150, 30));
```

### Materiales de marketing con marca

```java
// Use a semi‑transparent brand slogan as a watermark
watermark.setText("Acme Marketing 2026");
watermark.setOpacity(0.4);
```
```java
WatermarkAnnotation versionWatermark = new WatermarkAnnotation();
versionWatermark.setText("DRAFT - v2.1");
versionWatermark.setFontColor(255); // Blue
versionWatermark.setOpacity(0.8);
versionWatermark.setBox(new Rectangle(50, 750, 100, 30));
```

### Control de versiones para documentos

```java
// Append version number dynamically
watermark.setText("Version 3.2 – Reviewed");
```
```java
public void processMultiplePDFs(List<String> pdfPaths) {
    for (String path : pdfPaths) {
        Annotator annotator = null;
        try {
            annotator = new Annotator(path);
            // Add your watermark logic here
            annotator.save(path.replace(".pdf", "_watermarked.pdf"));
        } finally {
            if (annotator != null) {
                annotator.dispose(); // Always dispose, even if exceptions occur
            }
        }
    }
}
```

## Consejos de optimización de rendimiento

### Mejores prácticas de gestión de memoria

```java
// Explicitly release resources after each document
annotator.dispose();
System.gc(); // Hint to the JVM (optional)
```
```java
public class WatermarkTemplates {
    public static WatermarkAnnotation createConfidentialWatermark() {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setAngle(45.0);
        watermark.setText("CONFIDENTIAL");
        watermark.setFontColor(16711680);
        watermark.setOpacity(0.3);
        watermark.setFontSize(24.0);
        return watermark;
    }
    
    public static WatermarkAnnotation createBrandWatermark(String companyName) {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setText("© " + companyName + " 2025");
        watermark.setFontColor(0);
        watermark.setOpacity(0.6);
        watermark.setFontSize(10.0);
        return watermark;
    }
}
```

- Procesa documentos secuencialmente para mantener bajo el consumo de heap.  
- Usa un indicador de progreso para trabajos por lotes y monitorear el uso de memoria.  
- Evita cargar todo el PDF en memoria cuando solo un subconjunto de páginas necesita marca de agua; la biblioteca soporta carga a nivel de página.

### Consejos de organización de código

- Encapsula la creación de la marca de agua en un método utilitario: `createWatermark(String text, double opacity, int angle)`.  
- Mantén la configuración (colores, fuentes, opacidad) externalizada en un archivo de propiedades para facilitar ajustes en diferentes entornos.

## Preguntas frecuentes

**Q: ¿Cómo añado marcas de agua a múltiples páginas en un PDF?**  
A: Recorre el recuento de páginas del documento, clona una `WatermarkAnnotation` configurada para cada página, establece `setPageNumber(i)`, y añádela con `annotator.add()`.

**Q: ¿Puedo usar fuentes personalizadas para mis marcas de agua?**  
A: GroupDocs.Annotation usa fuentes instaladas en el sistema operativo host. Especifica una familia de fuentes que exista en el servidor; la biblioteca recurre a una predeterminada si la fuente no se encuentra.

**Q: ¿Qué configuración de opacidad funciona mejor para marcas de agua profesionales?**  
A: Entre **0.3** y **0.7** ofrece un equilibrio—suficientemente visible para ser notada pero aún permite leer el contenido subyacente.

**Q: ¿Cómo debo manejar archivos PDF muy grandes?**  
A: Aumenta el heap de JVM (`-Xmx4g` o más), procesa los archivos uno a la vez, y siempre llama a `dispose()` después de cada documento para liberar recursos nativos.

**Q: ¿Es posible eliminar o modificar marcas de agua existentes?**  
A: Sí—recupera anotaciones con `annotator.get()`, filtra por `WatermarkAnnotation`, luego edita o elimina según sea necesario:  

```java
List<AnnotationBase> watermarks = annotator.get().stream()
    .filter(a -> a instanceof WatermarkAnnotation)
    .collect(Collectors.toList());
annotator.delete(watermarks.get(0)); // Example: delete first watermark
```
```java
// Get existing annotations
List<AnnotationBase> annotations = annotator.get();
// Filter and modify as needed
```

## Recursos adicionales

- **Documentación:** [GroupDocs Annotation Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **Referencia completa de API:** [GroupDocs Annotation Java API](https://reference.groupdocs.com/annotation/java/)  
- **Descargar la última versión:** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Licenciamiento comercial:** [Purchase GroupDocs](https://purchase.groupdocs.com/buy)  
- **Soporte comunitario:** [GroupDocs Forums](https://forum.groupdocs.com/c/annotation/10)

---

**Última actualización:** 2026-07-30  
**Probado con:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

## Tutoriales relacionados

- [Cargar PDF Java con GroupDocs Annotation: Guía de carga de documentos](/annotation/java/document-loading/)  
- [Agregar anotación PDF Java – Guía completa de GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Cómo agregar una imagen a PDF usando Java y GroupDocs Annotation](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)