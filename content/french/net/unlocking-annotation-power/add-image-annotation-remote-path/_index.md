---
title: Ajouter une annotation d'image au document (chemin distant)
linktitle: Ajouter une annotation d'image au document (chemin distant)
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations d'image aux documents à l'aide de GroupDocs.Annotation pour .NET. Améliorez la gestion des documents grâce à de puissantes fonctionnalités d’annotation.
weight: 15
url: /fr/net/unlocking-annotation-power/add-image-annotation-remote-path/
---

# Ajouter une annotation d'image au document (chemin distant)

## Introduction
Dans ce didacticiel, nous allons parcourir le processus d'ajout d'annotations d'image à un document à l'aide de GroupDocs.Annotation pour .NET. Cette bibliothèque fournit des outils puissants pour annoter différents types de documents par programmation.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Annotation pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : assurez-vous de disposer d'un environnement de développement fonctionnel configuré pour le développement .NET.
3.  Document : Préparez le document que vous souhaitez annoter. Pour ce didacticiel, nous supposerons que vous disposez d'un document PDF nommé`input.pdf`.
4. Image pour l'annotation : choisissez l'image que vous souhaitez utiliser pour l'annotation. Assurez-vous que l'URL de l'image ou le chemin local est prêt.

## Importer des espaces de noms
Avant de commencer à coder, importons les espaces de noms nécessaires :
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Étape 1 : Définir le chemin de sortie
Tout d’abord, définissez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : initialiser l'annotateur
 Créez une instance du`Annotator` classe et spécifiez le document d’entrée.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation ira ici
}
```
## Étape 3 : ajouter une annotation d'image
Maintenant, ajoutons l'annotation d'image au document. Nous spécifierons les propriétés de l'annotation d'image telles que la position, l'opacité, le numéro de page et le chemin de l'image.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Spécifier la position de l'annotation
    CreatedOn = DateTime.Now, // Définir la date de création
    Opacity = 0.7, // Définir l'opacité (0 à 1)
    PageNumber = 0, // Précisez le numéro de page
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Fournissez l'URL de l'image
};
annotator.Add(image); // Ajouter l'annotation de l'image
```
## Étape 4 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Save(outputPath);
```
## Étape 5 : Afficher le chemin de sortie
Informez l'utilisateur de l'opération réussie d'enregistrement du document et affichez le chemin de sortie.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter des annotations d'image à un document à l'aide de GroupDocs.Annotation pour .NET. En suivant ces étapes, vous pouvez améliorer vos applications de gestion de documents avec de puissantes fonctionnalités d'annotation.
## FAQ
### GroupDocs.Annotation peut-il être utilisé avec d'autres formats de documents que le PDF ?
Oui, GroupDocs.Annotation prend en charge divers formats de documents, notamment Word, Excel, PowerPoint, etc.
### GroupDocs.Annotation est-il compatible avec .NET Core ?
Oui, GroupDocs.Annotation est compatible avec .NET Framework et .NET Core.
### Puis-je personnaliser l’apparence des annotations ?
Oui, vous pouvez personnaliser l'apparence des annotations telles que la couleur, l'opacité et la taille.
### GroupDocs.Annotation prend-il en charge les fonctionnalités d'annotation collaborative ?
Oui, GroupDocs.Annotation propose des fonctionnalités d'annotation collaborative pour une collaboration en temps réel sur des documents.
### Existe-t-il une version d'essai disponible pour tester ?
 Oui, vous pouvez obtenir un essai gratuit de GroupDocs.Annotation auprès de[ici](https://releases.groupdocs.com/).