---
title: Fügen Sie dem Dokument eine Textersetzungsanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Textersetzungsanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET mühelos Textersetzungsanmerkungen zu Ihren .NET-Dokumenten hinzufügen. Erweitern Sie Ihre Fähigkeiten zur Dokumentenbearbeitung.
weight: 24
url: /de/net/unlocking-annotation-power/add-text-replacement-annotation/
---

# Fügen Sie dem Dokument eine Textersetzungsanmerkung hinzu

## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens einer Textersetzungsanmerkung zu Ihren Dokumenten mithilfe von GroupDocs.Annotation für .NET. Mit dieser leistungsstarken Bibliothek können Entwickler verschiedene Arten von Dokumenten programmgesteuert bearbeiten und mit Anmerkungen versehen. Am Ende dieses Tutorials verfügen Sie über das Wissen, Textersetzungsanmerkungen nahtlos in Ihre .NET-Anwendungen zu integrieren.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:
### 1. .NET Framework installiert
Stellen Sie sicher, dass das .NET Framework auf Ihrem Entwicklungscomputer installiert ist. Sie können es von der Microsoft-Website herunterladen.
### 2. GroupDocs.Annotation für die .NET-Bibliothek
 Laden Sie die GroupDocs.Annotation für .NET-Bibliothek von herunter und installieren Sie sie[Webseite](https://releases.groupdocs.com/annotation/net/). Diese Bibliothek stellt die notwendigen Werkzeuge und Funktionen bereit, um mit Anmerkungen in verschiedenen Dokumentformaten zu arbeiten.
### 3. Einrichtung der Entwicklungsumgebung
Richten Sie Ihre bevorzugte Entwicklungsumgebung wie Visual Studio ein, um .NET-Anwendungen zu erstellen und auszuführen.

## Namespaces importieren
Bevor wir in den Codierungsteil eintauchen, importieren wir die notwendigen Namespaces, die für die Arbeit mit GroupDocs.Annotation für .NET erforderlich sind:
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
Wir initialisieren das Annotator-Objekt, indem wir das Eingabedokument („input.pdf“) innerhalb eines using-Blocks angeben, um eine ordnungsgemäße Entsorgung der Ressourcen sicherzustellen.
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
Hier erstellen wir ein ReplacementAnnotation-Objekt mit verschiedenen Eigenschaften wie Erstellungsdatum, Schriftfarbe, Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Punkten (Koordinaten), Antworten (Kommentaren) und dem zu ersetzenden Text.
## Schritt 4: Anmerkung hinzufügen
```csharp
annotator.Add(replacement);
```
Wir fügen die erstellte Ersatzannotation zum Annotator hinzu.
## Schritt 5: Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
## Schritt 6: Erfolgsmeldung anzeigen
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Es wird eine Erfolgsmeldung angezeigt, die angibt, dass das Dokument erfolgreich gespeichert wurde.

## Abschluss
In diesem Tutorial haben wir den Prozess des Hinzufügens von Textersetzungsanmerkungen zu Dokumenten mithilfe von GroupDocs.Annotation für .NET behandelt. Wenn Sie der Schritt-für-Schritt-Anleitung folgen und die Voraussetzungen verstehen, können Sie diese Funktionalität problemlos in Ihre .NET-Anwendungen integrieren.
## FAQs
### Kann ich Dokumente unterschiedlicher Formate mit GroupDocs.Annotation für .NET mit Anmerkungen versehen?
Ja, GroupDocs.Annotation für .NET unterstützt das Kommentieren verschiedener Dokumentformate wie PDF, DOCX, PPTX, XLSX und mehr.
### Ist GroupDocs.Annotation für .NET sowohl für Desktop- als auch für Webanwendungen geeignet?
Ja, GroupDocs.Annotation für .NET kann sowohl in Desktop- als auch in Webanwendungen verwendet werden und bietet Entwicklern Flexibilität.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen, die mit GroupDocs.Annotation für .NET hinzugefügt wurden?
Sie können das Erscheinungsbild von Anmerkungen auf jeden Fall anpassen, indem Sie Eigenschaften wie Farbe, Deckkraft, Schriftart usw. ändern.
### Bietet GroupDocs.Annotation für .NET Unterstützung für kollaborative Anmerkungsfunktionen?
Ja, GroupDocs.Annotation für .NET bietet Funktionen für kollaboratives Annotieren, sodass mehrere Benutzer gleichzeitig Dokumente mit Anmerkungen versehen können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET unter erhalten[Webseite](https://releases.groupdocs.com/).