---
categories:
- Java Development
date: '2026-05-16'
description: Apprenez à créer des réponses d'annotation java en utilisant GroupDocs.Annotation.
  Maîtrisez l'annotation PDF en Java avec des exemples pratiques, des conseils de
  performance et les meilleures pratiques.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Tutoriel d'annotation PDF Java
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
title: 'Java PDF Annotation Library: créer une réponse d''annotation java'
type: docs
url: /fr/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Bibliothèque Java d'annotation PDF : créer une réponse d'annotation java

If you need to **create annotation reply java** for PDFs—whether you’re building a contract‑review portal, an e‑learning system, or a bulk‑processing pipeline—this guide shows you exactly how to do it with GroupDocs.Annotation for Java. We’ll walk through setup, squiggly annotation creation, reply threading, and performance tuning so you can ship a reliable solution in days, not weeks.

## Réponses rapides
- **Quel est le but principal de GroupDocs.Annotation ?** Il permet la création, la modification et l'extraction programmatiques d'annotations PDF en Java.  
- **Comment ajouter une annotation squiggly ?** Instanciez `SquigglyAnnotation`, définissez sa géométrie et son style, puis appelez `annotator.add(...)`.  
- **Puis‑je attacher des réponses à une annotation ?** Oui — créez des objets `Reply`, définissez l'auteur et le texte, et associez‑les à l'annotation parent.  
- **Ai‑je besoin d’une licence pour la production ?** Absolument ; sans licence valide, la sortie contiendra des filigranes.  
- **Est‑elle adaptée au traitement par lots ?** Oui — utilisez try‑with‑resources pour ouvrir chaque document, l'annoter et le fermer, en maintenant une faible utilisation de la mémoire.

## Pourquoi les développeurs Java ont besoin de bibliothèques d'annotation PDF

Manually marking up PDFs is time‑consuming and error‑prone, especially when you have to review hundreds of contracts or exam papers. A Java PDF annotation library automates this work, letting you embed highlights, squiggly underlines, and threaded comments directly in the file. The result is a searchable, portable document that retains all markup without needing a separate viewer.

**What you’ll master in this guide**
- Installation et licence de GroupDocs.Annotation dans un projet Maven  
- Création d'annotations squiggly qui ressemblent aux soulignements natifs de Word  
- Ajout de réponses en fil de discussion à n'importe quelle annotation pour une révision collaborative  
- Optimisation de l'utilisation de la mémoire et du CPU lors du traitement de gros PDFs  
- Déploiement de la solution dans Spring Boot, micro‑services ou applications de bureau  

Que vous construisiez un système de révision de documents juridiques, un outil de notation éducatif ou un pipeline automatisé de contrôle qualité, les techniques ci‑dessous vous fourniront une base prête pour la production.

## Qu'est‑ce que create annotation reply java ?

`create annotation reply java` is the programmatic process of attaching a comment thread (a Reply) to an existing PDF annotation using Java. Replies let multiple reviewers discuss a specific markup without leaving the document, enabling seamless, in‑place collaboration. This capability turns a static PDF into an interactive discussion platform, preserving context and audit trails directly within the file.

## Prérequis : préparer votre environnement

Before we dive into code, verify that your development workstation meets these specs:

- **JDK** 8 ou supérieur (JDK 11 + est recommandé pour de meilleures performances de garbage‑collection)  
- **Maven** ou **Gradle** pour la gestion des dépendances (les exemples utilisent Maven)  
- Un IDE avec support Maven (IntelliJ IDEA, Eclipse ou VS Code)  
- Au moins **2 GB** de RAM libre pour l'IDE et les exécutions de test  
- Fichiers PDF d'exemple pour l'expérimentation (vous pouvez générer de simples PDFs avec n'importe quel éditeur PDF)

GroupDocs.Annotation runs entirely in‑process; no external PDF viewers or native libraries are required.

## Configuration de GroupDocs.Annotation pour Java

Integrating the library is a few‑step process, but a couple of hidden pitfalls can cause runtime errors if you miss them.

### Configuration de la dépendance Maven

Add the repository and dependency to your `pom.xml`. Place the `<repositories>` element **before** `<dependencies>` to ensure Maven can resolve the artifact.

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

> **Astuce :** Check the GroupDocs releases page for the latest version. New releases often include support for emerging PDF standards and performance improvements.

### Configuration de la licence (Ne pas sauter ceci !)

GroupDocs.Annotation requires a license file for production use. Without it, every generated PDF will carry a watermark.

1. **Free Trial** – Full feature set for 30 days, ideal for evaluation.  
2. **Temporary License** – Good for development and internal testing.  
3. **Full License** – Required for any commercial deployment.

Place the `GroupDocs.Annotation.lic` file in your resources folder and load it at startup:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Common gotcha:** Forgetting the license step results in watermarked PDFs and API calls that silently fail. Always validate the license early in your startup routine.

## Guide complet d'implémentation : ajout d'annotations squiggly

Below is a step‑by‑step walkthrough that shows how to **create annotation reply java** while building a squiggly annotation. Each step includes a concise explanation, so you understand the “why” behind every line.

### Étape 1 : importer toutes les classes requises

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` is the entry point for all document‑level operations.  
- `Point` represents a coordinate on a page (X and Y measured from the top‑left).  
- `SquigglyAnnotation` defines the wavy underline used to highlight errors.  
- `Reply` stores threaded comments attached to an annotation.  
- `SaveOptions` lets you control output format and compression.  

### Étape 2 : créer et configurer votre annotation squiggly

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

SquigglyAnnotation is a class that creates a wavy underline used to highlight errors in a PDF.

- **Coordinate system**: Points start at the top‑left corner. The two points above draw a horizontal wavy line from (100, 200) to (300, 200).  
- **Opacity** 0.7 means the annotation is 70 % opaque, letting underlying text remain readable.  

### Étape 3 : ajouter des réponses interactives (optionnel mais puissant)

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

Reply is a class representing a comment thread attached to an annotation.

- Replies create a **threaded discussion** directly on the annotation, mirroring the experience of modern PDF reviewers.  
- Each reply stores author information and a timestamp, which you can later filter or display in a UI.  

### Étape 4 : appliquer l'annotation et enregistrer le document

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- The **try‑with‑resources** construct automatically closes the `Annotator`, releasing file handles and native buffers.  
- `save` writes the modified PDF to `output.pdf`.  

> **Memory note:** The `Annotator` loads only the pages you touch. For multi‑hundred‑page PDFs, this approach keeps heap usage under 150 MB on a typical server.

## Options de configuration avancées

### Personnalisation de l'apparence de l'annotation

You can fine‑tune the visual style to match your brand guidelines:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** controls line thickness (in points).  
- **ARGB** format includes an alpha channel for transparency.  

### Positionnement précis des annotations

Getting coordinates right can be tricky on PDFs with varying page sizes. Follow this systematic approach:

1. **Open the PDF in a viewer** (e.g., Adobe Acrobat) and note the ruler values for the target area.  
2. **Translate ruler values** to points (1 point = 1/72 inch).  
3. **Use `annotator.getPageInfo(pageIndex)`** to retrieve page width and height, then calculate relative positions.  

## Problèmes courants et solutions

### Problème : les annotations n'apparaissent pas

**Most likely causes**
- Points lie outside the page bounds  
- License not loaded (watermark hides annotation)  
- Wrong page number (pages are zero‑based in the API)  

**Solution checklist**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Problème : mauvaise performance avec les gros fichiers

Loading a 500‑page PDF into memory can stall your service. Mitigate this by:

- **Processing one page at a time** – open the document, annotate a single page, save, then move to the next.  
- **Streaming** – use `Annotator`’s streaming API to avoid full document buffering.  
- **Caching** – store frequently accessed PDFs in a fast cache (e.g., Redis) and annotate the cached copy.  

### Problème : les valeurs de couleur ne fonctionnent pas

GroupDocs expects **ARGB** (Alpha, Red, Green, Blue) rather than plain RGB. An ARGB value of `0xFFFF0000` means fully opaque red. If you supply `0xFF0000` the library interprets it incorrectly, resulting in a black annotation.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Meilleures pratiques de performance

### Gestion de la mémoire

When annotating dozens of PDFs in a batch job, wrap each file in its own try‑with‑resources block:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- This pattern guarantees that native buffers are released after each iteration, preventing **OutOfMemoryError** on long‑running processes.

### Optimisation du traitement par lots

For high‑throughput environments, consider parallel streams combined with a bounded thread pool:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Bounded pool** avoids thread explosion, while parallel streams keep CPU cores busy.

### Considérations sur la taille des fichiers

Large PDFs (> 100 MB) can degrade performance. Apply these strategies:

- **Pre‑compress** the source PDF with a tool like Ghostscript before annotation.  
- **Annotate only needed pages** – skip pages that don’t require markup.  
- **Split** the document into logical sections (e.g., per chapter) and process each chunk independently.  

## Applications réelles

### Systèmes de révision de documents

Legal firms often need to flag problematic clauses. Squiggly annotations combined with threaded replies let multiple attorneys discuss a single paragraph without leaving the PDF:

- **Lawyer A** adds a red squiggly under a clause and writes “Ambiguous wording”.  
- **Lawyer B** replies “Add definition for ‘material breach’”.  
- The entire discussion stays embedded, searchable, and auditable.

### Intégration avec les systèmes existants

GroupDocs.Annotation works smoothly with popular Java frameworks:

- **Spring Boot** – expose a REST endpoint `/api/annotate` that accepts a PDF multipart upload, adds annotations, and streams the result back.  
- **JSF** – bind annotation actions to UI components for on‑the‑fly markup in a web view.  
- **Microservices** – the library’s small footprint (< 15 MB) lets you containerize it with Docker and scale horizontally.  

### Automatisation du flux de travail

Combine annotation with other GroupDocs products (e.g., GroupDocs.Signature) to build end‑to‑end pipelines:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Quand utiliser les annotations squiggly vs. alternatives

| Cas d’utilisation | Annotation recommandée |
|-------------------|------------------------|
| Marquer des fautes d'orthographe ou de grammaire | **Squiggly** – indice visuel similaire aux traitements de texte |
| Mettre en évidence des sections importantes sans impliquer une erreur | **Highlight** – superposition translucide |
| Fournir des retours détaillés | **Text** ou **Comment** – boîte de note libre |
| Approuver ou rejeter un document | **Stamp** – badge “Approved” ou “Rejected” |

## Conclusion

You now have a complete, production‑ready recipe for **create annotation reply java** using GroupDocs.Annotation. By mastering the API, handling licensing, and applying the performance tips above, you can:

- Automate error‑marking across thousands of PDFs  
- Enable collaborative, threaded discussions inside the file itself  
- Keep memory usage low even when processing massive documents  

**Next steps**

1. Experiment with other annotation types (highlights, stamps, text).  
2. Build a REST service that receives PDFs, annotates them, and returns the result.  
3. Explore the extraction API (`annotator.get()`) to pull existing comments for analytics.  

The power of programmatic PDF annotation lies in its ability to replace tedious manual markup with repeatable, auditable code. Whether you’re building a niche legal‑tech product or a general‑purpose document workflow engine, the techniques in this guide give you a solid foundation to move forward.

## Questions fréquentes

**Q : Qu’est‑ce qui rend GroupDocs.Annotation meilleur que les autres bibliothèques PDF Java ?**  
R : GroupDocs.Annotation focuses exclusively on annotation workflows, offering over 30 annotation types, threaded replies, and native support for 50 + file formats while keeping the memory footprint under 200 MB for 500‑page PDFs.

**Q : Puis‑je utiliser cette bibliothèque avec des applications Spring Boot ?**  
R : Absolutely. Create a `@RestController` that injects the `Annotator` service, processes multipart uploads, and streams the annotated PDF back to the client. Remember to configure a thread‑pool for concurrent requests.

**Q : Comment gérer les documents avec des tailles de page différentes ?**  
R : Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and calculate relative coordinates (e.g., percentages) instead of hard‑coding point values. This ensures annotations appear correctly on A4, Letter, and custom‑size pages.

**Q : Existe‑t‑il un moyen d’extraire les annotations existantes des PDFs ?**  
R : Yes. Call `annotator.get()` to retrieve a collection of all annotations, then iterate to read properties such as author, comment, and geometry. This is useful for migration or analytics scenarios.

**Q : Quelle est la meilleure approche pour gérer les permissions d’annotation dans des systèmes multi‑utilisateurs ?**  
R : Implement authentication at the application layer, store the user ID with each `Reply`, and enforce business rules (e.g., only the author or an admin can edit or delete a reply). The API itself does not enforce permissions, giving you full flexibility.

**Q : Comment optimiser l’utilisation de la mémoire lors du traitement de centaines de PDFs ?**  
R : Use try‑with‑resources for each document, process pages individually, and consider a bounded thread pool to limit concurrent memory consumption. Monitoring JVM heap with tools like VisualVM helps you fine‑tune the `-Xmx` setting.

---

**Last Updated:** 2026-05-16  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Ressources supplémentaires**

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

## Tutoriels associés

- [Java PDF Annotation Library Tutorial](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Remove Annotation Replies Java - Manage Replies by ID with GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)