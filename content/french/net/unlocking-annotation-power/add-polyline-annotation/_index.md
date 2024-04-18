---
title: Ajouter une annotation polyligne au document
linktitle: Ajouter une annotation polyligne au document
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter des annotations polylignes aux documents à l'aide de GroupDocs.Annotation pour .NET. Améliorez facilement les processus de collaboration et de révision de documents.
type: docs
weight: 18
url: /fr/net/unlocking-annotation-power/add-polyline-annotation/
---
## Introduction
GroupDocs.Annotation pour .NET est un outil puissant qui permet aux développeurs d'annoter des documents PDF et Microsoft Office par programme. Parmi ses fonctionnalités figure la possibilité d'ajouter des annotations polylignes aux documents, améliorant ainsi les processus de collaboration et de révision de documents.
## Conditions préalables
Avant de poursuivre ce didacticiel, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre système.
- Connaissance de base du langage de programmation C#.
-  GroupDocs.Annotation pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/annotation/net/).

## Importer des espaces de noms
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Étape 1 : Définir le chemin de sortie
Tout d’abord, définissez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : initialiser l'annotateur
Initialisez l'annotateur en fournissant le nom du document d'entrée.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 3 : Créer un objet d'annotation polyligne
Créez un objet d'annotation polyligne et définissez ses propriétés telles que la position, le message, l'opacité, la couleur du stylo, le style du stylo et la largeur du stylo.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Étape 4 : ajouter une annotation de polyligne
Ajoutez l'annotation polyligne au document à l'aide de l'objet annotateur.
```csharp
annotator.Add(polyline);
```
## Étape 5 : Enregistrer le document
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le message de réussite
Afficher un message confirmant la réussite de l'enregistrement du document.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce didacticiel, nous avons appris à ajouter une annotation polyligne à un document à l'aide de GroupDocs.Annotation pour .NET. Cette fonctionnalité améliore les processus de collaboration et de révision de documents, permettant aux utilisateurs de communiquer plus facilement et efficacement leurs commentaires et suggestions.
## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation pour .NET prend en charge les formats de documents courants tels que les formats PDF et Microsoft Office, notamment Word, Excel et PowerPoint.
### Puis-je personnaliser l’apparence des annotations ?
Oui, vous pouvez personnaliser diverses propriétés des annotations telles que la couleur, l'opacité, le style et la largeur en fonction de vos besoins.
### GroupDocs.Annotation pour .NET propose-t-il un essai gratuit ?
 Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET en visitant[ce lien](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Annotation pour .NET ?
 Vous pouvez trouver la documentation de GroupDocs.Annotation pour .NET[ici](https://reference.groupdocs.com/annotation/net/).
### Comment puis-je obtenir de l’aide pour tout problème ou requête lié à GroupDocs.Annotation pour .NET ?
 Vous pouvez obtenir de l'aide en visitant le forum GroupDocs.Annotation[ici](https://forum.groupdocs.com/c/annotation/10).