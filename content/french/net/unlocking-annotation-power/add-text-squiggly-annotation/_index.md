---
"description": "Apprenez à ajouter facilement des annotations textuelles ondulées à vos documents grâce à Groupdocs.Annotation pour .NET. Améliorez la collaboration et la révision de vos documents."
"linktitle": "Ajouter une annotation textuelle ondulée au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation textuelle ondulée au document"
"url": "/fr/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# Ajouter une annotation textuelle ondulée au document

## Introduction

Groupdocs.Annotation pour .NET est une bibliothèque polyvalente qui permet aux développeurs d'intégrer facilement de puissantes fonctionnalités d'annotation à leurs applications .NET. Que vous travailliez avec des fichiers PDF, Word ou d'autres formats de fichiers courants, Groupdocs.Annotation offre une solution transparente pour annoter et améliorer la collaboration documentaire.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous que vous disposez des prérequis suivants :

## Importer des espaces de noms

Assurez-vous d'importer les espaces de noms nécessaires pour accéder aux fonctionnalités fournies par Groupdocs.Annotation pour .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Maintenant que nous avons couvert les prérequis, décomposons le processus d'ajout d'annotations textuelles ondulées en plusieurs étapes.

## Étape 1 : Définir le chemin de sortie

Définissez le chemin où le document annoté sera enregistré.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 2 : Initialiser l'annotateur

Initialisez l'objet Annotator en fournissant le chemin du document d'entrée.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation va ici
}
```

## Étape 3 : Créer une annotation ondulée

Créez un objet SquigglyAnnotation et spécifiez ses propriétés.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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
    }
};
```

## Étape 4 : Ajouter une annotation

Ajoutez l’annotation ondulée créée au document.

```csharp
annotator.Add(squiggly);
```

## Étape 5 : Enregistrer le document

Enregistrez le document annoté dans le chemin de sortie spécifié.

```csharp
annotator.Save(outputPath);
```

## Étape 6 : Afficher la confirmation

Afficher un message confirmant la réussite de l'enregistrement du document annoté.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

En conclusion, Groupdocs.Annotation pour .NET offre aux développeurs un ensemble d'outils performants pour intégrer facilement des fonctionnalités d'annotation de documents à leurs applications .NET. En suivant ce guide étape par étape, vous pourrez facilement ajouter des annotations textuelles ondulées à vos documents, améliorant ainsi la collaboration et la révision des documents.

## FAQ

### Q : Groupdocs.Annotation peut-il prendre en charge l’annotation sur différents formats de fichiers ?

R : Oui, Groupdocs.Annotation prend en charge l’annotation sur une large gamme de formats de fichiers, notamment les fichiers PDF, les documents Word, les feuilles Excel, etc.

### Q : Groupdocs.Annotation est-il compatible avec les applications de bureau et Web ?

R : Absolument ! Groupdocs.Annotation s'intègre parfaitement aux applications de bureau et Web, offrant flexibilité et polyvalence.

### Q : Existe-t-il des options de licence disponibles pour Groupdocs.Annotation ?

: Oui, Groupdocs.Annotation propose des options de licence flexibles adaptées aux besoins individuels ou d'entreprise, y compris des licences temporaires à des fins d'essai.

### Q : Les annotations créées à l’aide de Groupdocs.Annotation peuvent-elles être personnalisées ?

R : Certainement ! Groupdocs.Annotation offre de nombreuses options de personnalisation pour les annotations, permettant aux développeurs d'adapter les annotations à leurs besoins spécifiques.

### Q : Groupdocs.Annotation offre-t-il un support et une documentation aux développeurs ?

R : En effet ! Groupdocs.Annotation fournit une documentation complète et des forums d'assistance dédiés pour aider les développeurs à utiliser efficacement ses fonctionnalités.