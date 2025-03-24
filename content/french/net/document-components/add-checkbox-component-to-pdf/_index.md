---
title: Ajouter un composant de case à cocher au document PDF
linktitle: Ajouter un composant de case à cocher au document PDF
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment ajouter un composant Checkbox aux documents PDF à l’aide de Groupdocs.Annotation pour .NET. Améliorez vos PDF avec des éléments interactifs.
weight: 11
url: /fr/net/document-components/add-checkbox-component-to-pdf/
---
## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus d'ajout d'un composant Checkbox à un document PDF à l'aide de Groupdocs.Annotation pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
1.  Groupdocs.Annotation pour le SDK .NET : vous pouvez le télécharger à partir de[ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : assurez-vous d'avoir configuré un environnement de développement .NET.

## Importer des espaces de noms
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Maintenant, décomposons l'exemple en plusieurs étapes :
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ici, nous définissons le chemin de sortie où le document PDF modifié sera enregistré.
## Étape 2 : initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Initialisez le`Annotator` objet en transmettant le chemin du document PDF d’entrée.
## Étape 3 : Créer un composant de case à cocher
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 Créer un`CheckBoxComponent` objet et personnaliser ses propriétés comme`Checked`, `Box` dimensions,`PenColor`, `Style`et ajoutez quelques réponses.
## Étape 4 : Ajouter un composant de case à cocher
```csharp
annotator.Add(checkBox);
```
Ajoutez le composant de case à cocher créé au document PDF.
## Étape 5 : Enregistrer le document
```csharp
annotator.Save("result.pdf");
```
Enregistrez le document PDF modifié avec le composant case à cocher.
## Étape 6 : Afficher le chemin de sortie
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Affichez le chemin où le document PDF modifié est enregistré.

## Conclusion
Dans ce didacticiel, nous avons appris comment ajouter un composant Checkbox à un document PDF à l'aide de Groupdocs.Annotation pour .NET. Grâce à ces connaissances, vous pouvez améliorer vos documents PDF avec des éléments interactifs.
## FAQ
### Puis-je personnaliser l’apparence de la case à cocher ?
Oui, vous pouvez personnaliser diverses propriétés telles que la couleur, le style et la taille en fonction de vos besoins.
### Groupdocs.Annotation pour .NET est-il adapté à un usage commercial ?
Oui, Groupdocs.Annotation pour .NET propose des licences commerciales pour les entreprises.
### Puis-je essayer Groupdocs.Annotation pour .NET avant d'acheter ?
 Oui, vous pouvez bénéficier d'un essai gratuit auprès de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de l’assistance pour Groupdocs.Annotation pour .NET ?
 Vous pouvez trouver du soutien et des ressources sur le[Forum Groupdocs](https://forum.groupdocs.com/c/annotation/10).
### Ai-je besoin d’une licence temporaire à des fins de test ?
 Vous pouvez obtenir une licence temporaire pour effectuer des tests auprès de[ici](https://purchase.groupdocs.com/temporary-license/).