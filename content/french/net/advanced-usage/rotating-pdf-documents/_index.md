---
"description": "Apprenez à faire pivoter vos documents PDF facilement grâce à Groupdocs.Annotation pour .NET. Améliorez votre gestion documentaire."
"linktitle": "Rotation des documents PDF"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Rotation des documents PDF"
"url": "/fr/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Rotation des documents PDF

## Introduction
La rotation de documents PDF peut être cruciale lorsque des fichiers doivent être visualisés ou traités différemment. Dans ce tutoriel, nous allons découvrir comment faire pivoter des documents PDF étape par étape avec Groupdocs.Annotation pour .NET.
## Prérequis
Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :
1. Bibliothèque Groupdocs.Annotation pour .NET : Assurez-vous d'avoir téléchargé et installé la bibliothèque Groupdocs.Annotation pour .NET. Vous pouvez la télécharger depuis [ici](https://releases.groupdocs.com/annotation/net/).
2. Connaissances de base de la programmation C# : ce didacticiel suppose que vous avez une compréhension de base du langage de programmation C# et que vous savez comment travailler avec les bibliothèques .NET.

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C# pour accéder aux fonctionnalités fournies par la bibliothèque Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Charger le document PDF
Commencez par charger le document PDF que vous souhaitez faire pivoter à l'aide de la `Annotator` classe.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Étape 2 : Définir la rotation et traiter les pages
Spécifiez l'angle de rotation et les pages à faire pivoter. Dans cet exemple, nous allons faire pivoter la première page de 90 degrés dans le sens des aiguilles d'une montre.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Étape 3 : Enregistrer le document pivoté
Enregistrez le document PDF pivoté avec les modifications spécifiées.
```csharp
annotator.Save("result.pdf");
```
## Étape 4 : Afficher la confirmation
Informez l'utilisateur que le document a été pivoté avec succès.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusion
La rotation de documents PDF est une opération fondamentale, et avec Groupdocs.Annotation pour .NET, elle devient simple et efficace. En suivant les étapes décrites dans ce tutoriel, vous pourrez facilement faire pivoter vos fichiers PDF selon vos besoins.
## FAQ
### Puis-je faire pivoter plusieurs pages dans un document PDF à l’aide de Groupdocs.Annotation pour .NET ?
Oui, vous pouvez spécifier plusieurs pages à faire pivoter en ajustant le `ProcessPages` propriété en conséquence.
### Groupdocs.Annotation pour .NET est-il compatible avec toutes les versions du framework .NET ?
Groupdocs.Annotation pour .NET prend en charge une large gamme de versions de .NET Framework, garantissant ainsi la compatibilité pour la plupart des environnements de développement.
### Groupdocs.Annotation pour .NET fournit-il des options permettant de faire pivoter les documents PDF dans différentes directions ?
Oui, vous pouvez faire pivoter les documents PDF dans le sens des aiguilles d'une montre, dans le sens inverse des aiguilles d'une montre ou selon des angles personnalisés en fonction de vos besoins.
### Puis-je intégrer Groupdocs.Annotation pour .NET dans mon système de gestion de documents existant ?
Absolument, Groupdocs.Annotation pour .NET offre des options d’intégration transparentes, vous permettant d’améliorer les capacités de gestion de documents sans effort.
### Existe-t-il une version d'essai disponible pour Groupdocs.Annotation pour .NET ?
Oui, vous pouvez obtenir une version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/).