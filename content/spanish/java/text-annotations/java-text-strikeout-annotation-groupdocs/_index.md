---
categories:
- Java Development
date: '2026-03-30'
description: Aprende cómo agregar anotaciones de tachado en Java usando GroupDocs.Annotation.
  Guía paso a paso con ejemplos de código, consejos de solución de problemas y mejores
  prácticas para el marcado de documentos.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Tutorial de Java para agregar anotación de tachado con GroupDocs
type: docs
url: /es/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Añadir anotación de tachado Java - Guía completa de GroupDocs

¿Alguna vez se ha quedado mirando un documento pensando, “Necesito tachar este texto, pero no puedo simplemente coger un bolígrafo rojo”? No está solo. Ya sea que esté construyendo un sistema de revisión de documentos, creando un flujo de trabajo de edición, o simplemente necesite marcar texto para eliminarlo en su aplicación Java, **add strikeout annotation java** es una habilidad esencial. En este tutorial repasaremos todo lo que necesita saber para implementar la funcionalidad de tachado de texto que realmente funciona en producción.

## Respuestas rápidas
- **¿Qué biblioteca admite anotaciones de tachado en Java?** GroupDocs.Annotation for Java  
- **¿Qué palabra clave principal debo apuntar para SEO?** add strikeout annotation java  
- **¿Necesito una licencia para ejecutar el código de ejemplo?** Una prueba gratuita o licencia temporal funciona para desarrollo; se requiere una licencia completa para producción.  
- **¿Puedo usar esto con archivos PDF, DOCX y PPTX?** Sí – GroupDocs.Annotation admite todos los formatos de documento principales.  
- **¿Qué versión de Java se requiere?** JDK 8 o superior (JDK 11+ recomendado).

## Qué es add strikeout annotation java
Una anotación de tachado dibuja una línea a través del texto seleccionado, indicando visualmente que el contenido debe ser eliminado o ignorado. Es una forma no destructiva de sugerir eliminaciones mientras se mantiene el texto original intacto para auditorías o revisiones colaborativas.

## Por qué usar anotaciones de tachado en aplicaciones Java
- **Flujos de revisión de documentos** – los revisores pueden marcar texto no deseado sin alterar la fuente.  
- **Edición colaborativa** – los miembros del equipo ven las eliminaciones sugeridas al instante.  
- **Legal y cumplimiento** – mantener una auditoría clara de los cambios.  
- **Migración de contenido** – marcar secciones obsoletas antes de mover contenido entre sistemas.  

## Requisitos previos y configuración del entorno
Necesitará lo siguiente antes de sumergirse en el código:

- **Java Development Kit (JDK)** 8+ (JDK 11+ recomendado)  
- **Maven o Gradle** para la gestión de dependencias  
- **IDE** – IntelliJ IDEA, Eclipse o VS Code con extensiones Java  
- **Biblioteca GroupDocs.Annotation** – usaremos la versión 25.2 en los ejemplos  

*Deseable:* conocimientos básicos de anotaciones Java y manejo de PDF.

## Configuración de GroupDocs.Annotation para Java

### Configuración de Maven que realmente funciona
Agregue el repositorio y la dependencia a su `pom.xml` exactamente como se muestra:

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

### Obtención de su licencia
GroupDocs ofrece varias opciones de licencia:

- **Prueba gratuita** – perfecta para pruebas (no se requiere tarjeta de crédito)  
- **Licencia temporal** – ideal para desarrollo y pruebas  
- **Licencia completa** – requerida para uso en producción; vea la [página de compra](https://purchase.groupdocs.com/buy)

> **Consejo profesional:** Comience con la prueba gratuita para explorar la API, luego cambie a una licencia temporal cuando esté listo para crear una funcionalidad del mundo real.

### Configuración rápida de verificación de sanidad
Ejecute este programa mínimo para verificar que la biblioteca se cargue correctamente:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Si la consola imprime el mensaje de éxito sin errores, está listo para añadir anotaciones de tachado.

## Cómo añadir anotación de tachado java

A continuación se muestra una implementación completa y lista para producción, dividida en pasos claros.

### Paso 1 – Inicializar el Annotator
Cree una instancia de `Annotator` que apunte al documento fuente:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Por qué es importante:** Usar una ruta absoluta o una ruta relativa resuelta correctamente evita excepciones de “archivo no encontrado”.

### Paso 2 – (Opcional) Preparar respuestas de comentarios
Agregar respuestas hace que la anotación sea colaborativa:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Estos comentarios aparecen cuando un usuario pasa el cursor sobre el tachado.

### Paso 3 – Definir el área de tachado
Especifique el rectángulo que envuelve el texto que desea tachar:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Consejo de coordenadas:** El origen (0,0) es la esquina superior izquierda de la página; X crece hacia la derecha, Y crece hacia abajo. Use un visor de PDF que muestre coordenadas para afinar estos valores.

### Paso 4 – Configurar la anotación de tachado
Establezca la apariencia, el número de página y adjunte los comentarios:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Nota de color:* `65535` corresponde a amarillo en formato RGB entero. Cambie el valor para usar otros colores.

### Paso 5 – Aplicar la anotación y guardar
Añada la anotación al documento y escriba el archivo de salida:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Paso 6 – Liberar recursos (¡Crítico!)
Siempre libere el annotator para liberar recursos nativos:

```java
if (annotator != null) {
    annotator.dispose();
}
```

En producción, envuelva el uso en un bloque try‑with‑resources o una construcción `try/finally`.

## Problemas comunes y cómo solucionarlos

| Problema | Síntoma | Solución |
|----------|---------|----------|
| **Archivo no encontrado** | `Annotator` lanza una excepción | Utilice rutas absolutas, verifique permisos de lectura, asegúrese de que ningún otro proceso bloquee el archivo |
| **Coordenadas incorrectas** | El tachado aparece alejado del texto previsto | Verifique nuevamente el sistema de coordenadas del visor PDF; ajuste los puntos en consecuencia |
| **Anotación invisible** | No hay tachado visible después de guardar | Aumente `opacity` (p. ej., `0.9`), verifique `pageNumber` (basado en 0), asegúrese de que los puntos formen un rectángulo válido |
| **OutOfMemoryError** | La aplicación se bloquea con PDFs grandes | Aumente el heap de JVM (`-Xmx2048m`), procese documentos en lotes, siempre llame a `dispose()` |

## Mejores prácticas de rendimiento para producción

### Gestión de memoria
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Estrategia de procesamiento por lotes
Cuando necesite anotar docenas o cientos de archivos:

- Procese 10‑20 documentos por lote.  
- Registre éxito/fallo para cada archivo.  
- Re‑inicialice el `Annotator` para cada documento para evitar fugas de memoria.  

### Consejos de caché
- Cache los plantillas de documento de uso frecuente.  
- Almacene mapas de coordenadas pre‑calculados para diseños estándar.  

## Casos de uso del mundo real

1. **Sistemas de revisión de documentos** – Los editores sugieren eliminaciones sin alterar el contrato original.  
2. **Enmiendas legales** – Los abogados rastrean la eliminación de cláusulas mientras preservan la redacción original para auditoría.  
3. **Revisión académica por pares** – Los revisores marcan secciones para eliminación y añaden comentarios en línea.  
4. **Migración de contenido** – Durante migraciones de CMS, los tachados resaltan copias obsoletas que necesitan ser reemplazadas.  

## Personalización avanzada

### Estilizado personalizado
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Añadiendo metadatos
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Lista de verificación de solución de problemas
- ✅ ¿Puede abrir el archivo fuente manualmente?  
- ✅ ¿Todas las dependencias de GroupDocs están presentes en el classpath?  
- ✅ ¿Los puntos forman un rectángulo válido?  
- ✅ ¿El número de página es correcto (basado en 0)?  
- ✅ ¿Hay suficiente memoria heap?  
- ✅ ¿Tiene permiso de escritura para la carpeta de salida?  
- ✅ ¿El formato del documento es compatible (PDF, DOCX, PPTX, etc.)?  

## Preguntas frecuentes

**Q: ¿Puedo usar GroupDocs.Annotation dentro de un servicio Spring Boot?**  
A: Sí. Añada la dependencia Maven, inyecte una clase de servicio que cree el `Annotator`, y gestione su ciclo de vida con los alcances de bean de Spring.

**Q: ¿Qué formatos de documento admiten anotaciones de tachado?**  
A: PDF, DOCX, PPTX y muchos otros formatos compatibles con GroupDocs.Annotation. PDF ofrece el manejo de coordenadas más preciso.

**Q: ¿Cómo manejo documentos con tamaños de página variables?**  
A: Obtenga las dimensiones de la página mediante `annotator.getPageInfo(pageNumber)` y escale sus coordenadas en consecuencia.

**Q: ¿Es posible editar o eliminar una anotación de tachado existente?**  
A: Absolutamente. Use `annotator.getAnnotations(pageNumber)` para obtenerlas, luego `annotator.update(updatedAnnotation)` o `annotator.delete(annotationId)`.

**Q: ¿Cuál es el impacto en el rendimiento al añadir muchas anotaciones?**  
A: Añadir cientos de anotaciones generalmente está bien, pero monitoree el uso de memoria. Para conjuntos de anotaciones muy grandes, considere paginar la vista o cargar anotaciones bajo demanda.

## Conclusión
Ahora tiene una guía completa y lista para producción para **add strikeout annotation java** usando GroupDocs.Annotation. Comience con el sencillo ejemplo de verificación, luego escale al procesamiento por lotes, estilizado personalizado y enriquecimiento de metadatos. Recuerde probar las coordenadas cuidadosamente, gestionar los recursos responsablemente y elegir el modelo de licencia adecuado para su entorno.

¿Listo para explorar más? Consulte otros tipos de anotación—resaltar, nota, imagen, flecha y marca de agua—para crear una suite de colaboración documental completa.

---

**Última actualización:** 2026-03-30  
**Probado con:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Recursos adicionales**
- [Documentación de GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Guía de referencia API](https://reference.groupdocs.com/annotation/java/)
- [Descargar última versión](https://releases.groupdocs.com/annotation/java/)
- [Comprar licencia completa](https://purchase.groupdocs.com/buy)
- [Iniciar prueba gratuita](https://releases.groupdocs.com/annotation/java/)
- [Obtener licencia temporal](https://purchase.groupdocs.com/temporary-license/)
- [Foro de soporte comunitario](https://forum.groupdocs.com/c/annotation/)