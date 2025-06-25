---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Textunterstreichungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und Kommunikation."
"linktitle": "Fügen Sie dem Dokument eine Unterstreichungsanmerkung hinzu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Fügen Sie dem Dokument eine Unterstreichungsanmerkung hinzu"
"url": "/de/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Fügen Sie dem Dokument eine Unterstreichungsanmerkung hinzu

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET eine Unterstreichungsanmerkung zu einem Dokument hinzufügen. Unterstreichungsanmerkungen können hilfreich sein, um bestimmte Teile eines Dokuments hervorzuheben, z. B. wichtige Passagen oder Schlüsselpunkte.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen installiert sind:
1. GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET herunter und installieren Sie es von [Hier](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem System installiert ist.

## Namespaces importieren
Importieren wir zunächst die erforderlichen Namespaces in unser Projekt:
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
In diesem Schritt definieren wir den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Hier initialisieren wir eine Instanz des `Annotator` Klasse, indem Sie den Pfad des Eingabedokuments angeben.
## Schritt 3: Unterstrichene Anmerkung erstellen
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // funktioniert unterstützt nur Word- und PDF-Dokumente
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
Dieser Schritt umfasst die Erstellung eines `UnderlineAnnotation` Objekt mit verschiedenen Eigenschaften wie Schriftfarbe, Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Unterstreichungsfarbe, Punkte und Antworten.
## Schritt 4: Anmerkung zum Dokument hinzufügen
```csharp
annotator.Add(underline);
```
Hier fügen wir dem Dokument die Unterstreichungsanmerkung hinzu.
## Schritt 5: Kommentiertes Dokument speichern
```csharp
annotator.Save(outputPath);
```
Abschließend speichern wir das kommentierte Dokument im angegebenen Ausgabepfad.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine Textunterstreichung hinzufügt. Diese leistungsstarke Bibliothek bietet verschiedene Anmerkungsoptionen zur Verbesserung der Zusammenarbeit und Kommunikation an Dokumenten.
## Häufig gestellte Fragen
### Kann ich das Erscheinungsbild der Unterstreichungsanmerkung anpassen?
Ja, Sie können Eigenschaften wie Farbe, Deckkraft und Position Ihren Anforderungen entsprechend anpassen.
### Ist GroupDocs.Annotation mit verschiedenen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter Word und PDF.
### Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?
Auf jeden Fall. Mit GroupDocs.Annotation können Sie einem Dokument mehrere Anmerkungen unterschiedlichen Typs hinzufügen.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
Ja, Sie können auf die kostenlose Testversion zugreifen von [Hier](https://releases.groupdocs.com/).
### Wo erhalte ich Support für GroupDocs.Annotation?
Sie erhalten Unterstützung im GroupDocs.Annotation-Community-Forum [Hier](https://forum.groupdocs.com/c/annotation/10).