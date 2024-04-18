---
title: Supprimer plusieurs annotations par ID
linktitle: Supprimer plusieurs annotations par ID
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment supprimer plusieurs annotations par ID dans .NET à l'aide de GroupDocs.Annotation, améliorant ainsi vos capacités de gestion de documents sans effort.
type: docs
weight: 13
url: /fr/net/removing-annotations/remove-multiple-annotations-by-ids/
---
## Introduction
Dans le monde de la gestion documentaire et de la collaboration, GroupDocs.Annotation pour .NET apparaît comme un outil puissant, permettant aux développeurs d'annoter et de manipuler des documents de manière transparente au sein de leurs applications .NET. Ce tutoriel approfondira l'une des fonctionnalités essentielles offertes par GroupDocs.Annotation pour .NET : supprimer plusieurs annotations par ID. En suivant ce guide étape par étape, vous obtiendrez une compréhension complète de la façon de supprimer efficacement les annotations, vous permettant ainsi d'améliorer vos capacités de gestion de documents.
## Conditions préalables
Avant de vous lancer dans ce didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
### 1. Installation de GroupDocs.Annotation pour .NET
 Tout d’abord, vous devez avoir GroupDocs.Annotation pour .NET installé dans votre environnement de développement. Vous pouvez télécharger le package requis à partir du[lien de téléchargement](https://releases.groupdocs.com/annotation/net/) fourni par GroupDocs.
### 2. Compréhension de base du .NET Framework
Une compréhension fondamentale du .NET Framework est nécessaire pour comprendre les exemples de code et mettre en œuvre efficacement la solution fournie.

## Importer des espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre application .NET. Ces espaces de noms donnent accès aux fonctionnalités requises pour la manipulation des annotations.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Étape 1 : définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Dans cette étape, nous définissons le chemin où le document modifié avec les annotations supprimées sera enregistré.
## Étape 2 : Instancier l'objet Annotateur
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 Ici, nous créons une instance du`Annotator` classe, en passant le chemin du document PDF annoté en paramètre.
## Étape 3 : Supprimer les annotations par ID
```csharp
annotator.Remove(new List<int>{0,1});
```
Dans cette étape cruciale, nous précisons les ID des annotations à supprimer. Plusieurs identifiants peuvent être transmis dans une liste pour une suppression simultanée.
## Étape 4 : Enregistrez le document modifié
```csharp
annotator.Save(outputPath);
```
Après avoir supprimé les annotations spécifiées, nous enregistrons le document modifié sur le chemin de sortie précédemment défini.
## Étape 5 : Afficher le message de réussite
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Enfin, nous informons l'utilisateur de la réussite du processus et lui fournissons le chemin où le document modifié est enregistré.

## Conclusion
En conclusion, ce didacticiel a expliqué le processus de suppression de plusieurs annotations par ID à l'aide de GroupDocs.Annotation pour .NET. En suivant les étapes décrites, les développeurs peuvent intégrer de manière transparente cette fonctionnalité dans leurs applications .NET, améliorant ainsi l'efficacité de la gestion des documents et la collaboration.
## FAQ
### Des annotations de différents types peuvent-elles être supprimées simultanément ?
Oui, les annotations de différents types peuvent être supprimées simultanément en spécifiant leurs identifiants respectifs dans la liste de suppression.
### GroupDocs.Annotation pour .NET est-il compatible avec toutes les versions de .NET Framework ?
Oui, GroupDocs.Annotation pour .NET est compatible avec différentes versions du .NET Framework, garantissant polyvalence et facilité d'intégration.
### Puis-je essayer GroupDocs.Annotation pour .NET avant d'acheter ?
 Absolument! Vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET à partir du[page de sortie](https://releases.groupdocs.com/)pour explorer ses caractéristiques et fonctionnalités.
### Ai-je besoin d’une licence temporaire à des fins de test ?
Même si une licence temporaire peut améliorer votre expérience de test, elle n'est pas obligatoire à des fins d'essai. Cependant, pour une utilisation en production, une licence valide est requise.
### Où puis-je demander de l’aide si je rencontre des problèmes lors de la mise en œuvre ?
 Vous pouvez demander de l'aide et interagir avec la communauté dynamique GroupDocs via le[forum d'entraide](https://forum.groupdocs.com/c/annotation/10), où des experts et des passionnés sont facilement disponibles pour répondre à vos questions et préoccupations.