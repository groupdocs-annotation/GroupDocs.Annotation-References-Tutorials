---
title: Dokument von FTP laden
linktitle: Dokument von FTP laden
second_title: GroupDocs.Annotation .NET-API
description: Erweitern Sie Ihre .NET-Anwendungen mit GroupDocs.Annotation für eine nahtlose Dokumentanmerkung. Schritt-für-Schritt-Anleitung enthalten.
weight: 12
url: /de/net/document-loading-essentials/load-document-from-ftp/
---
## Einführung
GroupDocs.Annotation für .NET ist eine vielseitige Bibliothek, die entwickelt wurde, um Dokumentanmerkungsfunktionen in .NET-Anwendungen mühelos zu ermöglichen. Unabhängig davon, ob Sie mit PDFs, Microsoft Office-Dokumenten, Bildern oder anderen Formaten arbeiten, bietet diese Bibliothek eine einheitliche Lösung zum Hinzufügen von Anmerkungen wie Kommentaren, Hervorhebungen und Formen, um die Zusammenarbeit und Dokumentenverwaltung zu verbessern.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Kenntnisse in C#: Kenntnisse in der Programmiersprache C# sind unerlässlich, um die in diesem Tutorial bereitgestellten Codebeispiele zu verstehen und umzusetzen.
2.  GroupDocs.Annotation für .NET: Stellen Sie sicher, dass Sie GroupDocs.Annotation für .NET von herunterladen und installieren[Download-Link](https://releases.groupdocs.com/annotation/net/). Befolgen Sie die Installationsanweisungen, um die Bibliothek erfolgreich in Ihr .NET-Projekt zu integrieren.
## Namespaces importieren
Um GroupDocs.Annotation für .NET-Funktionen nutzen zu können, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Folge diesen Schritten:

Fügen Sie in Ihrem C#-Projekt die erforderlichen Namespaces am Anfang Ihrer Codedatei ein:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Schauen wir uns nun den Prozess des Ladens eines Dokuments von FTP und des Hinzufügens von Anmerkungen mithilfe von GroupDocs.Annotation für .NET genauer an.
## Schritt 1: Ausgabepfad definieren
Geben Sie den Ausgabepfad an, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Dokument von FTP laden
Rufen Sie das Dokument über den angegebenen Dateipfad vom FTP-Server ab.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Anmerkungscode wird hier hinzugefügt
}
```
## Schritt 3: Anmerkung hinzufügen
Definieren Sie die gewünschte Anmerkung, beispielsweise eine Bereichsanmerkung, und fügen Sie sie zum Dokument hinzu.
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
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET Entwickler in die Lage versetzt, Dokumentanmerkungsfunktionen nahtlos in ihre .NET-Anwendungen zu integrieren. Wenn Sie der Schritt-für-Schritt-Anleitung in diesem Tutorial folgen, können Sie Dokumente effizient von FTP laden und problemlos Anmerkungen hinzufügen und so die Zusammenarbeit und Dokumentenverwaltung in Ihren Anwendungen verbessern.
## FAQs
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Office-Dokumente, Bilder und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen, die mit GroupDocs.Annotation für .NET hinzugefügt wurden?
Absolut, GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen für das Erscheinungsbild von Anmerkungen, einschließlich Farben, Stilen und Formen.
### Bietet GroupDocs.Annotation für .NET Unterstützung für Cloud-Speicherdienste?
Ja, GroupDocs.Annotation für .NET lässt sich nahtlos in beliebte Cloud-Speicherdienste integrieren, sodass Sie Dokumente von Diensten wie Dropbox, Google Drive und OneDrive laden und speichern können.
### Gibt es eine Testversion für GroupDocs.Annotation für .NET?
 Ja, Sie können die Funktionen von GroupDocs.Annotation für .NET erkunden, indem Sie die kostenlose Testversion von herunterladen[Release-Seite](https://releases.groupdocs.com/).
### Wie erhalte ich technische Hilfe oder Support für GroupDocs.Annotation für .NET?
 Für technische Unterstützung, Fehlerbehebung oder allgemeine Anfragen können Sie GroupDocs.Annotation für .NET besuchen[Hilfeforum](https://forum.groupdocs.com/c/annotation/10).