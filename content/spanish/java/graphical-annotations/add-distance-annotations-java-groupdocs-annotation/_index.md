---
categories:
- Java Development
date: '2026-06-16'
description: Aprende a agregar mediciones a una imagen y a otras mediciones de documentos
  en Java usando GroupDocs.Annotation. Tutorial completo con ejemplos de código, consejos
  de solución de problemas y buenas prácticas.
keywords:
- how to add measurement
- distance annotation Java
- measure image Java
- GroupDocs annotation tutorial
- Java document measurement
lastmod: '2026-06-16'
linktitle: Guía de anotaciones de distancia en Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  headline: 'Java Distance Annotation Tutorial: How to add measurement to image with
    GroupDocs'
  type: TechArticle
- description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  name: 'Java Distance Annotation Tutorial: How to add measurement to image with GroupDocs'
  steps:
  - name: Create Interactive Replies (Optional But Recommended)
    text: Replies let collaborators attach comments directly to a measurement, turning
      a simple ruler into a discussion thread. java import com.groupdocs.annotation.models.Reply;
      import java.util.ArrayList; import java.util.Calendar; Reply reply1 = new Reply();
      reply1.setComment("First comment"); reply1.setRe
  - name: Configure Your Distance Annotation
    text: The `DistanceAnnotation` class is GroupDocs.Annotation's top‑level object
      that represents a ruler measurement. You can customize its geometry, visual
      style, and attached message. `Rectangle` defines the annotation's bounding box
      on the page. `PenStyle` enumerates line styles such as solid, dash, and
  - name: Apply the Annotation and Save
    text: Once the annotation is ready, add it to the document and persist the changes.
      java annotator.add(distance); annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
      annotator.dispose(); **Important:** Always invoke `dispose()` after saving,
      especially when processing many documents in a batch job.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports PDFs, Word documents, PowerPoint presentations,
      Excel spreadsheets, and common image formats (PNG, JPEG, TIFF, BMP). The feature
      works consistently across all 50+ supported formats.
    question: What document formats support distance annotations?
  - answer: Absolutely! You have full control over pen color, line style (solid, dotted,
      dashed), line width, and opacity. You can also define custom end‑cap symbols
      for specialized engineering standards.
    question: Can I customize the appearance of measurement lines?
  - answer: The annotation itself displays the text you set in the `message` property.
      Perform any unit conversion (e.g., inches ↔ millimeters) in your Java code before
      assigning the message.
    question: How do I handle measurements in different units?
  - answer: Yes. In compatible viewers (GroupDocs.Viewer, Adobe Acrobat, or your own
      web viewer), users can click, drag, and edit the ruler. Replies and comments
      remain attached to the measurement for collaborative review.
    question: Can users interact with distance annotations after they're added?
  - answer: Adding up to several hundred annotations per document has a negligible
      impact (< 5 % CPU overhead). When you exceed 1,000 annotations, loading times
      may increase modestly, but the library remains stable and responsive.
    question: What's the performance impact of adding many annotations?
  type: FAQPage
tags:
- GroupDocs
- document-annotation
- Java-tutorial
- PDF-processing
title: 'Tutorial de anotación de distancia en Java: Cómo agregar mediciones a una
  imagen con GroupDocs'
type: docs
url: /es/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/
weight: 1
---

# Tutorial de anotación de distancia en Java: Cómo agregar medición a una imagen con GroupDocs

En esta guía completa descubrirás **cómo agregar medición** a imágenes, PDFs y otros tipos de documentos usando GroupDocs.Annotation para Java. Ya sea que estés construyendo un visor CAD, una herramienta de revisión arquitectónica o una plataforma de documentación técnica, las anotaciones de distancia brindan a tus usuarios una regla clara e interactiva en la que pueden confiar. Al final del tutorial tendrás una solución lista para producción que dibuja mediciones precisas, personaliza su apariencia e integra sin problemas con tu base de código Java existente.

## ¿Cómo agregar medición a una imagen en Java?

Carga el documento objetivo con `Annotator`, crea una `DistanceAnnotation`, configura sus propiedades visuales, añádela a la página deseada y, finalmente, guarda el archivo. En solo cuatro líneas de código obtienes una regla totalmente funcional que puede ser editada por los usuarios finales en cualquier visor compatible. Este enfoque funciona para PDFs, archivos Word, presentaciones PowerPoint, hojas de Excel y formatos de imagen comunes como PNG, JPEG y TIFF.

## Respuestas rápidas
- **¿Cuál es la forma más fácil de agregar medición a una imagen en Java?** Usa la clase `DistanceAnnotation` de GroupDocs.Annotation.  
- **¿Qué formatos son compatibles?** PDFs, Word, PowerPoint, Excel y tipos de imagen comunes (PNG, JPEG, TIFF).  
- **¿Necesito una licencia para desarrollo?** Una prueba gratuita o licencia temporal funciona para pruebas; se requiere una licencia comercial para producción.  
- **¿Puedo personalizar la apariencia de la línea de la regla?** Sí, puedes establecer color, estilo, ancho y opacidad.  
- **¿Cómo evito fugas de memoria?** Siempre libera la instancia de `Annotator` o usa try‑with‑resources.

## ¿Qué son las anotaciones de distancia (y por qué las necesitas)?

Las anotaciones de distancia son elementos visuales interactivos que muestran la longitud medida entre dos puntos en un documento. Actúan como reglas digitales que pueden colocarse en cualquier lugar, arrastrarse y editarse en tiempo real, proporcionando a los usuarios retroalimentación visual instantánea sin cálculos manuales.

Estas anotaciones aportan **claridad visual**, **retroalimentación interactiva** y una **apariencia profesional** a cualquier documento técnico. Son especialmente valiosas para planos arquitectónicos, esquemas de ingeniería, imágenes médicas y planos de inmuebles donde las dimensiones precisas son críticas.

## Mejores prácticas para la medición de documentos

Antes de comenzar a programar, ten en cuenta estas prácticas probadas:

1. **Indexación de páginas basada en cero** – `pageNumber = 0` se refiere a la primera página, lo que coincide con el modelo interno de GroupDocs.Annotation.  
2. **Colores de alto contraste** – Elige colores de regla que resalten sobre el fondo del documento (p. ej., amarillo brillante sobre esquemas oscuros).  
3. **Ajuste de opacidad** – Una opacidad de `0.7` equilibra la visibilidad y el detalle subyacente; aumenta a `1.0` para mediciones críticas.  
4. **Agrupar anotaciones relacionadas** – Usa respuestas o comentarios para mantener organizadas las discusiones alrededor de una medición específica.  
5. **Liberar rápidamente** – Siempre llama a `annotator.dispose()` o usa try‑with‑resources para liberar la memoria nativa, especialmente al manejar archivos grandes.

## Prerrequisitos: Qué necesitarás antes de comenzar

### Requisitos del entorno de desarrollo
- **Java Development Kit (JDK)**: Versión 8 o superior (se recomienda JDK 11+).  
- **Maven o Gradle**: Los ejemplos usan Maven, pero las mismas dependencias funcionan con Gradle.  
- **IDE**: Cualquier IDE de Java (IntelliJ IDEA, Eclipse, VS Code, etc.) sirve.

### Prerrequisitos de conocimientos
Ya deberías estar cómodo con:

- Conceptos básicos de Java (clases, objetos, métodos).  
- Añadir bibliotecas externas mediante Maven/Gradle.  
- Entrada/Salida de archivos básica y manejo de rutas.

### Documentos de prueba
Prepara algunos archivos de muestra:

- Una o más páginas PDF.  
- Imágenes PNG/JPEG/TIFF para pruebas basadas en raster.  
- Archivos CAD opcionales si deseas experimentar con dibujos de ingeniería.

## Configuración de GroupDocs.Annotation para Java

Integrar GroupDocs.Annotation es muy fácil. A continuación mostramos las coordenadas Maven que necesitas añadir a tu proyecto.

### Integración con Maven

Agrega la siguiente configuración a tu archivo `pom.xml`:

```xml
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
```

### Comprendiendo los requisitos de licencia

GroupDocs.Annotation ofrece tres modelos de licencia:

1. **Prueba gratuita** – Ideal para evaluación; incluye todas las funciones con limitaciones de uso menores.  
2. **Licencia temporal** – Elimina las restricciones de prueba para desarrollo y pruebas.  
3. **Licencia comercial** – Uso completo, listo para producción, sin límites.  

Comienza con la prueba gratuita, luego actualiza cuando estés listo para producción.

### Inicialización básica

La clase `Annotator` es el punto de entrada para todas las operaciones de anotación. Carga un documento, proporciona APIs de edición y escribe el resultado de vuelta al disco.

```java
```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

**Consejo profesional:** Envuelve el `Annotator` en un bloque try‑with‑resources o llama explícitamente a `dispose()` para evitar fugas de memoria nativa.

## Guía de implementación paso a paso

Ahora recorramos un flujo de trabajo completo y listo para producción para agregar anotaciones de distancia.

### Paso 1: Crear respuestas interactivas (Opcional pero recomendado)

Las respuestas permiten a los colaboradores adjuntar comentarios directamente a una medición, convirtiendo una regla simple en un hilo de discusión.

```java
```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

**Cuándo usar respuestas:** En ciclos de revisión multiusuario, cuando necesitas explicar por qué se eligió una dimensión o solicitar aclaraciones a un compañero.

### Paso 2: Configurar tu anotación de distancia

La clase `DistanceAnnotation` es el objeto de nivel superior de GroupDocs.Annotation que representa una medición de regla. Puedes personalizar su geometría, estilo visual y mensaje adjunto.

`Rectangle` define el cuadro delimitador de la anotación en la página. `PenStyle` enumera estilos de línea como sólido, guión y punto.

```java
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Set the annotation's position and size
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Attach replies
```
```

**Opciones clave de configuración**  
- `setBox()` – Establece el rectángulo delimitador de la anotación en la página.  
- `setOpacity()` – Controla la transparencia (`0.0` = invisible, `1.0` = totalmente opaco).  
- `setPenColor()` – Color RGB para la línea de medición.  
- `setPenStyle()` – Estilo de línea (`DOT`, `DASH`, `SOLID`).  
- `setPenWidth()` – Grosor de la línea en puntos.

### Paso 3: Aplicar la anotación y guardar

Una vez que la anotación está lista, añádela al documento y persiste los cambios.

```java
```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```
```

**Importante:** Siempre invoca `dispose()` después de guardar, especialmente al procesar muchos documentos en un trabajo por lotes.

## Ejemplo completo de trabajo

Juntando todo, aquí tienes un ejemplo completo de extremo a extremo que carga un PDF, agrega una anotación de distancia y guarda el resultado.

```java
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;
import java.util.ArrayList;
import java.util.Calendar;

public class DistanceAnnotationExample {
    public static void main(String[] args) {
        try (Annotator annotator = new Annotator("input.pdf")) {
            // Create replies for the annotation
            ArrayList<Reply> replies = new ArrayList<>();
            Reply reply = new Reply();
            reply.setComment("Measurement verified by engineering team");
            reply.setRepliedOn(Calendar.getInstance().getTime());
            replies.add(reply);

            // Configure the distance annotation
            DistanceAnnotation distance = new DistanceAnnotation();
            distance.setBox(new Rectangle(100, 100, 300, 50));
            distance.setCreatedOn(Calendar.getInstance().getTime());
            distance.setMessage("Wall length: 12 feet");
            distance.setOpacity(0.8);
            distance.setPageNumber(0);
            distance.setPenColor(0xFF0000); // Red color
            distance.setPenStyle(PenStyle.SOLID);
            distance.setPenWidth((byte) 2);
            distance.setReplies(replies);

            // Add and save
            annotator.add(distance);
            annotator.save("output_with_distance_annotation.pdf");
            
            System.out.println("Distance annotation added successfully!");
        } catch (Exception e) {
            System.err.println("Error adding distance annotation: " + e.getMessage());
        }
    }
}
```
```

Ejecuta el fragmento, abre el archivo de salida en cualquier visor PDF que soporte anotaciones, y verás una regla totalmente funcional lista para la interacción.

## Casos de uso comunes y aplicaciones del mundo real

Entender dónde brillan las anotaciones de distancia te ayuda a decidir cómo integrarlas en tu producto.

### Documentación técnica y manuales
- Resaltar dimensiones de componentes en guías de ensamblaje.  
- Mostrar zonas de holgura en manuales de instalación.  
- Proveer mediciones de referencia rápida para listas de verificación de control de calidad.  

### Proyectos arquitectónicos e ingenieriles
- Mostrar tamaños de habitaciones en planos.  
- Indicar espaciamiento de elementos estructurales.  
- Marcar distancias de líneas de servicios y holguras de seguridad.  

### Aplicaciones médicas y científicas
- Medir estructuras anatómicas en imágenes de radiología.  
- Añadir barras de escala a diapositivas de microscopía.  
- Documentar dimensiones de especímenes en informes de investigación.  

### Bienes raíces y gestión de propiedades
- Visualizar límites de lote y líneas de propiedad.  
- Mostrar dimensiones de habitaciones para listados.  
- Indicar tamaños de espacios de estacionamiento y mediciones de paisajismo.  

## Solución de problemas comunes

Incluso un ejemplo bien escrito puede presentar problemas. A continuación los problemas más frecuentes y cómo resolverlos.

### Problema: "Archivo no encontrado" o problemas de ruta

**Síntomas:** Se lanza una excepción al crear el `Annotator`.

**Solución:** Usa una ruta absoluta durante el desarrollo, verifica que el archivo exista y asegura que el proceso tenga permisos de lectura.

```java
```java
// Better path handling
String inputPath = new File("documents/input.pdf").getAbsolutePath();
final Annotator annotator = new Annotator(inputPath);
```
```

### Problema: Anotación no visible

**Síntomas:** El código se ejecuta sin errores, pero no aparece ninguna regla.

**Causas comunes:** Índice de página incorrecto (recuerda que las páginas empiezan en 0), anotación colocada fuera del lienzo visible, o opacidad establecida demasiado baja.

**Correcciones rápidas:**

```java
```java
distance.setPageNumber(0); // First page
distance.setOpacity(1.0);  // Fully opaque
distance.setBox(new Rectangle(50, 50, 200, 30)); // Visible position
```
```

### Problema: Problemas de memoria con documentos grandes

**Síntomas:** `OutOfMemoryError` o rendimiento lento en archivos de cientos de páginas.

**Soluciones:**
- Libera cada instancia de `Annotator` tan pronto como termines.  
- Procesa los documentos secuencialmente en lugar de cargarlos todos a la vez.  
- Incrementa el heap de JVM (`-Xmx4g` o superior) para entradas muy grandes.

```java
```java
// Good practice - use try-with-resources
try (Annotator annotator = new Annotator("large-document.pdf")) {
    // Your annotation code here
} // Automatic disposal
```
```

### Problema: Errores relacionados con la licencia

**Síntomas:** Advertencias sobre limitaciones de prueba o fallos de validación de licencia.

**Soluciones:**
- Confirma que la ruta del archivo de licencia sea correcta y que el archivo sea legible.  
- Asegúrate de que la versión de la licencia coincida con la versión de la biblioteca GroupDocs.Annotation que estás usando.  
- Verifica que una licencia temporal no haya expirado.

## Consejos de optimización de rendimiento

Cuando pases de un prototipo a producción, ten en cuenta estas consideraciones de rendimiento.

### Mejores prácticas de gestión de memoria
- **Siempre liberar**: Prefiere try‑with‑resources o `dispose()` explícito.  
- **Operaciones por lotes**: Agrupa múltiples cambios de anotación en una sola sesión de `Annotator` para reducir la sobrecarga.  
- **Perfilado**: Usa perfiles de Java (VisualVM, YourKit) para monitorizar el uso de memoria nativa.

### Optimización del procesamiento de archivos
- **Cachear documentos accedidos frecuentemente** en memoria cuando son solo de lectura.  
- **Preferir PDF** sobre imágenes de alta resolución para un renderizado más rápido; los PDFs son un 30‑40 % más pequeños en promedio para el mismo contenido visual.  
- **Ajustar la resolución de la imagen**: Reducir la escala de las imágenes fuente a un máximo de 150 DPI a menos que se requiera mayor fidelidad.

### Consideraciones de procesamiento concurrente
Si tu servicio procesa muchos archivos en paralelo, sigue estas reglas:

```java
```java
// Example of efficient batch processing
public void processMultipleDocuments(List<String> filePaths) {
    for (String path : filePaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Add multiple annotations per document
            addDistanceAnnotation(annotator, config1);
            addDistanceAnnotation(annotator, config2);
            // Save once with all annotations
            annotator.save(getOutputPath(path));
        }
    }
}
```
```

- Cada hilo debe instanciar su propio `Annotator`.  
- Usa un pool de hilos limitado para evitar agotar los recursos del sistema.  
- Monitoriza el uso de CPU y heap bajo carga; escala horizontalmente si es necesario.

## Opciones avanzadas de configuración

Una vez que domines lo básico, explora estas funciones avanzadas para afinar tus anotaciones.

### Opciones de estilo personalizado

```java
```java
// Advanced pen styling
distance.setPenStyle(PenStyle.DASH_DOT);
distance.setPenWidth((byte) 4);
distance.setPenColor(0x00FF00); // Hex color codes work too

// Custom opacity for different emphasis levels
distance.setOpacity(0.6); // Subtle background measurements
// vs
distance.setOpacity(1.0); // Prominent foreground measurements
```
```

Puedes definir un objeto `Pen` personalizado, aplicar rellenos degradados o incluso incrustar marcadores SVG al final de la línea de la regla.

### Posicionamiento dinámico

```java
```java
// Calculate position based on document dimensions or content
Rectangle dynamicBox = calculateOptimalPosition(documentWidth, documentHeight);
distance.setBox(dynamicBox);
```
```

Aprovecha coordenadas relativas a la página para que la anotación se reposicione automáticamente cuando el documento se amplíe o rote.

### Anotaciones condicionales

```java
```java
// Add annotations based on document content or user preferences
if (document.getType() == DocumentType.ARCHITECTURAL_PLAN) {
    distance.setMessage("Room dimension");
    distance.setPenStyle(PenStyle.SOLID);
} else if (document.getType() == DocumentType.ENGINEERING_DRAWING) {
    distance.setMessage("Component spacing");
    distance.setPenStyle(PenStyle.DOT);
}
```
```

Añade lógica que solo cree una anotación de distancia cuando se cumpla una condición determinada (p. ej., cuando un componente supera un umbral de tolerancia).

## Integración con otros sistemas

Las anotaciones de distancia no están aisladas; encajan naturalmente en ecosistemas más amplios de gestión documental.

### Integración con bases de datos

`AnnotationRecord` es un modelo de datos personalizado para persistir metadatos de anotaciones en una base de datos.

```java
```java
// Save annotation details to database
AnnotationRecord record = new AnnotationRecord();
record.setDocumentId(documentId);
record.setAnnotationType("distance");
record.setMeasurement(distance.getMessage());
record.setCreatedDate(distance.getCreatedOn());
```
```

Almacena metadatos de anotaciones (autor, marca de tiempo, valor de medición) en una base de datos relacional para informes y búsquedas.

### Integración con aplicaciones web

`DistanceAnnotationRequest` es un DTO que transporta los parámetros de anotación del cliente al servidor.

```java
```java
@PostMapping("/documents/{id}/annotations/distance")
public ResponseEntity<String> addDistanceAnnotation(
    @PathVariable String id,
    @RequestBody DistanceAnnotationRequest request) {
    // Process the annotation request
    // Return success/failure response
}
```
```

Expón un endpoint REST que acepte un archivo, añada una anotación de distancia basada en la carga JSON y devuelva el documento anotado.

### Integración con almacenamiento en la nube

```java
```java
// Download from cloud, process, upload result
byte[] documentBytes = cloudStorageService.download(documentPath);
// Process with GroupDocs.Annotation
byte[] annotatedDocument = processAnnotations(documentBytes);
cloudStorageService.upload(outputPath, annotatedDocument);
```
```

Lee y escribe archivos directamente desde AWS S3, Azure Blob Storage o Google Cloud Storage usando los SDK correspondientes, luego pasa los streams a `Annotator`.

## Preguntas frecuentes

**P: ¿Qué formatos de documento admiten anotaciones de distancia?**  
R: GroupDocs.Annotation admite PDFs, documentos Word, presentaciones PowerPoint, hojas de cálculo Excel y formatos de imagen comunes (PNG, JPEG, TIFF, BMP). La función funciona de manera consistente en los más de 50 formatos compatibles.

**P: ¿Puedo personalizar la apariencia de las líneas de medición?**  
R: ¡Absolutamente! Tienes control total sobre el color del lápiz, estilo de línea (sólido, punteado, guionado), ancho de línea y opacidad. También puedes definir símbolos de extremo personalizados para normas de ingeniería especializadas.

**P: ¿Cómo manejo mediciones en diferentes unidades?**  
R: La anotación muestra el texto que establezcas en la propiedad `message`. Realiza cualquier conversión de unidades (p. ej., pulgadas ↔ milímetros) en tu código Java antes de asignar el mensaje.

**P: ¿Pueden los usuarios interactuar con las anotaciones de distancia después de agregarlas?**  
R: Sí. En visores compatibles (GroupDocs.Viewer, Adobe Acrobat o tu propio visor web), los usuarios pueden hacer clic, arrastrar y editar la regla. Las respuestas y comentarios permanecen adjuntos a la medición para revisión colaborativa.

**P: ¿Cuál es el impacto en el rendimiento al agregar muchas anotaciones?**  
R: Añadir hasta varios cientos de anotaciones por documento tiene un impacto insignificante (< 5 % de sobrecarga de CPU). Cuando superas las 1,000 anotaciones, los tiempos de carga pueden aumentar ligeramente, pero la biblioteca sigue siendo estable y receptiva.

## Conclusión y próximos pasos

Ahora tienes una hoja de ruta completa y lista para producción sobre **cómo agregar medición** a imágenes y otros documentos en Java usando GroupDocs.Annotation. Al aprovechar las anotaciones de distancia puedes convertir dibujos estáticos en recursos interactivos y ricos en datos que mejoran la colaboración y reducen errores.

**Puntos clave**
- Las anotaciones de distancia proporcionan mediciones precisas y visuales en más de 50 formatos de archivo.  
- La implementación es concisa: cargar, configurar, añadir, guardar.  
- El rendimiento es sólido para documentos de tamaño medio; sigue los consejos de gestión de memoria para archivos grandes.  
- Los puntos de integración (BD, REST, nube) te permiten incrustar anotaciones en cualquier flujo de trabajo.

### Próximos pasos recomendados
1. **Prototipo**: Clona el ejemplo completo, ejecútalo con tus propios PDFs o imágenes y verifica que la regla aparezca como se espera.  
2. **Explora otros tipos de anotación**: Las anotaciones de resaltado, texto y sello pueden complementar las mediciones de distancia.  
3. **Construye una UI**: Diseña una interfaz de arrastrar y soltar que permita a los usuarios finales colocar reglas directamente en el navegador o cliente de escritorio.  
4. **Planifica la escala**: Si esperas miles de usuarios concurrentes, implementa una estrategia de pool de hilos y monitoriza el uso del heap como se describe en la sección de rendimiento.  

---

**Última actualización:** 2026-06-16  
**Probado con:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Recursos relacionados:**
- [Documentación de GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/) - Documentación completa de la API  
- [Referencia de API](https://reference.groupdocs.com/annotation/java/) - Referencias detalladas de métodos y clases  
- [Página de descarga](https://releases.groupdocs.com/annotation/java/) - Últimas versiones y notas de la versión  
- [Foro de soporte](https://forum.groupdocs.com/c/annotation/) - Soporte comunitario y discusiones  
- [Opciones de compra](https://purchase.groupdocs.com/buy) - Información de licencias comerciales  
- [Prueba gratuita](https://releases.groupdocs.com/annotation/java/) - Prueba antes de comprar  
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/) - Licencia de evaluación extendida  

## Tutoriales relacionados
- [Cómo agregar una flecha a PDF con Java – Tutorial completo y mejores prácticas](/annotation/java/graphical-annotations/add-arrow-annotations-java-groupdocs/)  
- [Anotación de imágenes PDF en Java - Tutorial completo de GroupDocs](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)  
- [Editar anotaciones PDF Java - Tutorial completo de GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)