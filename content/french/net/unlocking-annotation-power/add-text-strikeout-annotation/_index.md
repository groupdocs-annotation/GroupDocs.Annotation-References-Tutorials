---
"description": "Découvrez comment ajouter des annotations de texte barré à vos documents avec GroupDocs.Annotation pour .NET. Améliorez efficacement la collaboration et la révision de vos documents."
"linktitle": "Ajouter une annotation de texte barré au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de texte barré au document"
"url": "/fr/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# Ajouter une annotation de texte barré au document

## Introduction
Dans ce tutoriel, nous découvrirons comment ajouter une annotation de texte barré à un document à l'aide de GroupDocs.Annotation pour .NET. Cette bibliothèque fournit des outils puissants pour annoter différents types de documents, améliorant ainsi la collaboration et la révision des documents.
## Prérequis
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. GroupDocs.Annotation pour .NET : installez la bibliothèque. Vous pouvez la télécharger depuis [ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : Configurez un environnement de développement adapté au développement .NET.
3. Document : Préparez un document à annoter, comme un fichier PDF.

## Importation d'espaces de noms
Tout d’abord, importez les espaces de noms nécessaires pour accéder aux fonctionnalités de GroupDocs.Annotation :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Décomposons maintenant le processus d’ajout d’une annotation de texte barré en plusieurs étapes :
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ici, nous définissons le chemin de sortie où le document annoté sera enregistré.
## Étape 2 : Initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initialisez l'objet Annotator en fournissant le chemin d'accès au document d'entrée (fichier PDF dans ce cas).
## Étape 3 : Créer une annotation barrée
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Créez un objet StrikeoutAnnotation avec les propriétés souhaitées telles que le message, l'opacité, le numéro de page, la couleur d'arrière-plan, les points (coordonnées) et les réponses.
## Étape 4 : Ajouter une annotation
```csharp
annotator.Add(strikeout);
```
Ajoutez l’annotation barrée créée au document.
## Étape 5 : Enregistrer le document
```csharp
annotator.Save(outputPath);
```
Enregistrez le document annoté dans le chemin de sortie spécifié.

## Conclusion
Dans ce tutoriel, nous avons appris à ajouter une annotation de texte barré à un document à l'aide de GroupDocs.Annotation pour .NET. Cette puissante bibliothèque permet une annotation efficace des documents, améliorant ainsi la collaboration et la révision des documents.
## FAQ
### GroupDocs.Annotation est-il compatible avec différents formats de documents ?
Oui, GroupDocs.Annotation prend en charge une large gamme de formats de documents, notamment PDF, Word, Excel, PowerPoint, etc.
### Puis-je personnaliser l’apparence des annotations ?
Absolument, vous pouvez personnaliser les propriétés d'annotation telles que la couleur, l'opacité, la taille de la police, etc. en fonction de vos besoins.
### GroupDocs.Annotation fournit-il des fonctionnalités de collaboration ?
Oui, GroupDocs.Annotation facilite la collaboration en permettant aux utilisateurs d’ajouter des commentaires, des réponses et des annotations aux documents.
### Existe-t-il un essai gratuit disponible ?
Oui, vous pouvez bénéficier d'un essai gratuit à partir de [ici](https://releases.groupdocs.com/).
### Où puis-je obtenir de l'aide pour GroupDocs.Annotation ?
Vous pouvez obtenir du soutien auprès du [Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).