---
title: Charger un document à partir du disque local
linktitle: Charger un document à partir du disque local
second_title: API GroupDocs.Annotation .NET
description: Libérez la puissance de l’annotation de documents avec GroupDocs.Annotation pour .NET. Intégrez de manière transparente les fonctionnalités d’annotation dans vos applications .NET.
type: docs
weight: 13
url: /fr/net/document-loading-essentials/load-document-from-local-disk/
---
## Introduction
Libérer le potentiel de l’annotation de documents n’a jamais été aussi simple avec GroupDocs.Annotation pour .NET. Cet outil puissant permet aux développeurs d'intégrer de manière transparente des fonctionnalités d'annotation robustes dans leurs applications .NET. Dans ce guide complet, nous vous guiderons tout au long du processus d'utilisation de GroupDocs.Annotation pour .NET pour annoter des documents étape par étape. Que vous soyez un développeur chevronné ou débutant, ce didacticiel vous fournira les connaissances nécessaires pour améliorer la collaboration documentaire et rationaliser votre flux de travail.
## Conditions préalables
Avant de vous lancer dans l'annotation de documents avec GroupDocs.Annotation pour .NET, assurez-vous de disposer des prérequis suivants :
1. Connaissance de base de C# : Une connaissance des principes fondamentaux du langage de programmation C# est essentielle.
2. Installation de GroupDocs.Annotation pour .NET : Téléchargez et installez GroupDocs.Annotation pour .NET à partir de[ici](https://releases.groupdocs.com/annotation/net/).
3. Environnement de développement : configurez un environnement de développement avec Visual Studio ou tout autre IDE compatible.

## Importer des espaces de noms
Pour commencer à annoter des documents avec GroupDocs.Annotation pour .NET, importez les espaces de noms nécessaires dans votre projet :
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Étape 1 : Charger le document à partir du disque local
Tout d’abord, vous devez charger le document depuis votre disque local. Utilisez l'extrait de code suivant :
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 2 : Définir la zone d'annotation
Ensuite, définissez la zone d'annotation. Dans cet exemple, nous allons créer une AreaAnnotation :
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Étape 3 : Enregistrer le document avec les annotations
Après avoir annoté le document, enregistrez-le avec les annotations :
```csharp
    annotator.Save(outputPath);
}
```
## Étape 4 : Afficher le message de réussite
Enfin, affichez un message de réussite avec le chemin de sortie :
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
En conclusion, GroupDocs.Annotation pour .NET fournit une solution robuste pour intégrer des fonctionnalités d'annotation de documents dans vos applications .NET. En suivant ce guide étape par étape, vous pouvez facilement annoter des documents et améliorer la collaboration dans vos projets.
## FAQ
### Puis-je essayer GroupDocs.Annotation pour .NET avant d'acheter ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Annotation pour .NET ?
 Vous pouvez accéder à la documentation[ici](https://reference.groupdocs.com/annotation/net/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Annotation pour .NET ?
 Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### La prise en charge est-elle disponible pour GroupDocs.Annotation pour .NET ?
 Oui, vous pouvez trouver de l'aide sur le forum GroupDocs[ici](https://forum.groupdocs.com/c/annotation/10).
### Où puis-je acheter GroupDocs.Annotation pour .NET ?
 Vous pouvez acheter GroupDocs.Annotation pour .NET[ici](https://purchase.groupdocs.com/buy).