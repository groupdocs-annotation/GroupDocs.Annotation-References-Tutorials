---
"description": "Découvrez comment supprimer plusieurs annotations par ID dans .NET à l’aide de GroupDocs.Annotation, améliorant ainsi sans effort vos capacités de gestion de documents."
"linktitle": "Supprimer plusieurs annotations par identifiant"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Supprimer plusieurs annotations par identifiant"
"url": "/fr/net/removing-annotations/remove-multiple-annotations-by-ids/"
"weight": 13
---

# Supprimer plusieurs annotations par identifiant

## Introduction
Dans le monde de la gestion documentaire et de la collaboration, GroupDocs.Annotation pour .NET s'impose comme un outil puissant, permettant aux développeurs d'annoter et de manipuler des documents de manière fluide au sein de leurs applications .NET. Ce tutoriel explore l'une des fonctionnalités essentielles de GroupDocs.Annotation pour .NET : la suppression d'annotations multiples par identifiant. En suivant ce guide étape par étape, vous comprendrez parfaitement comment supprimer efficacement les annotations et améliorerez ainsi vos capacités de gestion documentaire.
## Prérequis
Avant de vous lancer dans ce tutoriel, assurez-vous de disposer des prérequis suivants :
### 1. Installation de GroupDocs.Annotation pour .NET
Tout d'abord, GroupDocs.Annotation pour .NET doit être installé dans votre environnement de développement. Vous pouvez télécharger le package requis depuis le [lien de téléchargement](https://releases.groupdocs.com/annotation/net/) fourni par GroupDocs.
### 2. Compréhension de base du .NET Framework
Une compréhension fondamentale du .NET Framework est nécessaire pour comprendre les exemples de code et mettre en œuvre efficacement la solution fournie.

## Importer des espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre application .NET. Ces espaces de noms donnent accès aux fonctionnalités nécessaires à la manipulation des annotations.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Dans cette étape, nous définissons le chemin où le document modifié avec les annotations supprimées sera enregistré.
## Étape 2 : instancier l'objet annotateur
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
Ici, nous créons une instance du `Annotator` classe, passant le chemin du document PDF annoté en paramètre.
## Étape 3 : Supprimer les annotations par identifiant
```csharp
annotator.Remove(new List<int>{0,1});
```
Dans cette étape cruciale, nous spécifions les identifiants des annotations à supprimer. Plusieurs identifiants peuvent être transmis dans une liste pour une suppression simultanée.
## Étape 4 : Enregistrer le document modifié
```csharp
annotator.Save(outputPath);
```
Après avoir supprimé les annotations spécifiées, nous enregistrons le document modifié dans le chemin de sortie précédemment défini.
## Étape 5 : Afficher le message de réussite
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Enfin, nous informons l'utilisateur de la réussite du processus et fournissons le chemin où le document modifié est enregistré.

## Conclusion
En conclusion, ce tutoriel a expliqué le processus de suppression de plusieurs annotations par identifiant à l'aide de GroupDocs.Annotation pour .NET. En suivant les étapes décrites, les développeurs peuvent intégrer facilement cette fonctionnalité à leurs applications .NET, améliorant ainsi l'efficacité de la gestion documentaire et la collaboration.
## FAQ
### Les annotations de différents types peuvent-elles être supprimées simultanément ?
Oui, les annotations de différents types peuvent être supprimées simultanément en spécifiant leurs identifiants respectifs dans la liste de suppression.
### GroupDocs.Annotation pour .NET est-il compatible avec toutes les versions de .NET Framework ?
Oui, GroupDocs.Annotation pour .NET est compatible avec différentes versions du .NET Framework, garantissant polyvalence et facilité d'intégration.
### Puis-je essayer GroupDocs.Annotation pour .NET avant d'acheter ?
Absolument ! Vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET depuis le [page de sortie](https://releases.groupdocs.com/) pour explorer ses caractéristiques et fonctionnalités.
### Ai-je besoin d’une licence temporaire à des fins de test ?
Bien qu'une licence temporaire puisse améliorer votre expérience de test, elle n'est pas obligatoire pour les essais. En revanche, pour une utilisation en production, une licence valide est requise.
### Où puis-je demander de l’aide si je rencontre des problèmes lors de la mise en œuvre ?
Vous pouvez demander de l'aide et vous engager auprès de la communauté dynamique de GroupDocs via le [forum d'assistance](https://forum.groupdocs.com/c/annotation/10), où des experts et des passionnés sont facilement disponibles pour répondre à vos questions et préoccupations.