---
title: Ajouter une annotation de fragment de texte de recherche au document
linktitle: Ajouter une annotation de fragment de texte de recherche au document
second_title: API GroupDocs.Annotation .NET
description: Explorez la puissance de GroupDocs.Annotation pour .NET et ajoutez sans effort des fonctionnalités d'annotation de documents à vos applications.
type: docs
weight: 20
url: /fr/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Introduction
Dans le domaine du développement .NET, GroupDocs.Annotation se distingue comme un outil puissant pour annoter des documents de manière transparente. Que vous soyez un développeur chevronné ou que vous débutiez tout juste dans le monde de .NET, ce didacticiel complet vous guidera à travers les bases de l'utilisation de GroupDocs.Annotation pour .NET, de l'importation d'espaces de noms à la maîtrise des subtilités de l'ajout d'annotations de fragments de texte de recherche à votre documents.
## Introduction
GroupDocs.Annotation pour .NET permet aux développeurs d'intégrer sans effort des fonctionnalités d'annotation de documents dans leurs applications. Grâce à son API intuitive et à ses fonctionnalités robustes, les développeurs peuvent annoter divers formats de documents, notamment des PDF, des documents Microsoft Office, des images, etc.
## Conditions préalables
Avant de plonger dans GroupDocs.Annotation pour .NET, assurez-vous que les conditions préalables suivantes sont remplies :

## Importer des espaces de noms
Tout d’abord, importez les espaces de noms nécessaires pour accéder aux classes et méthodes GroupDocs.Annotation dans votre projet .NET :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
Commencez par définir le chemin de sortie où le document annoté sera enregistré :
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : initialiser l'annotateur
 Ensuite, initialisez une instance de`Annotator` class en fournissant le chemin d'accès au document que vous souhaitez annoter :
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 3 : Créer une annotation de fragment de texte de recherche
 Créer un`SearchTextFragment` objet avec les propriétés souhaitées, telles que le texte à rechercher, la taille de la police, la famille de polices, la couleur de la police et la couleur d'arrière-plan :
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Étape 4 : Ajouter une annotation
 Ajoutez l'annotation de fragment de texte de recherche créée au document à l'aide du`Add` méthode de l'annotateur :
```csharp
annotator.Add(searchText);
```
## Étape 5 : Enregistrer le document annoté
Enregistrez le document annoté dans le chemin de sortie spécifié :
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le message de réussite
Informez l'utilisateur que le document a été enregistré avec succès :
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
En conclusion, GroupDocs.Annotation pour .NET simplifie le processus d'ajout d'annotations aux documents, améliorant ainsi les processus de collaboration et de révision de documents. En suivant les étapes décrites dans ce guide, vous pouvez intégrer de manière transparente les fonctionnalités d'annotation de documents dans vos applications .NET.
## FAQ
### GroupDocs.Annotation est-il compatible avec tous les formats de documents ?
Oui, GroupDocs.Annotation prend en charge un large éventail de formats de documents, notamment les PDF, les documents Microsoft Office, les images, etc.
### Puis-je personnaliser l’apparence des annotations ?
Absolument! GroupDocs.Annotation fournit des options de personnalisation étendues pour les annotations, vous permettant d'ajuster des propriétés telles que la taille, la couleur et le style de la police.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation ?
 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Annotation pour explorer ses fonctionnalités et capacités avant de faire un achat.[ici](https://releases.groupdocs.com/)..
### Où puis-je trouver de l’assistance pour GroupDocs.Annotation ?
 Pour obtenir de l'aide et de l'assistance concernant GroupDocs.Annotation, vous pouvez visiter le site GroupDocs[forum](https://forum.groupdocs.com/c/annotation/10) dédié aux requêtes et discussions liées aux annotations.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Annotation ?
 Vous pouvez acquérir une licence temporaire pour GroupDocs.Annotation via GroupDocs[site web](https://purchase.groupdocs.com/temporary-license/), vous permettant d'évaluer pleinement le produit.