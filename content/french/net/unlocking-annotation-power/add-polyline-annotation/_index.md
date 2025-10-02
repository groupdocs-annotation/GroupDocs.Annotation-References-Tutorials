---
"description": "Apprenez à ajouter des annotations polylignes à vos documents avec GroupDocs.Annotation pour .NET. Améliorez facilement la collaboration et la révision de vos documents."
"linktitle": "Ajouter une annotation de polyligne au document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Ajouter une annotation de polyligne au document"
"url": "/fr/net/unlocking-annotation-power/add-polyline-annotation/"
type: docs
"weight": 18
---

# Ajouter une annotation de polyligne au document

## Introduction
GroupDocs.Annotation pour .NET est un outil puissant qui permet aux développeurs d'annoter des documents PDF et Microsoft Office par programmation. Parmi ses fonctionnalités, on trouve la possibilité d'ajouter des annotations polylignes aux documents, améliorant ainsi la collaboration et la révision des documents.
## Prérequis
Avant de poursuivre ce tutoriel, assurez-vous de disposer des éléments suivants :
- Visual Studio installé sur votre système.
- Connaissances de base du langage de programmation C#.
- Bibliothèque GroupDocs.Annotation pour .NET installée. Vous pouvez la télécharger ici. [ici](https://releases.groupdocs.com/annotation/net/).

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
## Étape 2 : Initialiser l'annotateur
Initialisez l'annotateur en fournissant le nom du document d'entrée.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Étape 3 : Créer un objet d'annotation de polyligne
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
## Étape 4 : Ajouter une annotation de polyligne
Ajoutez l’annotation polyligne au document à l’aide de l’objet annotateur.
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
Dans ce tutoriel, nous avons appris à ajouter une annotation polyligne à un document avec GroupDocs.Annotation pour .NET. Cette fonctionnalité améliore la collaboration et la révision des documents, facilitant ainsi la communication efficace des commentaires et suggestions des utilisateurs.
## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation pour .NET prend en charge les formats de documents courants tels que PDF et les formats Microsoft Office, notamment Word, Excel et PowerPoint.
### Puis-je personnaliser l’apparence des annotations ?
Oui, vous pouvez personnaliser diverses propriétés des annotations telles que la couleur, l’opacité, le style et la largeur en fonction de vos besoins.
### GroupDocs.Annotation pour .NET propose-t-il un essai gratuit ?
Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET en visitant [ce lien](https://releases.groupdocs.com/).
### Où puis-je trouver la documentation pour GroupDocs.Annotation pour .NET ?
Vous pouvez trouver la documentation de GroupDocs.Annotation pour .NET [ici](https://tutorials.groupdocs.com/annotation/net/).
### Comment puis-je obtenir de l'aide pour tout problème ou question lié à GroupDocs.Annotation pour .NET ?
Vous pouvez obtenir de l'aide en visitant le forum GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).