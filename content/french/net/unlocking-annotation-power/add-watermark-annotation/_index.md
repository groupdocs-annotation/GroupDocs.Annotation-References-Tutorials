---
"description": "Apprenez à ajouter facilement des annotations en filigrane à vos documents grâce à GroupDocs.Annotation pour .NET. Améliorez la clarté et la sécurité de vos documents."
"linktitle": "Ajouter une annotation en filigrane au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation en filigrane au document"
"url": "/fr/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# Ajouter une annotation en filigrane au document

## Introduction
Dans ce tutoriel, nous allons vous expliquer comment ajouter un filigrane à un document à l'aide de GroupDocs.Annotation pour .NET. Les filigranes sont utiles pour indiquer le statut d'un document, le marquer comme confidentiel ou ajouter toute autre information pertinente.

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants :

1. GroupDocs.Annotation pour .NET : vous pouvez le télécharger à partir de [ici](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio : assurez-vous que Visual Studio est installé sur votre système.
3. Connaissances de base de C# : une familiarité avec le langage de programmation C# est nécessaire pour comprendre et implémenter les exemples de code.

## Importer des espaces de noms

Avant de commencer à coder, importons les espaces de noms nécessaires :

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Décomposons maintenant le processus d’ajout d’une annotation de filigrane en plusieurs étapes :

## Étape 1 : Définir le chemin de sortie

Tout d'abord, nous devons définir le chemin de sortie où le document annoté sera enregistré. Nous utiliserons `Path` classe de `System.IO` espace de noms pour combiner le chemin du répertoire de sortie avec le nom de fichier.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 2 : Initialiser l'annotateur

Ensuite, nous initialiserons l'annotateur en fournissant le chemin d'accès au document d'entrée. Cela nous permettra d'ajouter des annotations au document.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation sera placé ici
}
```

## Étape 3 : Créer une annotation en filigrane

Maintenant, créons un objet d'annotation de filigrane avec les propriétés souhaitées telles que l'angle, la position, le texte, la couleur de police, l'opacité, etc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Étape 4 : ajouter une annotation en filigrane

Maintenant, nous allons ajouter l'annotation en filigrane au document en utilisant le `Add` méthode de l'objet annotateur.

```csharp
annotator.Add(watermark);
```

## Étape 5 : Enregistrer le document

Enfin, nous enregistrerons le document annoté dans le chemin de sortie spécifié.

```csharp
annotator.Save(outputPath);
```

## Conclusion

Dans ce tutoriel, nous avons appris à ajouter un filigrane à un document à l'aide de GroupDocs.Annotation pour .NET. Les filigranes sont un outil précieux pour marquer les documents avec des informations pertinentes ou indiquer leur statut.

## FAQ

### Q : Puis-je personnaliser l’apparence de l’annotation du filigrane ?

R : Oui, vous pouvez personnaliser diverses propriétés telles que le texte, la taille de la police, la couleur, l'opacité, la position, etc., pour adapter le filigrane à vos besoins.

### Q : GroupDocs.Annotation pour .NET est-il compatible avec différents formats de documents ?

R : Oui, GroupDocs.Annotation prend en charge une large gamme de formats de documents, notamment les formats PDF, Microsoft Word, Excel, PowerPoint et image.

### Q : Puis-je ajouter plusieurs annotations à un seul document ?

R : Absolument, GroupDocs.Annotation vous permet d’ajouter plusieurs annotations de différents types à un seul document, permettant ainsi un balisage complet du document.

### Q : GroupDocs.Annotation prend-il en charge l’annotation collaborative ?

R : Oui, GroupDocs.Annotation facilite l’annotation collaborative en permettant aux utilisateurs d’ajouter des commentaires, des réponses et des annotations, favorisant ainsi une collaboration efficace entre les membres de l’équipe.

### Q : Existe-t-il une version d’essai disponible pour GroupDocs.Annotation pour .NET ?

R : Oui, vous pouvez télécharger une version d’essai gratuite à partir de [ici](https://releases.groupdocs.com/).