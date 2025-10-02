---
"description": "Erfahren Sie, wie Sie PDF-Dokumente mit GroupDocs.Annotation für .NET programmgesteuert kommentieren. Schritt-für-Schritt-Anleitung mit Codebeispielen."
"linktitle": "Dokument von URL laden"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dokument von URL laden"
"url": "/de/net/document-loading-essentials/load-document-from-url/"
type: docs
"weight": 15
---

# Dokument von URL laden

## Einführung
GroupDocs.Annotation für .NET ist eine funktionsreiche Bibliothek, mit der Entwickler ihren .NET-Anwendungen mühelos Anmerkungsfunktionen hinzufügen können. Mit GroupDocs.Annotation können Sie PDF-Dokumente programmgesteuert kommentieren. So können Benutzer Text hervorheben, Kommentare hinzufügen, Formen zeichnen und vieles mehr. Dieses Tutorial führt Sie durch das Laden eines Dokuments von einer URL, das Hinzufügen von Anmerkungen und das Speichern des kommentierten Dokuments mit GroupDocs.Annotation für .NET.
## Voraussetzungen
Stellen Sie zunächst sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Entwicklungscomputer installiert ist.
2. GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET herunter und installieren Sie es von der [Webseite](https://releases.groupdocs.com/annotation/net/).
3. Grundkenntnisse in C#: Machen Sie sich mit der Programmiersprache C# vertraut.
4. Internetverbindung: Sie benötigen eine Internetverbindung, um auf externe Ressourcen zuzugreifen und Beispieldateien herunterzuladen.

## Namespaces importieren
Importieren wir zunächst die erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Schritt 1: Dokument von URL laden
Um ein PDF-Dokument über eine URL mit Anmerkungen zu versehen, gehen Sie folgendermaßen vor:
### Schritt 1.1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Schritt 1.2: URL angeben
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Schritt 1.3: Dokument laden
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Fügen Sie hier Anmerkungen hinzu
    annotator.Save(outputPath);
}
```
## Schritt 2: Anmerkungen hinzufügen
Fügen wir nun dem geladenen Dokument Anmerkungen hinzu. In diesem Beispiel fügen wir eine Bereichsanmerkung hinzu:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Schritt 3: Kommentiertes Dokument speichern
Speichern Sie abschließend das kommentierte Dokument im angegebenen Ausgabepfad:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie Sie PDF-Dokumente mit GroupDocs.Annotation für .NET kommentieren. Folgen Sie der Schritt-für-Schritt-Anleitung, um die Kommentarfunktion nahtlos in Ihre .NET-Anwendungen zu integrieren und Benutzern die effektive Zusammenarbeit an PDF-Dateien zu ermöglichen.

## Häufig gestellte Fragen
### Ist GroupDocs.Annotation für .NET mit allen .NET-Frameworks kompatibel?
Ja, GroupDocs.Annotation für .NET ist mit verschiedenen .NET-Frameworks kompatibel, einschließlich .NET Framework, .NET Core und .NET Standard.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsmöglichkeiten, mit denen Sie das Aussehen und Verhalten von Anmerkungen Ihren Anforderungen entsprechend ändern können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET herunterladen von der [Webseite](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Annotation für .NET?
Wenn Sie technische Probleme haben oder Fragen zu GroupDocs.Annotation für .NET haben, können Sie sich an die [Support-Forum](https://forum.groupdocs.com/c/annotation/10).
### Wo kann ich eine Lizenz für GroupDocs.Annotation für .NET erwerben?
Sie können eine Lizenz für GroupDocs.Annotation für .NET erwerben von der [Kaufseite](https://purchase.groupdocs.com/buy).