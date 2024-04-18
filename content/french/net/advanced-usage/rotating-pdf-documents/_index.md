---
title: Rotation de documents PDF
linktitle: Rotation de documents PDF
second_title: API GroupDocs.Annotation .NET
description: Apprenez à faire pivoter des documents PDF sans effort à l'aide de Groupdocs.Annotation pour .NET. Améliorer l’efficacité de la gestion des documents.
type: docs
weight: 22
url: /fr/net/advanced-usage/rotating-pdf-documents/
---
## Introduction
La rotation de documents PDF peut s'avérer une tâche cruciale lorsqu'il s'agit de fichiers qui doivent être visualisés ou traités différemment. Dans ce didacticiel, nous explorerons comment faire pivoter des documents PDF étape par étape à l'aide de Groupdocs.Annotation pour .NET.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous d'avoir les prérequis suivants :
1.  Groupdocs.Annotation pour la bibliothèque .NET : assurez-vous d'avoir téléchargé et installé la bibliothèque Groupdocs.Annotation pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/annotation/net/).
2. Connaissance de base de la programmation C# : ce didacticiel suppose que vous possédez une compréhension de base du langage de programmation C# et comment utiliser les bibliothèques .NET.

## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C# pour accéder aux fonctionnalités fournies par la bibliothèque Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Charger le document PDF
 Commencez par charger le document PDF que vous souhaitez faire pivoter à l'aide du`Annotator` classe.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Étape 2 : Définir la rotation et les pages de processus
Spécifiez l'angle de rotation et les pages que vous souhaitez faire pivoter. Dans cet exemple, nous allons faire pivoter la première page de 90 degrés dans le sens des aiguilles d'une montre.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Étape 3 : Enregistrez le document pivoté
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
La rotation des documents PDF est une opération fondamentale, et avec Groupdocs.Annotation pour .NET, cela devient simple et efficace. En suivant les étapes décrites dans ce didacticiel, vous pouvez facilement faire pivoter les fichiers PDF selon vos besoins.
## FAQ
### Puis-je faire pivoter plusieurs pages dans un document PDF à l’aide de Groupdocs.Annotation pour .NET ?
 Oui, vous pouvez spécifier plusieurs pages à faire pivoter en ajustant le`ProcessPages` propriété en conséquence.
### Groupdocs.Annotation pour .NET est-il compatible avec toutes les versions du framework .NET ?
Groupdocs.Annotation for .NET prend en charge une large gamme de versions du framework .NET, garantissant la compatibilité avec la plupart des environnements de développement.
### Groupdocs.Annotation pour .NET propose-t-il des options pour faire pivoter les documents PDF dans différentes directions ?
Oui, vous pouvez faire pivoter les documents PDF dans le sens des aiguilles d'une montre, dans le sens inverse des aiguilles d'une montre ou selon des angles personnalisés en fonction de vos besoins.
### Puis-je intégrer Groupdocs.Annotation pour .NET dans mon système de gestion de documents existant ?
Absolument, Groupdocs.Annotation pour .NET offre des options d'intégration transparentes, vous permettant d'améliorer les capacités de gestion de documents sans effort.
### Existe-t-il une version d’essai disponible pour Groupdocs.Annotation pour .NET ?
 Oui, vous pouvez obtenir une version d'essai gratuite auprès de[ici](https://releases.groupdocs.com/).