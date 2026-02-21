---
categories:
- Java Development
date: '2026-02-21'
description: Apprenez comment ajouter une flèche à un PDF en utilisant GroupDocs.Annotation
  pour Java. Tutoriel étape par étape avec code, meilleures pratiques et dépannage.
keywords: Java PDF arrow annotations, GroupDocs annotation tutorial, PDF annotation
  Java library, Java document annotation, PDF collaboration tools Java
lastmod: '2026-02-21'
linktitle: Java PDF Arrow Annotations Guide
tags:
- pdf-annotations
- java-tutorial
- document-processing
- groupdocs
title: Comment ajouter une flèche à un PDF avec Java – Tutoriel complet et meilleures
  pratiques
type: docs
url: /fr/java/graphical-annotations/add-arrow-annotations-java-groupdocs/
weight: 1
---

# Annotations de flèches PDF Java - Tutoriel complet et meilleures pratiques (2025)

## Introduction

Vous avez déjà eu du mal à amener votre équipe à se concentrer sur des sections spécifiques d'un document PDF lors des revues ? Vous n'êtes pas seul. Que vous gériez de la documentation technique, des contrats juridiques ou des spécifications de projet, signaler les zones exactes à discuter peut être frustrant sans les bons outils.

**Voici la solution** : les annotations de flèches PDF Java en utilisant l'API GroupDocs.Annotation. Cette approche puissante vous permet d'ajouter programmétiquement **add arrow to pdf** aux fichiers, rendant la collaboration fluide et professionnelle.

Dans ce guide complet, vous découvrirez comment implémenter des annotations de flèches qui fonctionnent réellement en environnement de production. Nous couvrirons tout, de la configuration de base à la personnalisation avancée, ainsi que des scénarios réels que vous rencontrerez (et comment les gérer).

**Ce qui rend ce tutoriel différent** ? Vous bénéficierez d'aperçus pratiques d'une personne qui l'a implémenté dans des applications d'entreprise, y compris les pièges que la documentation ne mentionne pas.

## Réponses rapides
- **Quelle bibliothèque me permet d'add arrow to pdf en Java ?** GroupDocs.Annotation for Java.
- **Ai-je besoin d'une licence pour la production ?** Oui, une licence commerciale supprime les filigranes.
- **Quelle version de Java est recommandée ?** JDK 11 offre les meilleures performances.
- **Puis-je ajouter plusieurs flèches dans un même document ?** Absolument – il suffit de créer plusieurs objets ArrowAnnotation.
- **Le traitement par lots est-il pris en charge ?** Oui, traitez les documents dans des boucles et libérez les objets Annotator.

## Qu'est-ce que add arrow to pdf ?

Ajouter une annotation de flèche signifie dessiner programmétiquement un marqueur directionnel sur une page PDF. Cela aide les relecteurs à signaler des sections, mettre en évidence des problèmes ou guider les lecteurs à travers un flux de travail sans modifier manuellement le fichier.

## Pourquoi choisir GroupDocs.Annotation pour les annotations de flèches PDF Java ?

Avant de plonger dans le code, abordons l'éléphant dans la pièce : pourquoi utiliser GroupDocs alors qu'il existe d'autres bibliothèques d'annotation PDF disponibles ?

**La comparaison honnête :**

- **iText** : Excellent pour les annotations de base, mais la personnalisation des flèches est limitée  
- **PDFBox** : Gratuit et performant, mais nécessite plus de code boilerplate  
- **GroupDocs.Annotation** : Le meilleur équilibre entre fonctionnalités et facilité d'utilisation (bien que ce soit commercial)

**GroupDocs excelle lorsque vous avez besoin de :**

- Plusieurs types d'annotation dans un même projet  
- Support et documentation de niveau entreprise  
- Implémentation rapide avec un minimum de code  
- Fonctionnalités de collaboration intégrées (comme les réponses)

**Avertissement** : Ce n'est pas gratuit. Mais si vous construisez une application commerciale où le time‑to‑market est crucial, l'investissement se rembourse généralement grâce à la réduction du temps de développement.

## Prérequis - Ce dont vous avez réellement besoin

Soyez pratiques sur ce dont vous avez besoin avant de commencer. J'ai vu trop de développeurs se lancer sans configuration adéquate et perdre des heures sur des problèmes de configuration.

### Bibliothèques et dépendances requises

Tout d'abord, vous devez ajouter GroupDocs.Annotation à votre projet Maven. Voici la configuration qui fonctionne réellement (je l'ai testée sur plusieurs projets) :

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

**Astuce** : Vérifiez toujours la dernière version sur leur page de releases. La version 25.2 est actuelle à la date de rédaction, mais les versions plus récentes incluent souvent d'importantes corrections de bugs.

### Configuration de l'environnement qui ne causera pas de maux de tête

Voici ce dont vous avez besoin pour une expérience de développement fluide :

- **JDK 8 ou supérieur** (je recommande JDK 11 pour de meilleures performances)  
- **Maven 3.6+** (les versions plus anciennes peuvent parfois rencontrer des problèmes de résolution des dépendances)  
- **IDE** : IntelliJ IDEA ou Eclipse (VS Code fonctionne aussi, mais le débogage est plus facile avec des IDE Java dédiés)  
- **Mémoire** : Assurez‑vous que votre JVM dispose d'au moins 2 Go d'espace heap pour le traitement de gros PDF

### Prérequis de connaissances (Soyez honnête avec vous-même)

Vous devriez être à l'aise avec :

- La programmation Java de base (collections, gestion des exceptions)  
- La gestion des dépendances Maven  
- Les opérations d'E/S de fichiers en Java

Si vous êtes novice sur l'un de ces points, ce n'est pas grave – prévoyez simplement de passer du temps supplémentaire sur ces aspects.

## Configurer GroupDocs.Annotation - La bonne façon

Voici comment configurer correctement GroupDocs.Annotation, y compris les étapes que la documentation omet souvent.

### Étape 1 : Configuration Maven (avec dépannage)

Ajoutez le dépôt et la dépendance ci‑dessus. Si vous rencontrez des problèmes de résolution des dépendances (ce qui arrive parfois), essayez d'ajouter ceci à votre `pom.xml` :

```xml
<properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
</properties>
```

### Étape 2 : Configuration de la licence (critique pour la production)

Pour le développement et les tests :

```java
// For evaluation purposes
License license = new License();
// license.setLicense("path/to/license.lic"); // Comment this out for trial
```

**Vérification de la réalité** : La version d'essai ajoute des filigranes à votre sortie. Pour la production, vous aurez besoin d'une licence appropriée de [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Étape 3 : Modèle d'initialisation de base

Utilisez toujours ce modèle pour initialiser l'annotateur :

```java
Annotator annotator = null;
try {
    annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
    // Your annotation code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

**Pourquoi le bloc try‑finally ?** Faites‑moi confiance – les objets GroupDocs doivent être correctement libérés pour éviter les fuites de mémoire, surtout lors du traitement de plusieurs documents.

## Guide complet d'implémentation - De zéro à la production

Construisons une implémentation d'annotation de flèche réaliste que vous pouvez réellement utiliser en production.

### Comprendre les annotations de flèches dans le contexte

Les annotations de flèches ne sont pas seulement décoratives – ce sont des outils de communication. Dans les flux de travail de documents, elles servent généralement à ces fins :

1. **Retour de révision** – « Cette section nécessite une révision »  
2. **Lien de référence** – « Voir le contenu associé ici »  
3. **Guidage du processus** – « Commencez votre révision à partir de ce point »  
4. **Mise en évidence d'un problème** – « Problème identifié dans cette zone »

Comprendre le contexte vous aide à concevoir de meilleurs systèmes d'annotation.

### Étape 1 : Construire des réponses d'annotation (la méthode intelligente)

Les réponses rendent vos annotations interactives. Voici comment créer des réponses pertinentes :

```java
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

**Bonne pratique** : Incluez les informations utilisateur dans les réponses pour un meilleur suivi de la collaboration. En production, vous les récupérerez généralement depuis votre système de gestion des utilisateurs.

### Étape 2 : Créer l'annotation de flèche (avec considérations réelles)

Voici l'implémentation principale avec des explications pour chaque paramètre :

```java
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100)); // Position and size
arrow.setCreatedOn(Calendar.getInstance().getTime()); // Creation time
arrow.setMessage("This is an arrow annotation"); // Annotation message
arrow.setOpacity(0.7); // Opacity level
arrow.setPageNumber(0); // Page number
arrow.setPenColor(65535); // ARGB pen color
arrow.setPenStyle(PenStyle.DOT); // Pen style
arrow.setPenWidth((byte) 3); // Arrow line width
arrow.setReplies(replies); // Attach replies
```

**Décomposons les parties complexes :**

- **Coordonnées du rectangle** : (x, y, largeur, hauteur) où x,y est le coin supérieur gauche  
- **PenColor** : Utilise le format ARGB. 65535 correspond à un bleu vif. Utilisez des convertisseurs de couleur en ligne pour des couleurs personnalisées  
- **Options PenStyle** : DOT, DASH, SOLID, DASHDOT, DASHDOTDOT  
- **Opacité** : 0,0 (transparent) à 1,0 (opaque). 0,7 est généralement parfait pour la visibilité sans être envahissant  

### Étape 3 : Ajout et sauvegarde (avec gestion des erreurs)

Voici la méthode prête pour la production afin d'ajouter des annotations :

```java
try {
    annotator.add(arrow);
    annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
    System.out.println("Arrow annotation added successfully!");
} catch (Exception e) {
    System.err.println("Failed to add annotation: " + e.getMessage());
    // Log the full stack trace in production
    e.printStackTrace();
} finally {
    annotator.dispose();
}
```

**Point critique** : Gérez toujours les exceptions lors des opérations sur les fichiers. Les PDF peuvent être corrompus, les chemins peuvent être invalides et les permissions peuvent poser problème.

## Pièges courants et comment les éviter

Après avoir implémenté cela dans plusieurs projets, voici les problèmes que vous rencontrerez le plus souvent :

### Problème 1 : Les coordonnées ne correspondent pas à la position attendue

**Problème** : Votre flèche apparaît au mauvais endroit sur le PDF.

**Solution** : Les systèmes de coordonnées PDF commencent en bas‑gauche, mais la plupart des bibliothèques d'annotation utilisent le coin supérieur gauche. GroupDocs gère cette conversion, mais vous pourriez devoir ajuster en fonction des caractéristiques de votre PDF.

```java
// If arrows appear in wrong positions, try adjusting the Y coordinate
int adjustedY = pageHeight - originalY - annotationHeight;
arrow.setBox(new Rectangle(x, adjustedY, width, height));
```

### Problème 2 : Les annotations disparaissent après la sauvegarde

**Problème** : Les annotations apparaissent pendant le traitement mais disparaissent dans le PDF final.

**Solution** : Il s'agit généralement d'un problème de licence. Assurez‑vous que votre licence est correctement chargée :

```java
License license = new License();
try {
    license.setLicense("GroupDocs.Annotation.lic");
} catch (Exception e) {
    System.out.println("License not found, using trial mode");
}
```

### Problème 3 : Fuites de mémoire lors du traitement par lots

**Problème** : L'application manque de mémoire lors du traitement de plusieurs documents.

**Solution** : Libérez toujours les objets annotator et envisagez de traiter les documents par lots :

```java
for (String documentPath : documentPaths) {
    Annotator annotator = null;
    try {
        annotator = new Annotator(documentPath);
        // Process document
    } finally {
        if (annotator != null) {
            annotator.dispose();
        }
    }
    
    // Force garbage collection every 10 documents
    if (processedCount % 10 == 0) {
        System.gc();
    }
}
```

## Techniques de personnalisation avancées

### Positionnement dynamique des flèches

Pour les applications interactives, vous pourriez devoir positionner les flèches en fonction de l'entrée utilisateur :

```java
public ArrowAnnotation createArrowAt(int x, int y, String message) {
    ArrowAnnotation arrow = new ArrowAnnotation();
    
    // Create arrow pointing to specific coordinates
    int arrowLength = 50;
    arrow.setBox(new Rectangle(x - arrowLength, y - arrowLength, arrowLength, arrowLength));
    arrow.setMessage(message);
    arrow.setOpacity(0.8);
    arrow.setPenColor(0xFF0000); // Red color
    arrow.setPenStyle(PenStyle.SOLID);
    arrow.setPenWidth((byte) 2);
    
    return arrow;
}
```

### Styliser les flèches pour différents cas d'utilisation

```java
// Error highlighting (red, thick, solid)
public ArrowAnnotation createErrorArrow() {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setPenColor(0xFF0000); // Red
    arrow.setPenWidth((byte) 4);
    arrow.setPenStyle(PenStyle.SOLID);
    arrow.setOpacity(0.9);
    return arrow;
}

// Suggestion arrows (blue, thin, dashed)
public ArrowAnnotation createSuggestionArrow() {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setPenColor(0x0000FF); // Blue
    arrow.setPenWidth((byte) 2);
    arrow.setPenStyle(PenStyle.DASH);
    arrow.setOpacity(0.6);
    return arrow;
}
```

## Scénarios d'implémentation réels

### Scénario 1 : Système de révision de documents

Vous construisez un système de révision de documents où plusieurs utilisateurs peuvent ajouter des commentaires :

```java
public class DocumentReviewSystem {
    public void addReviewArrow(String documentPath, int x, int y, 
                              String reviewComment, String reviewerName) {
        Annotator annotator = new Annotator(documentPath);
        
        ArrowAnnotation arrow = new ArrowAnnotation();
        arrow.setBox(new Rectangle(x, y, 50, 50));
        arrow.setMessage("Review by " + reviewerName);
        
        // Add reviewer's comment as reply
        Reply review = new Reply();
        review.setComment(reviewComment);
        review.setUser(new User(reviewerName));
        review.setRepliedOn(new Date());
        
        arrow.setReplies(Arrays.asList(review));
        
        annotator.add(arrow);
        annotator.save(documentPath.replace(".pdf", "_reviewed.pdf"));
        annotator.dispose();
    }
}
```

### Scénario 2 : Détection automatisée des problèmes

Intégration avec des outils d'analyse pour mettre automatiquement en évidence les problèmes potentiels :

```java
public void highlightDetectedIssues(String documentPath, List<Issue> issues) {
    Annotator annotator = new Annotator(documentPath);
    
    for (Issue issue : issues) {
        ArrowAnnotation arrow = createArrowForIssue(issue);
        annotator.add(arrow);
    }
    
    annotator.save(documentPath.replace(".pdf", "_issues_highlighted.pdf"));
    annotator.dispose();
}

private ArrowAnnotation createArrowForIssue(Issue issue) {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setBox(new Rectangle(issue.getX(), issue.getY(), 40, 40));
    arrow.setMessage("Issue detected: " + issue.getType());
    
    // Color‑code by severity
    switch (issue.getSeverity()) {
        case HIGH:
            arrow.setPenColor(0xFF0000); // Red
            break;
        case MEDIUM:
            arrow.setPenColor(0xFFA500); // Orange
            break;
        case LOW:
            arrow.setPenColor(0xFFFF00); // Yellow
            break;
    }
    
    return arrow;
}
```

## Conseils d'optimisation des performances

### Meilleures pratiques de gestion de la mémoire

Lors du traitement de gros documents ou de plusieurs fichiers :

1. **Utilisez le modèle try‑with‑resources** (si votre version le supporte) :

```java
try (Annotator annotator = new Annotator("document.pdf")) {
    // Your annotation code
} // Automatically disposed
```

2. **Traitez par lots** :

```java
public void processBatch(List<String> documents, int batchSize) {
    for (int i = 0; i < documents.size(); i += batchSize) {
        List<String> batch = documents.subList(i, 
            Math.min(i + batchSize, documents.size()));
        
        processBatchInternal(batch);
        
        // Allow GC between batches
        System.gc();
        Thread.sleep(100);
    }
}
```

3. **Surveillez l'utilisation de la mémoire** :

```java
Runtime runtime = Runtime.getRuntime();
long memoryBefore = runtime.totalMemory() - runtime.freeMemory();

// Your annotation processing

long memoryAfter = runtime.totalMemory() - runtime.freeMemory();
System.out.println("Memory used: " + (memoryAfter - memoryBefore) + " bytes");
```

### Considérations de performance CPU

- Évitez la création d'objets inutiles dans les boucles  
- Réutilisez les objets couleur et style lorsque c'est possible  
- Envisagez le traitement parallèle pour les documents indépendants (mais surveillez l'utilisation de la mémoire)

## Guide de dépannage - Solutions aux problèmes réels

### Problème : Annotations non visibles dans Adobe Reader

**Symptômes** : Les annotations s'affichent dans votre application mais pas dans Adobe Reader ou d'autres visionneuses PDF.

**Solutions** :

1. Assurez‑vous d'enregistrer avec les normes PDF appropriées :

```java
// Try different save options if available
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationType(AnnotationType.All);
annotator.save(outputPath, saveOptions);
```

2. Vérifiez la compatibilité de la version du PDF – les versions plus anciennes du PDF peuvent ne pas prendre en charge toutes les fonctionnalités d'annotation.

### Problème : Mauvaises performances avec de gros PDF

**Symptômes** : L'application devient lente ou ne répond plus avec de gros documents.

**Solutions** :

1. **Traitez les pages individuellement** au lieu de l'ensemble du document :

```java
// Process specific pages
LoadOptions loadOptions = new LoadOptions();
loadOptions.setLoadCharts(false); // Skip charts if not needed
Annotator annotator = new Annotator(documentPath, loadOptions);
```

2. **Utilisez le streaming lorsque possible** pour les fichiers très volumineux.  

3. **Augmentez la taille du heap JVM** :

```bash
java -Xmx4g -jar your-application.jar
```

### Problème : Problèmes de rendu des couleurs

**Symptômes** : Les couleurs apparaissent différentes de ce qui était prévu dans le PDF final.

**Solution** : Utilisez les définitions d'espace couleur appropriées :

```java
// Use hex values for consistent colors
int red = 0xFFFF0000;    // ARGB format
int blue = 0xFF0000FF;
int green = 0xFF00FF00;

// Or convert from RGB
public int rgbToArgb(int r, int g, int b) {
    return (0xFF << 24) | (r << 16) | (g << 8) | b;
}
```

## Tester votre implémentation

### Tests unitaires des annotations de flèches

Voici une structure de test pratique :

```java
@Test
public void testArrowAnnotationCreation() {
    // Arrange
    String inputPath = "test-documents/sample.pdf";
    String outputPath = "test-output/annotated.pdf";
    
    // Act
    Annotator annotator = new Annotator(inputPath);
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setBox(new Rectangle(100, 100, 50, 50));
    arrow.setMessage("Test annotation");
    
    annotator.add(arrow);
    annotator.save(outputPath);
    annotator.dispose();
    
    // Assert
    assertTrue("Output file should exist", new File(outputPath).exists());
    
    // Verify annotation was added
    Annotator verifyAnnotator = new Annotator(outputPath);
    List<AnnotationInfo> annotations = verifyAnnotator.get();
    assertEquals("Should have one annotation", 1, annotations.size());
    verifyAnnotator.dispose();
}
```

### Tests d'intégration

Testez avec différents types et tailles de PDF pour vous assurer que votre implémentation fonctionne dans divers scénarios.

## Conclusion

Vous disposez maintenant d'une boîte à outils complète pour implémenter des annotations de flèches PDF Java avec GroupDocs.Annotation. Il ne s'agit pas seulement d'ajouter des flèches aux PDF – c'est construire des fonctionnalités de collaboration documentaire robustes qui fonctionnent réellement en production.

**Points clés de ce guide :**

- Gérez toujours correctement les ressources (utilisez des blocs try‑finally)  
- Testez avec différents types et tailles de PDF  
- Prenez en compte la gestion de la mémoire pour le traitement par lots  
- Implémentez une gestion appropriée des erreurs pour la production  
- Stylisez les annotations de manière appropriée à leur objectif  

**Vos prochaines étapes** : Commencez par un prototype simple en utilisant l'implémentation de base, puis ajoutez progressivement des fonctionnalités avancées comme le positionnement dynamique et le style personnalisé à mesure que vos exigences évoluent.

**Prêt à aller plus loin ?** Explorez d'autres fonctionnalités de GroupDocs.Annotation comme les annotations de texte, les annotations de zone et les filigranes. Les modèles que vous avez appris ici s'appliquent à tous les types d'annotation.

## Foire aux questions

**Q : Puis-je ajouter des annotations de flèches à des PDF protégés par mot de passe ?**  
R : Oui, mais vous devrez fournir le mot de passe lors de la création de l'Annotator :  
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("protected.pdf", loadOptions);
```

**Q : Comment traiter efficacement plusieurs documents par lots ?**  
R : Traitez les documents par petits lots et libérez correctement les ressources :  
```java
for (String doc : documents) {
    try (Annotator annotator = new Annotator(doc)) {
        // Add annotations
        annotator.save(doc.replace(".pdf", "_annotated.pdf"));
    }
    if (processedCount % 10 == 0) {
        System.gc(); // Encourage garbage collection
    }
}
```

**Q : Quel est le nombre maximal d'annotations par document ?**  
R : Il n'y a pas de limite stricte imposée par GroupDocs, mais les limites pratiques dépendent de la mémoire, des capacités du visualiseur PDF et des exigences de performance. Pour de grands nombres (1000+), appliquez les techniques d'optimisation des performances discutées précédemment.

**Q : Puis-je personnaliser les formes de flèches au-delà des options standard ?**  
R : GroupDocs.Annotation fournit des formes de flèches standard. Pour des formes personnalisées, vous pourriez devoir utiliser des annotations de zone, combiner plusieurs annotations simples, ou passer à une bibliothèque graphique plus spécialisée.

**Q : Comment gérer différents systèmes de coordonnées PDF ?**  
R : GroupDocs gère généralement la conversion des coordonnées automatiquement. Si vous rencontrez des problèmes :  
```java
// Get page info for coordinate calculations
PageInfo pageInfo = annotator.getDocument().getPages().get(pageNumber);
int pageHeight = pageInfo.getHeight();

// Adjust Y coordinate if needed
int adjustedY = pageHeight - originalY;
```

**Q : Quel est le coût de la licence pour une utilisation en production ?**  
R : GroupDocs propose différents modèles de licence (Développeur, Site, OEM). Consultez les tarifs actuels sur la [page de tarification de GroupDocs](https://purchase.groupdocs.com/buy).

**Q : Comment intégrer cela avec des applications Spring Boot ?**  
R : Créez une classe de service pour les opérations d'annotation :  
```java
@Service
public class AnnotationService {
    public void addArrowAnnotation(String inputPath, String outputPath, 
                                 int x, int y, String message) {
        try (Annotator annotator = new Annotator(inputPath)) {
            ArrowAnnotation arrow = new ArrowAnnotation();
            arrow.setBox(new Rectangle(x, y, 50, 50));
            arrow.setMessage(message);
            
            annotator.add(arrow);
            annotator.save(outputPath);
        }
    }
}
```

**Q : Puis-je extraire les annotations de flèches existantes d'un PDF ?**  
R : Oui, utilisez la méthode `get()` pour récupérer les annotations existantes :  
```java
Annotator annotator = new Annotator("document.pdf");
List<AnnotationInfo> annotations = annotator.get();

for (AnnotationInfo annotation : annotations) {
    if (annotation instanceof ArrowAnnotation) {
        ArrowAnnotation arrow = (ArrowAnnotation) annotation;
        System.out.println("Arrow message: " + arrow.getMessage());
    }
}
```

## Ressources supplémentaires

- **Documentation** : [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- **Référence API** : [Complete API Reference](https://reference.groupdocs.com/annotation/java/)  
- **Télécharger la dernière version** : [GroupDocs Releases](https://releases.groupdocs.com/annotation/java/)  
- **Acheter une licence** : [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Essai gratuit** : [Download Free Trial](https://releases.groupdocs.com/annotation/java/)  
- **Licence temporaire** : [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support communautaire** : [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)  
- **Support professionnel** : Disponible avec les licences payantes pour une assistance prioritaire  

---

**Dernière mise à jour :** 2026-02-21  
**Testé avec :** GroupDocs.Annotation 25.2 for Java  
**Auteur :** GroupDocs