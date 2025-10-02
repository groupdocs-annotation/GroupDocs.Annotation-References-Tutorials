---
"description": "Apprenez à charger facilement des versions annotées de documents avec GroupDocs.Annotation pour .NET. Simplifiez les processus de collaboration et de révision."
"linktitle": "Chargement de la version annotée du document"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Chargement de la version annotée du document"
"url": "/fr/net/document-loading-essentials/loading-annotated-document-version/"
type: docs
"weight": 16
---

# Chargement de la version annotée du document

## Introduction
À l'ère du numérique, l'annotation de documents est devenue un outil essentiel pour la collaboration, la révision et le feedback dans divers secteurs. Que vous soyez un développeur intégrant des fonctionnalités d'annotation à votre application ou un utilisateur souhaitant exploiter ces fonctionnalités, GroupDocs.Annotation pour .NET offre une solution performante. Dans ce tutoriel, nous allons explorer le processus de chargement de versions de documents annotés avec GroupDocs.Annotation pour .NET.
## Prérequis
Avant de commencer, assurez-vous que vous disposez des conditions préalables suivantes :
### 1. Installer GroupDocs.Annotation pour .NET
Vous pouvez télécharger les fichiers nécessaires à partir du [page des communiqués](https://releases.groupdocs.com/annotation/net/)Suivez les instructions d’installation fournies pour configurer la bibliothèque dans votre environnement .NET.
### 2. Obtenir un document avec des annotations
Pour ce tutoriel, vous aurez besoin d'un document annoté. Assurez-vous d'avoir un format de document compatible (par exemple, PDF) contenant les annotations que vous souhaitez charger.

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


Maintenant que nous avons couvert les prérequis et les importations d'espaces de noms, plongeons dans le processus étape par étape de chargement des versions de documents annotés à l'aide de GroupDocs.Annotation pour .NET.
## Étape 1 : Définir le chemin de sortie
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Spécifier les options de chargement
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Étape 3 : Initialiser l'annotateur
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
Dans ce tutoriel, nous avons découvert comment charger des versions annotées de documents avec GroupDocs.Annotation pour .NET. En suivant le guide étape par étape et en exploitant les fonctionnalités de cette puissante bibliothèque, vous pourrez intégrer facilement la fonctionnalité d'annotation de documents à vos applications .NET.
## FAQ
### Puis-je annoter des documents de différents formats avec GroupDocs.Annotation pour .NET ?
Oui, GroupDocs.Annotation prend en charge l'annotation de documents dans des formats tels que PDF, DOCX, PPTX, XLSX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Annotation pour .NET ?
Oui, vous pouvez accéder à la version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/).
### Où puis-je trouver la documentation pour GroupDocs.Annotation pour .NET ?
Vous pouvez vous référer à la documentation détaillée [ici](https://tutorials.groupdocs.com/annotation/net/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Annotation pour .NET ?
Vous pouvez acquérir une licence temporaire auprès de [ce lien](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je demander de l'aide ou poser des questions sur GroupDocs.Annotation pour .NET ?
Vous pouvez visiter le forum GroupDocs.Annotation [ici](https://forum.groupdocs.com/c/annotation/10).