---
title: Fügen Sie dem Dokument durchgestrichene Textanmerkungen hinzu
linktitle: Fügen Sie dem Dokument durchgestrichene Textanmerkungen hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET durchgestrichene Textanmerkungen zu Dokumenten hinzufügen. Verbessern Sie die Zusammenarbeit und Dokumentenprüfungsprozesse effizient.
weight: 26
url: /de/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET eine durchgestrichene Textanmerkung zu einem Dokument hinzufügen. Diese Bibliothek bietet leistungsstarke Tools zum Kommentieren verschiedener Dokumenttypen und verbessert die Zusammenarbeit und Dokumentüberprüfungsprozesse.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Annotation für .NET: Installieren Sie die Bibliothek. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung für die .NET-Entwicklung ein.
3. Dokument: Halten Sie ein Dokument zum Kommentieren bereit, beispielsweise eine PDF-Datei.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces, um auf die Funktionalitäten von GroupDocs.Annotation zuzugreifen:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Lassen Sie uns nun den Prozess des Hinzufügens einer durchgestrichenen Textanmerkung in mehrere Schritte unterteilen:
## Schritt 1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definieren wir den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
## Schritt 2: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initialisieren Sie das Annotator-Objekt, indem Sie den Pfad zum Eingabedokument (in diesem Fall PDF-Datei) angeben.
## Schritt 3: Erstellen Sie eine durchgestrichene Anmerkung
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Erstellen Sie ein StrikeoutAnnotation-Objekt mit den gewünschten Eigenschaften wie Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Punkten (Koordinaten) und Antworten.
## Schritt 4: Anmerkung hinzufügen
```csharp
annotator.Add(strikeout);
```
Fügen Sie die erstellte durchgestrichene Anmerkung zum Dokument hinzu.
## Schritt 5: Dokument speichern
```csharp
annotator.Save(outputPath);
```
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine durchgestrichene Textanmerkung hinzufügt. Diese leistungsstarke Bibliothek ermöglicht eine effiziente Dokumentanmerkung und verbessert die Zusammenarbeit und Dokumentenprüfungsprozesse.
## FAQs
### Ist GroupDocs.Annotation mit verschiedenen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Word, Excel, PowerPoint und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Selbstverständlich können Sie Anmerkungseigenschaften wie Farbe, Deckkraft, Schriftgröße und mehr entsprechend Ihren Anforderungen anpassen.
### Bietet GroupDocs.Annotation Funktionen für die Zusammenarbeit?
Ja, GroupDocs.Annotation erleichtert die Zusammenarbeit, indem es Benutzern ermöglicht, Kommentare, Antworten und Anmerkungen zu Dokumenten hinzuzufügen.
### Gibt es eine kostenlose Testversion?
 Ja, Sie können eine kostenlose Testversion von nutzen[Hier](https://releases.groupdocs.com/).
### Wo erhalte ich Unterstützung für GroupDocs.Annotation?
 Unterstützung erhalten Sie von der[GroupDocs.Annotation-Forum](https://forum.groupdocs.com/c/annotation/10).