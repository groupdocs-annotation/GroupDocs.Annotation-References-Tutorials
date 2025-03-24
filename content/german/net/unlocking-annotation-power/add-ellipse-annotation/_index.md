---
title: Fügen Sie dem Dokument eine Ellipsenanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Ellipsenanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation Ellipsenanmerkungen zu Dokumenten in .NET hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und Kommunikation.
weight: 13
url: /de/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET eine Ellipsenanmerkung zu einem Dokument hinzufügen. Diese Schritt-für-Schritt-Anleitung führt Sie durch den Prozess und stellt sicher, dass Sie jeden Schritt klar verstehen.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Annotation für .NET: Stellen Sie sicher, dass Sie GroupDocs.Annotation für .NET heruntergeladen und installiert haben. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): Sie benötigen eine auf Ihrem System installierte IDE, z. B. Visual Studio, um den Code zu schreiben und auszuführen.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad festlegen
Definieren Sie den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den Annotator, indem Sie den Pfad des Eingabedokuments angeben:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Schritt 3: Erstellen Sie eine Ellipsenanmerkung
 Erstellen Sie eine Instanz von`EllipseAnnotation` Klasse und legen Sie ihre Eigenschaften fest:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## Schritt 4: Anmerkung hinzufügen
Fügen Sie dem Dokument die Ellipsenanmerkung hinzu:
```csharp
annotator.Add(ellipse);
```
## Schritt 5: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im Ausgabepfad:
```csharp
annotator.Save(outputPath);
```

## Abschluss
Glückwunsch! Sie haben mit GroupDocs.Annotation für .NET erfolgreich eine Ellipsenanmerkung zu einem Dokument hinzugefügt. Sie können diese Funktionalität jetzt in Ihre .NET-Anwendungen integrieren, um die Zusammenarbeit und Kommunikation an Dokumenten zu verbessern.
## FAQs
### Kann ich das Erscheinungsbild der Ellipsenanmerkung anpassen?
Ja, Sie können verschiedene Eigenschaften wie Hintergrundfarbe, Rahmenfarbe, Deckkraft usw. entsprechend Ihren Anforderungen anpassen.
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, DOCX, PPTX, XLSX und mehr.
### Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?
Ja, Sie können einem einzelnen Dokument mehrere Anmerkungen hinzufügen, darunter Ellipsen, Rechtecke, Text usw.
### Gibt es zu Testzwecken eine Testversion?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/) um seine Eigenschaften zu bewerten.
### Wo erhalte ich technischen Support für GroupDocs.Annotation für .NET?
 Technischen Support erhalten Sie im GroupDocs.Annotation-Community-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).