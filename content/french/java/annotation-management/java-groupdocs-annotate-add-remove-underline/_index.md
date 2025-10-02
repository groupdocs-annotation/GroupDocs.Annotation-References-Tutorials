---
"date": "2025-05-06"
"description": "Apprenez à ajouter et supprimer des annotations soulignées dans vos documents Java à l'aide de GroupDocs.Annotation. Améliorez la gestion de vos documents grâce à ce guide détaillé."
"title": "Ajouter et supprimer des annotations soulignées en Java à l'aide de GroupDocs - Un guide complet"
"url": "/fr/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Comment implémenter Java : ajouter et supprimer des annotations soulignées avec GroupDocs

## Introduction

Vous souhaitez améliorer votre système de gestion de documents en ajoutant ou supprimant des annotations par programmation ? Ce tutoriel vous guide dans l'utilisation de la puissante bibliothèque GroupDocs.Annotation en Java pour ajouter et supprimer des annotations soulignées dans des documents tels que des PDF.

**Ce que vous apprendrez :**
- Initialiser la classe Annotator.
- Ajoutez une annotation soulignée avec des commentaires à l’aide de GroupDocs.Annotation pour Java.
- Supprimer toutes les annotations d'un document.
- Configurez votre environnement pour utiliser GroupDocs.Annotation efficacement.

Voyons comment exploiter ces fonctionnalités dans vos projets. Assurez-vous de disposer des prérequis nécessaires avant de commencer.

## Prérequis

### Bibliothèques et dépendances requises
Pour suivre efficacement ce tutoriel, assurez-vous d'avoir :
- **GroupDocs.Annotation pour Java**:La version 25.2 ou ultérieure est recommandée.
- **Kit de développement Java (JDK)**:La version 8 ou supérieure est requise.

### Configuration requise pour l'environnement
Assurez-vous que votre environnement de développement comprend un IDE comme IntelliJ IDEA ou Eclipse et un outil de création tel que Maven.

### Prérequis en matière de connaissances
Une compréhension de base de la programmation Java, en particulier du travail avec des bibliothèques via Maven, sera bénéfique.

## Configuration de GroupDocs.Annotation pour Java

Pour commencer à utiliser GroupDocs.Annotation dans vos projets Java, suivez ces étapes de configuration :

**Configuration Maven :**
Ajoutez la configuration suivante à votre `pom.xml` fichier à télécharger et intégrer GroupDocs.Annotation.

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

**Acquisition de licence :**
Commencez par télécharger une version d'essai gratuite ou obtenir une licence temporaire auprès de GroupDocs pour explorer toutes les fonctionnalités de leur bibliothèque. Pour une utilisation en production, l'achat d'une licence est nécessaire.

## Guide de mise en œuvre

### Fonctionnalité 1 : Initialiser l'annotateur et ajouter une annotation soulignée

Cette section vous guide dans l'initialisation du `Annotator` classe et ajout d'une annotation de soulignement à votre document.

#### Aperçu
L'ajout d'annotations permet de mettre en évidence des parties spécifiques d'un document. Ici, nous nous concentrons sur le soulignement du texte avec des commentaires pour clarification ou retour.

#### Mise en œuvre étape par étape

**1. Initialiser l'annotateur**
Créer un `Annotator` objet et chargez votre fichier PDF.

```java
import com.groupdocs.annotation.Annotator;

// Chargez le document que vous souhaitez annoter
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Créez des commentaires avec des réponses**
Définissez les commentaires associés à l'annotation soulignée.

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

**3. Définir des points pour l'annotation soulignée**
Définissez des coordonnées pour déterminer où le soulignement doit apparaître.

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

**4. Créer et configurer l'annotation soulignée**
Créez l'annotation de soulignement et définissez ses propriétés telles que la couleur, l'opacité et les commentaires.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Jaune au format ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Enregistrez le document annoté**
Enregistrez vos modifications dans un nouveau fichier.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Conseils de dépannage
- Assurez-vous que toutes les coordonnées des points se trouvent dans les limites du document.
- Vérifiez que le `outputPath` le répertoire existe et est accessible en écriture.

### Fonctionnalité 2 : Enregistrer le document sans annotations

Cette section explique comment supprimer toutes les annotations d’un document précédemment annoté.

#### Aperçu
Vous devrez peut-être enregistrer une version propre de votre document sans aucune annotation à des fins de partage ou d'archivage.

#### Mise en œuvre étape par étape

**1. Initialiser Annotator avec le document annoté**
Chargez le document contenant des annotations existantes.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configurer les options d'enregistrement pour supprimer les annotations**
Spécifiez qu'aucune annotation ne doit être enregistrée dans le fichier de sortie.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Enregistrez le document sans annotations**
Définissez le chemin du document nettoyé et enregistrez-le.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Applications pratiques

Voici quelques scénarios réels dans lesquels ces fonctionnalités peuvent être bénéfiques :
1. **Examen des documents**: Mettre en évidence et commenter des sections d’un contrat ou d’un rapport pour examen.
2. **Outils pédagogiques**: Annoter des manuels avec des notes ou des corrections pour les étudiants.
3. **Édition collaborative**:Partage de brouillons annotés entre les membres de l'équipe pour obtenir des commentaires.
4. **Documentation juridique**:Souligner les clauses clés des documents juridiques lors des discussions.
5. **Matériel de marketing**:Mise en évidence des informations importantes dans les brochures avant distribution.

## Considérations relatives aux performances
Lorsque vous travaillez avec GroupDocs.Annotation, tenez compte de ces conseils pour optimiser les performances :
- **Gestion de la mémoire**:Éliminer correctement `Annotator` objets pour libérer des ressources.
- **Traitement par lots**: Si vous annotez plusieurs documents, traitez-les par lots pour gérer efficacement la charge du système.
- **Allocation des ressources**: Assurez-vous que votre environnement dispose de suffisamment de mémoire et de puissance de traitement pour gérer des fichiers volumineux.

## Conclusion
Vous avez appris à ajouter et supprimer des annotations soulignées avec GroupDocs.Annotation pour Java. Ce tutoriel a abordé l'initialisation de la classe Annotator, la configuration des annotations avec commentaires et l'enregistrement de documents sans annotations. 

Pour une exploration plus approfondie, envisagez d’intégrer ces fonctionnalités dans vos systèmes de gestion de documents existants ou d’expérimenter d’autres types d’annotations fournis par GroupDocs.

## Section FAQ
1. **Comment configurer plusieurs annotations soulignées en une seule exécution ?**
   - Créer plusieurs `UnderlineAnnotation` objets et les ajouter séquentiellement à l'aide de la `annotator.add()` méthode.
2. **Puis-je annoter des images dans des fichiers PDF à l’aide de cette bibliothèque ?**
   - Oui, GroupDocs.Annotation prend en charge l'annotation d'images dans des documents tels que des PDF.
3. **Quels formats de fichiers GroupDocs.Annotation prend-il en charge ?**
   - Il prend en charge divers formats de documents, notamment PDF, Word, Excel, etc.