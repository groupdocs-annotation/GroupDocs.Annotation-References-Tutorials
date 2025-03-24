---
title: Charger le document à partir de l'URL
linktitle: Charger le document à partir de l'URL
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment annoter des documents PDF par programmation à l'aide de GroupDocs.Annotation pour .NET. Tutoriel étape par étape avec des exemples de code.
weight: 15
url: /fr/net/document-loading-essentials/load-document-from-url/
---

# Charger le document à partir de l'URL

## Introduction
GroupDocs.Annotation for .NET est une bibliothèque riche en fonctionnalités qui permet aux développeurs d'ajouter facilement des fonctionnalités d'annotation à leurs applications .NET. Avec GroupDocs.Annotation, vous pouvez annoter des documents PDF par programmation, permettant aux utilisateurs de surligner du texte, d'ajouter des commentaires, de dessiner des formes, etc. Ce didacticiel vous guidera à travers les étapes de chargement d'un document à partir d'une URL, d'ajout d'annotations et d'enregistrement du document annoté à l'aide de GroupDocs.Annotation pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des conditions préalables suivantes :
1. Visual Studio : assurez-vous que Visual Studio est installé sur votre ordinateur de développement.
2.  GroupDocs.Annotation pour .NET : téléchargez et installez GroupDocs.Annotation pour .NET à partir du[site web](https://releases.groupdocs.com/annotation/net/).
3. Connaissance de base de C# : Familiarisez-vous avec le langage de programmation C#.
4. Connexion Internet : vous aurez besoin d'une connexion Internet pour accéder aux ressources externes et télécharger des exemples de fichiers.

## Importer des espaces de noms
Commençons par importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Étape 1 : Charger le document à partir de l'URL
Pour annoter un document PDF à partir d'une URL, procédez comme suit :
### Étape 1.1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Étape 1.2 : Spécifiez l'URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true" ;
```
### Étape 1.3 : Charger le document
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Ajouter des annotations ici
    annotator.Save(outputPath);
}
```
## Étape 2 : ajouter des annotations
Maintenant, ajoutons des annotations au document chargé. Dans cet exemple, nous ajouterons une annotation de zone :
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Étape 3 : Enregistrer le document annoté
Enfin, enregistrez le document annoté dans le chemin de sortie spécifié :
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce didacticiel, nous avons appris à annoter des documents PDF à l'aide de GroupDocs.Annotation pour .NET. En suivant le guide étape par étape, vous pouvez intégrer de manière transparente la fonctionnalité d'annotation dans vos applications .NET, permettant ainsi aux utilisateurs de collaborer efficacement sur les fichiers PDF.

## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les frameworks .NET ?
Oui, GroupDocs.Annotation pour .NET est compatible avec divers frameworks .NET, notamment .NET Framework, .NET Core et .NET Standard.
### Puis-je personnaliser l’apparence des annotations ?
Absolument! GroupDocs.Annotation pour .NET fournit des options de personnalisation étendues, vous permettant de modifier l'apparence et le comportement des annotations en fonction de vos besoins.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
 Oui, vous pouvez télécharger un essai gratuit de GroupDocs.Annotation pour .NET à partir du[site web](https://releases.groupdocs.com/).
### Comment puis-je obtenir une assistance technique pour GroupDocs.Annotation pour .NET ?
 Si vous rencontrez des problèmes techniques ou avez des questions sur GroupDocs.Annotation pour .NET, vous pouvez demander de l'aide au[forum d'entraide](https://forum.groupdocs.com/c/annotation/10).
### Où puis-je acheter une licence pour GroupDocs.Annotation pour .NET ?
 Vous pouvez acheter une licence pour GroupDocs.Annotation pour .NET à partir du[page d'achat](https://purchase.groupdocs.com/buy).