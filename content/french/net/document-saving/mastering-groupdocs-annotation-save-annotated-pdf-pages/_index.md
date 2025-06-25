---
"date": "2025-05-06"
"description": "Découvrez comment enregistrer efficacement uniquement les pages annotées d'un PDF grâce à GroupDocs.Annotation pour .NET. Améliorez la gestion de vos documents et la collaboration grâce à ce guide détaillé."
"title": "Comment enregistrer des pages annotées dans un PDF avec GroupDocs.Annotation pour .NET"
"url": "/fr/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# Comment enregistrer des pages annotées dans un PDF avec GroupDocs.Annotation pour .NET

## Introduction

Vous avez du mal à enregistrer des pages annotées spécifiques de vos documents PDF ? Ce guide complet explique comment y parvenir efficacement avec GroupDocs.Annotation pour .NET. En exploitant les fonctionnalités d'annotation, simplifiez la gestion des documents et améliorez la collaboration en vous concentrant sur le contenu pertinent.

Dans ce tutoriel, vous apprendrez :
- Configurer votre environnement de développement avec GroupDocs.Annotation
- Ajout de différents types d'annotations
- Enregistrer efficacement uniquement les pages annotées

Prêt à commencer ? Assurez-vous que tout est prêt.

### Prérequis

Avant de commencer, assurez-vous d'avoir les éléments suivants :
- **.NET Framework** (version 4.6 ou ultérieure) ou **.NET Core/5+**
- Un éditeur de code comme Visual Studio
- Connaissances de base de la configuration de projets C# et .NET

## Configuration de GroupDocs.Annotation pour .NET

Pour commencer à utiliser GroupDocs.Annotation, installez-le via NuGet.

**Console du gestionnaire de packages NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Acquisition de licence

GroupDocs propose un essai gratuit pour explorer pleinement son logiciel. Pour une utilisation prolongée, achetez une licence ou demandez une licence temporaire :
- **Essai gratuit**:Explorez les fonctionnalités sans limitations pendant une période initiale.
- **Licence temporaire**: Utilisez GroupDocs.Annotation en production temporairement.
- **Achat**:Sécurisez vos besoins à long terme avec une licence commerciale.

Une fois installée, initialisez la bibliothèque comme suit :

```csharp
using GroupDocs.Annotation;

// Configuration de base pour charger et annoter des documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Guide de mise en œuvre

### Ajout d'annotations

#### Aperçu

Les annotations permettent de mettre en évidence les zones importantes de votre document. Découvrons comment en ajouter une. `AreaAnnotation` et un `EllipseAnnotation`.

**Étape 1 : Créer une annotation de zone**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Définir l'annotation de zone
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position et taille
    BackgroundColor = 65535,                // Valeur de couleur ARGB pour la surbrillance
    PageNumber = 1                          // Numéro de page spécifique
};
```

Le `AreaAnnotation` met en évidence une zone rectangulaire du document. Personnalisez sa position (`Box`) et la couleur d'arrière-plan.

**Étape 2 : Créer une annotation d'ellipse**

```csharp
// Définir l'annotation de l'ellipse
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position et taille
    BackgroundColor = 123456,                // Valeur de couleur ARGB pour la surbrillance
    PageNumber = 1                           // Numéro de page spécifique
};
```

Le `EllipseAnnotation` Permet de dessiner une forme ovale sur le document. Ajustez la position et les dimensions à l'aide des `Box` propriété.

**Étape 3 : Ajouter des annotations**

```csharp
// Ajout d'annotations à l'instance Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

En utilisant le `Add` méthode, inclure plusieurs types d'annotations. Cette étape ajoute à la fois `AreaAnnotation` et `EllipseAnnotation`.

### Enregistrer uniquement les pages annotées

#### Aperçu

Pour enregistrer uniquement les pages contenant des annotations, configurez vos options d’enregistrement en conséquence.

**Étape 4 : Enregistrer les pages annotées**

```csharp
using GroupDocs.Annotation.Options;

// Configurer les options d'enregistrement pour inclure uniquement les pages annotées
annotator.Save("path/to/output/document.pdf\