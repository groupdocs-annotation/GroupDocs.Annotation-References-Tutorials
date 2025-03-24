---
title: Ajouter une annotation de texte ondulé au document
linktitle: Ajouter une annotation de texte ondulé au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter sans effort des annotations de texte ondulées à des documents à l'aide de Groupdocs.Annotation pour .NET. Améliorez les processus de collaboration et de révision des documents.
weight: 25
url: /fr/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# Ajouter une annotation de texte ondulé au document

## Introduction

Groupdocs.Annotation for .NET est une bibliothèque polyvalente qui permet aux développeurs d'intégrer sans effort des fonctionnalités d'annotation robustes dans leurs applications .NET. Que vous travailliez avec des PDF, des documents Word ou d'autres formats de fichiers populaires, Groupdocs.Annotation fournit une solution transparente pour annoter et améliorer la collaboration documentaire.

## Conditions préalables

Avant de plonger dans le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :

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

Maintenant que nous avons couvert les conditions préalables, décomposons le processus d'ajout d'annotations de texte ondulées en plusieurs étapes.

## Étape 1 : Définir le chemin de sortie

Définissez le chemin où le document annoté sera enregistré.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 2 : initialiser l'annotateur

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

Ajoutez l'annotation ondulée créée au document.

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

En conclusion, Groupdocs.Annotation pour .NET fournit aux développeurs un ensemble d'outils robustes pour intégrer de manière transparente les fonctionnalités d'annotation de documents dans leurs applications .NET. En suivant ce guide étape par étape, vous pouvez facilement ajouter des annotations de texte ondulées à vos documents, améliorant ainsi les processus de collaboration et de révision de documents.

## FAQ

### Q : Groupdocs.Annotation peut-il prendre en charge les annotations sur différents formats de fichiers ?

R : Oui, Groupdocs.Annotation prend en charge l'annotation sur un large éventail de formats de fichiers, notamment les PDF, les documents Word, les feuilles Excel, etc.

### Q : Groupdocs.Annotation est-il compatible avec les applications de bureau et Web ?

R : Absolument ! Groupdocs.Annotation peut être intégré de manière transparente aux applications de bureau et Web, offrant flexibilité et polyvalence.

### Q : Existe-t-il des options de licence disponibles pour Groupdocs.Annotation ?

: Oui, Groupdocs.Annotation propose des options de licence flexibles adaptées aux besoins individuels ou d'entreprise, y compris des licences temporaires à des fins d'essai.

### Q : Les annotations créées à l’aide de Groupdocs.Annotation peuvent-elles être personnalisées ?

R : Certainement ! Groupdocs.Annotation fournit des options de personnalisation étendues pour les annotations, permettant aux développeurs d'adapter les annotations à leurs besoins spécifiques.

### Q : Groupdocs.Annotation propose-t-il une assistance et une documentation aux développeurs ?

R : En effet ! Groupdocs.Annotation fournit une documentation complète et des forums d'assistance dédiés pour aider les développeurs à utiliser efficacement ses fonctionnalités.