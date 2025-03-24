---
title: Fügen Sie dem Dokument eine Textunterstreichungsanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Textunterstreichungsanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET Textunterstreichungsanmerkungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und Kommunikation.
weight: 27
url: /de/net/unlocking-annotation-power/add-text-underline-annotation/
---

# Fügen Sie dem Dokument eine Textunterstreichungsanmerkung hinzu

## Einführung
In diesem Tutorial führen wir den Prozess des Hinzufügens einer Textunterstreichungsanmerkung zu einem Dokument mithilfe von GroupDocs.Annotation für .NET durch. Textunterstreichungsanmerkungen können nützlich sein, um bestimmte Teile eines Dokuments hervorzuheben, beispielsweise wichtige Passagen oder wichtige Punkte.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:
1.  GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET herunter und installieren Sie es von[Hier](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem System installiert ist.

## Namespaces importieren
Importieren wir zunächst die notwendigen Namespaces in unser Projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Lassen Sie uns das Beispiel nun in mehrere Schritte unterteilen:
## Schritt 1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In diesem Schritt definieren wir den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Hier initialisieren wir eine Instanz von`Annotator` Klasse, indem Sie den Pfad des Eingabedokuments angeben.
## Schritt 3: Erstellen Sie eine Unterstreichungsanmerkung
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // Werke unterstützt nur Word- und PDF-Dokumente
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
    }
};
```
 Dieser Schritt umfasst das Erstellen einer`UnderlineAnnotation`Objekt mit verschiedenen Eigenschaften wie Schriftfarbe, Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Unterstreichungsfarbe, Punkten und Antworten.
## Schritt 4: Anmerkung zum Dokument hinzufügen
```csharp
annotator.Add(underline);
```
Hier fügen wir dem Dokument die Unterstreichungsanmerkung hinzu.
## Schritt 5: Kommentiertes Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine Textunterstreichungsanmerkung hinzufügt. Diese leistungsstarke Bibliothek bietet verschiedene Anmerkungsoptionen zur Verbesserung der Zusammenarbeit und Kommunikation an Dokumenten.
## FAQs
### Kann ich das Erscheinungsbild der Unterstreichungsanmerkung anpassen?
Ja, Sie können Eigenschaften wie Farbe, Deckkraft und Position entsprechend Ihren Anforderungen anpassen.
### Ist GroupDocs.Annotation mit verschiedenen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, einschließlich Word und PDF.
### Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?
Absolut, mit GroupDocs.Annotation können Sie einem Dokument mehrere Anmerkungen unterschiedlicher Art hinzufügen.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
 Ja, Sie können auf die kostenlose Testversion zugreifen[Hier](https://releases.groupdocs.com/).
### Wo erhalte ich Unterstützung für GroupDocs.Annotation?
 Unterstützung erhalten Sie im GroupDocs.Annotation-Community-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).