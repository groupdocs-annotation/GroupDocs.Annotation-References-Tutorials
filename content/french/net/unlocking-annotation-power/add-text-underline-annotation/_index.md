---
"description": "Apprenez à ajouter des annotations de soulignement de texte à vos documents avec GroupDocs.Annotation pour .NET. Améliorez la collaboration et la communication sans effort."
"linktitle": "Ajouter une annotation de soulignement de texte au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de soulignement de texte au document"
"url": "/fr/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# Ajouter une annotation de soulignement de texte au document

## Introduction
Dans ce tutoriel, nous allons vous expliquer comment ajouter un soulignement de texte à un document à l'aide de GroupDocs.Annotation pour .NET. Les annotations de soulignement de texte peuvent être utiles pour mettre en valeur des parties spécifiques d'un document, comme des passages importants ou des points clés.
## Prérequis
Avant de commencer, assurez-vous que les prérequis suivants sont installés :
1. GroupDocs.Annotation pour .NET : téléchargez et installez GroupDocs.Annotation pour .NET depuis [ici](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework : assurez-vous que .NET Framework est installé sur votre système.

## Importation d'espaces de noms
Tout d’abord, importons les espaces de noms nécessaires dans notre projet :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Maintenant, décomposons l’exemple en plusieurs étapes :
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Dans cette étape, nous définissons le chemin de sortie où le document annoté sera enregistré.
## Étape 2 : Initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Ici, nous initialisons une instance du `Annotator` classe en fournissant le chemin du document d'entrée.
## Étape 3 : Créer une annotation soulignée
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // fonctionne uniquement avec les documents Word et PDF
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
Cette étape consiste à créer un `UnderlineAnnotation` objet avec diverses propriétés telles que la couleur de police, le message, l'opacité, le numéro de page, la couleur d'arrière-plan, la couleur de soulignement, les points et les réponses.
## Étape 4 : Ajouter une annotation au document
```csharp
annotator.Add(underline);
```
Ici, nous ajoutons l’annotation de soulignement au document.
## Étape 5 : Enregistrer le document annoté
```csharp
annotator.Save(outputPath);
```
Enfin, nous enregistrons le document annoté dans le chemin de sortie spécifié.

## Conclusion
Dans ce tutoriel, nous avons appris à ajouter une annotation de soulignement de texte à un document à l'aide de GroupDocs.Annotation pour .NET. Cette puissante bibliothèque offre diverses options d'annotation pour améliorer la collaboration et la communication sur les documents.
## FAQ
### Puis-je personnaliser l’apparence de l’annotation soulignée ?
Oui, vous pouvez personnaliser les propriétés telles que la couleur, l'opacité et la position en fonction de vos besoins.
### GroupDocs.Annotation est-il compatible avec différents formats de documents ?
Oui, GroupDocs.Annotation prend en charge une large gamme de formats de documents, notamment Word et PDF.
### Puis-je ajouter plusieurs annotations à un seul document ?
Absolument, GroupDocs.Annotation vous permet d'ajouter plusieurs annotations de différents types à un document.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation ?
Oui, vous pouvez accéder à la version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/).
### Où puis-je obtenir de l'aide pour GroupDocs.Annotation ?
Vous pouvez obtenir de l'aide sur le forum communautaire GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).