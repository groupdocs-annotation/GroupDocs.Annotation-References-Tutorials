---
title: Définir une licence limitée
linktitle: Définir une licence limitée
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment configurer une licence limitée pour GroupDocs.Annotation .NET pour utiliser les ressources et documenter les fonctionnalités d'annotation dans vos applications .NET.
weight: 12
url: /fr/net/applying-licenses/set-metered-license/
---

# Définir une licence limitée

## Introduction
GroupDocs.Annotation for .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter sans effort des fonctionnalités d'annotation de documents à leurs applications .NET. Que vous construisiez un système de gestion de documents, une plateforme de collaboration ou toute autre application impliquant la révision et le balisage de documents, GroupDocs.Annotation pour .NET fournit un ensemble complet d'outils pour rationaliser le processus.
Dans ce didacticiel, nous aborderons le processus de configuration d'une licence limitée pour GroupDocs.Annotation .NET. Une licence mesurée vous permet de payer uniquement pour les ressources que vous consommez, ce qui en fait une solution rentable pour les projets de toute envergure. En suivant les étapes décrites ci-dessous, vous pourrez intégrer de manière transparente GroupDocs.Annotation dans votre application .NET tout en optimisant l'utilisation des ressources et en maintenant le contrôle budgétaire.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :
1.  GroupDocs.Annotation pour la bibliothèque .NET : téléchargez la bibliothèque à partir du[site web](https://releases.groupdocs.com/annotation/net/).
2. Accès au compte GroupDocs : vous aurez besoin d'un compte GroupDocs pour obtenir les clés publiques et privées requises pour la configuration de la licence limitée. Si vous n'avez pas encore de compte, vous pouvez vous inscrire pour un essai gratuit[ici](https://releases.groupdocs.com/).
3. Compréhension de base de C# et du .NET Framework : une connaissance du langage de programmation C# et du framework .NET sera bénéfique pour la mise en œuvre des étapes décrites dans ce didacticiel.

## Importer des espaces de noms
Pour commencer, assurez-vous d'importer les espaces de noms nécessaires dans votre projet C#. Ces espaces de noms sont essentiels pour interagir avec la fonctionnalité GroupDocs.Annotation.
```csharp
using System;
```
## Étape 1 : Obtenir les clés publiques et privées
Avant de configurer la licence limitée, vous devez obtenir vos clés publiques et privées à partir du tableau de bord de votre compte GroupDocs.
1. Connectez-vous à votre compte GroupDocs.
2. Accédez à la section de gestion des licences.
3. Copiez vos clés publiques et privées fournies par GroupDocs.
## Étape 2 : Définir une licence limitée
Une fois que vous avez obtenu vos clés publiques et privées, vous pouvez configurer la licence limitée dans votre application .NET.
```csharp
string publicKey = "*****"; // Remplacez ***** par votre clé publique
string privateKey = "*****"; // Remplacez ***** par votre clé privée
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusion
En conclusion, la configuration d'une licence limitée pour GroupDocs.Annotation .NET est un processus simple qui garantit une utilisation efficace des ressources et une rentabilité pour vos projets d'annotation de documents. En suivant les étapes décrites dans ce didacticiel, vous pouvez intégrer de manière transparente GroupDocs.Annotation dans votre application .NET et améliorer les capacités de collaboration et de révision de documents.
## FAQ
### Puis-je utiliser GroupDocs.Annotation pour .NET dans des projets commerciaux ?
Oui, GroupDocs.Annotation pour .NET peut être utilisé dans des projets commerciaux et non commerciaux. Cependant, vous devez acquérir une licence appropriée en fonction des exigences de votre projet.
### Existe-t-il une version d’essai disponible pour GroupDocs.Annotation pour .NET ?
 Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET en visitant[ce lien](https://releases.groupdocs.com/).
### Comment puis-je obtenir une assistance technique pour GroupDocs.Annotation pour .NET ?
 Vous pouvez demander une assistance technique en visitant le forum GroupDocs[ici](https://forum.groupdocs.com/c/annotation/10).
### Existe-t-il des options de licence temporaire disponibles ?
 Oui, vous pouvez obtenir une licence temporaire auprès de GroupDocs pour une utilisation à court terme ou à des fins d'évaluation. Visite[ce lien](https://purchase.groupdocs.com/temporary-license/) pour plus d'informations.
### Puis-je personnaliser les fonctionnalités d'annotation en fonction des exigences de mon projet ?
Oui, GroupDocs.Annotation pour .NET offre des options de personnalisation étendues, vous permettant d'adapter les fonctionnalités d'annotation aux besoins spécifiques de votre projet.