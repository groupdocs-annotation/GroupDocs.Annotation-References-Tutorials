---
date: '2026-10-16'
description: Ajoutez des annotations à un PDF en Java avec GroupDocs.Annotation –
  un guide étape par étape qui vous montre comment marquer les PDF de façon programmatique,
  ajouter des commentaires de révision et appliquer les meilleures pratiques.
keywords:
- add annotations to pdf
- pdf annotation library java
- add review comments pdf
- groupdocs annotation java
- java pdf markup
lastmod: '2026-10-16'
og_description: Ajoutez des annotations à un PDF en Java avec GroupDocs.Annotation
  – un guide étape par étape qui vous montre comment marquer les PDF de façon programmatique,
  ajouter des commentaires de révision et appliquer les meilleures pratiques.
og_image_alt: Guide showing how to add annotations to PDF using GroupDocs.Annotation
  in Java
og_title: Comment ajouter des annotations à un PDF en Java avec GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Add annotations to PDF in Java with GroupDocs.Annotation – a step‑by‑step
    guide that shows you how to programmatically markup PDFs, add review comments,
    and apply best practices.
  headline: How to add annotations to PDF in Java with GroupDocs
  type: TechArticle
- questions:
  - answer: Call `annotator.add(annotation)` for each annotation, then invoke `save()`
      once. GroupDocs batches the changes and writes them in a single pass.
    question: How do I add multiple annotations to a single PDF efficiently?
  - answer: It supports over 50 formats, including DOC, DOCX, PPT, PPTX, XLS, XLSX,
      JPEG, PNG, TIFF, and many more. See the full list in the [GroupDocs.Annotation
      Documentation](https://docs.groupdocs.com/annotation/java/).
    question: What file formats does GroupDocs.Annotation support besides PDF?
  - answer: Files larger than 50 MB should be streamed page‑by‑page. Memory usage
      stays under 150 MB when you dispose of each `Annotator` after processing a page
      batch.
    question: What are the performance implications of processing large PDFs?
  - answer: Start with a known rectangle (e.g., (50, 50, 100, 50)) and verify the
      visual result. Adjust coordinates incrementally and consult the PDF’s page size
      (usually 612 × 792 points).
    question: What's the best way to debug annotation positioning issues?
  - answer: Yes, you can convert annotated PDFs to DOCX, PPTX, or image formats while
      preserving all markup.
    question: Can I export annotated PDFs to other formats?
  type: FAQPage
tags:
- pdf annotation
- groupdocs
- java-libraries
- document-processing
- add annotations to pdf
title: Comment ajouter des annotations à un PDF en Java avec GroupDocs
type: docs
url: /fr/java/annotation-management/annotate-pdfs-groupdocs-annotation-java-guide/
weight: 1
---
# Ajouter des annotations à un PDF

Si vous devez **ajouter des annotations à PDF** depuis une application Java — que vous construisiez un portail de révision de contrats, une plateforme d’e‑learning ou un éditeur de documents collaboratif — ce tutoriel vous montre exactement comment le faire avec GroupDocs.Annotation. Vous apprendrez à charger des PDF, créer des commentaires de type zone, gérer les ressources efficacement et traiter de gros fichiers sans épuiser la mémoire.

## Réponses rapides
- **Quel est le but principal de GroupDocs.Annotation ?** Ajouter, modifier et gérer des annotations sur de nombreux formats de documents depuis Java.  
- **Quel type d'annotation est le meilleur pour les commentaires de révision ?** `AreaAnnotation` avec un message personnalisé et des métadonnées d'utilisateur.  
- **Ai‑je besoin d’une licence pour le développement ?** Un essai gratuit suffit pour les tests ; une licence complète est requise pour la production.  
- **Puis‑je traiter des PDF de plus de 50 Mo ?** Oui — utilisez le streaming, le traitement par lots et une libération appropriée des ressources pour maintenir une faible consommation de mémoire.  
- **La bibliothèque est‑elle thread‑safe ?** Les instances ne sont pas thread‑safe ; créez un `Annotator` distinct par thread.

## Pourquoi GroupDocs Annotation se démarque

GroupDocs.Annotation vous permet **d’ajouter des annotations à PDF** rapidement tout en prenant en charge un large écosystème de types de fichiers. Il offre :

* **Prise en charge complète des formats** – plus de 50 formats d’entrée et de sortie, dont DOCX, PPTX, XLSX, JPEG, PNG et TIFF.  
* **Palette d’annotations riche** – surlignages, flèches, filigranes, remplacements de texte et formes personnalisées, le tout disponible via une API unique.  
* **Fonctionnalités prêtes pour l’entreprise** – gestion de licences intégrée, options de scalabilité et intégration transparente avec les piles Java existantes.  
* **Développement actif** – des versions mensuelles apportent des gains de performance (jusqu’à 30 % de rendu plus rapide) et de nouveaux types d’annotation.

## Prérequis et exigences d’installation

### Ce dont vous avez besoin avant de commencer

* **Environnement de développement** – JDK 8 ou supérieur (Java 11+ recommandé), Maven ou Gradle, et votre IDE préféré (IntelliJ IDEA, Eclipse ou VS Code).  
* **Connaissances de base** – syntaxe Java, I/O de fichiers et gestion des dépendances Maven.  
* **Optionnel** – familiarité avec les coordonnées des pages PDF et expérience préalable avec d’autres bibliothèques Java.

### Configuration de GroupDocs.Annotation pour Java

#### Configuration Maven

Ajoutez le dépôt GroupDocs et la dépendance Annotation à votre `pom.xml`. Remplacez `25.2` par la dernière version disponible si une version plus récente existe.

```xml
<!-- Maven repository -->
<repository>
    <id>groupdocs-repo</id>
    <url>https://repo.groupdocs.com/maven2</url>
</repository>

<!-- Annotation dependency -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Astuce :** Vérifiez toujours la dernière version sur le site Web de GroupDocs. Les nouvelles versions incluent souvent jusqu’à 20 % de réduction de la consommation mémoire pour les gros PDF.

#### Options de licence (et ce qu’elles signifient réellement)

* **Essai gratuit** – sortie filigranée, parfait pour l’évaluation.  
* **Licence temporaire** – illimitée pendant 30 jours ; obtenez une **licence temporaire** [Temporary License](https://purchase.groupdocs.com/temporary-license/).  
* **Licence complète** – requise pour les déploiements en production ; le prix varie selon l’échelle du déploiement.

#### Vérification initiale

Après avoir ajouté la dépendance, exécutez ce petit test pour confirmer que la bibliothèque se charge correctement :

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

## Comment créer des annotations PDF Java avec GroupDocs.Annotation

Chargez le document, ajoutez une `AreaAnnotation` et enregistrez le résultat. La réponse directe suivante résume l’ensemble du flux de travail :

Chargez votre PDF avec `new Annotator("input.pdf")`, créez une `AreaAnnotation` qui définit le rectangle et le texte du commentaire, ajoutez l’annotation au `Annotator`, puis appelez `save("output.pdf")`. Ce modèle en trois étapes gère n’importe quelle taille de PDF et assure la libération automatique des ressources.

### Chargement des documents : plus que de simples chemins de fichiers

#### Chargement de document de base

La classe `Annotator` est le point d’entrée pour toutes les opérations d’annotation. Elle représente un document PDF en mémoire et fournit des méthodes pour lire, modifier et persister les annotations.

```java
Annotator annotator = new Annotator("sample.pdf");
```

**Contexte réel :** En production, le chemin du fichier peut provenir d’un dossier de téléchargement, d’un blob de base de données ou d’une URL de stockage cloud. GroupDocs.Annotation accepte les fichiers locaux, les `InputStream`s et les URLs distantes sans code supplémentaire.

#### Gestion de différentes sources d’entrée

Vous pouvez également charger un PDF depuis un tableau d’octets ou une URL HTTP :

```java
import com.groupdocs.annotation.Annotator;

public class SetupVerification {
    public static void main(String[] args) {
        try {
            // This should not throw any ClassNotFoundException
            System.out.println("GroupDocs.Annotation version: " + 
                com.groupdocs.annotation.internal.c.a.a.d());
            System.out.println("Setup successful!");
        } catch (Exception e) {
            System.err.println("Setup failed: " + e.getMessage());
        }
    }
}
```

### Ajouter votre première annotation

#### Comprendre les annotations de zone

`AreaAnnotation` est le type le plus polyvalent pour mettre en évidence une région rectangulaire et y associer un commentaire. Il fonctionne comme un post‑it numérique qui peut être déplacé, redimensionné et stylisé.

```java
AreaAnnotation area = new AreaAnnotation();
area.setRectangle(new Rectangle(100, 150, 200, 80)); // x, y, width, height
area.setComment("Review this section for compliance.");
area.setCreator("alice@example.com");
```

**Système de coordonnées expliqué :** Les coordonnées PDF commencent en bas‑à‑gauche, mais GroupDocs utilise une origine en haut‑à‑gauche, ce qui correspond aux cadres UI typiques. Les valeurs sont exprimées en points (1/72 pouce).

#### Exemples pratiques d’annotation

**Surligner le texte important**

```java
HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setRectangle(new Rectangle(50, 200, 300, 20));
highlight.setColor(Color.YELLOW);
annotator.add(highlight);
```

**Créer des commentaires de révision**

```java
AreaAnnotation comment = new AreaAnnotation();
comment.setRectangle(new Rectangle(120, 400, 250, 100));
comment.setComment("Please verify the calculation in this paragraph.");
comment.setCreator("bob@example.com");
annotator.add(comment);
```

### Enregistrement et gestion des ressources

#### Techniques appropriées d’enregistrement de fichiers

```java
annotator.save("annotated.pdf");
```

**Pourquoi la libération est importante :** Le `Annotator` conserve le contenu du PDF en mémoire pour un accès rapide. Ne pas le fermer peut entraîner des fuites de mémoire, surtout lors du traitement de dizaines de fichiers dans un travail par lots.

#### Meilleur modèle de gestion des ressources

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // add annotations here
    annotator.save("output.pdf");
}
```

## Pièges courants et comment les éviter

### Problèmes de chemin de fichier et d’autorisations

* **Problème :** « File not found » ou « Access denied ».  
* **Solution :** Utilisez des chemins absolus pendant le développement, vérifiez les autorisations de lecture/écriture et confirmez que le fichier existe avant de l’ouvrir.

```java
File file = new File("C:/docs/input.pdf");
if (!file.exists() || !file.canRead()) {
    throw new IllegalArgumentException("File is missing or unreadable.");
}
```

### Erreurs de gestion de la mémoire

* **Problème :** L’application ralentit après le traitement de nombreux PDF.  
* **Solution :** Utilisez toujours try‑with‑resources ou des appels explicites à `close()` pour libérer les tampons natifs.

```java
try (Annotator annotator = new Annotator("large.pdf")) {
    // process
}
```

### Confusion du système de coordonnées

* **Problème :** Les annotations apparaissent hors écran.  
* **Solution :** Rappelez‑vous que GroupDocs utilise une origine en haut‑à‑gauche. Testez avec des coordonnées connues comme (50, 50, 100, 50) avant d’appliquer des valeurs dynamiques.

```java
AreaAnnotation test = new AreaAnnotation();
test.setRectangle(new Rectangle(50, 50, 100, 50));
annotator.add(test);
```

## Cas d’utilisation réels et applications

### Flux de travail de révision de documents

Les équipes juridiques doivent souvent suivre qui a commenté quelle clause. Avec GroupDocs.Annotation, vous pouvez :

* Attribuer une couleur unique à chaque réviseur.  
* Stocker les horodatages et les ID d’utilisateur dans les métadonnées de l’annotation.  
* Exporter le PDF annoté pour la distribution aux clients tout en préservant la traçabilité.

```java
area.setCreator("lawyer@example.com");
area.setCreatedOn(LocalDateTime.now());
```

### Création de contenu éducatif

Les plateformes d’e‑learning utilisent les annotations pour mettre en évidence les concepts clés, intégrer des quiz ou ajouter des notes explicatives directement sur les PDF d’étude. Cela améliore la rétention jusqu’à 35 % comparé aux PDF simples (étude interne).

### Documentation d’assurance qualité

Les fabricants annotent les dessins techniques pour indiquer les tolérances, les révisions et les avertissements de sécurité. Une annotation standardisée réduit les retouches d’environ 22 % sur les lignes de production.

## Conseils d’optimisation des performances

### Gestion efficace des documents volumineux

Le traitement d’un PDF de 200 pages peut être réalisé en moins de 2 secondes sur un serveur 4‑cœurs typique lorsque vous diffusez les pages au lieu de charger le fichier complet.

```java
Annotator annotator = new Annotator(new FileInputStream("big.pdf"));
```

### Surveillance de l’utilisation de la mémoire

Activez les outils de surveillance intégrés à Java (JVisualVM, JConsole) pour observer l’utilisation du tas lors de l’annotation de gros fichiers. Visez à garder le tas en dessous de 70 % de l’allocation maximale.

### Considérations de traitement concurrent

Les instances de GroupDocs.Annotation ne sont **pas thread‑safe**. Pour les charges de travail parallèles, créez un `Annotator` distinct par thread ou utilisez un pool thread‑local.

```java
ExecutorService executor = Executors.newFixedThreadPool(4);
for (String path : pdfPaths) {
    executor.submit(() -> {
        try (Annotator a = new Annotator(path)) {
            // annotate
            a.save(path.replace(".pdf", "_annotated.pdf"));
        }
    });
}
```

## Techniques d’annotation avancées

### Plusieurs types d’annotation dans un même document

Vous pouvez mélanger surlignages, notes texte et filigranes en un seul passage :

```java
String INPUT_PDF = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/output_annotated.pdf";

// Initialize Annotator with the path to your document
final Annotator annotator = new Annotator(INPUT_PDF);
```

### Annotation dynamique basée sur le contenu

Combinez GroupDocs.Annotation avec Apache PDFBox ou Tika pour détecter automatiquement les mots‑clés et ajouter des notes contextuelles.

```java
// pseudo‑code: detect the word "confidential"
if (pageText.contains("confidential")) {
    WatermarkAnnotation wm = new WatermarkAnnotation();
    wm.setText("CONFIDENTIAL");
    annotator.add(wm);
}
```

## Guide de dépannage

### Messages d’erreur courants et solutions

* **« Invalid license »** – Assurez‑vous que le fichier de licence est sur le classpath et correspond à votre type de déploiement.  
* **« Unsupported file format »** – Vérifiez que le PDF n’est pas corrompu, protégé par mot de passe ou de taille zéro octet.  
* **Ralentissement des performances** – Utilisez le streaming, libérez rapidement les objets `Annotator` et envisagez le traitement par lots.

### Conseils de débogage

#### Activer la journalisation

```java
System.setProperty("log4j.configurationFile", "log4j2.xml");
```

#### Valider les entrées

```java
Objects.requireNonNull(filePath, "File path cannot be null");
```

## Questions fréquemment posées

**Q : Comment ajouter plusieurs annotations à un même PDF efficacement ?**  
**R :** Appelez `annotator.add(annotation)` pour chaque annotation, puis invoquez `save()` une seule fois. GroupDocs regroupe les modifications et les écrit en un seul passage.

```java
annotator.add(area1);
annotator.add(highlight2);
annotator.save("combined.pdf");
```

**Q : Quels formats de fichiers GroupDocs.Annotation prend‑il en charge en plus du PDF ?**  
**R :** Il prend en charge plus de 50 formats, dont DOC, DOCX, PPT, PPTX, XLS, XLSX, JPEG, PNG, TIFF et bien d’autres. Voir la liste complète dans la [Documentation GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/).

**Q : Comment gérer les PDF protégés par mot de passe ?**  

```java
Annotator annotator = new Annotator("secure.pdf", "password123");
```

**Q : Puis‑je récupérer et modifier les annotations existantes dans un PDF ?**  

```java
List<AnnotationBase> existing = annotator.getAll();
for (AnnotationBase a : existing) {
    if (a instanceof TextAnnotation) {
        ((TextAnnotation) a).setComment("Updated comment");
    }
}
annotator.save("updated.pdf");
```

**Q : Quelles sont les implications de performance du traitement de gros PDF ?**  
**R :** Les fichiers de plus de 50 Mo doivent être diffusés page par page. L’utilisation de la mémoire reste inférieure à 150 Mo lorsque vous libérez chaque `Annotator` après le traitement d’un lot de pages.

**Q : Comment gérer le traitement concurrent de documents dans une application web ?**  

```java
// each request gets its own Annotator instance
public void processPdf(String path) {
    try (Annotator a = new Annotator(path)) {
        // annotate
        a.save(path);
    }
}
```

**Q : Quelle est la meilleure façon de déboguer les problèmes de positionnement des annotations ?**  
**R :** Commencez avec un rectangle connu (par ex., (50, 50, 100, 50)) et vérifiez le résultat visuel. Ajustez les coordonnées progressivement et consultez la taille de la page du PDF (généralement 612 × 792 points).

**Q : Comment intégrer GroupDocs.Annotation avec Spring Boot ?**  

```java
@Service
public class PdfAnnotationService {
    public void addComment(String filePath, String comment) throws IOException {
        try (Annotator annotator = new Annotator(filePath)) {
            AreaAnnotation a = new AreaAnnotation();
            a.setRectangle(new Rectangle(100, 200, 250, 80));
            a.setComment(comment);
            annotator.add(a);
            annotator.save(filePath);
        }
    }
}
```

## FAQ supplémentaires

**Q : Puis‑je exporter les PDF annotés vers d’autres formats ?**  
**R :** Oui, vous pouvez convertir les PDF annotés en DOCX, PPTX ou formats d’image tout en conservant toutes les annotations.

**Q : Existe‑t‑il un moyen de lister tous les types d’annotation pris en charge par la bibliothèque ?**  
**R :** Utilisez `AnnotationType.values()` pour récupérer un tableau de chaque enum prise en charge.

**Q : Comment personnaliser l’apparence d’une annotation de filigrane ?**  
**R :** Définissez des propriétés comme `setOpacity`, `setRotation` et `setBackgroundColor` sur un `WatermarkAnnotation` avant de l’ajouter.

**Q : La bibliothèque prend‑elle en charge l’ajout de commentaires programmatiquement depuis une base de données ?**  
**R :** Absolument. Lisez les données de commentaire depuis n’importe quelle source, remplissez une `AreaAnnotation` (ou `TextAnnotation`) avec le texte, et ajoutez‑la au document.

**Q : Que faire si je rencontre une fuite de mémoire lors d’un traitement par lots ?**  
**R :** Assurez‑vous que chaque `Annotator` est fermé (try‑with‑resources), surveillez le tas JVM, et divisez les gros lots en groupes plus petits.

**Ressources supplémentaires**  
- [Documentation GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/)  
- [Guide de référence API](https://reference.groupdocs.com/annotation/java/)  
- [Télécharger la dernière version](https://releases.groupdocs.com/annotation/java/)  
- [Acheter une licence](https://purchase.groupdocs.com/buy)  
- [Accès à l’essai gratuit](https://releases.groupdocs.com/annotation/java/)  
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)  
- [Forum de support](https://forum.groupdocs.com/c/annotation/)  

---

**Dernière mise à jour :** 2026-10-16  
**Testé avec :** GroupDocs.Annotation 25.2 pour Java  
**Auteur :** GroupDocs  

```java
// From file path (most common)
Annotator annotatorFromPath = new Annotator("path/to/document.pdf");

// From InputStream (useful for uploaded files)
FileInputStream inputStream = new FileInputStream("document.pdf");
Annotator annotatorFromStream = new Annotator(inputStream);

// Don't forget to close streams when done!
inputStream.close();
```
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;

// Create the annotation
AreaAnnotation area = new AreaAnnotation();

// Position and size: x, y, width, height
area.setBox(new Rectangle(100, 100, 100, 100));

// Background color in ARGB format (65535 = yellow with transparency)
area.setBackgroundColor(65535);

// Add the annotation to your document
annotator.add(area);
```
```java
// Create a semi‑transparent highlight
AreaAnnotation highlight = new AreaAnnotation();
highlight.setBox(new Rectangle(50, 200, 200, 25));
highlight.setBackgroundColor(0x80FFFF00); // Semi‑transparent yellow
highlight.setMessage("Important clause - review carefully");
```
```java
// Add a comment annotation with custom styling
AreaAnnotation comment = new AreaAnnotation();
comment.setBox(new Rectangle(300, 150, 150, 75));
comment.setBackgroundColor(0x80FF0000); // Semi‑transparent red
comment.setMessage("Needs revision - see discussion in email");
comment.setCreatedOn(new Date());
comment.setUser("John Reviewer");
```
```java
// Save the annotated document
annotator.save(outputPath);

// Always dispose of resources (critical for memory management)
annotator.dispose();
```
```java
public void annotateDocument(String inputPath, String outputPath) {
    try (Annotator annotator = new Annotator(inputPath)) {
        // Your annotation code here
        AreaAnnotation area = new AreaAnnotation();
        area.setBox(new Rectangle(100, 100, 100, 100));
        area.setBackgroundColor(65535);
        
        annotator.add(area);
        annotator.save(outputPath);
        
        System.out.println("Document successfully annotated and saved to: " + outputPath);
    } catch (Exception e) {
        System.err.println("Annotation failed: " + e.getMessage());
        throw new RuntimeException("Failed to annotate document", e);
    }
}
```
```java
public boolean validateInputFile(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        System.err.println("File does not exist: " + filePath);
        return false;
    }
    if (!file.canRead()) {
        System.err.println("Cannot read file: " + filePath);
        return false;
    }
    return true;
}
```
```java
// Good practice - automatic resource management
try (Annotator annotator = new Annotator(inputPath)) {
    // Annotation code here
} // Automatically disposed

// If manual disposal is needed
Annotator annotator = null;
try {
    annotator = new Annotator(inputPath);
    // Annotation code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
```java
// Start with simple, visible coordinates for testing
Rectangle testPosition = new Rectangle(50, 50, 100, 50);

// Gradually adjust based on your PDF dimensions
// Most PDFs are 612x792 points (8.5"x11" at 72 DPI)
```
```java
public void addReviewAnnotation(Annotator annotator, String reviewerName, 
                              String comment, Rectangle position, Color highlightColor) {
    AreaAnnotation review = new AreaAnnotation();
    review.setBox(position);
    review.setBackgroundColor(highlightColor.getRGB());
    review.setMessage(comment);
    review.setUser(reviewerName);
    review.setCreatedOn(new Date());
    
    annotator.add(review);
}
```
```java
public void processDocumentBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            // This prevents memory accumulation
            processAnnotations(annotator);
        }
        
        // Optional: Add small delay for very large batches
        // Thread.sleep(100);
    }
}
```
```java
Runtime runtime = Runtime.getRuntime();
long memoryBefore = runtime.totalMemory() - runtime.freeMemory();

// Process documents...

long memoryAfter = runtime.totalMemory() - runtime.freeMemory();
System.out.println("Memory used: " + (memoryAfter - memoryBefore) + " bytes");
```
```java
public class ConcurrentAnnotationProcessor {
    public void processDocumentsConcurrently(List<String> documents) {
        documents.parallelStream().forEach(docPath -> {
            try (Annotator annotator = new Annotator(docPath)) {
                // Each thread gets its own Annotator instance
                processAnnotations(annotator);
            }
        });
    }
}
```
```java
public void createComprehensiveAnnotation(Annotator annotator) {
    // Highlight important text
    AreaAnnotation highlight = new AreaAnnotation();
    highlight.setBox(new Rectangle(100, 100, 200, 30));
    highlight.setBackgroundColor(0x80FFFF00);
    
    // Add explanatory note
    AreaAnnotation note = new AreaAnnotation();
    note.setBox(new Rectangle(320, 95, 150, 40));
    note.setBackgroundColor(0x80ADD8E6);
    note.setMessage("See reference document #123");
    
    annotator.add(highlight);
    annotator.add(note);
}
```
```java
// Add to your application properties or logging configuration
java.util.logging.Logger.getLogger("com.groupdocs").setLevel(Level.FINE);
```
```java
public boolean validateAnnotationParameters(Rectangle box, int color) {
    if (box.getWidth() <= 0 || box.getHeight() <= 0) {
        System.err.println("Invalid annotation dimensions");
        return false;
    }
    
    if (box.getX() < 0 || box.getY() < 0) {
        System.err.println("Annotation position cannot be negative");
        return false;
    }
    
    return true;
}
```
```java
try (Annotator annotator = new Annotator("document.pdf")) {
    annotator.add(annotation1);
    annotator.add(annotation2);
    annotator.add(annotation3);
    annotator.save("output.pdf"); // All annotations applied at once
}
```
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("protected.pdf", loadOptions);
```
```java
try (Annotator annotator = new Annotator("annotated.pdf")) {
    List<AnnotationInfo> annotations = annotator.get(AnnotationType.Area);
    for (AnnotationInfo annotation : annotations) {
        // Modify properties as needed
        annotation.setMessage("Updated comment");
    }
    annotator.update(annotations);
    annotator.save("updated.pdf");
}
```
```java
@Service
public class AnnotationService {
    public CompletableFuture<String> annotateAsync(String inputPath) {
        return CompletableFuture.supplyAsync(() -> {
            try (Annotator annotator = new Annotator(inputPath)) {
                // Process annotations
                return processDocument(annotator);
            }
        });
    }
}
```
```java
@Service
public class DocumentAnnotationService {
    
    public void annotateDocument(MultipartFile file, List<AnnotationRequest> requests) {
        try (InputStream inputStream = file.getInputStream();
             Annotator annotator = new Annotator(inputStream)) {
            
            // Process annotation requests
            requests.forEach(request -> addAnnotation(annotator, request));
            annotator.save("output.pdf");
        }
    }
}
```

## Tutoriels associés

- [Créer des surlignages PDF Java : guide complet avec GroupDocs Annotation](/annotation/java/annotation-management/)
- [Modifier les annotations PDF Java – Tutoriel complet GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annoter des PDF depuis des URLs GroupDocs Java](/annotation/java/annotation-management/annotate-pdfs-from-urls-groupdocs-java/)
