---
"description": "Découvrez comment ajouter facilement des annotations de remplacement de texte à vos documents .NET grâce à GroupDocs.Annotation pour .NET. Améliorez vos capacités de manipulation de documents."
"linktitle": "Ajouter une annotation de remplacement de texte au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de remplacement de texte au document"
"url": "/fr/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Ajouter une annotation de remplacement de texte au document

## Introduction
Dans ce tutoriel, nous vous guiderons dans l'ajout d'annotations de remplacement de texte à vos documents avec GroupDocs.Annotation pour .NET. Cette puissante bibliothèque permet aux développeurs de manipuler et d'annoter différents types de documents par programmation. À la fin de ce tutoriel, vous maîtriserez les connaissances nécessaires pour intégrer facilement des annotations de remplacement de texte à vos applications .NET.
## Prérequis
Avant de commencer, assurez-vous que les prérequis suivants sont installés :
### 1. .NET Framework installé
Assurez-vous que .NET Framework est installé sur votre machine de développement. Vous pouvez le télécharger depuis le site web de Microsoft.
### 2. Bibliothèque GroupDocs.Annotation pour .NET
Téléchargez et installez la bibliothèque GroupDocs.Annotation pour .NET à partir du [site web](https://releases.groupdocs.com/annotation/net/). Cette bibliothèque fournit les outils et fonctionnalités nécessaires pour travailler avec des annotations dans divers formats de documents.
### 3. Configuration de l'environnement de développement
Configurez votre environnement de développement préféré, tel que Visual Studio, pour créer et exécuter des applications .NET.

## Importer des espaces de noms
Avant de plonger dans la partie codage, importons les espaces de noms nécessaires pour travailler avec GroupDocs.Annotation pour .NET :
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ici, nous définissons le chemin de sortie où le document annoté sera enregistré.
## Étape 2 : Initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation sera placé ici
}
```
Nous initialisons l'objet Annotator en spécifiant le document d'entrée (« input.pdf ») dans un bloc using pour garantir une élimination appropriée des ressources.
## Étape 3 : Créer une annotation de remplacement
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
Ici, nous créons un objet ReplacementAnnotation avec diverses propriétés telles que la date de création, la couleur de la police, le message, l'opacité, le numéro de page, la couleur d'arrière-plan, les points (coordonnées), les réponses (commentaires) et le texte à remplacer.
## Étape 4 : Ajouter une annotation
```csharp
annotator.Add(replacement);
```
Nous ajoutons l’annotation de remplacement créée à l’annotateur.
## Étape 5 : Enregistrer le document
```csharp
annotator.Save(outputPath);
```
Enfin, nous enregistrons le document annoté dans le chemin de sortie spécifié.
## Étape 6 : Afficher le message de réussite
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Un message de réussite s'affiche indiquant que le document a été enregistré avec succès.

## Conclusion
Dans ce tutoriel, nous avons abordé le processus d'ajout d'annotations de remplacement de texte aux documents à l'aide de GroupDocs.Annotation pour .NET. En suivant le guide étape par étape et en comprenant les prérequis, vous pourrez facilement intégrer cette fonctionnalité à vos applications .NET.
## FAQ
### Puis-je annoter des documents de différents formats à l’aide de GroupDocs.Annotation pour .NET ?
Oui, GroupDocs.Annotation pour .NET prend en charge l'annotation de divers formats de documents tels que PDF, DOCX, PPTX, XLSX, etc.
### GroupDocs.Annotation pour .NET convient-il aux applications de bureau et Web ?
Oui, GroupDocs.Annotation pour .NET peut être utilisé dans les applications de bureau et Web, offrant ainsi une flexibilité aux développeurs.
### Puis-je personnaliser l’apparence des annotations ajoutées à l’aide de GroupDocs.Annotation pour .NET ?
Absolument, vous pouvez personnaliser l'apparence des annotations en modifiant des propriétés telles que la couleur, l'opacité, la police, etc.
### GroupDocs.Annotation pour .NET offre-t-il une prise en charge des fonctionnalités d’annotation collaborative ?
Oui, GroupDocs.Annotation pour .NET fournit des fonctionnalités d’annotation collaborative, permettant à plusieurs utilisateurs d’annoter des documents simultanément.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET à partir du [site web](https://releases.groupdocs.com/).