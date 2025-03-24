---
title: Chargement de la version du document annoté
linktitle: Chargement de la version du document annoté
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment charger sans effort des versions de documents annotées à l'aide de GroupDocs.Annotation pour .NET. Simplifiez les processus de collaboration et de révision.
weight: 16
url: /fr/net/document-loading-essentials/loading-annotated-document-version/
---
## Introduction
À l'ère numérique d'aujourd'hui, l'annotation de documents est devenue un outil essentiel de collaboration, de révision et de feedback dans divers secteurs. Que vous soyez un développeur intégrant des fonctionnalités d'annotation dans votre application ou un utilisateur cherchant à tirer parti de ces fonctionnalités, GroupDocs.Annotation pour .NET fournit une solution puissante. Dans ce didacticiel, nous aborderons le processus de chargement des versions de documents annotées à l'aide de GroupDocs.Annotation pour .NET.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
### 1. Installez GroupDocs.Annotation pour .NET
 Vous pouvez télécharger les fichiers nécessaires à partir du[page des versions](https://releases.groupdocs.com/annotation/net/). Suivez les instructions d'installation fournies pour configurer la bibliothèque dans votre environnement .NET.
### 2. Obtenez un document avec des annotations
Pour ce didacticiel, vous aurez besoin d'un document avec des annotations. Assurez-vous que vous disposez d'un format de document compatible (par exemple, PDF) contenant les annotations que vous souhaitez charger.

## Importation d'espaces de noms
Pour lancer le processus, vous devez importer les espaces de noms requis dans votre projet. Ces espaces de noms donnent accès aux fonctionnalités de GroupDocs.Annotation pour .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


Maintenant que nous avons couvert les conditions préalables et les importations d’espaces de noms, passons au processus étape par étape de chargement des versions de documents annotées à l’aide de GroupDocs.Annotation pour .NET.
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Spécifier les options de chargement
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Étape 3 : initialiser l'annotateur
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## Étape 4 : Récupérer les annotations
```csharp
var annotations = annotator.Get();
```
## Étape 5 : Enregistrer le document avec les annotations
```csharp
annotator.Save(outputPath);
```
## Étape 6 : Afficher le message de confirmation
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
Dans ce didacticiel, nous avons expliqué comment charger des versions de documents annotées à l'aide de GroupDocs.Annotation pour .NET. En suivant le guide étape par étape et en tirant parti des capacités de cette puissante bibliothèque, vous pouvez intégrer de manière transparente la fonctionnalité d'annotation de documents dans vos applications .NET.
## FAQ
### Puis-je annoter des documents de différents formats avec GroupDocs.Annotation pour .NET ?
Oui, GroupDocs.Annotation prend en charge l'annotation de documents dans des formats tels que PDF, DOCX, PPTX, XLSX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
 Oui, vous pouvez accéder à la version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Annotation pour .NET ?
 Vous pouvez vous référer à la documentation détaillée[ici](https://tutorials.groupdocs.com/annotation/net/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Annotation pour .NET ?
 Vous pouvez acquérir une licence temporaire auprès de[ce lien](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je demander de l’aide ou poser des questions sur GroupDocs.Annotation pour .NET ?
 Vous pouvez visiter le forum GroupDocs.Annotation[ici](https://forum.groupdocs.com/c/annotation/10).