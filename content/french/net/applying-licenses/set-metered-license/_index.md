---
"description": "Découvrez comment configurer une licence mesurée pour GroupDocs.Annotation .NET pour l’utilisation des ressources et les fonctionnalités d’annotation de documents dans vos applications .NET."
"linktitle": "Définir une licence mesurée"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Définir une licence mesurée"
"url": "/fr/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Définir une licence mesurée

## Introduction
GroupDocs.Annotation pour .NET est une bibliothèque puissante qui permet aux développeurs d'ajouter facilement des fonctionnalités d'annotation de documents à leurs applications .NET. Que vous développiez un système de gestion documentaire, une plateforme collaborative ou toute application impliquant la révision et le balisage de documents, GroupDocs.Annotation pour .NET offre un ensemble complet d'outils pour simplifier le processus.
Dans ce tutoriel, nous allons explorer la configuration d'une licence à la consommation pour GroupDocs.Annotation .NET. Une licence à la consommation vous permet de payer uniquement pour les ressources que vous consommez, ce qui en fait une solution économique pour les projets de toute envergure. En suivant les étapes ci-dessous, vous pourrez intégrer GroupDocs.Annotation de manière transparente à votre application .NET tout en optimisant l'utilisation des ressources et en maîtrisant votre budget.
## Prérequis
Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :
1. Bibliothèque GroupDocs.Annotation pour .NET : téléchargez la bibliothèque à partir du [site web](https://releases.groupdocs.com/annotation/net/).
2. Accès au compte GroupDocs : Vous aurez besoin d'un compte GroupDocs pour obtenir les clés publiques et privées nécessaires à la configuration de la licence à usage limité. Si vous n'avez pas encore de compte, vous pouvez vous inscrire pour un essai gratuit. [ici](https://releases.groupdocs.com/).
3. Compréhension de base de C# et .NET Framework : une connaissance du langage de programmation C# et de .NET Framework sera bénéfique pour mettre en œuvre les étapes décrites dans ce didacticiel.

## Importer des espaces de noms
Pour commencer, assurez-vous d'importer les espaces de noms nécessaires dans votre projet C#. Ces espaces de noms sont essentiels pour interagir avec la fonctionnalité GroupDocs.Annotation.
```csharp
using System;
```
## Étape 1 : Obtenir les clés publiques et privées
Avant de configurer la licence mesurée, vous devez obtenir vos clés publiques et privées à partir du tableau de bord de votre compte GroupDocs.
1. Connectez-vous à votre compte GroupDocs.
2. Accédez à la section de gestion des licences.
3. Copiez vos clés publiques et privées fournies par GroupDocs.
## Étape 2 : Définir une licence mesurée
Une fois que vous avez obtenu vos clés publiques et privées, vous pouvez configurer la licence mesurée dans votre application .NET.
```csharp
string publicKey = "*****"; // Remplacez ***** par votre clé publique
string privateKey = "*****"; // Remplacez ***** par votre clé privée
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusion
En conclusion, la configuration d'une licence à tarif limité pour GroupDocs.Annotation .NET est un processus simple qui garantit une utilisation efficace des ressources et une rentabilité optimale pour vos projets d'annotation de documents. En suivant les étapes décrites dans ce tutoriel, vous pourrez intégrer GroupDocs.Annotation en toute transparence à votre application .NET et améliorer les fonctionnalités de collaboration et de révision de documents.
## FAQ
### Puis-je utiliser GroupDocs.Annotation pour .NET dans des projets commerciaux ?
Oui, GroupDocs.Annotation pour .NET peut être utilisé dans des projets commerciaux et non commerciaux. Cependant, vous devez acquérir une licence adaptée aux besoins de votre projet.
### Existe-t-il une version d'essai disponible pour GroupDocs.Annotation pour .NET ?
Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Annotation pour .NET en visitant [ce lien](https://releases.groupdocs.com/).
### Comment puis-je obtenir une assistance technique pour GroupDocs.Annotation pour .NET ?
Vous pouvez demander une assistance technique en visitant le forum GroupDocs [ici](https://forum.groupdocs.com/c/annotation/10).
### Existe-t-il des options de licence temporaire disponibles ?
Oui, vous pouvez obtenir une licence temporaire auprès de GroupDocs pour une utilisation à court terme ou à des fins d'évaluation. Visitez [ce lien](https://purchase.groupdocs.com/temporary-license/) pour plus d'informations.
### Puis-je personnaliser les fonctionnalités d’annotation en fonction des exigences de mon projet ?
Oui, GroupDocs.Annotation pour .NET offre de nombreuses options de personnalisation, vous permettant d’adapter les fonctionnalités d’annotation en fonction des besoins spécifiques de votre projet.