---
"description": "Découvrez comment ajouter des annotations d'image à vos documents avec GroupDocs.Annotation pour .NET. Améliorez la gestion de vos documents grâce à de puissantes fonctionnalités d'annotation."
"linktitle": "Ajouter une annotation d'image au document (chemin distant)"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation d'image au document (chemin distant)"
"url": "/fr/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Ajouter une annotation d'image au document (chemin distant)

## Introduction
Dans ce tutoriel, nous allons vous expliquer comment ajouter des annotations d'image à un document à l'aide de GroupDocs.Annotation pour .NET. Cette bibliothèque fournit des outils puissants pour annoter différents types de documents par programmation.
## Prérequis
Avant de commencer, assurez-vous d’avoir les éléments suivants :
1. GroupDocs.Annotation pour .NET : téléchargez et installez la bibliothèque depuis [ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : assurez-vous de disposer d’un environnement de développement fonctionnel configuré pour le développement .NET.
3. Document : Préparez le document à annoter. Pour ce tutoriel, nous supposerons que vous disposez d'un document PDF nommé `input.pdf`.
4. Image à annoter : Choisissez l'image à annoter. Assurez-vous d'avoir l'URL ou le chemin local de l'image à portée de main.

## Importer des espaces de noms
Avant de commencer à coder, importons les espaces de noms nécessaires :
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Étape 1 : définir le chemin de sortie
Tout d’abord, définissez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Initialiser l'annotateur
Créer une instance de `Annotator` classe et spécifiez le document d'entrée.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation sera placé ici
}
```
## Étape 3 : Ajouter une annotation d'image
Ajoutons maintenant l'annotation d'image au document. Nous allons spécifier ses propriétés, telles que sa position, son opacité, son numéro de page et son chemin d'accès.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Spécifier la position de l'annotation
    CreatedOn = DateTime.Now, // Définir la date de création
    Opacity = 0.7, // Définir l'opacité (0 à 1)
    PageNumber = 0, // Spécifiez le numéro de page
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Indiquez l'URL de l'image
};
annotator.Add(image); // Ajouter l'annotation de l'image
```
## Étape 4 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Save(outputPath);
```
## Étape 5 : Afficher le chemin de sortie
Informez l'utilisateur de la réussite de l'opération d'enregistrement du document et affichez le chemin de sortie.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce tutoriel, nous avons appris à ajouter des annotations d'image à un document avec GroupDocs.Annotation pour .NET. En suivant ces étapes, vous pourrez enrichir vos applications de gestion documentaire avec de puissantes fonctionnalités d'annotation.
## FAQ
### GroupDocs.Annotation peut-il être utilisé avec d'autres formats de documents en plus du PDF ?
Oui, GroupDocs.Annotation prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, etc.
### GroupDocs.Annotation est-il compatible avec .NET Core ?
Oui, GroupDocs.Annotation est compatible avec .NET Framework et .NET Core.
### Puis-je personnaliser l’apparence des annotations ?
Oui, vous pouvez personnaliser l’apparence des annotations telles que la couleur, l’opacité et la taille.
### GroupDocs.Annotation prend-il en charge les fonctionnalités d’annotation collaborative ?
Oui, GroupDocs.Annotation propose des fonctionnalités d’annotation collaborative pour une collaboration en temps réel sur des documents.
### Existe-t-il une version d'essai disponible pour tester ?
Oui, vous pouvez obtenir un essai gratuit de GroupDocs.Annotation à partir de [ici](https://releases.groupdocs.com/).