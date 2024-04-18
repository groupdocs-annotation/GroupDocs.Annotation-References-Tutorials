---
title: Fügen Sie dem Dokument eine verschnörkelte Textanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine verschnörkelte Textanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit Groupdocs.Annotation für .NET mühelos Textanmerkungen zu Dokumenten hinzufügen. Verbessern Sie die Prozesse der Zusammenarbeit und Dokumentenprüfung.
type: docs
weight: 25
url: /de/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Einführung

Groupdocs.Annotation für .NET ist eine vielseitige Bibliothek, die es Entwicklern ermöglicht, mühelos robuste Annotationsfunktionen in ihre .NET-Anwendungen zu integrieren. Ganz gleich, ob Sie mit PDFs, Word-Dokumenten oder anderen gängigen Dateiformaten arbeiten, Groupdocs.Annotation bietet eine nahtlose Lösung zum Kommentieren und Verbessern der Zusammenarbeit an Dokumenten.

## Voraussetzungen

Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

## Namespaces importieren

Stellen Sie sicher, dass Sie die erforderlichen Namespaces importieren, um auf die von Groupdocs.Annotation für .NET bereitgestellten Funktionen zuzugreifen.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nachdem wir nun die Voraussetzungen erfüllt haben, unterteilen wir den Prozess des Hinzufügens von verschnörkelten Textanmerkungen in mehrere Schritte.

## Schritt 1: Ausgabepfad definieren

Definieren Sie den Pfad, in dem das kommentierte Dokument gespeichert wird.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Schritt 2: Annotator initialisieren

Initialisieren Sie das Annotator-Objekt, indem Sie den Eingabedokumentpfad angeben.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode kommt hierher
}
```

## Schritt 3: Erstellen Sie eine verschnörkelte Anmerkung

Erstellen Sie ein SquigglyAnnotation-Objekt und geben Sie seine Eigenschaften an.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## Schritt 4: Anmerkung hinzufügen

Fügen Sie die erstellte verschnörkelte Anmerkung zum Dokument hinzu.

```csharp
annotator.Add(squiggly);
```

## Schritt 5: Dokument speichern

Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.

```csharp
annotator.Save(outputPath);
```

## Schritt 6: Bestätigung anzeigen

Zeigt eine Meldung an, die das erfolgreiche Speichern des mit Anmerkungen versehenen Dokuments bestätigt.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss

Zusammenfassend stellt Groupdocs.Annotation für .NET Entwicklern einen robusten Satz an Tools zur nahtlosen Integration von Dokumentanmerkungsfunktionen in ihre .NET-Anwendungen zur Verfügung. Wenn Sie dieser Schritt-für-Schritt-Anleitung folgen, können Sie Ihren Dokumenten mühelos Textanmerkungen hinzufügen und so die Zusammenarbeit und die Dokumentüberprüfungsprozesse verbessern.

## FAQs

### F: Kann Groupdocs.Annotation Annotationen in verschiedenen Dateiformaten unterstützen?

A: Ja, Groupdocs.Annotation unterstützt Anmerkungen in einer Vielzahl von Dateiformaten, darunter PDFs, Word-Dokumente, Excel-Tabellen und mehr.

### F: Ist Groupdocs.Annotation sowohl mit Desktop- als auch mit Webanwendungen kompatibel?

A: Auf jeden Fall! Groupdocs.Annotation lässt sich nahtlos in Desktop- und Webanwendungen integrieren und bietet Flexibilität und Vielseitigkeit.

### F: Gibt es Lizenzoptionen für Groupdocs.Annotation?

A: Ja, Groupdocs.Annotation bietet flexible Lizenzoptionen, die auf die Bedürfnisse von Einzelpersonen oder Unternehmen zugeschnitten sind, einschließlich temporärer Lizenzen für Testzwecke.

### F: Können mit Groupdocs.Annotation erstellte Anmerkungen angepasst werden?

A: Auf jeden Fall! Groupdocs.Annotation bietet umfangreiche Anpassungsoptionen für Anmerkungen, sodass Entwickler Anmerkungen an ihre spezifischen Anforderungen anpassen können.

### F: Bietet Groupdocs.Annotation Support und Dokumentation für Entwickler?

A: Tatsächlich! Groupdocs.Annotation bietet umfassende Dokumentation und spezielle Support-Foren, um Entwickler bei der effektiven Nutzung seiner Funktionen zu unterstützen.