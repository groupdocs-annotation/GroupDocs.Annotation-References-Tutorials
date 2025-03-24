---
title: Linkanmerkung zum Dokument hinzufügen
linktitle: Linkanmerkung zum Dokument hinzufügen
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs.Annotation für .NET Linkanmerkungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und Interaktivität.
weight: 16
url: /de/net/unlocking-annotation-power/add-link-annotation/
---

# Linkanmerkung zum Dokument hinzufügen

## Einführung
Groupdocs.Annotation für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, umfassende Annotationsfunktionen mühelos in ihre .NET-Anwendungen zu integrieren. Eine der wichtigsten Funktionen ist die Möglichkeit, Linkanmerkungen zu Dokumenten hinzuzufügen und so die Zusammenarbeit und Interaktivität zu verbessern.
## Voraussetzungen
Bevor Sie mit dem Hinzufügen von Linkanmerkungen beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
- Grundlegendes Verständnis der Programmiersprache C#.
- Installierte Groupdocs.Annotation für die .NET-Bibliothek.
- Zugriff auf ein Dokument, das Sie mit Anmerkungen versehen möchten.

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces importieren, um Groupdocs.Annotation für .NET-Funktionen nutzen zu können. Dadurch kann Ihre Anwendung auf die Klassen und Methoden zugreifen, die zum Kommentieren von Dokumenten erforderlich sind.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad festlegen
Definieren Sie den Pfad, in dem Sie das mit Anmerkungen versehene Dokument speichern möchten.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Erstellen Sie eine Instanz von`Annotator` Klasse, indem Sie den Pfad des Dokuments angeben, das Sie mit Anmerkungen versehen möchten.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```
## Schritt 3: Linkanmerkung erstellen
 Definieren Sie a`LinkAnnotation` Objekt und geben Sie seine Eigenschaften wie Nachricht, Deckkraft, Seitenzahl, Hintergrundfarbe, Punkte, Antworten und URL an.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## Schritt 4: Anmerkung hinzufügen
 Fügen Sie die erstellte Linkanmerkung mithilfe von zum Dokument hinzu`Add` Methode der Annotator-Instanz.
```csharp
annotator.Add(link);
```
## Schritt 5: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Informieren Sie den Benutzer über das erfolgreiche Speichern des kommentierten Dokuments.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass Sie durch Befolgen der oben genannten Schritte mithilfe von Groupdocs.Annotation für .NET nahtlos Linkanmerkungen zu Dokumenten hinzufügen können. Dies verbessert die Zusammenarbeit an Dokumenten und bietet Benutzern interaktive Funktionen.
## FAQs
### Ist Groupdocs.Annotation für .NET mit allen Arten von Dokumenten kompatibel?
Groupdocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Word, Excel und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, Sie können verschiedene Eigenschaften von Anmerkungen wie Farbe, Deckkraft und Größe an Ihre Anforderungen anpassen.
### Bietet Groupdocs.Annotation für .NET Funktionen für die Zusammenarbeit in Echtzeit?
Ja, Groupdocs.Annotation für .NET bietet Funktionen für die Zusammenarbeit in Echtzeit, sodass mehrere Benutzer Dokumente gleichzeitig mit Anmerkungen versehen können.
### Ist technischer Support für Groupdocs-Produkte verfügbar?
 Ja, technischer Support für Groupdocs-Produkte ist über das Forum und den Support verfügbar[Hier](https://forum.groupdocs.com/c/annotation/10).
### Kann ich Groupdocs.Annotation für .NET vor dem Kauf testen?
Ja, Sie können eine kostenlose Testversion von Groupdocs.Annotation für .NET nutzen, um die Funktionen zu erkunden, bevor Sie einen Kauf tätigen[Hier](https://purchase.groupdocs.com/temporary-license/).