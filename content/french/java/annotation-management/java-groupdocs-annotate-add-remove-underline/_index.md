---
date: '2026-10-16'
description: Apprenez à enregistrer un PDF sans annotations en Java, maîtrisez la
  gestion de la mémoire des PDF en Java, et ajoutez des annotations de soulignement
  avec GroupDocs.Annotation. Guide étape par étape.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Annotation de documents Java avec GroupDocs
og_description: Apprenez à enregistrer un PDF sans annotations en Java, maîtrisez
  la gestion de la mémoire des PDF en Java, et ajoutez des annotations de soulignement
  avec GroupDocs.Annotation. Guide étape par étape.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Comment enregistrer un PDF sans annotations en Java avec GroupDocs
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
title: Comment enregistrer un PDF sans annotations en Java avec GroupDocs
type: docs
url: /fr/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Comment enregistrer un PDF sans annotations en Java avec GroupDocs

Si vous devez **enregistrer un PDF sans annotations** tout en pouvant ajouter des notes de soulignement collaboratives, vous êtes au bon endroit. De nombreux développeurs Java ont du mal à conserver une version propre d’un document pour la distribution finale, surtout lorsque le même fichier est utilisé pour des revues itératives. Dans ce tutoriel, vous apprendrez à générer un PDF propre, à gérer la mémoire efficacement et à appliquer des annotations de soulignement avec des commentaires à l’aide de GroupDocs.Annotation. À la fin, vous comprendrez le flux de travail complet — du chargement d’un PDF à la production d’une copie finale sans filigrane — ainsi que des conseils de bonnes pratiques pour créer un **système de révision de documents Java** robuste.

## Réponses rapides
- **Comment ajouter une annotation de soulignement ?** Utilisez `UnderlineAnnotation` avec `annotator.add()` puis enregistrez le document.  
- **Comment enregistrer un PDF sans annotations ?** Chargez le fichier annoté, définissez `AnnotationType.NONE` dans `SaveOptions`, puis enregistrez une nouvelle copie.  
- **Quelles bibliothèques sont requises ?** GroupDocs.Annotation v25.2 (ou plus récent) et son dépôt Maven.  
- **Ai-je besoin d’une licence pour la production ?** Oui —appliquez une licence GroupDocs valide pour éviter les filigranes.  
- **Puis-je traiter plusieurs documents efficacement ?** Encapsulez chaque `Annotator` dans un bloc try‑with‑resources et libérez‑le après chaque fichier.

## Comment enregistrer un PDF sans annotations en Java ?

Chargez le PDF source avec un `Annotator`, configurez `SaveOptions` pour exclure tous les types d’annotation, puis appelez `save()` pour écrire une copie propre. Cette opération ne modifie pas le fichier original, vous conservez ainsi à la fois la version annotée pour les relecteurs et une version immaculée pour la distribution. Le processus utilise le streaming en interne, ce qui signifie que le document complet ne réside jamais entièrement en mémoire — crucial pour les PDF volumineux.

## `save pdf without annotations` désigne l’exportation d’un document PDF en supprimant tous les objets d’annotation (surlignages, commentaires, tampons, soulignements, etc.). Le fichier résultant ne contient que le contenu et la mise en page d’origine, ce qui le rend adapté au dépôt juridique, à la diffusion publique ou au stockage d’archives.

## Pourquoi créer des fichiers PDF propres dans un système de révision de documents Java ?

Une version propre élimine les marques des relecteurs, les commentaires et les surlignages, vous offrant un document soigné prêt pour les clients, les régulateurs ou la diffusion publique. Elle réduit également la taille du fichier jusqu’à 30 % en moyenne et empêche la divulgation accidentelle de notes internes — crucial pour les flux de travail juridiques et de conformité. GroupDocs.Annotation peut supprimer tous les objets d’annotation en une seule passe, prenant en charge les PDF jusqu’à 500 Mo sans charger le fichier complet en mémoire.

## Prérequis et configuration de l’environnement

### Exigences avant de commencer

**Exigences de l’environnement de développement**  
- Java Development Kit (JDK) 8 ou supérieur (JDK 11+ recommandé)  
- Maven 3.6+ ou Gradle 6.0+ pour la gestion des dépendances  
- IDE tel qu’IntelliJ IDEA, Eclipse ou VS Code avec extensions Java  
- Au moins 2 Go de RAM disponible (le traitement de documents peut être gourmand en mémoire)

**Pré‑requis de connaissances**  
Vous devez être à l’aise avec les concepts Java de base — initialisation d’objets, appels de méthodes et dépendances Maven. Une expérience préalable avec des bibliothèques tierces accélérera l’adoption.

**Documents de test**  
Préparez quelques PDF d’exemple. Les PDF basés sur du texte fonctionnent mieux ; les images numérisées peuvent nécessiter une OCR avant l’annotation.

### Configuration Maven : intégrer GroupDocs à votre projet

Ajoutez la dépendance suivante à votre `pom.xml`. Cette étape pose problème à de nombreux développeurs lors de leur première tentative car le groupId et l’artifactId doivent correspondre exactement.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Important :** La version 25.2 est la dernière version stable au moment de la rédaction. Vérifiez régulièrement le dépôt GroupDocs pour des versions plus récentes incluant des corrections de bugs et des améliorations de performance.

### Configuration de la licence (ne pas ignorer)

**Pour le développement/les tests** – Téléchargez l’essai gratuit depuis le site GroupDocs. L’essai inclut toutes les fonctionnalités mais ajoute un filigrane aux documents traités.

**Pour la production** – Achetez une licence et appliquez‑la lors du démarrage de l’application. Sans licence valide, les builds de production seront limités et filigranés.

## Guide d’implémentation : ajouter des annotations de soulignement

### Comprendre le flux de travail d’annotation

Avant de plonger dans le code, parcourons le flux de travail en quatre étapes qui se produit lorsque vous **annotate PDF in Java** :

1. **Chargement du document** – `Annotator` lit le fichier en mémoire.  
2. **Création de l’annotation** – Définissez les propriétés telles que la position, le style et les commentaires.  
3. **Application de l’annotation** – La bibliothèque injecte l’annotation dans la structure du PDF.  
4. **Enregistrement du document** – Persistez le fichier modifié, éventuellement en conservant l’original.

Le processus est non destructif ; le fichier source reste intact à moins que vous ne le remplaciez.

### Étape 1 : initialiser l’annotateur et charger votre document

`Annotator` est le point d’entrée principal de GroupDocs.Annotation pour charger et modifier des documents PDF. Il abstrait la gestion du système de fichiers, la gestion des flux et l’allocation des ressources natives.

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

**Conseil pro :** Utilisez des chemins absolus pendant le développement pour éviter les erreurs « file not found ». En production, envisagez de charger les ressources depuis le classpath ou un bucket de stockage cloud.

### Étape 2 : créer des commentaires et des réponses (la partie collaborative)

Les objets `Comment` représentent une discussion en fil attachée à une annotation. Chaque commentaire peut avoir un auteur, un horodatage et des réponses optionnelles, permettant une conversation complète autour d’une annotation spécifique.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Utilisation concrète :** Les relecteurs peuvent discuter d’une clause précise en ajoutant des réponses en fil, maintenant la conversation liée à l’annotation exacte.

### Étape 3 : définir les coordonnées de l’annotation (obtenir la bonne position)

`Point` définit une seule coordonnée dans l’espace PDF (mesurée en points, où 72 points = 1 pouce). Quatre points sont requis pour un soulignement : deux pour la ligne de départ et deux pour la ligne de fin.

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

**Système de coordonnées :**  
- Les points 1 & 2 définissent le bord supérieur du soulignement.  
- Les points 3 & 4 définissent le bord inférieur.  
- La différence en Y (730 vs 650) contrôle l’épaisseur.

### Étape 4 : créer et configurer l’annotation de soulignement

`UnderlineAnnotation` est la classe concrète qui représente un marquage de soulignement. Elle hérite de la classe de base `Annotation` et ajoute des propriétés spécifiques aux soulignements, telles que l’épaisseur de ligne et le style.

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

**Conseils couleur & opacité :**  
- `FontColor` utilise ARGB ; `65535` (0x00FFFF) donne un jaune vif.  
- Pour le rouge, utilisez `16711680` (0xFF0000) ; pour le bleu, `255` (0x0000FF).  
- Des valeurs d’opacité entre 0,5 et 0,8 offrent une bonne lisibilité sans masquer le texte.

### Étape 5 : enregistrer votre document annoté

`SaveOptions` vous permet de contrôler le format de sortie, d’inclure ou non les annotations et de gérer les métadonnées. Définir `AnnotationType.NONE` indique à la bibliothèque de supprimer tous les objets d’annotation, ce qui est la clé pour **save PDF without annotations**.

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

**Gestion de la mémoire :** L’appel `dispose()` libère les ressources natives et empêche les fuites de mémoire — crucial lors du traitement de nombreux fichiers en lot.

## Suppression des annotations : créer des versions de documents propres

Parfois, vous avez besoin d’une version du PDF **sans aucune annotation** — par exemple, lors de la remise du contrat final approuvé. GroupDocs rend cela simple.

### Comprendre les options de suppression d’annotation

Vous pouvez :  
- Supprimer **toutes** les annotations (le plus courant)  
- Supprimer des types spécifiques (par ex., uniquement les surlignages)  
- Supprimer les annotations par auteur ou par page  

### Suppression d’annotation étape par étape

**Étape 1 : charger le document précédemment annoté**

`Annotator` agit à nouveau comme chargeur ; il lira le fichier qui contient encore les objets d’annotation.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Étape 2 : configurer les options d’enregistrement pour une sortie propre**

`SaveOptions` fournit une API fluide pour spécifier qu’aucun type d’annotation ne doit être écrit dans le fichier de sortie.

```java
Annotator annotator = new Annotator(outputPath);
```

**Étape 3 : enregistrer la version propre**

L’appel `save()` avec les options configurées écrit un PDF qui ne contient que le contenu original.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Cela produit un fichier **PDF propre** qui ne contient aucun objet d’annotation, parfait pour la distribution finale.

## Problèmes courants et solutions

### Problème 1 : erreurs « Document not found »

Assurez‑vous que le chemin du fichier est correct et que l’application possède les permissions de lecture. Utiliser `Path.of()` avec des chemins absolus élimine la plupart des ambiguïtés.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problème 2 : les annotations apparaissent aux mauvais emplacements

L’origine des coordonnées PDF se trouve dans le coin inférieur gauche. Vérifiez que vos valeurs Y augmentent vers le haut et que vous tenez compte de la rotation de la page.

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

### Problème 3 : problèmes de mémoire avec de gros documents

GroupDocs.Annotation diffuse le contenu et ne charge jamais le fichier complet dans la mémoire du tas. Cependant, vous devez toujours appeler `dispose()` et envisager d’augmenter le tas JVM (`-Xmx`) pour les fichiers supérieurs à 200 Mo.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problème 4 : problèmes de licence en production

Si le fichier de licence est manquant ou que le chemin est incorrect, la bibliothèque revient en mode essai, ajoutant un filigrane à chaque page. Placez le fichier de licence à un emplacement présent sur le classpath et chargez‑le tôt dans le cycle de vie de votre application.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Meilleures pratiques de performance pour les applications de production

### Stratégies de gestion de la mémoire

GroupDocs.Annotation traite les PDF de manière streaming, ce qui lui permet de gérer des fichiers jusqu’à 500 Mo sans charger le document complet en mémoire. Suivez néanmoins ces directives :

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

### Considérations de threading

GroupDocs.Annotation n’est **pas thread‑safe** par défaut. Si votre application traite des documents de façon concurrente :

- **Ne partagez jamais** une instance `Annotator` entre les threads.  
- **Synchronisez** l’accès aux fichiers ou utilisez un mécanisme de verrouillage.  
- Envisagez un **pool** d’objets `Annotator` si vous avez besoin d’un débit élevé.

### Stratégies de mise en cache

- Mettez en cache les modèles d’annotation fréquemment utilisés.  
- Réutilisez les collections `Point` pour des ensembles de coordonnées courants.  
- Conservez un **PDF modèle** en mémoire si vous annotez à plusieurs reprises le même document de base.

## Meilleures pratiques de gestion de la mémoire Java PDF

Une utilisation efficace de la mémoire est essentielle lors du traitement de gros PDF ou du traitement de nombreux fichiers en lot. Voici quelques recommandations pratiques :

- **Utilisez try‑with‑resources** pour chaque `Annotator` afin de garantir la libération.  
- **Augmentez le tas JVM** (`-Xmx`) uniquement si nécessaire ; surveillez l’utilisation avec des outils de profilage.  
- **Traitez les documents séquentiellement** lorsque possible, en libérant la mémoire après chaque fichier.  
- **Évitez de charger le même PDF plusieurs fois** ; réutilisez le même flux si vous devez le lire à plusieurs reprises.

Appliquer ces pratiques aide votre application à rester réactive et prévient les plantages d’out‑of‑memory lors de charges d’annotation importantes.

## Applications réelles et cas d’utilisation

### Systèmes de révision de documents

- **Revue juridique :** Soulignez les clauses du contrat et ajoutez des commentaires sur les risques.  
- **Audits de conformité :** Surlignez les sections problématiques dans les états financiers.  
- **Évaluation académique par les pairs :** Les professeurs soulignent les passages nécessitant des éclaircissements.

### Plateformes éducatives

- **Outils d’annotation pour étudiants :** Permet aux apprenants de souligner les concepts clés dans les livres électroniques.  
- **Feedback des enseignants :** Fournissez des commentaires en ligne directement sur les devoirs soumis.

### Flux de travail d’assurance qualité

- **Revue de documentation technique :** Les ingénieurs soulignent les sections nécessitant des mises à jour.  
- **Procédures opérationnelles standard :** Les agents de sécurité mettent en évidence les étapes critiques.

### Systèmes de gestion de contenu

- **Flux éditorial :** Les éditeurs soulignent le texte nécessitant une vérification des faits.  
- **Contrôle de version :** Suivez l’historique des annotations à travers les révisions de documents.

## Astuces avancées pour une implémentation professionnelle

### Styles d’annotation personnalisés

Vous pouvez étendre l’apparence visuelle d’un soulignement en définissant des motifs de tirets, des terminaisons de ligne et des niveaux d’opacité personnalisés. Cela est utile lorsque vous devez différencier les rôles des relecteurs (par ex., juridique vs. ingénierie).

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

### Métadonnées d’annotation pour le suivi

Chaque annotation peut contenir un dictionnaire de métadonnées défini par l’utilisateur. Stockez des ID, des horodatages ou l’état du workflow pour les intégrer à des systèmes de suivi externes.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Intégration avec les systèmes de gestion des utilisateurs

Mappez la propriété `author` d’un `Comment` aux ID d’utilisateur de votre application. Cela permet une stylisation basée sur les rôles et la génération d’audits.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Dépannage des problèmes en production

### Surveillance des performances

Surveillez ces métriques en production :

- **Utilisation du tas** – assurez‑vous que `dispose()` est appelé.  
- **Temps de traitement par document** – journalisez les horodatages avant/après `annotator.save()`.  
- **Taux d’erreurs** – capturez les exceptions et catégorisez‑les.

### Pièges courants en production

- **Verrouillage de fichiers** – assurez‑vous que les fichiers téléchargés sont fermés avant l’annotation.  
- **Éditions concurrentes** – implémentez un verrouillage optimiste ou des vérifications de version.  
- **Fichiers volumineux (> 50 Mo)** – augmentez le délai d’attente JVM et envisagez les API de streaming.

### Meilleures pratiques de gestion des erreurs

Encapsulez tous les appels d’annotation dans des blocs try‑catch, journalisez la trace complète de la pile et relancez une `AnnotationException` personnalisée avec un message convivial. Ce modèle simplifie le débogage et fournit un retour clair aux consommateurs de l’API.

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

## Questions fréquemment posées

**Q : Comment annoter plusieurs zones de texte en une seule opération ?**  
R : Créez plusieurs objets `UnderlineAnnotation` avec des coordonnées différentes et ajoutez‑les séquentiellement en utilisant `annotator.add()`.

**Q : Puis‑je annoter des images dans des documents PDF ?**  
R : Oui. Utilisez le même système de coordonnées, en veillant à ce que les points se trouvent à l’intérieur des limites de l’image.

**Q : Quels formats de fichier, en plus du PDF, GroupDocs.Annotation prend‑il en charge ?**  
R : Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) et les formats d’image tels que JPEG, PNG, TIFF.

**Q : Comment gérer des documents très volumineux sans épuiser la mémoire ?**  
R : Traitez les documents un à un, augmentez le tas JVM (`-Xmx`) et libérez toujours rapidement les instances `Annotator`.

**Q : Est‑il possible d’extraire les annotations existantes d’un document ?**  
R : Oui. Utilisez `annotator.get()` pour récupérer toutes les annotations, puis filtrez par type, auteur ou page selon les besoins.

**Dernière mise à jour :** 2026-10-16  
**Testé avec :** GroupDocs.Annotation 25.2  
**Auteur :** GroupDocs  

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

## Tutoriels associés

- [Créer un PDF propre Java : annotations de soulignement avec GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Modifier les annotations PDF Java - Tutoriel complet GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annoter des PDF GroupDocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)