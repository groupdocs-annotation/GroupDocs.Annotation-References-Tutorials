---
categories:
- Java Development
date: '2026-03-30'
description: Apprenez à ajouter une annotation de texte barré en Java avec GroupDocs.Annotation.
  Guide étape par étape avec des exemples de code, des conseils de dépannage et les
  meilleures pratiques pour le marquage de documents.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Ajouter une annotation de texte barré – Tutoriel Java avec GroupDocs
type: docs
url: /fr/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Ajouter une annotation de texte barré Java - Guide complet GroupDocs

Vous avez déjà été en train de regarder un document en pensant « Je dois barrer ce texte, mais je ne peux pas simplement prendre un stylo rouge » ? Vous n'êtes pas seul. Que vous construisiez un système de révision de documents, créiez un flux de travail d'édition, ou que vous ayez simplement besoin de marquer du texte pour suppression dans votre application Java, **add strikeout annotation java** est une compétence essentielle. Dans ce tutoriel, nous passerons en revue tout ce que vous devez savoir pour implémenter la fonctionnalité de texte barré qui fonctionne réellement en production.

## Réponses rapides
- **Quelle bibliothèque prend en charge les annotations de texte barré en Java ?** GroupDocs.Annotation for Java  
- **Quel mot‑clé principal devrais‑je cibler pour le SEO ?** add strikeout annotation java  
- **Ai‑je besoin d’une licence pour exécuter le code d’exemple ?** Un essai gratuit ou une licence temporaire fonctionne pour le développement ; une licence complète est requise pour la production.  
- **Puis‑je l’utiliser avec des fichiers PDF, DOCX et PPTX ?** Oui – GroupDocs.Annotation prend en charge tous les principaux formats de documents.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieure (JDK 11+ recommandé).

## Qu’est‑ce que add strikeout annotation java ?
Une annotation de texte barré trace une ligne à travers le texte sélectionné, indiquant visuellement que le contenu doit être supprimé ou ignoré. C’est une façon non destructive de suggérer des suppressions tout en conservant le texte original intact pour les pistes d’audit ou les revues collaboratives.

## Pourquoi utiliser des annotations de texte barré dans les applications Java ?
- **Flux de révision de documents** – les réviseurs peuvent signaler du texte indésirable sans modifier la source.  
- **Édition collaborative** – les membres de l’équipe voient les suppressions suggérées instantanément.  
- **Légal et conformité** – garder une piste d’audit claire des modifications.  
- **Migration de contenu** – marquer les sections obsolètes avant de déplacer le contenu entre les systèmes.  

## Prérequis et configuration de l’environnement
Vous aurez besoin de ce qui suit avant de plonger dans le code :

- **Java Development Kit (JDK)** 8+ (JDK 11+ recommandé)  
- **Maven ou Gradle** pour la gestion des dépendances  
- **IDE** – IntelliJ IDEA, Eclipse ou VS Code avec extensions Java  
- **Bibliothèque GroupDocs.Annotation** – nous utiliserons la version 25.2 dans les exemples  

*Bon à avoir :* connaissances de base des annotations Java et de la gestion des PDF.

## Configuration de GroupDocs.Annotation pour Java

### Configuration Maven qui fonctionne réellement
Add the repository and dependency to your `pom.xml` exactly as shown:

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

### Obtenir votre licence
GroupDocs propose plusieurs options de licence :

- **Essai gratuit** – parfait pour les tests (aucune carte de crédit requise)  
- **Licence temporaire** – idéale pour le développement et la mise en scène  
- **Licence complète** – requise pour une utilisation en production ; voir la [page d'achat](https://purchase.groupdocs.com/buy)

> **Conseil pro :** Commencez avec l’essai gratuit pour explorer l’API, puis passez à une licence temporaire lorsque vous êtes prêt à développer une fonctionnalité réelle.

### Configuration rapide de vérification
Run this minimal program to verify that the library loads correctly:

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

## Comment ajouter add strikeout annotation java

Voici une implémentation complète, prête pour la production, découpée en étapes claires.

### Étape 1 – Initialiser l’Annotateur
Create an `Annotator` instance that points to the source document:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Pourquoi c’est important :** Utiliser un chemin absolu ou correctement résolu empêche les exceptions « file not found ».

### Étape 2 – (Optionnel) Préparer les réponses aux commentaires
Adding replies makes the annotation collaborative:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Ces commentaires apparaissent lorsqu’un utilisateur survole le texte barré.

### Étape 3 – Définir la zone de texte barré
Specify the rectangle that encloses the text you want to cross out:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Astuce de coordonnées :** L’origine (0,0) est le coin supérieur gauche de la page ; X augmente vers la droite, Y augmente vers le bas. Utilisez un visualiseur PDF affichant les coordonnées pour affiner ces valeurs.

### Étape 4 – Configurer l’annotation de texte barré
Set appearance, page number, and attach the comments:

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

*Note couleur :* `65535` correspond au jaune en format entier RGB. Changez la valeur pour utiliser d’autres couleurs.

### Étape 5 – Appliquer l’annotation et enregistrer
Add the annotation to the document and write the output file:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Étape 6 – Nettoyer les ressources (Critique !)
Always dispose of the annotator to free native resources:

```java
if (annotator != null) {
    annotator.dispose();
}
```

En production, encapsulez l’utilisation dans un bloc try‑with‑resources ou une construction `try/finally`.

## Problèmes courants et comment les résoudre

| Problème | Symptôme | Solution |
|----------|----------|----------|
| **Fichier non trouvé** | `Annotator` lance une exception | Utilisez des chemins absolus, vérifiez les permissions de lecture, assurez‑vous qu’aucun autre processus ne verrouille le fichier |
| **Coordonnées incorrectes** | Le texte barré apparaît loin du texte prévu | Vérifiez à nouveau le système de coordonnées du visualiseur PDF ; ajustez les points en conséquence |
| **Annotation invisible** | Aucun texte barré visible après l’enregistrement | Augmentez `opacity` (par ex., `0.9`), vérifiez `pageNumber` (indexé à 0), assurez‑vous que les points forment un rectangle correct |
| **OutOfMemoryError** | L’application plante sur de gros PDF | Augmentez le tas JVM (`-Xmx2048m`), traitez les documents par lots, appelez toujours `dispose()` |

## Meilleures pratiques de performance pour la production

### Gestion de la mémoire
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

### Stratégie de traitement par lots
Lorsque vous devez annoter des dizaines ou des centaines de fichiers :

- Traitez 10‑20 documents par lot.  
- Enregistrez le succès/échec pour chaque fichier.  
- Ré‑initialisez le `Annotator` pour chaque document afin d’éviter les fuites de mémoire.  

### Conseils de mise en cache
- Mettez en cache les modèles de documents fréquemment utilisés.  
- Stockez les cartes de coordonnées pré‑calculées pour les mises en page standard.

## Cas d’utilisation réels

1. **Systèmes de révision de documents** – Les éditeurs suggèrent des suppressions sans modifier le contrat original.  
2. **Amendements juridiques** – Les avocats suivent les suppressions de clauses tout en préservant le libellé original pour l’audit.  
3. **Évaluation par les pairs académiques** – Les évaluateurs marquent les sections à supprimer et ajoutent des commentaires en ligne.  
4. **Migration de contenu** – Lors des migrations CMS, les textes barrés mettent en évidence les copies obsolètes qui doivent être remplacées.  

## Personnalisation avancée

### Style personnalisé
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Ajout de métadonnées
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Liste de contrôle de dépannage
- ✅ Pouvez‑vous ouvrir le fichier source manuellement ?  
- ✅ Toutes les dépendances GroupDocs sont‑elles présentes dans le classpath ?  
- ✅ Les points forment‑ils un rectangle valide ?  
- ✅ Le numéro de page est‑il correct (indexé à 0) ?  
- ✅ Y a‑t‑il suffisamment de mémoire du tas ?  
- ✅ Avez‑vous la permission d’écriture pour le dossier de sortie ?  
- ✅ Le format du document est‑il pris en charge (PDF, DOCX, PPTX, etc.) ?  

## Questions fréquemment posées

**Q : Puis‑je utiliser GroupDocs.Annotation dans un service Spring Boot ?**  
R : Oui. Ajoutez la dépendance Maven, injectez une classe de service qui crée le `Annotator`, et gérez son cycle de vie avec les portées de bean de Spring.

**Q : Quels formats de documents prennent en charge les annotations de texte barré ?**  
R : PDF, DOCX, PPTX, et de nombreux autres formats pris en charge par GroupDocs.Annotation. Le PDF offre la gestion de coordonnées la plus précise.

**Q : Comment gérer les documents avec des tailles de page variables ?**  
R : Récupérez les dimensions de la page via `annotator.getPageInfo(pageNumber)` et adaptez vos coordonnées en conséquence.

**Q : Est‑il possible de modifier ou de supprimer une annotation de texte barré existante ?**  
R : Absolument. Utilisez `annotator.getAnnotations(pageNumber)` pour récupérer, puis `annotator.update(updatedAnnotation)` ou `annotator.delete(annotationId)`.

**Q : Quel est l’impact sur les performances de l’ajout de nombreuses annotations ?**  
R : Ajouter des centaines d’annotations est généralement acceptable, mais surveillez l’utilisation de la mémoire. Pour des ensembles d’annotations très volumineux, envisagez de paginer la vue ou de charger les annotations à la demande.

## Conclusion
Vous disposez maintenant d’un guide complet, prêt pour la production, sur **add strikeout annotation java** avec GroupDocs.Annotation. Commencez avec l’exemple de vérification simple, puis passez à un traitement par lots, à un style personnalisé et à l’enrichissement des métadonnées. N’oubliez pas de tester les coordonnées avec soin, de gérer les ressources de façon responsable, et de choisir le modèle de licence adapté à votre environnement.

Prêt à explorer davantage ? Découvrez les autres types d’annotation — surlignage, note, image, flèche et filigrane—pour créer une suite de collaboration documentaire complète.

---

**Dernière mise à jour :** 2026-03-30  
**Testé avec :** GroupDocs.Annotation 25.2 for Java  
**Auteur :** GroupDocs  

**Ressources supplémentaires**

- [Documentation GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Guide de référence API](https://reference.groupdocs.com/annotation/java/)
- [Télécharger la dernière version](https://releases.groupdocs.com/annotation/java/)
- [Acheter une licence complète](https://purchase.groupdocs.com/buy)
- [Commencer un essai gratuit](https://releases.groupdocs.com/annotation/java/)
- [Obtenir une licence temporaire](https://purchase.groupdocs.com/temporary-license/)
- [Forum de support communautaire](https://forum.groupdocs.com/c/annotation/)