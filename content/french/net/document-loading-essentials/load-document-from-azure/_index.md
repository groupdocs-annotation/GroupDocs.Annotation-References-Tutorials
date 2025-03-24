---
title: Charger un document depuis Azure
linktitle: Charger un document depuis Azure
second_title: API GroupDocs.Annotation .NET
description: Découvrez comment annoter des documents dans .NET à l'aide de GroupDocs.Annotation. Tutoriel étape par étape pour une intégration transparente avec Azure Blob Storage.
weight: 11
url: /fr/net/document-loading-essentials/load-document-from-azure/
---

# Charger un document depuis Azure

## Introduction
Dans le domaine de la gestion de documents et de la collaboration, GroupDocs.Annotation pour .NET apparaît comme une solution robuste, facilitant des fonctionnalités transparentes d'annotation et de balisage au sein des applications .NET. Ce didacticiel explore les subtilités de l'utilisation de GroupDocs.Annotation pour .NET pour annoter des documents, offrant des conseils étape par étape, depuis les conditions préalables jusqu'à l'utilisation avancée.
## Conditions préalables
Avant de plonger dans GroupDocs.Annotation pour .NET, assurez-vous que les conditions préalables suivantes sont remplies :
1. Installation de .NET Framework : GroupDocs.Annotation pour .NET nécessite un environnement d'exécution .NET compatible. Assurez-vous que le .NET Framework est installé sur votre système.
2. Accès à la bibliothèque GroupDocs.Annotation : accédez à la bibliothèque GroupDocs.Annotation pour .NET soit en la téléchargeant à partir du site Web, soit via des gestionnaires de packages comme NuGet.
3. Document à annoter : préparez le document (par exemple, PDF) que vous avez l'intention d'annoter. Assurez-vous que le document est accessible localement ou via un service de stockage cloud comme Azure Blob Storage.

## Importer des espaces de noms
Pour commencer à annoter des documents à l'aide de GroupDocs.Annotation pour .NET, importez les espaces de noms nécessaires dans votre projet. Cette étape garantit que vous avez accès aux classes et fonctionnalités requises.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Charger un document depuis Azure
Pour annoter un document stocké dans Azure Blob Storage, procédez comme suit :
### Étape 1 : Définir le chemin de sortie
Définissez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Étape 2 : Télécharger le document
 Récupérez le document depuis Azure Blob Storage en appelant le`DownloadFile` méthode.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logique d'annotation
    annotator.Save(outputPath);
}
```
## Télécharger le fichier à partir du stockage Azure Blob
 Pour télécharger le document depuis Azure Blob Storage, implémentez le`DownloadFile` méthode.
### Étape 1 : Récupérer le Blob
Accédez au conteneur Azure Blob Storage et récupérez le blob souhaité.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Étape 2 : Télécharger le contenu Blob
Téléchargez le contenu du blob dans un flux de mémoire.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Obtenir le conteneur de stockage Azure Blob
 Pour interagir avec Azure Blob Storage, implémentez le`GetContainer` méthode.
### Étape 1 : initialiser les informations d'identification de stockage
Fournissez les informations d’identification du compte et les informations sur le point de terminaison nécessaires.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Étape 2 : Créer un client Blob
Créez un client pour interagir avec Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Étape 3 : Récupérer la référence du conteneur
Obtenez une référence au conteneur spécifié.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Étape 4 : Créer un conteneur s'il n'existe pas
Assurez-vous que le conteneur existe et créez-le sinon.
```csharp
container.CreateIfNotExists();
```

## Conclusion
GroupDocs.Annotation pour .NET offre aux développeurs de solides capacités d'annotation de documents, s'intégrant de manière transparente aux applications .NET. En suivant les étapes décrites dans ce didacticiel, vous pouvez exploiter efficacement les fonctionnalités de GroupDocs.Annotation pour annoter les documents stockés dans Azure Blob Storage.
#### FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
GroupDocs.Annotation prend en charge un large éventail de formats de documents, notamment PDF, DOCX, PPTX, etc.
### Les annotations peuvent-elles être personnalisées en fonction d’exigences spécifiques ?
Oui, GroupDocs.Annotation offre des options de personnalisation étendues pour les annotations, permettant aux utilisateurs de modifier l'apparence, le comportement et les métadonnées.
### GroupDocs.Annotation est-il adapté à l’annotation de documents collaboratifs ?
Absolument! GroupDocs.Annotation facilite l'annotation collaborative de documents en permettant à plusieurs utilisateurs d'ajouter, de modifier et de réviser des annotations simultanément.
### GroupDocs.Annotation offre-t-il une compatibilité multiplateforme ?
Oui, GroupDocs.Annotation est conçu pour fonctionner de manière transparente sur diverses plates-formes, notamment Windows, Linux et macOS.
### Le support technique est-il disponible pour les utilisateurs de GroupDocs.Annotation ?
Oui, GroupDocs fournit une assistance technique complète via ses forums et ses canaux d'assistance dédiés.