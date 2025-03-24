---
title: Ajouter une annotation de distance au document
linktitle: Ajouter une annotation de distance au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations de distance aux documents à l'aide de GroupDocs.Annotation pour .NET. Améliorez la collaboration et la communication sans effort.
weight: 12
url: /fr/net/unlocking-annotation-power/add-distance-annotation/
---
## Introduction
Dans ce didacticiel, vous apprendrez comment ajouter une annotation à distance à un document à l'aide de GroupDocs.Annotation pour .NET. Suivez ces étapes pour accomplir la tâche :
## Conditions préalables

Assurez-vous que les conditions préalables suivantes sont remplies avant de continuer :

-  GroupDocs.Annotation pour la bibliothèque .NET : téléchargez et installez la bibliothèque GroupDocs.Annotation pour .NET à partir de[ce lien](https://releases.groupdocs.com/annotation/net/).
- Document à annoter : préparez le document (par exemple, PDF) auquel vous souhaitez ajouter l'annotation de distance.
- Environnement de développement : configurez votre environnement de développement avec Visual Studio ou tout autre IDE de votre choix.

## Importer des espaces de noms

Avant de commencer, assurez-vous d'inclure les espaces de noms nécessaires dans votre code. Ces espaces de noms sont essentiels pour accéder aux classes et méthodes requises.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Étape 1 : initialiser l'annotateur

 Commencez par initialiser le`Annotator` objet avec le chemin d’accès au document que vous souhaitez annoter.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Le code d'annotation ira ici
}
```

## Étape 2 : Créer une annotation de distance

 Maintenant, créez un`DistanceAnnotation` objet et configurez ses propriétés telles que les dimensions de la boîte, le message, l'opacité, la couleur du stylo, etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

 Ajoutez l'annotation de distance créée au document à l'aide du`Add` méthode de l’objet annotateur.

```csharp
annotator.Add(distance);
```

## Étape 4 : Enregistrer le document

Enregistrez le document annoté à l'emplacement souhaité sur votre système.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Étape 5 : Afficher la confirmation

Enfin, affichez un message confirmant la réussite de l'enregistrement du document annoté.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

L'ajout d'annotations de distance aux documents à l'aide de GroupDocs.Annotation pour .NET est un processus simple. En suivant les étapes décrites dans ce didacticiel, vous pouvez améliorer vos documents avec des annotations précieuses, facilitant ainsi une meilleure collaboration et communication.

## FAQ

### Q : Puis-je personnaliser l’apparence de l’annotation de distance ?

R : Oui, vous pouvez personnaliser diverses propriétés telles que la couleur, l'opacité, le style de ligne, etc., en fonction de vos besoins.

### Q : GroupDocs.Annotation prend-il en charge les annotations sur différents types de documents ?

R : Oui, GroupDocs.Annotation prend en charge les annotations sur un large éventail de formats de documents, notamment PDF, Word, Excel, PowerPoint, etc.

### Q : Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation ?

 R : Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Annotation à partir de[ce lien](https://releases.groupdocs.com/).

### Q : Où puis-je trouver la documentation de GroupDocs.Annotation pour .NET ?

 R : Vous pouvez vous référer à la documentation détaillée disponible[ici](https://tutorials.groupdocs.com/annotation/net/).

### Q : Comment puis-je obtenir de l'aide ou de l'assistance concernant GroupDocs.Annotation ?

 R : Vous pouvez demander de l'aide et de l'aide auprès du forum de la communauté GroupDocs.Annotation.[ici](https://forum.groupdocs.com/c/annotation/10).