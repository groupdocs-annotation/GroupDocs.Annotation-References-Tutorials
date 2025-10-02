---
"description": "Découvrez comment ajouter des annotations d’image sur du texte dans .NET à l’aide de GroupDocs.Annotation pour une gestion et une collaboration efficaces des documents."
"linktitle": "Mettre l'annotation d'image sur le texte"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Mettre l'annotation d'image sur le texte"
"url": "/fr/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Mettre l'annotation d'image sur le texte

## Introduction
Dans le monde du développement .NET, GroupDocs.Annotation offre une solution puissante pour annoter les documents, améliorant ainsi la collaboration et la gestion documentaire. L'ajout d'annotations d'images sur du texte est une exigence courante, ce qui est possible en toute simplicité grâce à GroupDocs.Annotation pour .NET.
## Prérequis
Avant de vous lancer dans le processus d'ajout d'annotations d'image sur du texte à l'aide de GroupDocs.Annotation pour .NET, assurez-vous de disposer des éléments suivants :
1. Bibliothèque GroupDocs.Annotation pour .NET : téléchargez et installez la bibliothèque à partir de [ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : configurez un environnement de développement approprié, tel que Visual Studio ou tout autre IDE .NET.
3. Fichiers de documents et d'images : préparez le fichier de document (PDF, DOCX, etc.) et le fichier image que vous souhaitez utiliser pour les annotations.
4. Compréhension de base de C# : une connaissance du langage de programmation C# est nécessaire pour implémenter les extraits de code fournis dans ce didacticiel.

## Importer des espaces de noms
Avant de procéder au processus d’annotation, assurez-vous d’importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Étape 1 : Définir le chemin de sortie
Tout d’abord, définissez le chemin de sortie où le document annoté sera enregistré :
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Étape 2 : Initialiser l'annotateur
Initialiser le `Annotator` objet en fournissant le chemin du document d'entrée :
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation sera placé ici
}
```
## Étape 3 : Créer une annotation d'image
Créer un `ImageAnnotation` objet avec les propriétés souhaitées telles que les dimensions de la boîte, l'opacité, le numéro de page, le chemin de l'image et l'index z :
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Étape 4 : Ajouter une annotation
Ajoutez l'annotation d'image au document à l'aide de l' `Add` méthode de la `Annotator` objet:
```csharp
annotator.Add(image);
```
## Étape 5 : Enregistrer le document annoté
Enregistrez le document annoté dans le chemin de sortie spécifié :
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le message de réussite
Afficher un message de réussite avec le chemin d'accès au document annoté :
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
En conclusion, l'ajout d'annotations d'images sur du texte dans les applications .NET à l'aide de GroupDocs.Annotation est un processus simple. En suivant le guide étape par étape fourni dans ce tutoriel, vous pourrez annoter efficacement des documents et améliorer la collaboration et la gestion documentaire dans vos projets .NET.
## FAQ
### Puis-je annoter des documents autres que des PDF ?
Oui, GroupDocs.Annotation prend en charge divers formats de documents tels que DOCX, XLSX, PPTX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation ?
Oui, vous pouvez télécharger une version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide pour GroupDocs.Annotation ?
Vous pouvez obtenir de l'aide sur le forum communautaire GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).
### Ai-je besoin d’une licence temporaire à des fins de test ?
Oui, vous pouvez obtenir un permis temporaire auprès de [ici](https://purchase.groupdocs.com/temporary-license/) à des fins de test.
### Puis-je personnaliser l’apparence des annotations ?
Oui, GroupDocs.Annotation fournit diverses options pour personnaliser l'apparence des annotations telles que la couleur, l'opacité, la taille de la police, etc.