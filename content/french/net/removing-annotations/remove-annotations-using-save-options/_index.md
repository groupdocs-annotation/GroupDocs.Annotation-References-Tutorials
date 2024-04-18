---
title: Supprimer les annotations à l'aide des options d'enregistrement dans .NET
linktitle: Supprimer les annotations à l'aide des options d'enregistrement dans .NET
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment supprimer des annotations d'un PDF et d'autres documents dans .NET à l'aide de GroupDocs.Annotation. Guide étape par étape avec des exemples de code.
type: docs
weight: 14
url: /fr/net/removing-annotations/remove-annotations-using-save-options/
---
## Introduction

GroupDocs.Annotation for .NET est un outil puissant qui permet aux développeurs d'ajouter facilement des fonctionnalités d'annotation à leurs applications .NET. Que vous travailliez sur un système de gestion de documents, une plateforme de collaboration ou toute autre application impliquant le traitement de documents, GroupDocs.Annotation fournit un ensemble complet de fonctionnalités pour annoter des PDF et d'autres formats de documents de manière transparente.

## Conditions préalables

Avant de plonger dans le monde de l'annotation de documents à l'aide de GroupDocs.Annotation pour .NET, assurez-vous d'avoir les conditions préalables suivantes en place :

### 1. Installez GroupDocs.Annotation pour .NET

 Commencez par télécharger et installer GroupDocs.Annotation pour .NET. Vous pouvez télécharger la dernière version à partir du[download page](https://releases.groupdocs.com/annotation/net/).

## Importation d'espaces de noms

Pour commencer à utiliser GroupDocs.Annotation dans votre projet .NET, vous devez importer les espaces de noms nécessaires. Voici les espaces de noms que vous utiliserez couramment :

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Passons maintenant au processus de suppression des annotations d'un document à l'aide de la fonctionnalité Options d'enregistrement dans .NET :

## Étape 1 : Définir le chemin de sortie

Tout d’abord, définissez le chemin de sortie où le document avec les annotations supprimées sera enregistré. Vous pouvez utiliser le`Path.Combine` méthode pour combiner le chemin du répertoire avec le nom du fichier de sortie.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 2 : initialiser l'annotateur

 Ensuite, initialisez une instance de`Annotator` classe en fournissant le chemin d’accès au document contenant les annotations.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Le code de suppression des annotations sera ici
}
```

## Étape 3 : Enregistrer le document avec suppression des annotations

 Maintenant, utilisez le`Save` méthode du`Annotator` classe avec le`SaveOptions` pour enregistrer le document avec les annotations supprimées. Dans le`SaveOptions` , met le`AnnotationTypes` propriété à`AnnotationType.None` pour supprimer toutes les annotations.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Étape 4 : Afficher le message de réussite

Enfin, affichez un message de réussite indiquant que le document a été enregistré avec succès avec les annotations supprimées.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

En conclusion, GroupDocs.Annotation pour .NET simplifie le processus de suppression des annotations des documents. En suivant le guide étape par étape décrit ci-dessus, les développeurs peuvent intégrer de manière transparente la fonctionnalité de suppression d'annotations dans leurs applications .NET.

## FAQ

### Q : GroupDocs.Annotation peut-il supprimer les annotations d'autres formats de document que le PDF ?

R : GroupDocs.Annotation prend en charge divers formats de documents, notamment PDF, Word, Excel et PowerPoint, vous permettant de supprimer les annotations d'un large éventail de documents.

### Q : GroupDocs.Annotation est-il facile à intégrer dans des projets .NET existants ?

R : Oui, GroupDocs.Annotation fournit une API simple et une documentation complète, permettant aux développeurs d'intégrer facilement des fonctionnalités d'annotation dans leurs applications .NET.

### Q : GroupDocs.Annotation prend-il en charge la suppression sélective des annotations ?

R : Oui, GroupDocs.Annotation permet aux développeurs de spécifier les types d'annotations à supprimer, ce qui leur donne une flexibilité dans la gestion des annotations dans leurs documents.

### Q : Puis-je essayer GroupDocs.Annotation gratuitement avant d'acheter ?

 R : Oui, vous pouvez télécharger une version d'essai gratuite de GroupDocs.Annotation à partir du[page des versions](https://releases.groupdocs.com/) pour explorer ses fonctionnalités avant de prendre une décision d’achat.

### Q : Où puis-je obtenir de l'aide pour GroupDocs.Annotation ?

 R : Pour obtenir une assistance technique et un support communautaire, vous pouvez visiter le[Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).