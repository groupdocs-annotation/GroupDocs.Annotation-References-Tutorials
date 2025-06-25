---
"description": "Améliorez vos applications .NET avec GroupDocs.Annotation pour une annotation fluide de vos documents. Tutoriel pas à pas inclus."
"linktitle": "Charger un document depuis FTP"
"second_title": "API .NET GroupDocs.Annotation"
"title": "Charger un document depuis FTP"
"url": "/fr/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Charger un document depuis FTP

## Introduction
GroupDocs.Annotation pour .NET est une bibliothèque polyvalente conçue pour simplifier l'annotation de documents dans les applications .NET. Que vous travailliez avec des PDF, des documents Microsoft Office, des images ou d'autres formats, cette bibliothèque offre une solution unifiée pour l'ajout d'annotations, telles que des commentaires, des surlignages et des formes, afin d'améliorer la collaboration et la gestion des documents.
## Prérequis
Avant de plonger dans le didacticiel, assurez-vous que vous disposez des prérequis suivants :
1. Connaissance de C# : La maîtrise du langage de programmation C# est essentielle pour comprendre et mettre en œuvre les exemples de code fournis dans ce tutoriel.
2. GroupDocs.Annotation pour .NET : assurez-vous de télécharger et d'installer GroupDocs.Annotation pour .NET à partir du [lien de téléchargement](https://releases.groupdocs.com/annotation/net/)Suivez les instructions d’installation pour intégrer la bibliothèque dans votre projet .NET avec succès.
## Importer des espaces de noms
Pour utiliser les fonctionnalités de GroupDocs.Annotation pour .NET, vous devez importer les espaces de noms requis dans votre projet C#. Suivez ces étapes :

Dans votre projet C#, incluez les espaces de noms nécessaires au début de votre fichier de code :
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Examinons maintenant le processus de chargement d’un document à partir de FTP et d’ajout d’annotations à l’aide de GroupDocs.Annotation pour .NET.
## Étape 1 : Définir le chemin de sortie
Spécifiez le chemin de sortie où le document annoté sera enregistré.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Étape 2 : Charger le document à partir du FTP
Récupérez le document à partir du serveur FTP en utilisant le chemin de fichier fourni.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Le code d'annotation sera ajouté ici
}
```
## Étape 3 : Ajouter une annotation
Définissez et ajoutez l’annotation souhaitée, telle qu’une annotation de zone, au document.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Étape 4 : Enregistrer le document annoté
Enregistrez le document annoté dans le chemin de sortie spécifié.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Étape 5 : Récupérer le fichier à partir du FTP
Implémentez la méthode pour récupérer le fichier à partir du serveur FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Étape 6 : Créer une requête FTP
Générer une requête FTP pour télécharger le fichier.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Étape 7 : Obtenir le flux de fichiers
Récupérez le flux de fichiers à partir de la réponse FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Conclusion
En conclusion, GroupDocs.Annotation pour .NET permet aux développeurs d'intégrer facilement des fonctionnalités d'annotation de documents à leurs applications .NET. En suivant le guide étape par étape décrit dans ce tutoriel, vous pourrez charger efficacement des documents depuis FTP et ajouter facilement des annotations, améliorant ainsi la collaboration et la gestion documentaire au sein de vos applications.
## FAQ
### GroupDocs.Annotation pour .NET est-il compatible avec tous les formats de documents ?
Oui, GroupDocs.Annotation pour .NET prend en charge une large gamme de formats de documents, notamment les documents PDF, Microsoft Office, les images, etc.
### Puis-je personnaliser l’apparence des annotations ajoutées à l’aide de GroupDocs.Annotation pour .NET ?
Absolument, GroupDocs.Annotation pour .NET offre de nombreuses options de personnalisation pour l’apparence des annotations, notamment les couleurs, les styles et les formes.
### GroupDocs.Annotation pour .NET prend-il en charge les services de stockage cloud ?
Oui, GroupDocs.Annotation pour .NET s'intègre parfaitement aux services de stockage cloud populaires, vous permettant de charger et d'enregistrer des documents à partir de services tels que Dropbox, Google Drive et OneDrive.
### Existe-t-il une version d'essai disponible pour GroupDocs.Annotation pour .NET ?
Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Annotation pour .NET en téléchargeant la version d'essai gratuite à partir du [page de sortie](https://releases.groupdocs.com/).
### Comment puis-je obtenir une assistance technique ou un support pour GroupDocs.Annotation pour .NET ?
Pour une assistance technique, un dépannage ou des demandes générales, vous pouvez visiter GroupDocs.Annotation pour .NET [forum d'assistance](https://forum.groupdocs.com/c/annotation/10).