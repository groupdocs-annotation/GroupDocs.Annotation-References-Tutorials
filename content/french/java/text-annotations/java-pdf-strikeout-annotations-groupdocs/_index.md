---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Apprenez comment ajouter des annotations de texte barré aux PDF en Java
  avec GroupDocs. Ce tutoriel étape par étape couvre la configuration, le code, le
  dépannage et les conseils de performance.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Guide de texte barré PDF Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Comment ajouter des annotations de texte barré aux PDF en Java – Guide complet
  GroupDocs
type: docs
url: /fr/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Comment ajouter des annotations de texte barré aux PDF en Java

Vous avez déjà eu besoin de barrer du texte dans un PDF de manière programmatique ? Que vous construisiez un système de révision de documents, créiez un flux de travail d'édition, ou simplement ayez besoin de marquer du texte pour suppression, les annotations **how to add strikeout** en Java sont une compétence pratique qui fait gagner du temps et réduit les efforts manuels. Dans ce guide complet, vous découvrirez tout ce qu’il faut savoir pour implémenter des annotations de texte barré avec GroupDocs.Annotation pour Java, de la configuration du projet à l’optimisation des performances.

## Réponses rapides
- **Quelle est la première étape ?** Ajoutez la dépendance Maven GroupDocs.Annotation à votre `pom.xml`.  
- **Comment créer un texte barré ?** Instanciez `Annotator`, définissez `StrikeoutAnnotation` avec des points, définissez la couleur/l’opacité, puis appelez `addAnnotation`.  
- **Puis-je ajouter des commentaires ?** Oui, attachez un objet `Comment` à l'annotation pour la collaboration.  
- **Que faire si l'annotation est mal placée ?** Ajustez les points de coordonnées ; le PDF utilise un système d’origine en bas à gauche.  
- **Y a-t-il une limite de taille de document ?** GroupDocs traite des PDF de plusieurs centaines de pages sans charger le fichier complet en mémoire.

## Qu’est‑ce que “how to add strikeout” dans l’annotation PDF ?
L’expression “how to add strikeout” désigne le processus de dessin programmatique d’une ligne à travers le texte sélectionné dans un document PDF à l’aide d’une API d’annotation. En Java, GroupDocs.Annotation fournit une classe dédiée `StrikeoutAnnotation` qui gère le rendu, le style et la persistance des marques de texte barré.

## Pourquoi utiliser GroupDocs pour le texte barré PDF en Java ?
GroupDocs.Annotation prend en charge **plus de 50 formats d’entrée et de sortie** — y compris PDF, DOCX, XLSX, PPTX, HTML et les types d’image courants — vous n’êtes donc pas limité à un seul type de fichier. Il fournit une API de haut niveau qui abstrait la structure PDF bas‑niveau, gérant automatiquement l’intégration des polices, le rendu des pages et la persistance des annotations, ce qui permet aux développeurs de se concentrer sur la logique métier plutôt que sur les détails internes du PDF.

## Pré-requis et exigences de configuration

### Exigences essentielles
- **Java Development Kit (JDK) :** Version 8 ou supérieure (JDK 11+ recommandé pour une collecte des déchets optimale).  
- **GroupDocs.Annotation for Java :** Intégré via Maven (voir l’extrait Maven ci‑dessous).  
- **IDE :** IntelliJ IDEA, Eclipse ou tout éditeur compatible Java.

### Configuration des dépendances Maven
Ajoutez le bloc de dépendance suivant à votre `pom.xml` :

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

**Pro Tip :** Vérifiez toujours la dernière version sur la page de publication de GroupDocs ; les nouvelles versions ajoutent des fonctionnalités et corrigent des bugs pouvant affecter le rendu des annotations.

### Obtenir votre licence
GroupDocs.Annotation nécessite une licence valide pour une utilisation en production. Vous avez trois options :

- **Free Trial :** Téléchargez depuis [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License :** Demandez une clé de développement sur [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Full License :** Achetez pour la production sur [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

L’essai ajoute un filigrane discret, planifiez donc vos tests en conséquence.

## Guide d’implémentation étape par étape

### Comprendre les composants de base
Les définitions suivantes vous donnent un modèle mental rapide :

- **Annotator :** L’objet API principal qui charge un PDF et expose les méthodes d’annotation.  
- **StrikeoutAnnotation :** Représente la ligne de texte barré visuelle et ses options de style.  
- **Point :** Une paire de coordonnées (X, Y) qui indique à la bibliothèque où la ligne commence et se termine.  
- **Comment :** Texte optionnel attaché à une annotation pour la collaboration.

### Étape 1 : Configuration des chemins de fichiers
Définissez les emplacements de votre PDF source et du fichier de destination. Des chemins incorrects sont une source fréquente d’erreurs “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert :** Assurez‑vous que le répertoire de sortie existe et est accessible en écriture ; GroupDocs ne créera pas automatiquement les dossiers manquants.

### Étape 2 : Initialiser l’Annotator
Créez une instance `Annotator` qui charge le PDF en mémoire.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here ?** La bibliothèque analyse la structure du PDF, construit une représentation interne et prépare un canevas d’annotation page par page. Pour des fichiers de plusieurs centaines de pages, cette étape peut prendre quelques secondes.

### Étape 3 : Ajout de commentaires (Optionnel mais recommandé)
`Comment` est une classe qui représente une note textuelle attachée à une annotation, permettant aux collaborateurs d’expliquer la raison du texte barré.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip :** Utilisez les commentaires pour expliquer pourquoi le texte est supprimé — cela est particulièrement utile dans les flux de travail de révision juridique ou éditoriale.

### Étape 4 : Définir les coordonnées de l’annotation
Les objets `Point` stockent des paires de coordonnées X‑Y qui définissent l’emplacement exact d’une annotation sur une page PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained :** Les coordonnées PDF commencent au coin inférieur gauche (0,0). L’exemple crée une ligne horizontale de (80,730) à (240,730) sur la page cible.

**Finding the Right Coordinates :** De nombreux développeurs créent une fonction d’aide qui convertit les pourcentages de largeur/hauteur de page en points absolus, rendant le code résilient aux différentes tailles de page.

### Étape 5 : Créer l’annotation de texte barré
`StrikeoutAnnotation` encapsule la ligne visuelle, ses propriétés de style telles que la couleur et l’opacité, ainsi que les métadonnées associées à une marque de texte barré.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values :** Le `fontColor` utilise des valeurs décimales RGB (par ex., 65535 pour un jaune vif). Utilisez un convertisseur en ligne si vous avez besoin de nuances spécifiques à votre marque.

**Opacity Recommendation :** Une opacité de `0.7` (70 %) offre un indice visuel clair tout en gardant le texte sous‑jacent lisible.

### Étape 6 : Appliquer l’annotation
`addAnnotation` est une méthode de `Annotator` qui enregistre l’annotation préparée dans le document afin qu’elle soit rendue et sauvegardée.

```java
annotator.add(strikeout);
```

### Étape 7 : Enregistrer et nettoyer
`dispose()` libère les ressources natives détenues par l’instance `Annotator`, empêchant les fuites de mémoire après la fin du traitement.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note :** Appeler `dispose()` libère les ressources natives et empêche les fuites de mémoire lors du traitement de lots de PDF.

## Problèmes courants et comment les résoudre

### Problème 1 : Erreurs “File Not Found”
**Symptoms :** Exception levée lors de la construction de `Annotator`.  
**Solution :** Vérifiez les chemins d’entrée et de sortie, et confirmez que l’application dispose des permissions de lecture/écriture.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problème 2 : Le texte barré apparaît au mauvais endroit
**Symptoms :** La ligne ne correspond pas au texte prévu.  
**Solution :** Rappelez‑vous que les coordonnées Y du PDF augmentent vers le haut. Utilisez un outil de débogage visuel ou imprimez les dimensions de la page pour affiner les points.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problème 3 : Annotation non visible
**Symptoms :** Aucun texte barré n’apparaît après l’enregistrement.  
**Possible Causes & Fixes :**  
- **Opacity too low :** Réglez temporairement l’opacité à `1.0` pour vérifier la visibilité.  
- **Color blending :** Utilisez une couleur à fort contraste comme le rouge (`255`).  
- **Incorrect page index :** Les numéros de page commencent à zéro ; assurez‑vous de cibler la bonne page.

### Problème 4 : Problèmes de mémoire avec les gros fichiers
**Symptoms :** `OutOfMemoryError` ou performances lentes.  
**Solutions :**  
- Traitez les documents par lots plus petits.  
- Utilisez l’API de streaming si disponible.  
- Appelez toujours `dispose()` après chaque document.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Applications et cas d’utilisation réels

### Révision de documents juridiques
Les cabinets d’avocats annotent les contrats avec des textes barrés pour indiquer les clauses supprimées tout en conservant une traçabilité.

### Édition d’articles académiques
Les professeurs utilisent les textes barrés pour suggérer des suppressions lors de la révision par les pairs, en gardant le texte original visible pour le contexte.

### Systèmes de gestion de contenu
Les plateformes de publication signalent automatiquement les sections violant les politiques avec des textes barrés avant la modération manuelle.

### Contrôle de version pour les documents
Les entreprises traitent les annotations de texte barré comme des “marqueurs de suppression” dans un flux de travail de contrôle de version centré sur les documents, similaire aux diff de code.

## Conseils d’optimisation des performances

### Stratégie de traitement par lots
Lors du traitement de nombreux PDF, réutilisez une seule instance `Annotator` lorsque cela est possible et traitez les fichiers dans des threads parallèles.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Bonnes pratiques de gestion de la mémoire
- Appelez `dispose()` sur chaque `Annotator`.  
- Limitez le nombre de chargements de documents simultanés pour éviter la pression sur le tas.  
- Surveillez l’utilisation de la mémoire JVM avec des outils comme VisualVM.

### Mise en cache des coordonnées
Si vous appliquez la même mise en page d’annotation sur plusieurs fichiers, mettez en cache les objets `Point` pour éviter les recomputations.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Options de personnalisation avancées

### Sélection dynamique de couleur
Choisissez les couleurs à l’exécution en fonction des règles métier (par ex., rouge pour les suppressions critiques, jaune pour les suppressions provisoires).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Textes barrés multi‑lignes
Créez une série de paires `Point` pour dessiner une ligne en zigzag qui traverse plusieurs lignes de texte.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Liste de contrôle de dépannage
1. **File Permissions :** Vérifiez l’accès en lecture/écriture.  
2. **Library Version :** Assurez‑vous d’utiliser une version prise en charge de GroupDocs.Annotation.  
3. **License Status :** Confirmez que le fichier de licence est correctement référencé.  
4. **PDF Compatibility :** Vérifiez que le PDF n’est pas corrompu et qu’il respecte les limites de taille prises en charge.  
5. **Coordinate Validation :** Assurez‑vous que tous les points se trouvent à l’intérieur des limites de la page.  
6. **Heap Space :** Augmentez le paramètre JVM `-Xmx` si vous traitez des fichiers très volumineux.

## FAQ

**Q : Puis‑je barrer du texte sur plusieurs lignes ?**  
A : Oui. Créez plusieurs objets `Point` qui tracent le chemin souhaité ; l’annotation suivra la polyligne fournie.

**Q : Que se passe‑t‑il si je spécifie des coordonnées en dehors des limites de la page ?**  
A : L’annotation sera découpée et pourra devenir invisible. Validez toujours les coordonnées par rapport à la largeur et à la hauteur de la page.

**Q : Puis‑je supprimer les annotations de texte barré après les avoir ajoutées ?**  
A : Absolument. Utilisez la méthode `removeAnnotation` avec l’ID de l’annotation ou filtrez par type pour les supprimer programmatique­ment.

**Q : Y a‑t‑il une limite au nombre d’annotations que je peux ajouter à un seul PDF ?**  
A : GroupDocs n’impose pas de plafond strict, mais les performances peuvent se dégrader après des milliers d’annotations. Envisagez la pagination ou le résumé des annotations pour des ensembles très volumineux.

**Q : Comment travailler avec des PDF protégés par mot de passe ?**  
A : Transmettez le mot de passe au constructeur `Annotator`. La bibliothèque déchiffrera le document en mémoire avant d’appliquer les annotations.

**Q : Comment gérer les PDF avec différentes tailles et orientations de page ?**  
A : Récupérez les dimensions de chaque page via `annotator.getPageInfo(pageNumber)` et calculez les coordonnées relatives à ces dimensions pour garantir un placement cohérent.

## Conclusion
Vous disposez maintenant d’une solution complète et prête pour la production d’annotations **how to add strikeout** aux PDF en Java avec GroupDocs.Annotation. En maîtrisant la gestion des chemins de fichiers, le calcul des coordonnées et la gestion des ressources, vous pouvez intégrer cette fonctionnalité dans des outils de révision de documents, des pipelines de contenu ou toute application Java nécessitant un retour visuel précis.

## Prochaines étapes
1. Clonez le projet d’exemple et exécutez‑le sur un PDF d’exemple.  
2. Expérimentez avec différentes couleurs, opacités et textes de commentaires.  
3. Intégrez le flux de travail d’annotation dans votre service de traitement de documents existant.  
4. Explorez les types d’annotation associés — surlignages, notes autocollantes et annotations de forme — pour élargir votre boîte à outils de manipulation PDF.  
Prêt pour plus ? Plongez dans la documentation officielle pour des informations API plus approfondies.

## Ressources supplémentaires

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Documentation générale des bibliothèques GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Référence API complète  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Détails méthode par méthode  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Gardez votre bibliothèque à jour  
- [Purchase License](https://purchase.groupdocs.com/buy) - Licence prête pour la production  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Évaluez avant d’acheter  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Test de développement  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Aide communautaire et support officiel  

---  

**Dernière mise à jour :** 2026-05-21  
**Testé avec :** GroupDocs.Annotation 23.12 for Java  
**Auteur :** GroupDocs  

## Tutoriels associés

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)