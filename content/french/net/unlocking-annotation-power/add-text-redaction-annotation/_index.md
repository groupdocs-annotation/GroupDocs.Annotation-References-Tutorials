---
title: Ajouter une annotation de rédaction de texte au document
linktitle: Ajouter une annotation de rédaction de texte au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations de rédaction de texte aux documents PDF à l'aide de GroupDocs.Annotation pour .NET. Protégez les informations sensibles sans effort.
type: docs
weight: 23
url: /fr/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Introduction
L’ajout d’une annotation de rédaction de texte à un document peut être une étape cruciale dans la gestion sécurisée des informations sensibles. GroupDocs.Annotation pour .NET fournit une solution robuste pour y parvenir de manière transparente. Dans ce didacticiel, nous vous guiderons étape par étape tout au long du processus d'ajout d'une annotation de rédaction de texte à votre document.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
1.  GroupDocs.Annotation pour .NET : assurez-vous d'avoir installé la bibliothèque GroupDocs.Annotation pour .NET. Vous pouvez le télécharger depuis le[site web](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : configurez un environnement de développement avec un IDE compatible .NET tel que Visual Studio.

## Importation d'espaces de noms
Tout d'abord, importons les espaces de noms nécessaires dans notre projet :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
Définissez le chemin de sortie où vous souhaitez enregistrer le document annoté. Assurez-vous qu’il est accessible et accessible en écriture.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : initialiser l'annotateur
 Initialisez l'annotateur avec le chemin du document d'entrée. Remplacer`"input.pdf"` avec le chemin d'accès à votre document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation ira ici
}
```
## Étape 3 : Créer une annotation de rédaction de texte
 Créer un`TextRedactionAnnotation`objet avec les propriétés requises telles que`PageNumber`, `FontColor` , et`Points`. Personnalisez l'annotation selon vos besoins.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Étape 4 : ajouter une annotation et enregistrer
Ajoutez l'annotation créée au document à l'aide de l'annotateur et enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Étape 5 : Vérifier la sortie
Enfin, confirmez que le document a été enregistré avec succès dans le chemin de sortie spécifié.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce didacticiel, nous avons parcouru le processus d'ajout d'une annotation de rédaction de texte à un document à l'aide de GroupDocs.Annotation pour .NET. Grâce à ces étapes, vous pouvez désormais gérer en toute sécurité les informations sensibles dans vos documents.
## FAQ
### Puis-je personnaliser l’apparence de l’annotation de rédaction de texte ?
Oui, vous pouvez personnaliser diverses propriétés telles que la couleur de la police, la couleur de remplissage et l'opacité en fonction de vos besoins.
### Existe-t-il une version d'essai disponible avant d'acheter ?
 Oui, vous pouvez accéder à une version d'essai gratuite à partir du[site web](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide si je rencontre des problèmes ?
 Vous pouvez obtenir de l'aide sur le forum de la communauté GroupDocs.Annotation.[ici](https://forum.groupdocs.com/c/annotation/10).
### Ai-je besoin d’une licence temporaire à des fins de test ?
 Oui, vous pouvez obtenir une licence temporaire auprès du[page d'achat](https://purchase.groupdocs.com/temporary-license/)pour tester.
### Puis-je ajouter plusieurs annotations à un seul document ?
Absolument, GroupDocs.Annotation vous permet d'ajouter différents types d'annotations et plusieurs instances à un seul document.