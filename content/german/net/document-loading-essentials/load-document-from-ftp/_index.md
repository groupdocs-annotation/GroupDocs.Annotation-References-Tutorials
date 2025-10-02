---
"description": "Verbessern Sie Ihre .NET-Anwendungen mit GroupDocs.Annotation für nahtlose Dokumentannotationen. Schritt-für-Schritt-Anleitung inklusive."
"linktitle": "Dokument vom FTP laden"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dokument vom FTP laden"
"url": "/de/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# Dokument vom FTP laden

## Einführung
GroupDocs.Annotation für .NET ist eine vielseitige Bibliothek, die die Erstellung von Dokumentanmerkungen in .NET-Anwendungen mühelos ermöglicht. Ob PDFs, Microsoft Office-Dokumente, Bilder oder andere Formate – diese Bibliothek bietet eine einheitliche Lösung zum Hinzufügen von Anmerkungen wie Kommentaren, Hervorhebungen und Formen, um die Zusammenarbeit und das Dokumentenmanagement zu verbessern.
## Voraussetzungen
Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Kenntnisse in C#: Um die in diesem Tutorial bereitgestellten Codebeispiele zu verstehen und umzusetzen, sind Kenntnisse in der Programmiersprache C# unerlässlich.
2. GroupDocs.Annotation für .NET: Stellen Sie sicher, dass Sie GroupDocs.Annotation für .NET von der [Download-Link](https://releases.groupdocs.com/annotation/net/). Befolgen Sie die Installationsanweisungen, um die Bibliothek erfolgreich in Ihr .NET-Projekt zu integrieren.
## Namespaces importieren
Um die Funktionen von GroupDocs.Annotation für .NET nutzen zu können, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Gehen Sie dazu folgendermaßen vor:

Fügen Sie in Ihrem C#-Projekt die erforderlichen Namespaces am Anfang Ihrer Codedatei ein:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Lassen Sie uns nun tiefer in den Prozess des Ladens eines Dokuments von FTP und des Hinzufügens von Anmerkungen dazu mithilfe von GroupDocs.Annotation für .NET eintauchen.
## Schritt 1: Ausgabepfad definieren
Geben Sie den Ausgabepfad an, in dem das kommentierte Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Dokument vom FTP laden
Rufen Sie das Dokument mithilfe des angegebenen Dateipfads vom FTP-Server ab.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Der Anmerkungscode wird hier hinzugefügt
}
```
## Schritt 3: Anmerkung hinzufügen
Definieren und fügen Sie die gewünschte Annotation, beispielsweise eine Bereichsannotation, zum Dokument hinzu.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Schritt 4: Kommentiertes Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Schritt 5: Datei vom FTP abrufen
Implementieren Sie die Methode zum Abrufen der Datei vom FTP-Server.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Schritt 6: FTP-Anfrage erstellen
Generieren Sie eine FTP-Anfrage, um die Datei herunterzuladen.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Schritt 7: Dateistream abrufen
Rufen Sie den Dateistream aus der FTP-Antwort ab.
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
## Abschluss
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET Entwicklern die nahtlose Integration von Dokumentannotationsfunktionen in ihre .NET-Anwendungen ermöglicht. Mit der Schritt-für-Schritt-Anleitung in diesem Tutorial können Sie Dokumente effizient vom FTP laden und problemlos Anmerkungen hinzufügen. Dies verbessert die Zusammenarbeit und das Dokumentenmanagement in Ihren Anwendungen.
## Häufig gestellte Fragen
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Office-Dokumente, Bilder und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen, die mit GroupDocs.Annotation für .NET hinzugefügt wurden?
Auf jeden Fall, GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen für das Erscheinungsbild von Anmerkungen, einschließlich Farben, Stilen und Formen.
### Bietet GroupDocs.Annotation für .NET Unterstützung für Cloud-Speicherdienste?
Ja, GroupDocs.Annotation für .NET lässt sich nahtlos in beliebte Cloud-Speicherdienste integrieren, sodass Sie Dokumente von Diensten wie Dropbox, Google Drive und OneDrive laden und speichern können.
### Gibt es eine Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können die Funktionen von GroupDocs.Annotation für .NET erkunden, indem Sie die kostenlose Testversion von der [Veröffentlichungsseite](https://releases.groupdocs.com/).
### Wie erhalte ich technische Unterstützung oder Support für GroupDocs.Annotation für .NET?
Für technische Unterstützung, Fehlerbehebung oder allgemeine Anfragen können Sie die GroupDocs.Annotation für .NET besuchen. [Support-Forum](https://forum.groupdocs.com/c/annotation/10).