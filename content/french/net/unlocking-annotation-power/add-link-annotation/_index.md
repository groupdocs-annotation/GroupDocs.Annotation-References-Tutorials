---
title: Ajouter une annotation de lien au document
linktitle: Ajouter une annotation de lien au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations de lien aux documents à l'aide de Groupdocs.Annotation pour .NET. Améliorez la collaboration et l’interactivité sans effort.
type: docs
weight: 16
url: /fr/net/unlocking-annotation-power/add-link-annotation/
---
## Introduction
Groupdocs.Annotation for .NET est une bibliothèque puissante qui permet aux développeurs d'intégrer sans effort des fonctionnalités d'annotation complètes dans leurs applications .NET. L'une des fonctionnalités clés qu'il offre est la possibilité d'ajouter des annotations de liens aux documents, améliorant ainsi la collaboration et l'interactivité.
## Conditions préalables
Avant de vous lancer dans le processus d'ajout d'annotations de lien, assurez-vous de disposer des conditions préalables suivantes :
- Compréhension de base du langage de programmation C#.
- Installation de la bibliothèque Groupdocs.Annotation pour .NET.
- Accès à un document que vous souhaitez annoter.

## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires pour utiliser Groupdocs.Annotation pour les fonctionnalités .NET. Cela permet à votre application d'accéder aux classes et méthodes requises pour annoter des documents.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
Définissez le chemin où vous souhaitez enregistrer le document annoté.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : initialiser l'annotateur
 Créez une instance du`Annotator` classe en fournissant le chemin du document que vous souhaitez annoter.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation ira ici
}
```
## Étape 3 : Créer une annotation de lien
 Définir un`LinkAnnotation` objet et spécifiez ses propriétés telles que le message, l'opacité, le numéro de page, la couleur d'arrière-plan, les points, les réponses et l'URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    Url = "https://www.google.com"
};
```
## Étape 4 : Ajouter une annotation
 Ajoutez l'annotation de lien créée au document à l'aide du`Add` méthode de l’instance d’annotateur.
```csharp
annotator.Add(link);
```
## Étape 5 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le message de réussite
Informez l'utilisateur de la sauvegarde réussie du document annoté.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
En conclusion, en suivant les étapes ci-dessus, vous pouvez ajouter de manière transparente des annotations de lien aux documents à l'aide de Groupdocs.Annotation pour .NET. Cela améliore la collaboration documentaire et offre aux utilisateurs des fonctionnalités interactives.
## FAQ
### Groupdocs.Annotation pour .NET est-il compatible avec tous les types de documents ?
Groupdocs.Annotation pour .NET prend en charge un large éventail de formats de documents, notamment PDF, Word, Excel, etc.
### Puis-je personnaliser l’apparence des annotations ?
Oui, vous pouvez personnaliser diverses propriétés des annotations telles que la couleur, l'opacité et la taille en fonction de vos besoins.
### Groupdocs.Annotation pour .NET offre-t-il des fonctionnalités de collaboration en temps réel ?
Oui, Groupdocs.Annotation pour .NET fournit des fonctionnalités de collaboration en temps réel permettant à plusieurs utilisateurs d'annoter des documents simultanément.
### Un support technique est-il disponible pour les produits Groupdocs ?
 Oui, le support technique pour les produits Groupdocs est disponible via le forum et le support[ici](https://forum.groupdocs.com/c/annotation/10).
### Puis-je essayer Groupdocs.Annotation pour .NET avant d'acheter ?
Oui, vous pouvez bénéficier d'un essai gratuit de Groupdocs.Annotation pour .NET pour explorer ses fonctionnalités avant de faire un achat.[ici](https://purchase.groupdocs.com/temporary-license/).