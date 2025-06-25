---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Distanzanmerkungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und Kommunikation."
"linktitle": "Entfernungsanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Entfernungsanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Entfernungsanmerkung zum Dokument hinzufügen

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET eine Distanzanmerkung zu einem Dokument hinzufügen. Führen Sie dazu die folgenden Schritte aus:
## Voraussetzungen

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie fortfahren:

- GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die GroupDocs.Annotation für .NET-Bibliothek herunter und installieren Sie sie von [dieser Link](https://releases.groupdocs.com/annotation/net/).
- Zu kommentierendes Dokument: Bereiten Sie das Dokument (z. B. PDF) vor, dem Sie die Entfernungsanmerkung hinzufügen möchten.
- Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung mit Visual Studio oder einer anderen IDE Ihrer Wahl ein.

## Namespaces importieren

Bevor Sie beginnen, stellen Sie sicher, dass Ihr Code die erforderlichen Namespaces enthält. Diese Namespaces sind für den Zugriff auf die erforderlichen Klassen und Methoden unerlässlich.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Schritt 1: Annotator initialisieren

Beginnen Sie mit der Initialisierung des `Annotator` Objekt mit dem Pfad zum Dokument, das Sie mit Anmerkungen versehen möchten.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier eingefügt
}
```

## Schritt 2: Entfernungsanmerkung erstellen

Erstellen Sie nun eine `DistanceAnnotation` Objekt und konfigurieren Sie seine Eigenschaften wie Kastenabmessungen, Nachricht, Deckkraft, Stiftfarbe usw.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Schritt 3: Anmerkung hinzufügen

Fügen Sie die erstellte Distanzanmerkung dem Dokument hinzu, indem Sie `Add` Methode des Annotatorobjekts.

```csharp
annotator.Add(distance);
```

## Schritt 4: Dokument speichern

Speichern Sie das kommentierte Dokument am gewünschten Speicherort auf Ihrem System.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Schritt 5: Bestätigung anzeigen

Zeigen Sie abschließend eine Meldung an, die das erfolgreiche Speichern des kommentierten Dokuments bestätigt.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss

Das Hinzufügen von Distanzanmerkungen zu Dokumenten mit GroupDocs.Annotation für .NET ist unkompliziert. Mit den in diesem Tutorial beschriebenen Schritten können Sie Ihre Dokumente mit wertvollen Anmerkungen versehen und so die Zusammenarbeit und Kommunikation verbessern.

## Häufig gestellte Fragen

### F: Kann ich das Erscheinungsbild der Entfernungsanmerkung anpassen?

A: Ja, Sie können verschiedene Eigenschaften wie Farbe, Deckkraft, Linienstil usw. an Ihre Anforderungen anpassen.

### F: Unterstützt GroupDocs.Annotation Anmerkungen zu verschiedenen Dokumenttypen?

A: Ja, GroupDocs.Annotation unterstützt Anmerkungen in einer Vielzahl von Dokumentformaten, darunter PDF, Word, Excel, PowerPoint und mehr.

### F: Gibt es eine kostenlose Testversion für GroupDocs.Annotation?

A: Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Annotation zugreifen von [dieser Link](https://releases.groupdocs.com/).

### F: Wo finde ich die Dokumentation für GroupDocs.Annotation für .NET?

A: Sie können die ausführliche Dokumentation zu Rate ziehen, die verfügbar ist [Hier](https://tutorials.groupdocs.com/annotation/net/).

### F: Wie kann ich Support oder Hilfe zu GroupDocs.Annotation erhalten?

A: Sie können Unterstützung und Hilfe im GroupDocs.Annotation-Community-Forum suchen. [Hier](https://forum.groupdocs.com/c/annotation/10).