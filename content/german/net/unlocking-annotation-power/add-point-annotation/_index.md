---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Punktanmerkungen zu PDFs hinzufügen. Schritt-für-Schritt-Anleitung für die nahtlose Integration."
"linktitle": "Punktanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Punktanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# Punktanmerkung zum Dokument hinzufügen

## Einführung
GroupDocs.Annotation für .NET ist ein leistungsstarkes Tool, mit dem Entwickler verschiedene Arten von Anmerkungen programmgesteuert zu Dokumenten hinzufügen können. In diesem Tutorial konzentrieren wir uns auf das Hinzufügen einer Punktanmerkung zu einem Dokument mit C#.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:
1. Grundlegende Kenntnisse der Programmiersprache C#.
2. Visual Studio ist auf Ihrem System installiert.
3. GroupDocs.Annotation für .NET-Bibliothek installiert. Sie können es herunterladen von [Hier](https://releases.groupdocs.com/annotation/net/).

## Importieren der erforderlichen Namespaces
Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In diesem Schritt definieren wir den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Hier initialisieren wir die `Annotator` Objekt mit dem Eingabedokument („input.pdf“).
## Schritt 3: Punktanmerkung erstellen
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
    }
};
```
In diesem Schritt erstellen wir eine `PointAnnotation` Objekt und geben Sie seine Eigenschaften wie Position, Nachricht, Seitenzahl und Antworten an.
## Schritt 4: Anmerkung hinzufügen
```csharp
annotator.Add(point);
```
Hier fügen wir die erstellte Punktanmerkung dem Dokument hinzu.
## Schritt 5: Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das kommentierte Dokument im angegebenen Ausgabepfad.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET eine Punktanmerkung zu einem Dokument hinzufügt. Mit dieser leistungsstarken Bibliothek können Sie Ihre Dokumentenverwaltungsanwendungen durch die Integration von Anmerkungsfunktionen verbessern.
## Häufig gestellte Fragen
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation für .NET bietet umfangreiche Optionen zum Anpassen der Darstellung von Anmerkungen an die Anforderungen Ihrer Anwendung.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion nutzen von [Hier](https://releases.groupdocs.com/).
### Wie erhalte ich Support bei Problemen oder Fragen zu GroupDocs.Annotation für .NET?
Sie erhalten Unterstützung im GroupDocs.Annotation-Forum [Hier](https://forum.groupdocs.com/c/annotation/10).
### Kann ich zu Testzwecken eine temporäre Lizenz erhalten?
Ja, Sie können eine vorläufige Lizenz erhalten von [Hier](https://purchase.groupdocs.com/temporary-license/).