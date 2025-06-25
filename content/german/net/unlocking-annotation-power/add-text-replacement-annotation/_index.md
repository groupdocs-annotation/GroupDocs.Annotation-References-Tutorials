---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET mühelos Textersetzungsanmerkungen zu Ihren .NET-Dokumenten hinzufügen. Erweitern Sie Ihre Möglichkeiten zur Dokumentbearbeitung."
"linktitle": "Textersetzungsanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Textersetzungsanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Textersetzungsanmerkung zum Dokument hinzufügen

## Einführung
In diesem Tutorial führen wir Sie durch das Hinzufügen einer Textersetzungsanmerkung zu Ihren Dokumenten mithilfe von GroupDocs.Annotation für .NET. Diese leistungsstarke Bibliothek ermöglicht Entwicklern die programmgesteuerte Bearbeitung und Kommentierung verschiedener Dokumenttypen. Am Ende dieses Tutorials verfügen Sie über das Wissen, Textersetzungsanmerkungen nahtlos in Ihre .NET-Anwendungen zu integrieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:
### 1. .NET Framework installiert
Stellen Sie sicher, dass das .NET Framework auf Ihrem Entwicklungscomputer installiert ist. Sie können es von der Microsoft-Website herunterladen.
### 2. GroupDocs.Annotation für die .NET-Bibliothek
Laden Sie die Bibliothek GroupDocs.Annotation für .NET herunter und installieren Sie sie von der [Webseite](https://releases.groupdocs.com/annotation/net/). Diese Bibliothek bietet die notwendigen Tools und Funktionen zum Arbeiten mit Anmerkungen in verschiedenen Dokumentformaten.
### 3. Einrichten der Entwicklungsumgebung
Richten Sie Ihre bevorzugte Entwicklungsumgebung, beispielsweise Visual Studio, ein, um .NET-Anwendungen zu erstellen und auszuführen.

## Namespaces importieren
Bevor wir uns in den Codierungsteil stürzen, importieren wir die erforderlichen Namespaces, die für die Arbeit mit GroupDocs.Annotation für .NET erforderlich sind:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Schritt 1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definieren wir den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier platziert
}
```
Wir initialisieren das Annotator-Objekt, indem wir das Eingabedokument („input.pdf“) innerhalb eines Using-Blocks angeben, um die ordnungsgemäße Bereitstellung der Ressourcen sicherzustellen.
## Schritt 3: Ersatzanmerkung erstellen
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
Hier erstellen wir ein ReplacementAnnotation-Objekt mit verschiedenen Eigenschaften wie Erstellungsdatum, Schriftfarbe, Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Punkte (Koordinaten), Antworten (Kommentare) und dem zu ersetzenden Text.
## Schritt 4: Anmerkung hinzufügen
```csharp
annotator.Add(replacement);
```
Wir fügen die erstellte Ersatzannotation dem Annotator hinzu.
## Schritt 5: Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das kommentierte Dokument im angegebenen Ausgabepfad.
## Schritt 6: Erfolgsmeldung anzeigen
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Es wird eine Erfolgsmeldung angezeigt, die angibt, dass das Dokument erfolgreich gespeichert wurde.

## Abschluss
In diesem Tutorial haben wir das Hinzufügen von Textersetzungsanmerkungen zu Dokumenten mit GroupDocs.Annotation für .NET erläutert. Wenn Sie der Schritt-für-Schritt-Anleitung folgen und die Voraussetzungen verstehen, können Sie diese Funktionalität problemlos in Ihre .NET-Anwendungen integrieren.
## Häufig gestellte Fragen
### Kann ich mit GroupDocs.Annotation für .NET Dokumente unterschiedlicher Formate mit Anmerkungen versehen?
Ja, GroupDocs.Annotation für .NET unterstützt das Kommentieren verschiedener Dokumentformate wie PDF, DOCX, PPTX, XLSX und mehr.
### Ist GroupDocs.Annotation für .NET sowohl für Desktop- als auch für Webanwendungen geeignet?
Ja, GroupDocs.Annotation für .NET kann sowohl in Desktop- als auch in Webanwendungen verwendet werden und bietet Entwicklern Flexibilität.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen, die mit GroupDocs.Annotation für .NET hinzugefügt wurden?
Natürlich können Sie das Erscheinungsbild von Anmerkungen anpassen, indem Sie Eigenschaften wie Farbe, Deckkraft, Schriftart usw. ändern.
### Bietet GroupDocs.Annotation für .NET Unterstützung für kollaborative Anmerkungsfunktionen?
Ja, GroupDocs.Annotation für .NET bietet Funktionen für die gemeinsame Kommentierung, sodass mehrere Benutzer Dokumente gleichzeitig kommentieren können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET nutzen von der [Webseite](https://releases.groupdocs.com/).