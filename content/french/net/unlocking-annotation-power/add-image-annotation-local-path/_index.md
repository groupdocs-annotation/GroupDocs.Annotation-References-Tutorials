---
"description": "Apprenez à ajouter des annotations d'image à vos documents avec GroupDocs.Annotation pour .NET. Améliorez facilement vos capacités de traitement de documents."
"linktitle": "Ajouter une annotation d'image au document (chemin local)"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation d'image au document (chemin local)"
"url": "/fr/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Ajouter une annotation d'image au document (chemin local)

## Introduction
GroupDocs.Annotation pour .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter différents types d'annotations aux documents par programmation. Dans ce tutoriel, nous allons apprendre à ajouter des annotations d'image à un document via un chemin local.
## Prérequis
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. Connaissances de base du langage de programmation C#.
2. Visual Studio installé sur votre système.
3. Bibliothèque GroupDocs.Annotation pour .NET installée ou tutorialsd dans votre projet.
4. Un document d'entrée (par exemple, PDF) et un fichier image pour l'annotation.
## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre fichier C#. Ces espaces de noms donnent accès aux classes et méthodes nécessaires à l'utilisation de GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Étape 1 : Définir le chemin de sortie
Définissez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Initialiser l'annotateur
Initialisez l'annotateur en fournissant le chemin vers le document d'entrée.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation va ici
}
```
## Étape 3 : Créer une annotation d'image
Créer une instance de `ImageAnnotation` classe et spécifiez ses propriétés telles que la position, l'opacité, le numéro de page et le chemin de l'image.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Étape 4 : Ajouter une annotation
Ajoutez l'annotation d'image créée au document à l'aide de l' `Add` méthode de l'annotateur.
```csharp
annotator.Add(image);
```
## Étape 5 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie.
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le chemin de sortie
Affiche un message indiquant la réussite de l'enregistrement du document et l'emplacement du fichier de sortie.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce tutoriel, nous avons appris à ajouter des annotations d'image à un document avec GroupDocs.Annotation pour .NET. En suivant ces étapes simples, vous pouvez améliorer vos capacités de traitement de documents grâce à de puissantes fonctionnalités d'annotation.
## FAQ
### Puis-je annoter des documents autres que PDF ?
Oui, GroupDocs.Annotation prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, etc.
### GroupDocs.Annotation est-il compatible avec .NET Core ?
Oui, GroupDocs.Annotation est compatible avec .NET Framework et .NET Core.
### Puis-je personnaliser l’apparence des annotations ?
Absolument, vous pouvez personnaliser l'apparence, la taille, la couleur et d'autres propriétés des annotations en fonction de vos besoins.
### GroupDocs.Annotation fournit-il un support pour l'annotation collaborative ?
Oui, GroupDocs.Annotation propose des fonctionnalités d’annotation collaborative qui permettent à plusieurs utilisateurs d’annoter des documents simultanément.
### Où puis-je trouver de l’aide ou du soutien supplémentaire ?
Vous pouvez visiter le forum GroupDocs.Annotation pour obtenir de l'aide et du soutien de la communauté.