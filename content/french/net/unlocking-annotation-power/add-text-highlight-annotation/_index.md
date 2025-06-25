---
"description": "Apprenez à ajouter des annotations de surlignage de texte à vos documents avec GroupDocs.Annotation pour .NET. Améliorez la collaboration et la productivité grâce à cette solution complète."
"linktitle": "Ajouter une annotation de surbrillance de texte au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de surbrillance de texte au document"
"url": "/fr/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Ajouter une annotation de surbrillance de texte au document

## Introduction
Dans le domaine de la gestion documentaire et de la collaboration, GroupDocs.Annotation pour .NET s'impose comme une solution robuste, permettant aux développeurs d'intégrer facilement des annotations de surlignage de texte à leurs applications. Ce tutoriel est un guide complet pour ajouter des annotations de surlignage de texte à vos documents avec GroupDocs.Annotation pour .NET. Grâce à des instructions pas à pas et des explications détaillées, vous maîtriserez les fonctionnalités de cette puissante bibliothèque.
## Prérequis
Avant de vous plonger dans la mise en œuvre des annotations de surbrillance de texte, assurez-vous que les conditions préalables suivantes sont en place :
1. Configuration de l'environnement : disposez d'un environnement de développement adapté configuré pour le développement .NET.
2. Installation de GroupDocs.Annotation pour .NET : Téléchargez et installez GroupDocs.Annotation pour .NET à partir du fichier fourni. [lien de téléchargement](https://releases.groupdocs.com/annotation/net/).
3. Familiarité avec C# : Compréhension de base du langage de programmation C#.
4. Document à annoter : Préparez un document (par exemple, PDF) que vous avez l'intention d'annoter.

## Importer des espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre code C# pour utiliser les fonctionnalités de GroupDocs.Annotation pour .NET :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Maintenant, décomposons le processus d'ajout d'annotations de surbrillance de texte en plusieurs étapes :
## Étape 1 : Définir le chemin de sortie
Spécifiez le chemin de sortie où le document annoté sera enregistré :
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Initialiser l'annotateur
Créer une instance de `Annotator` classe, en passant le nom du fichier du document en paramètre :
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Étape 3 : Créer une annotation de surbrillance
Instancier un `HighlightAnnotation` objet et configurer ses propriétés :
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## Étape 4 : Ajouter une annotation
Ajoutez l’annotation de surbrillance créée au document :
```csharp
annotator.Add(highlight);
```
## Étape 5 : Enregistrer le document annoté
Enregistrez le document annoté dans le chemin de sortie spécifié :
```csharp
annotator.Save(outputPath);
```

## Conclusion
En conclusion, GroupDocs.Annotation pour .NET offre une approche simplifiée pour intégrer des annotations de surlignage de texte dans les documents. En suivant les étapes décrites dans ce tutoriel, les développeurs peuvent améliorer facilement la collaboration et la productivité de leurs applications.
## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation pour .NET prend en charge divers formats de documents, notamment PDF, Word, Excel, etc. Consultez la documentation pour en connaître la liste complète.
### Les annotations peuvent-elles être personnalisées en fonction d’exigences spécifiques ?
Oui, les développeurs ont un contrôle total sur les propriétés et l’apparence des annotations, ce qui permet une personnalisation pour répondre à divers besoins.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Annotation pour .NET en accédant à l'essai gratuit à partir du [lien](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide pour tout problème ou question lié à GroupDocs.Annotation pour .NET ?
Pour obtenir de l'aide et de l'assistance, vous pouvez visiter le forum GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).
### Quelles options de licence sont disponibles pour GroupDocs.Annotation pour .NET ?
GroupDocs.Annotation pour .NET propose différentes options de licence, notamment des licences temporaires pour les tests et des licences commerciales pour les environnements de production. Consultez la page d'achat. [ici](https://purchase.groupdocs.com/buy) pour plus de détails.