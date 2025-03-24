---
title: Ajouter une annotation de point au document
linktitle: Ajouter une annotation de point au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter une annotation de point aux PDF à l’aide de GroupDocs.Annotation pour .NET. Guide étape par étape pour une intégration transparente.
weight: 17
url: /fr/net/unlocking-annotation-power/add-point-annotation/
---
## Introduction
GroupDocs.Annotation pour .NET est un outil puissant qui permet aux développeurs d'ajouter différents types d'annotations aux documents par programme. Dans ce didacticiel, nous nous concentrerons sur l'ajout d'une annotation de point à un document à l'aide de C#.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1. Compréhension de base du langage de programmation C#.
2. Visual Studio installé sur votre système.
3.  GroupDocs.Annotation pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/annotation/net/).

## Importation des espaces de noms nécessaires
Pour commencer, vous devez importer les espaces de noms requis dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Dans cette étape, nous définissons le chemin de sortie où le document annoté sera enregistré.
## Étape 2 : initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Ici, nous initialisons le`Annotator` objet avec le document d'entrée ("input.pdf").
## Étape 3 : Créer une annotation de point
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 Dans cette étape, nous créons un`PointAnnotation` objet et spécifiez ses propriétés telles que la position, le message, le numéro de page et les réponses.
## Étape 4 : Ajouter une annotation
```csharp
annotator.Add(point);
```
Ici, nous ajoutons l'annotation de point créée au document.
## Étape 5 : Enregistrer le document
```csharp
annotator.Save(outputPath);
```
Enfin, nous enregistrons le document annoté dans le chemin de sortie spécifié.

## Conclusion
Dans ce didacticiel, nous avons appris comment ajouter une annotation de point à un document à l'aide de GroupDocs.Annotation pour .NET. Avec cette puissante bibliothèque, vous pouvez améliorer vos applications de gestion de documents en intégrant des fonctionnalités d'annotation.
## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
Oui, GroupDocs.Annotation pour .NET prend en charge un large éventail de formats de documents, notamment PDF, Microsoft Word, Excel, PowerPoint, etc.
### Puis-je personnaliser l’apparence des annotations ?
Absolument! GroupDocs.Annotation pour .NET fournit des options étendues pour personnaliser l'apparence des annotations en fonction des besoins de votre application.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
 Oui, vous pouvez bénéficier d'un essai gratuit auprès de[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l’aide pour tout problème ou requête lié à GroupDocs.Annotation pour .NET ?
 Vous pouvez obtenir de l'aide sur le forum GroupDocs.Annotation[ici](https://forum.groupdocs.com/c/annotation/10).
### Puis-je obtenir une licence temporaire à des fins de test ?
 Oui, vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).