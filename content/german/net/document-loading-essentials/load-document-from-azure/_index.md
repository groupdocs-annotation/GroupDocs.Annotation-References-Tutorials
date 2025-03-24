---
title: Dokument aus Azure laden
linktitle: Dokument aus Azure laden
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie Dokumente in .NET mit GroupDocs.Annotation mit Anmerkungen versehen. Schritt-für-Schritt-Anleitung für die nahtlose Integration mit Azure Blob Storage.
weight: 11
url: /de/net/document-loading-essentials/load-document-from-azure/
---

# Dokument aus Azure laden

## Einführung
Im Bereich der Dokumentenverwaltung und -zusammenarbeit erweist sich GroupDocs.Annotation für .NET als robuste Lösung, die nahtlose Annotations- und Markup-Funktionen innerhalb von .NET-Anwendungen ermöglicht. Dieses Tutorial befasst sich mit den Feinheiten der Nutzung von GroupDocs.Annotation für .NET zum Kommentieren von Dokumenten und bietet eine Schritt-für-Schritt-Anleitung von den Voraussetzungen bis zur erweiterten Verwendung.
## Voraussetzungen
Bevor Sie sich mit GroupDocs.Annotation für .NET befassen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Installation von .NET Framework: GroupDocs.Annotation für .NET erfordert eine kompatible .NET-Laufzeitumgebung. Stellen Sie sicher, dass das .NET Framework auf Ihrem System installiert ist.
2. Zugriff auf die GroupDocs.Annotation-Bibliothek: Erhalten Sie Zugriff auf die GroupDocs.Annotation für .NET-Bibliothek, indem Sie sie entweder von der Website herunterladen oder über Paketmanager wie NuGet.
3. Dokument zum Kommentieren: Bereiten Sie das Dokument (z. B. PDF) vor, das Sie kommentieren möchten. Stellen Sie sicher, dass auf das Dokument entweder lokal oder über einen Cloud-Speicherdienst wie Azure Blob Storage zugegriffen werden kann.

## Namespaces importieren
Um mit dem Kommentieren von Dokumenten mit GroupDocs.Annotation für .NET zu beginnen, importieren Sie die erforderlichen Namespaces in Ihr Projekt. Dieser Schritt stellt sicher, dass Sie Zugriff auf die erforderlichen Klassen und Funktionalitäten haben.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Dokument aus Azure laden
Um ein in Azure Blob Storage gespeichertes Dokument mit Anmerkungen zu versehen, führen Sie die folgenden Schritte aus:
### Schritt 1: Ausgabepfad festlegen
Definieren Sie den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Schritt 2: Dokument herunterladen
 Rufen Sie das Dokument aus Azure Blob Storage ab, indem Sie Folgendes aufrufen`DownloadFile` Methode.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Anmerkungslogik
    annotator.Save(outputPath);
}
```
## Laden Sie die Datei von Azure Blob Storage herunter
 Um das Dokument aus Azure Blob Storage herunterzuladen, implementieren Sie Folgendes`DownloadFile` Methode.
### Schritt 1: Blob abrufen
Greifen Sie auf den Azure Blob Storage-Container zu und rufen Sie das gewünschte Blob ab.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Schritt 2: Blob-Inhalt herunterladen
Laden Sie den Blob-Inhalt in einen Speicherstream herunter.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Holen Sie sich den Azure Blob Storage-Container
 Um mit Azure Blob Storage zu interagieren, implementieren Sie Folgendes`GetContainer` Methode.
### Schritt 1: Speicheranmeldeinformationen initialisieren
Geben Sie die erforderlichen Kontoanmeldeinformationen und Endpunktinformationen an.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Schritt 2: Erstellen Sie einen Blob-Client
Erstellen Sie einen Client für die Interaktion mit Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Schritt 3: Containerreferenz abrufen
Rufen Sie einen Verweis auf den angegebenen Container ab.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Schritt 4: Container erstellen, falls nicht vorhanden
Stellen Sie sicher, dass der Container vorhanden ist, und erstellen Sie ihn, falls nicht.
```csharp
container.CreateIfNotExists();
```

## Abschluss
GroupDocs.Annotation für .NET bietet Entwicklern robuste Dokumentannotationsfunktionen und lässt sich nahtlos in .NET-Anwendungen integrieren. Wenn Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie die Funktionen von GroupDocs.Annotation effektiv nutzen, um in Azure Blob Storage gespeicherte Dokumente mit Anmerkungen zu versehen.
#### FAQs
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, DOCX, PPTX und mehr.
### Können Anmerkungen entsprechend spezifischer Anforderungen angepasst werden?
Ja, GroupDocs.Annotation bietet umfangreiche Anpassungsoptionen für Anmerkungen, sodass Benutzer das Erscheinungsbild, das Verhalten und die Metadaten ändern können.
### Ist GroupDocs.Annotation für die gemeinsame Annotation von Dokumenten geeignet?
Absolut! GroupDocs.Annotation erleichtert die kollaborative Dokumentanmerkung, indem es mehreren Benutzern ermöglicht, Anmerkungen gleichzeitig hinzuzufügen, zu bearbeiten und zu überprüfen.
### Bietet GroupDocs.Annotation plattformübergreifende Kompatibilität?
Ja, GroupDocs.Annotation ist so konzipiert, dass es nahtlos auf verschiedenen Plattformen funktioniert, einschließlich Windows, Linux und macOS.
### Ist technischer Support für GroupDocs.Annotation-Benutzer verfügbar?
Ja, GroupDocs bietet über seine Foren und speziellen Supportkanäle umfassenden technischen Support.