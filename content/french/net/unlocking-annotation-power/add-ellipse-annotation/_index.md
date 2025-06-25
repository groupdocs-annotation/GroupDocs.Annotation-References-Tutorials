---
"description": "Apprenez à ajouter des annotations en forme d'ellipse à vos documents .NET avec GroupDocs.Annotation. Améliorez la collaboration et la communication sans effort."
"linktitle": "Ajouter une annotation Ellipse au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation Ellipse au document"
"url": "/fr/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Ajouter une annotation Ellipse au document

## Introduction
Dans ce tutoriel, vous apprendrez à ajouter une annotation ellipse à un document avec GroupDocs.Annotation pour .NET. Ce guide étape par étape vous guidera tout au long du processus, vous permettant de bien comprendre chaque étape.
## Prérequis
Avant de commencer, assurez-vous d’avoir les éléments suivants :
1. GroupDocs.Annotation pour .NET : Assurez-vous d'avoir téléchargé et installé GroupDocs.Annotation pour .NET. Vous pouvez le télécharger depuis [ici](https://releases.groupdocs.com/annotation/net/).
2. IDE (environnement de développement intégré) : vous aurez besoin d’un IDE installé sur votre système, tel que Visual Studio, pour écrire et exécuter le code.

## Importer des espaces de noms
Tout d’abord, importez les espaces de noms nécessaires dans votre projet :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : définir le chemin de sortie
Définissez le chemin de sortie où le document annoté sera enregistré :
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Initialiser l'annotateur
Initialisez l'annotateur en fournissant le chemin du document d'entrée :
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 3 : Créer une annotation d'ellipse
Créer une instance de `EllipseAnnotation` classe et définir ses propriétés :
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
Ajoutez l'annotation ellipse au document :
```csharp
annotator.Add(ellipse);
```
## Étape 5 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie :
```csharp
annotator.Save(outputPath);
```

## Conclusion
Félicitations ! Vous avez ajouté une annotation ellipse à un document avec GroupDocs.Annotation pour .NET. Vous pouvez désormais intégrer cette fonctionnalité à vos applications .NET pour améliorer la collaboration et la communication sur vos documents.
## FAQ
### Puis-je personnaliser l’apparence de l’annotation ellipse ?
Oui, vous pouvez personnaliser diverses propriétés telles que la couleur d'arrière-plan, la couleur de la bordure, l'opacité, etc., selon vos besoins.
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation pour .NET prend en charge une large gamme de formats de documents, notamment PDF, DOCX, PPTX, XLSX, etc.
### Puis-je ajouter plusieurs annotations à un seul document ?
Oui, vous pouvez ajouter plusieurs annotations, notamment des ellipses, des rectangles, du texte, etc., à un seul document.
### Existe-t-il une version d'essai disponible à des fins de test ?
Oui, vous pouvez télécharger une version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/) pour évaluer ses caractéristiques.
### Où puis-je obtenir une assistance technique pour GroupDocs.Annotation pour .NET ?
Vous pouvez obtenir une assistance technique sur le forum communautaire GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).