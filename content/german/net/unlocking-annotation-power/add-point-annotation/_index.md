---
title: Punktanmerkung zum Dokument hinzufügen
linktitle: Punktanmerkung zum Dokument hinzufügen
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Punktanmerkungen zu PDFs hinzufügen. Schritt-für-Schritt-Anleitung für eine nahtlose Integration.
weight: 17
url: /de/net/unlocking-annotation-power/add-point-annotation/
---
## Einführung
GroupDocs.Annotation für .NET ist ein leistungsstarkes Tool, mit dem Entwickler programmgesteuert verschiedene Arten von Anmerkungen zu Dokumenten hinzufügen können. In diesem Tutorial konzentrieren wir uns auf das Hinzufügen einer Punktanmerkung zu einem Dokument mithilfe von C#.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. Grundlegendes Verständnis der Programmiersprache C#.
2. Visual Studio ist auf Ihrem System installiert.
3.  GroupDocs.Annotation für .NET-Bibliothek installiert. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).

## Notwendige Namespaces importieren
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
In diesem Schritt definieren wir den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Hier initialisieren wir die`Annotator` Objekt mit dem Eingabedokument („input.pdf“).
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
 In diesem Schritt erstellen wir eine`PointAnnotation` Objekt und geben Sie seine Eigenschaften wie Position, Nachricht, Seitenzahl und Antworten an.
## Schritt 4: Anmerkung hinzufügen
```csharp
annotator.Add(point);
```
Hier fügen wir die erstellte Punktanmerkung zum Dokument hinzu.
## Schritt 5: Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine Punktanmerkung hinzufügt. Mit dieser leistungsstarken Bibliothek können Sie Ihre Dokumentenverwaltungsanwendungen durch die Integration von Anmerkungsfunktionen erweitern.
## FAQs
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation für .NET bietet umfangreiche Optionen zum Anpassen des Erscheinungsbilds von Anmerkungen an die Anforderungen Ihrer Anwendung.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
 Ja, Sie können eine kostenlose Testversion von nutzen[Hier](https://releases.groupdocs.com/).
### Wie kann ich Unterstützung bei Problemen oder Fragen im Zusammenhang mit GroupDocs.Annotation für .NET erhalten?
 Unterstützung erhalten Sie im GroupDocs.Annotation-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).
### Kann ich zu Testzwecken eine temporäre Lizenz erhalten?
 Ja, Sie können eine temporäre Lizenz erhalten von[Hier](https://purchase.groupdocs.com/temporary-license/).