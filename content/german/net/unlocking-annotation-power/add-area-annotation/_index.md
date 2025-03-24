---
title: Bereichsanmerkung zum Dokument hinzufügen
linktitle: Bereichsanmerkung zum Dokument hinzufügen
second_title: GroupDocs.Annotation .NET-API
description: Verbessern Sie Ihre Zusammenarbeit an Dokumenten mit Groupdocs.Annotation für .NET. Erfahren Sie Schritt für Schritt, wie Sie Bereichsanmerkungen hinzufügen.
weight: 10
url: /de/net/unlocking-annotation-power/add-area-annotation/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens von Bereichsanmerkungen zu Dokumenten mithilfe von Groupdocs.Annotation für .NET. Bereichsanmerkungen sind eine wertvolle Funktion, die es Benutzern ermöglicht, bestimmte Bereiche eines Dokuments hervorzuheben und so für Klarheit und Kontext zum Inhalt zu sorgen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  Groupdocs.Annotation für .NET: Stellen Sie sicher, dass die erforderlichen Bibliotheken und Abhängigkeiten installiert sind. Sie können sie hier herunterladen[Webseite](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung für die .NET-Entwicklung ein.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt. Diese Namespaces enthalten die Klassen und Methoden, die für die Arbeit mit Annotationen erforderlich sind.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## Schritt 1: Ausgabepfad initialisieren
Definieren Sie den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Erstellen Sie eine Instanz von`Annotator` Klasse, indem Sie den Pfad des Dokuments als Parameter übergeben.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```
## Schritt 3: Bereichsanmerkung erstellen
Definieren Sie die Eigenschaften der Bereichsanmerkung, z. B. Hintergrundfarbe, Position, Nachricht, Deckkraft usw.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
 Fügen Sie die Bereichsanmerkung mit dem Dokument zum Dokument hinzu`Add` Methode der`Annotator` Beispiel.
```csharp
annotator.Add(area);
```
## Schritt 5: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Informieren Sie den Benutzer darüber, dass das Dokument erfolgreich mit Anmerkungen versehen und gespeichert wurde.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mithilfe von Groupdocs.Annotation für .NET Bereichsanmerkungen zu Dokumenten hinzufügt. Wenn Sie der Schritt-für-Schritt-Anleitung folgen, können Sie Ihre Dokumente ganz einfach mit wertvollen Anmerkungen ergänzen und so die Zusammenarbeit und das Verständnis verbessern.
## FAQs
### Kann ich das Erscheinungsbild der Bereichsanmerkung anpassen?
Ja, Sie können verschiedene Aspekte wie Hintergrundfarbe, Deckkraft, Stiftstil usw. an Ihre Vorlieben anpassen.
### Ist Groupdocs.Annotation mit anderen Dokumentformaten kompatibel?
Ja, Groupdocs.Annotation unterstützt verschiedene Dokumentformate, darunter PDF, DOCX, PPTX und mehr.
### Kann ich dem gleichen Dokument mehrere Anmerkungen hinzufügen?
Auf jeden Fall können Sie bei Bedarf mehrere Anmerkungen unterschiedlicher Art zu demselben Dokument hinzufügen.
### Bietet Groupdocs.Annotation plattformübergreifende Kompatibilität?
Ja, Groupdocs.Annotation ist mit dem .NET Framework kompatibel und eignet sich daher für Windows-, Linux- und macOS-Entwicklungsumgebungen.
### Gibt es zu Testzwecken eine Testversion?
 Ja, Sie können über die auf eine kostenlose Testversion zugreifen[Webseite](https://releases.groupdocs.com/).