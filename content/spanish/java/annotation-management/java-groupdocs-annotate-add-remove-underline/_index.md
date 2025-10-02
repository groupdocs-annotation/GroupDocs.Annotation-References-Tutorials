---
"date": "2025-05-06"
"description": "Aprenda a añadir y eliminar anotaciones subrayadas en documentos Java con GroupDocs.Annotation. Mejore la gestión de sus documentos con esta guía detallada."
"title": "Agregar y eliminar anotaciones subrayadas en Java con GroupDocs&#58; una guía completa"
"url": "/es/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Cómo implementar Java: agregar y eliminar anotaciones subrayadas con GroupDocs

## Introducción

¿Quiere mejorar su sistema de gestión de documentos añadiendo o eliminando anotaciones mediante programación? Este tutorial le guiará en el uso de la potente biblioteca GroupDocs.Annotation de Java para añadir y eliminar anotaciones subrayadas en documentos como PDF.

**Lo que aprenderás:**
- Inicializar la clase Anotador.
- Agregue una anotación subrayada con comentarios usando GroupDocs.Annotation para Java.
- Eliminar todas las anotaciones de un documento.
- Configure su entorno para utilizar GroupDocs.Annotation de manera eficiente.

Exploremos cómo aprovechar estas funcionalidades en sus proyectos. Asegúrese de cumplir con los requisitos previos necesarios antes de comenzar.

## Prerrequisitos

### Bibliotecas y dependencias requeridas
Para seguir este tutorial de manera eficaz, asegúrese de tener:
- **GroupDocs.Annotation para Java**Se recomienda la versión 25.2 o posterior.
- **Kit de desarrollo de Java (JDK)**Se requiere la versión 8 o superior.

### Requisitos de configuración del entorno
Asegúrese de que su entorno de desarrollo incluya un IDE como IntelliJ IDEA o Eclipse y una herramienta de compilación como Maven.

### Requisitos previos de conocimiento
Será beneficioso tener conocimientos básicos de programación Java, especialmente trabajar con bibliotecas a través de Maven.

## Configuración de GroupDocs.Annotation para Java

Para comenzar a utilizar GroupDocs.Annotation en sus proyectos Java, siga estos pasos de configuración:

**Configuración de Maven:**
Agregue la siguiente configuración a su `pom.xml` archivo para descargar e integrar GroupDocs.Annotation.

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

**Adquisición de licencia:**
Empiece por descargar una prueba gratuita u obtener una licencia temporal de GroupDocs para explorar todas las funciones de su biblioteca. Para uso en producción, es necesario adquirir una licencia.

## Guía de implementación

### Característica 1: Inicializar el anotador y agregar anotación subrayada

Esta sección le guiará a través de la inicialización del `Annotator` clase y agregar una anotación subrayada a su documento.

#### Descripción general
Añadir anotaciones ayuda a resaltar partes específicas de un documento. Aquí, nos centramos en subrayar el texto con comentarios para aclarar o dar sugerencias.

#### Implementación paso a paso

**1. Inicializar el anotador**
Crear un `Annotator` objeto y cargue su archivo PDF.

```java
import com.groupdocs.annotation.Annotator;

// Cargue el documento que desea anotar
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Crea comentarios con respuestas**
Define comentarios asociados con la anotación subrayada.

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

**3. Definir puntos para la anotación subrayada**
Establezca coordenadas para determinar dónde debe aparecer el subrayado.

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

**4. Crear y configurar la anotación subrayada**
Cree la anotación subrayada y configure sus propiedades como color, opacidad y comentarios.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Amarillo en formato ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Guardar el documento anotado**
Guarde los cambios en un nuevo archivo.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Consejos para la solución de problemas
- Asegúrese de que todas las coordenadas de los puntos estén dentro de los límites del documento.
- Verificar que el `outputPath` El directorio existe y se puede escribir.

### Función 2: Guardar documento sin anotaciones

Esta sección explica cómo eliminar todas las anotaciones de un documento previamente anotado.

#### Descripción general
Es posible que necesite guardar una versión limpia de su documento sin anotaciones para compartirlo o archivarlo.

#### Implementación paso a paso

**1. Inicializar el Anotador con el Documento Anotado**
Cargue el documento que tiene anotaciones existentes.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configurar las opciones de guardado para eliminar anotaciones**
Especifica que no se deben guardar anotaciones en el archivo de salida.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Guardar el documento sin anotaciones**
Define la ruta para el documento limpio y guárdalo.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Aplicaciones prácticas

A continuación se presentan algunos escenarios del mundo real en los que estas características pueden resultar beneficiosas:
1. **Revisión de documentos**:Resaltar y comentar secciones de un contrato o informe para su revisión.
2. **Herramientas educativas**:Anotar libros de texto con notas o correcciones para los estudiantes.
3. **Edición colaborativa**:Compartir borradores anotados entre los miembros del equipo para recibir comentarios.
4. **Documentación legal**:Subrayar cláusulas claves en documentos legales durante las discusiones.
5. **Materiales de marketing**:Destacar información importante en los folletos antes de su distribución.

## Consideraciones de rendimiento
Al trabajar con GroupDocs.Annotation, tenga en cuenta estos consejos para optimizar el rendimiento:
- **Gestión de la memoria**: Deseche adecuadamente `Annotator` objetos para liberar recursos.
- **Procesamiento por lotes**:Si anota varios documentos, proceselos en lotes para administrar la carga del sistema de manera eficaz.
- **Asignación de recursos**:Asegúrese de que su entorno tenga suficiente memoria y potencia de procesamiento para manejar archivos grandes.

## Conclusión
Aprendió a añadir y eliminar anotaciones subrayadas con GroupDocs.Annotation para Java. Este tutorial abordó la inicialización de la clase Annotator, la configuración de anotaciones con comentarios y el guardado de documentos sin anotaciones. 

Para explorar más a fondo, considere integrar estas funciones en sus sistemas de gestión de documentos existentes o experimentar con otros tipos de anotaciones proporcionados por GroupDocs.

## Sección de preguntas frecuentes
1. **¿Cómo configuro múltiples anotaciones subrayadas en una sola ejecución?**
   - Crear múltiples `UnderlineAnnotation` objetos y agregarlos secuencialmente usando el `annotator.add()` método.
2. **¿Puedo anotar imágenes dentro de archivos PDF usando esta biblioteca?**
   - Sí, GroupDocs.Annotation admite la anotación de imágenes dentro de documentos como PDF.
3. **¿Qué formatos de archivos admite GroupDocs.Annotation?**
   - Admite varios formatos de documentos, incluidos PDF, Word, Excel y más.