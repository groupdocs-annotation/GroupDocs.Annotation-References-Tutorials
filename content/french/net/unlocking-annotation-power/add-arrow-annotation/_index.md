---
title: Ajouter une annotation de flèche au document
linktitle: Ajouter une annotation de flèche au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations fléchées à vos documents à l'aide de GroupDocs.Annotation pour .NET. Améliorez la clarté et l’interactivité des documents sans effort.
weight: 11
url: /fr/net/unlocking-annotation-power/add-arrow-annotation/
---
## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'annotations fléchées à vos documents à l'aide de GroupDocs.Annotation pour .NET. Les annotations fléchées sont utiles pour indiquer une direction ou souligner des éléments spécifiques dans un document.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  GroupDocs.Annotation pour .NET : installez la bibliothèque GroupDocs.Annotation pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : assurez-vous de disposer d'un environnement de développement configuré pour le développement .NET, y compris Visual Studio ou tout autre IDE préféré.

## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires pour accéder aux classes et méthodes requises pour l'annotation.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : initialiser l'annotateur
Initialisez l'annotateur en fournissant le chemin du fichier du document d'entrée.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 2 : Créer une annotation de flèche
Créez une instance de la classe ArrowAnnotation et définissez ses propriétés telles que la position, le message, l'opacité, la couleur du stylo, le style, la largeur, etc.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
## Étape 3 : Ajouter une annotation
 Ajoutez l'annotation de flèche au document à l'aide du`Add` méthode de l’annotateur.
```csharp
	annotator.Add(arrow);
```
## Étape 4 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
	annotator.Save(outputPath);
}
```
## Étape 5 : Afficher la confirmation
Afficher un message de confirmation indiquant la réussite de l'enregistrement du document.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Vous avez maintenant ajouté avec succès une annotation de flèche à votre document à l'aide de GroupDocs.Annotation pour .NET.

## Conclusion
Dans ce didacticiel, nous avons couvert le processus d'ajout d'annotations de flèches aux documents à l'aide de GroupDocs.Annotation pour .NET. En suivant ces étapes, vous pouvez améliorer vos documents avec des indicateurs directionnels clairs, les rendant plus informatifs et attrayants.
## FAQ
### Puis-je personnaliser l’apparence de l’annotation en forme de flèche ?
Oui, vous pouvez personnaliser diverses propriétés telles que la couleur, le style, la largeur et l'opacité en fonction de vos préférences et des exigences du document.
### GroupDocs.Annotation est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation prend en charge un large éventail de formats de documents, notamment PDF, DOCX, PPTX, XLSX, etc.
### Puis-je ajouter des annotations par programme à l’aide de GroupDocs.Annotation ?
Oui, GroupDocs.Annotation fournit des API qui vous permettent d'ajouter, de modifier et de supprimer par programmation des annotations des documents.
### GroupDocs.Annotation propose-t-il un essai gratuit ?
 Oui, vous pouvez essayer GroupDocs.Annotation gratuitement en le téléchargeant depuis[ici](https://releases.groupdocs.com/).
### Où puis-je obtenir une assistance technique pour GroupDocs.Annotation ?
Pour obtenir un support et une assistance techniques, vous pouvez visiter le forum GroupDocs.Annotation[ici](https://forum.groupdocs.com/c/annotation/10).