---
"description": "Apprenez à ajouter des annotations de rédaction de texte à vos documents PDF avec GroupDocs.Annotation pour .NET. Protégez vos informations sensibles en toute simplicité."
"linktitle": "Ajouter une annotation de rédaction de texte au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de rédaction de texte au document"
"url": "/fr/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Ajouter une annotation de rédaction de texte au document

## Introduction
L'ajout d'une annotation de rédaction de texte à un document peut être une étape cruciale pour la gestion sécurisée des informations sensibles. GroupDocs.Annotation pour .NET offre une solution robuste pour y parvenir en toute simplicité. Dans ce tutoriel, nous vous guiderons pas à pas dans l'ajout d'une annotation de rédaction de texte à votre document.
## Prérequis
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
1. GroupDocs.Annotation pour .NET : Assurez-vous d'avoir installé la bibliothèque GroupDocs.Annotation pour .NET. Vous pouvez la télécharger depuis le [site web](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : configurez un environnement de développement avec un IDE compatible .NET tel que Visual Studio.

## Importation d'espaces de noms
Tout d’abord, importons les espaces de noms nécessaires à notre projet :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
Définissez le chemin de sortie où vous souhaitez enregistrer le document annoté. Assurez-vous qu'il est accessible et inscriptible.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Initialiser l'annotateur
Initialisez l'annotateur avec le chemin du document d'entrée. Remplacez `"input.pdf"` avec le chemin vers votre document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation sera placé ici
}
```
## Étape 3 : Créer une annotation de rédaction de texte
Créer un `TextRedactionAnnotation` objet avec les propriétés requises telles que `PageNumber`, `FontColor`, et `Points`Personnalisez l'annotation selon vos besoins.
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
Ajoutez l’annotation créée au document à l’aide de l’annotateur et enregistrez le document annoté dans le chemin de sortie spécifié.
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
Dans ce tutoriel, nous avons expliqué comment ajouter une annotation de rédaction de texte à un document à l'aide de GroupDocs.Annotation pour .NET. Grâce à ces étapes, vous pouvez désormais gérer en toute sécurité les informations sensibles de vos documents.
## FAQ
### Puis-je personnaliser l'apparence de l'annotation de rédaction de texte ?
Oui, vous pouvez personnaliser diverses propriétés telles que la couleur de la police, la couleur de remplissage et l'opacité en fonction de vos besoins.
### Existe-t-il une version d'essai disponible avant l'achat ?
Oui, vous pouvez accéder à une version d'essai gratuite à partir du [site web](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l’aide si je rencontre des problèmes ?
Vous pouvez obtenir de l'aide sur le forum communautaire GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).
### Ai-je besoin d’une licence temporaire à des fins de test ?
Oui, vous pouvez obtenir un permis temporaire auprès du [page d'achat](https://purchase.groupdocs.com/temporary-license/) pour les tests.
### Puis-je ajouter plusieurs annotations à un seul document ?
Absolument, GroupDocs.Annotation vous permet d'ajouter différents types d'annotations et plusieurs instances à un seul document.