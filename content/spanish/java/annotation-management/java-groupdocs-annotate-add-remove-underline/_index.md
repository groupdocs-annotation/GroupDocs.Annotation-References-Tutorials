---
categories:
- Java Development
date: '2025-12-21'
description: Aprende cómo crear archivos PDF limpios en Java y anotar PDFs en Java
  usando GroupDocs.Annotation, con ejemplos de código completos y consejos de solución
  de problemas.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Crear PDF limpio en Java - Subrayar anotaciones con GroupDocs'
type: docs
url: /es/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Crear PDF limpio Java: Anotaciones subrayadas con GroupDocs

## Introducción

¿Tienes problemas con la gestión y colaboración de documentos en tus aplicaciones Java? No estás solo. Muchos desarrolladores enfrentan el desafío de implementar funciones robustas de anotación de documentos que funcionen de manera fiable en diferentes formatos de archivo.

En esta guía, **crearás PDF limpio Java** y aprenderás cómo **anotar PDF en Java** usando GroupDocs.Annotation. Al final de este tutorial, sabrás exactamente cómo agregar anotaciones subrayadas con comentarios, eliminar anotaciones existentes e integrar estas funciones sin problemas en tus proyectos.

**Lo que dominarás en esta guía:**
- Configurar GroupDocs.Annotation en tu proyecto Java (de la manera correcta)  
- Añadir anotaciones subrayadas con comentarios y estilos personalizados  
- Eliminar todas las anotaciones para crear versiones limpias del documento  
- Solucionar problemas comunes que encuentran los desarrolladores  
- Optimizar el rendimiento para aplicaciones en producción  

Ya sea que estés construyendo un sistema de revisión de documentos, una plataforma educativa o una herramienta de edición colaborativa, este tutorial te cubre con ejemplos de código prácticos y probados.

## Respuestas rápidas
- **¿Cómo agrego una anotación subrayada?** Usa `UnderlineAnnotation` y `annotator.add()` y luego guarda el documento.  
- **¿Cómo creo un PDF limpio Java?** Carga el archivo anotado, establece `AnnotationType.NONE` en `SaveOptions` y guarda una nueva copia.  
- **¿Qué bibliotecas se requieren?** GroupDocs.Annotation v25.2 (o superior) y su repositorio Maven.  
- **¿Necesito una licencia para producción?** Sí—aplica una licencia válida de GroupDocs para evitar marcas de agua.  
- **¿Puedo procesar varios documentos de forma eficiente?** Envuelve cada `Annotator` en un bloque try‑with‑resources y dispón de él después de cada archivo.

## Cómo crear archivos PDF limpio Java
Crear un archivo PDF limpio Java significa generar una versión del documento **sin ninguna anotación** mientras se conserva el contenido original. Esto es útil para la distribución final, archivado o cuando necesitas compartir una copia “limpia” después de un ciclo de revisión.

GroupDocs.Annotation hace esto sencillo: carga el archivo anotado, configura `SaveOptions` para excluir todos los tipos de anotación y guarda el resultado. Los pasos se ilustran más adelante en la sección **Eliminación de anotaciones**.

## Cómo anotar PDF en Java usando GroupDocs
GroupDocs.Annotation proporciona una API completa para **anotar PDF en Java**. Soporta una amplia gama de tipos de anotación, incluidos resaltados, sellos y subrayados. En este tutorial nos centramos en las anotaciones subrayadas porque se usan comúnmente para enfatizar texto mientras se permiten comentarios en hilo.

## Requisitos previos y configuración del entorno

### Qué necesitarás antes de comenzar

**Requisitos del entorno de desarrollo:**
- Java Development Kit (JDK) 8 o superior (se recomienda JDK 11+)  
- Maven 3.6+ o Gradle 6.0+ para la gestión de dependencias  
- IDE como IntelliJ IDEA, Eclipse o VS Code con extensiones Java  
- Al menos 2 GB de RAM disponible (el procesamiento de documentos puede consumir mucha memoria)

**Conocimientos previos:**
Debes estar cómodo con conceptos básicos de Java—inicialización de objetos, llamadas a métodos y dependencias Maven. La experiencia previa con bibliotecas de terceros acelerará la adopción.

**Documentos de prueba:**
Ten algunos PDFs de muestra listos. Los PDFs basados en texto funcionan mejor; las imágenes escaneadas pueden requerir OCR antes de anotarlos.

### Configuración de Maven: Añadiendo GroupDocs a tu proyecto

Así es como debes configurar correctamente tu proyecto Maven (esto confunde a muchos desarrolladores en su primer intento):

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

**Importante:** La versión 25.2 es la última versión estable al momento de escribir este documento. Revisa el repositorio de GroupDocs regularmente para versiones más nuevas que incluyan correcciones de errores y mejoras de rendimiento.

### Configuración de la licencia (No lo omitas)

**Para desarrollo/pruebas:**  
Descarga la prueba gratuita desde el sitio web de GroupDocs. La prueba incluye todas las funciones pero agrega una marca de agua a los documentos procesados.

**Para producción:**  
Compra una licencia y aplícala durante el inicio de la aplicación. Sin una licencia válida, las compilaciones de producción estarán limitadas.

## Guía de implementación: Añadiendo anotaciones subrayadas

### Entendiendo el flujo de trabajo de anotación

Antes de sumergirnos en el código, repasemos el flujo de trabajo de cuatro pasos que ocurre cuando **anotas PDF en Java**:

1. **Carga del documento** – `Annotator` lee el archivo en memoria.  
2. **Creación de la anotación** – Define propiedades como posición, estilo y comentarios.  
3. **Aplicación de la anotación** – La biblioteca inserta la anotación en la estructura del PDF.  
4. **Guardado del documento** – Persiste el archivo modificado, opcionalmente conservando el original.

El proceso es no destructivo; el archivo fuente permanece intacto a menos que lo sobrescribas.

### Paso 1: Inicializar el Annotator y cargar tu documento

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Consejo profesional:** Usa rutas absolutas mientras desarrollas para evitar errores de “archivo no encontrado”. En producción, considera cargar recursos desde el classpath o un bucket de almacenamiento en la nube.

### Paso 2: Crear comentarios y respuestas (La parte colaborativa)

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

**Uso en el mundo real:** Los revisores pueden discutir una cláusula específica añadiendo respuestas en hilo, manteniendo la conversación vinculada a la anotación exacta.

### Paso 3: Definir las coordenadas de la anotación (Obtener la posición correcta)

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

**Sistema de coordenadas:**  
- Los puntos 1 y 2 definen el borde superior del subrayado.  
- Los puntos 3 y 4 definen el borde inferior.  
- La diferencia en Y (730 vs 650) controla el grosor.

### Paso 4: Crear y configurar la anotación subrayada

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

**Consejos de color y opacidad:**  
- `FontColor` usa ARGB; `65535` (0x00FFFF) produce un amarillo brillante.  
- Para rojo, usa `16711680` (0xFF0000); para azul, `255` (0x0000FF).  
- Valores de opacidad entre 0.5 y 0.8 ofrecen buena legibilidad sin ocultar el texto.

### Paso 5: Guardar tu documento anotado

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Gestión de memoria:** La llamada a `dispose()` libera recursos nativos y previene fugas de memoria—crítico al procesar muchos archivos en lote.

## Eliminación de anotaciones: Creando versiones limpias del documento

A veces necesitas una versión del PDF **sin ninguna anotación**—por ejemplo, al entregar el contrato final aprobado. GroupDocs lo hace fácil.

### Entendiendo las opciones de eliminación de anotaciones

Puedes:
- Eliminar **todas** las anotaciones (lo más común)  
- Eliminar tipos específicos (p. ej., solo resaltados)  
- Eliminar anotaciones por autor o página  

### Eliminación de anotaciones paso a paso

**Paso 1: Cargar el documento previamente anotado**

```java
Annotator annotator = new Annotator(outputPath);
```

**Paso 2: Configurar las opciones de guardado para una salida limpia**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Paso 3: Guardar la versión limpia**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Esto produce un **PDF limpio Java** que no contiene objetos de anotación, perfecto para la distribución final.

## Problemas comunes y soluciones

### Problema 1: Error “Documento no encontrado”

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

### Problema 2: Anotaciones aparecen en ubicaciones incorrectas

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problema 3: Problemas de memoria con documentos grandes

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problema 4: Problemas de licencia en producción

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

## Mejores prácticas de rendimiento para aplicaciones en producción

### Estrategias de gestión de memoria

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

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

### Consideraciones de subprocesos

GroupDocs.Annotation **no es thread‑safe** por defecto. Si tu aplicación procesa documentos concurrentemente:

- **Nunca compartas** una instancia de `Annotator` entre hilos.  
- **Sincroniza** el acceso a archivos o usa un mecanismo de bloqueo.  
- Considera un **pool** de objetos `Annotator` si necesitas alto rendimiento.

### Estrategias de caché

- Cachea plantillas de anotación usadas frecuentemente.  
- Reutiliza colecciones `Point` para conjuntos de coordenadas comunes.  
- Mantén un **PDF plantilla** en memoria si anotas repetidamente el mismo documento base.

## Aplicaciones del mundo real y casos de uso

### Sistemas de revisión de documentos

- **Revisión legal:** Subraya cláusulas contractuales y agrega comentarios sobre riesgos.  
- **Auditorías de cumplimiento:** Resalta secciones problemáticas en estados financieros.  
- **Revisión académica por pares:** Profesores subrayan pasajes que necesitan aclaración.

### Plataformas educativas

- **Herramientas de anotación para estudiantes:** Permiten a los alumnos subrayar conceptos clave en libros electrónicos.  
- **Retroalimentación docente:** Proporciona comentarios en línea directamente sobre tareas entregadas.

### Flujos de trabajo de aseguramiento de calidad

- **Revisión de documentación técnica:** Ingenieros subrayan secciones que requieren actualizaciones.  
- **Procedimientos operativos estándar:** Oficiales de seguridad resaltan pasos críticos.

### Sistemas de gestión de contenido

- **Flujo editorial:** Editores subrayan texto que necesita verificación de hechos.  
- **Control de versiones:** Rastrea el historial de anotaciones a través de revisiones de documentos.

## Consejos avanzados para una implementación profesional

### Estilos de anotación personalizados

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadatos de anotación para seguimiento

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integración con sistemas de gestión de usuarios

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

## Solución de problemas en producción

### Monitoreo de rendimiento

Observa estas métricas en producción:
- **Uso de heap** – asegura que se llame a `dispose()`.  
- **Tiempo de procesamiento por documento** – registra marcas de tiempo antes y después de `annotator.save()`.  
- **Tasa de errores** – captura excepciones y clasifícalas.

### Trucos comunes en producción

- **Bloqueo de archivos** – asegura que los archivos subidos estén cerrados antes de anotarlos.  
- **Ediciones concurrentes** – implementa bloqueo optimista o verificaciones de versión.  
- **Archivos grandes (> 50 MB)** – aumenta el timeout de la JVM y considera APIs de streaming.

### Mejores prácticas de manejo de errores

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

## Conclusión

Ahora tienes todo lo necesario para **crear PDF limpio Java** y **anotar PDF en Java** con anotaciones subrayadas usando GroupDocs.Annotation. Recuerda:

- Gestionar los recursos con try‑with‑resources o con `dispose()` explícito.  
- Validar las coordenadas temprano para evitar subrayados mal ubicados.  
- Implementar un manejo de errores robusto para la estabilidad en producción.  
- Aprovechar estilos basados en roles y metadatos para adaptarlos a tu flujo de trabajo.

¿Próximos pasos? Prueba a añadir otros tipos de anotación—resaltados, sellos o reemplazos de texto—para construir una solución completa de revisión de documentos.

## Preguntas frecuentes

**P: ¿Cómo anoto varias áreas de texto en una sola operación?**  
R: Crea varios objetos `UnderlineAnnotation` con diferentes coordenadas y añádelos secuencialmente usando `annotator.add()`.

**P: ¿Puedo anotar imágenes dentro de documentos PDF?**  
R: Sí. Usa el mismo sistema de coordenadas, asegurándote de que los puntos estén dentro de los límites de la imagen.

**P: ¿Qué formatos de archivo, además de PDF, soporta GroupDocs.Annotation?**  
R: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) y formatos de imagen como JPEG, PNG, TIFF.

**P: ¿Cómo manejo documentos muy grandes sin quedarme sin memoria?**  
R: Procesa los documentos uno a la vez, aumenta el heap de la JVM (`-Xmx`) y siempre dispone de las instancias de `Annotator` rápidamente.

**P: ¿Es posible extraer anotaciones existentes de un documento?**  
R: Sí. Usa `annotator.get()` para obtener todas las anotaciones, luego filtra por tipo, autor o página según sea necesario.

---

**Última actualización:** 2025-12-21  
**Probado con:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---