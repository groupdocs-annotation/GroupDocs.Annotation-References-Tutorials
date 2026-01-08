---
categories:
- Java Development
date: '2025-12-21'
description: Apprenez à créer des fichiers PDF Java propres et à annoter des PDF en
  Java à l'aide de GroupDocs.Annotation, avec des exemples de code complets et des
  conseils de dépannage.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Créer un PDF propre en Java : annotations soulignées avec GroupDocs'
type: docs
url: /fr/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Créer des PDF propres en Java : annotations soulignées avec GroupDocs

## Introduction

Vous avez des difficultés à gérer les documents et la collaboration dans vos applications Java ? Vous n'êtes pas seul. De nombreux développeurs rencontrent le défi de mettre en œuvre des fonctionnalités d'annotation de documents robustes qui fonctionnent de manière fiable sur différents formats de fichiers.

Dans ce guide, vous **créerez des PDF propres en Java** et apprendrez comment **annoter un PDF en Java** à l'aide de GroupDocs.Annotation. À la fin de ce tutoriel, vous saurez exactement comment ajouter des annotations soulignées avec des commentaires, supprimer les annotations existantes et intégrer ces fonctionnalités de façon fluide dans vos projets.

**Ce que vous maîtriserez dans ce guide :**
- Configurer GroupDocs.Annotation dans votre projet Java (de la bonne façon)  
- Ajouter des annotations soulignées avec des commentaires et un style personnalisés  
- Supprimer toutes les annotations pour créer des versions de documents propres  
- Résoudre les problèmes courants rencontrés par les développeurs  
- Optimiser les performances pour les applications en production  

Que vous construisiez un système de révision de documents, une plateforme éducative ou un outil d’édition collaborative, ce tutoriel vous couvre avec des exemples de code pratiques et testés.

## Réponses rapides
- **Comment ajouter une annotation soulignée ?** Utilisez `UnderlineAnnotation` et `annotator.add()` puis enregistrez le document.  
- **Comment créer un PDF propre en Java ?** Chargez le fichier annoté, définissez `AnnotationType.NONE` dans `SaveOptions`, puis enregistrez une nouvelle copie.  
- **Quelles bibliothèques sont requises ?** GroupDocs.Annotation v25.2 (ou plus récent) et son dépôt Maven.  
- **Faut‑il une licence pour la production ?** Oui — appliquez une licence GroupDocs valide pour éviter les filigranes.  
- **Puis‑je traiter plusieurs documents efficacement ?** Encapsulez chaque `Annotator` dans un bloc try‑with‑resources et libérez‑le après chaque fichier.

## Comment créer des PDF propres en Java
Créer un PDF propre en Java signifie générer une version du document **sans aucune annotation** tout en préservant le contenu original. Cela est utile pour la distribution finale, l’archivage ou lorsque vous devez partager une copie « propre » après un cycle de révision.

GroupDocs.Annotation rend cela simple : chargez le fichier annoté, configurez `SaveOptions` pour exclure tous les types d’annotation, puis enregistrez le résultat. Les étapes sont illustrées plus loin dans la section **Suppression des annotations**.

## Comment annoter un PDF en Java avec GroupDocs
GroupDocs.Annotation fournit une API riche pour **annoter un PDF en Java**. Elle prend en charge un large éventail de types d’annotation, y compris les surlignages, les tampons et les soulignements. Dans ce tutoriel, nous nous concentrons sur les annotations soulignées car elles sont couramment utilisées pour mettre en évidence du texte tout en permettant des commentaires en fil de discussion.

## Prérequis et configuration de l’environnement

### Ce dont vous avez besoin avant de commencer

**Exigences de l’environnement de développement :**
- Java Development Kit (JDK) 8 ou supérieur (JDK 11+ recommandé)  
- Maven 3.6+ ou Gradle 6.0+ pour la gestion des dépendances  
- IDE tel qu’IntelliJ IDEA, Eclipse ou VS Code avec extensions Java  
- Au moins 2 Go de RAM disponible (le traitement de documents peut être gourmand en mémoire)

**Prérequis de connaissances :**
Vous devez être à l’aise avec les concepts Java de base — initialisation d’objets, appels de méthodes et dépendances Maven. Une expérience préalable avec des bibliothèques tierces accélérera l’adoption.

**Documents de test :**
Préparez quelques PDF d’exemple. Les PDF basés sur du texte fonctionnent le mieux ; les images numérisées peuvent nécessiter une OCR avant l’annotation.

### Configuration Maven : ajouter GroupDocs à votre projet

Voici comment configurer correctement votre projet Maven (c’est souvent la première difficulté rencontrée) :

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

**Important :** La version 25.2 est la dernière version stable au moment de la rédaction. Vérifiez régulièrement le dépôt GroupDocs pour des versions plus récentes incluant des corrections de bugs et des améliorations de performances.

### Configuration de la licence (ne pas ignorer)

**Pour le développement/les tests :**  
Téléchargez l’essai gratuit depuis le site GroupDocs. L’essai comprend toutes les fonctionnalités mais ajoute un filigrane aux documents traités.

**Pour la production :**  
Achetez une licence et appliquez‑la au démarrage de l’application. Sans licence valide, les builds de production seront limités.

## Guide d’implémentation : ajouter des annotations soulignées

### Comprendre le flux de travail d’annotation

Avant de plonger dans le code, parcourons le flux de travail en quatre étapes qui se produit lorsque vous **annoter un PDF en Java** :

1. **Chargement du document** – `Annotator` lit le fichier en mémoire.  
2. **Création de l’annotation** – Définissez les propriétés telles que la position, le style et les commentaires.  
3. **Application de l’annotation** – La bibliothèque injecte l’annotation dans la structure du PDF.  
4. **Enregistrement du document** – Persistez le fichier modifié, éventuellement en conservant l’original.

Le processus est non destructif ; le fichier source reste intact sauf si vous l’écrasez.

### Étape 1 : initialiser l’Annotator et charger votre document

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Astuce :** Utilisez des chemins absolus pendant le développement pour éviter les erreurs « fichier introuvable ». En production, envisagez de charger les ressources depuis le classpath ou un bucket de stockage cloud.

### Étape 2 : créer des commentaires et des réponses (partie collaborative)

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

**Cas réel :** Les réviseurs peuvent discuter d’une clause spécifique en ajoutant des réponses en fil, gardant la conversation liée à l’annotation exacte.

### Étape 3 : définir les coordonnées de l’annotation (obtenir la bonne position)

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

**Système de coordonnées :**  
- Les points 1 et 2 définissent le bord supérieur du soulignement.  
- Les points 3 et 4 définissent le bord inférieur.  
- La différence en Y (730 vs 650) contrôle l’épaisseur.

### Étape 4 : créer et configurer l’annotation soulignée

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

**Conseils couleur & opacité :**  
- `FontColor` utilise le format ARGB ; `65535` (0x00FFFF) donne un jaune vif.  
- Pour du rouge, utilisez `16711680` (0xFF0000) ; pour du bleu, `255` (0x0000FF).  
- Des valeurs d’opacité entre 0,5 et 0,8 offrent une bonne lisibilité sans masquer le texte.

### Étape 5 : enregistrer votre document annoté

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Gestion de la mémoire :** L’appel `dispose()` libère les ressources natives et empêche les fuites de mémoire — crucial lors du traitement de nombreux fichiers en lot.

## Suppression des annotations : créer des versions de documents propres

Parfois, vous avez besoin d’une version du PDF **sans aucune annotation** — par exemple, lors de la remise du contrat final approuvé. GroupDocs simplifie cela.

### Comprendre les options de suppression d’annotation

Vous pouvez :
- Supprimer **toutes** les annotations (le cas le plus fréquent)  
- Supprimer des types spécifiques (par ex. uniquement les surlignages)  
- Supprimer les annotations par auteur ou par page  

### Suppression d’annotation étape par étape

**Étape 1 : charger le document précédemment annoté**

```java
Annotator annotator = new Annotator(outputPath);
```

**Étape 2 : configurer les options d’enregistrement pour une sortie propre**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Étape 3 : enregistrer la version propre**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Cela produit un **PDF propre en Java** qui ne contient aucun objet d’annotation, idéal pour la distribution finale.

## Problèmes courants et solutions

### Problème 1 : erreurs « Document introuvable »

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

### Problème 2 : les annotations apparaissent aux mauvais emplacements

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problème 3 : problèmes de mémoire avec de gros documents

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problème 4 : problèmes de licence en production

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

## Meilleures pratiques de performance pour les applications en production

### Stratégies de gestion de la mémoire

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

### Considérations de multithreading

GroupDocs.Annotation n’est **pas thread‑safe** par défaut. Si votre application traite des documents de façon concurrente :

- **Ne partagez jamais** une instance d’`Annotator` entre plusieurs threads.  
- **Synchronisez** l’accès aux fichiers ou utilisez un mécanisme de verrouillage.  
- Envisagez un **pool** d’objets `Annotator` si vous avez besoin d’un débit élevé.

### Stratégies de mise en cache

- Mettez en cache les modèles d’annotation fréquemment utilisés.  
- Réutilisez les collections `Point` pour des ensembles de coordonnées courants.  
- Gardez un **PDF modèle** en mémoire si vous devez annoter plusieurs fois le même document de base.

## Applications réelles et cas d’utilisation

### Systèmes de révision de documents

- **Révision juridique :** Soulignez les clauses du contrat et ajoutez des commentaires sur les risques.  
- **Audits de conformité :** Mettez en évidence les sections problématiques des états financiers.  
- **Évaluation académique :** Les professeurs soulignent les passages nécessitant clarification.

### Plateformes éducatives

- **Outils d’annotation pour étudiants :** Permettez aux apprenants de souligner les concepts clés dans les e‑books.  
- **Feedback des enseignants :** Fournissez des commentaires en ligne directement sur les devoirs soumis.

### Flux de travail d’assurance qualité

- **Revue de documentation technique :** Les ingénieurs soulignent les sections à mettre à jour.  
- **Procédures opérationnelles standard :** Les agents de sécurité mettent en avant les étapes critiques.

### Systèmes de gestion de contenu

- **Flux éditorial :** Les éditeurs soulignent le texte nécessitant une vérification des faits.  
- **Contrôle de version :** Suivez l’historique des annotations à travers les révisions de documents.

## Astuces avancées pour une implémentation professionnelle

### Styles d’annotation personnalisés

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Métadonnées d’annotation pour le suivi

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Intégration avec les systèmes de gestion des utilisateurs

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

## Dépannage des problèmes en production

### Surveillance des performances

Surveillez ces métriques en production :
- **Utilisation du tas** – assurez‑vous que `dispose()` est appelé.  
- **Temps de traitement par document** – journalisez les horodatages avant/après `annotator.save()`.  
- **Taux d’erreurs** – capturez les exceptions et catégorisez‑les.

### Pièges courants en production

- **Verrouillage de fichiers** – assurez‑vous que les fichiers téléchargés sont fermés avant l’annotation.  
- **Éditions concurrentes** – implémentez un verrouillage optimiste ou des vérifications de version.  
- **Fichiers volumineux (> 50 Mo)** – augmentez le timeout JVM et envisagez les API de streaming.

### Meilleures pratiques de gestion des erreurs

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

## Conclusion

Vous disposez maintenant de tout le nécessaire pour **créer des PDF propres en Java** et **annoter un PDF en Java** avec des annotations soulignées grâce à GroupDocs.Annotation. N’oubliez pas de :

- Gérer les ressources avec try‑with‑resources ou `dispose()` explicite.  
- Valider les coordonnées tôt pour éviter les soulignements mal placés.  
- Implémenter une gestion robuste des erreurs pour la stabilité en production.  
- Exploiter le style basé sur les rôles et les métadonnées pour s’adapter à votre flux de travail.

Etapes suivantes ? Essayez d’ajouter d’autres types d’annotation — surlignages, tampons ou remplacements de texte—pour construire une solution complète de révision de documents.

## FAQ

**Q : Comment annoter plusieurs zones de texte en une seule opération ?**  
R : Créez plusieurs objets `UnderlineAnnotation` avec des coordonnées différentes et ajoutez‑les séquentiellement avec `annotator.add()`.

**Q : Puis‑je annoter des images dans les documents PDF ?**  
R : Oui. Utilisez le même système de coordonnées, en veillant à ce que les points se situent à l’intérieur des limites de l’image.

**Q : Quels formats de fichier, en plus du PDF, GroupDocs.Annotation prend‑il en charge ?**  
R : Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) et les formats d’image tels que JPEG, PNG, TIFF.

**Q : Comment gérer des documents très volumineux sans épuiser la mémoire ?**  
R : Traitez les documents un à un, augmentez le tas JVM (`-Xmx`), et libérez toujours les instances `Annotator` rapidement.

**Q : Est‑il possible d’extraire les annotations existantes d’un document ?**  
R : Oui. Utilisez `annotator.get()` pour récupérer toutes les annotations, puis filtrez par type, auteur ou page selon vos besoins.

---

**Dernière mise à jour :** 2025-12-21  
**Testé avec :** GroupDocs.Annotation 25.2  
**Auteur :** GroupDocs  

---