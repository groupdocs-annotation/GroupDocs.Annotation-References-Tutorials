---
title: Fügen Sie dem Dokument eine Texthervorhebungsanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Texthervorhebungsanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET Texthervorhebungsanmerkungen zu Dokumenten hinzufügen. Verbessern Sie die Zusammenarbeit und Produktivität mit dieser umfassenden Lösung.
weight: 22
url: /de/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Einführung
Im Bereich der Dokumentenverwaltung und -zusammenarbeit erweist sich GroupDocs.Annotation für .NET als robuste Lösung, die es Entwicklern ermöglicht, Texthervorhebungsanmerkungen nahtlos in ihre Anwendungen zu integrieren. Dieses Tutorial dient als umfassende Anleitung zum Hinzufügen von Texthervorhebungsanmerkungen zu Dokumenten mithilfe von GroupDocs.Annotation für .NET. Durch Schritt-für-Schritt-Anleitungen und ausführliche Erklärungen werden Sie in der Lage sein, die Möglichkeiten dieser leistungsstarken Bibliothek zu nutzen.
## Voraussetzungen
Bevor Sie sich mit der Implementierung von Texthervorhebungsanmerkungen befassen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Umgebungseinrichtung: Konfigurieren Sie eine geeignete Entwicklungsumgebung für die .NET-Entwicklung.
2.  Installation von GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET von der bereitgestellten Website herunter und installieren Sie sie[Download-Link](https://releases.groupdocs.com/annotation/net/).
3. Vertrautheit mit C#: Grundlegendes Verständnis der Programmiersprache C#.
4. Dokument zum Kommentieren: Bereiten Sie ein Dokument (z. B. PDF) vor, das Sie kommentieren möchten.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihren C#-Code, um die Funktionen von GroupDocs.Annotation für .NET zu nutzen:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Lassen Sie uns nun den Prozess des Hinzufügens von Texthervorhebungsanmerkungen in mehrere Schritte unterteilen:
## Schritt 1: Ausgabepfad definieren
Geben Sie den Ausgabepfad an, in dem das mit Anmerkungen versehene Dokument gespeichert werden soll:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Erstellen Sie eine Instanz von`Annotator` Klasse, wobei der Dateiname des Dokuments als Parameter übergeben wird:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Schritt 3: Hervorhebungsanmerkung erstellen
 Instanziieren Sie a`HighlightAnnotation` Objekt und konfigurieren Sie seine Eigenschaften:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
Fügen Sie die erstellte Hervorhebungsanmerkung zum Dokument hinzu:
```csharp
annotator.Add(highlight);
```
## Schritt 5: Kommentiertes Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad:
```csharp
annotator.Save(outputPath);
```

## Abschluss
Zusammenfassend bietet GroupDocs.Annotation für .NET einen optimierten Ansatz zur Integration von Texthervorhebungsanmerkungen in Dokumente. Durch Befolgen der in diesem Tutorial beschriebenen Schritte können Entwickler die Zusammenarbeit und Produktivität von Dokumenten in ihren Anwendungen nahtlos verbessern.
## FAQs
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation für .NET unterstützt verschiedene Dokumentformate, darunter PDF, Word, Excel und mehr. Die vollständige Liste finden Sie in der Dokumentation.
### Können Anmerkungen entsprechend spezifischer Anforderungen angepasst werden?
Ja, Entwickler haben die volle Kontrolle über die Eigenschaften und das Erscheinungsbild von Anmerkungen und können diese so an unterschiedliche Anforderungen anpassen.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
 Ja, Sie können die Funktionen von GroupDocs.Annotation für .NET erkunden, indem Sie über die bereitgestellte Website auf die kostenlose Testversion zugreifen[Verknüpfung](https://releases.groupdocs.com/).
### Wie kann ich Unterstützung bei Problemen oder Fragen im Zusammenhang mit GroupDocs.Annotation für .NET erhalten?
 Für Unterstützung und Unterstützung können Sie das GroupDocs.Annotation-Forum besuchen[Hier](https://forum.groupdocs.com/c/annotation/10).
### Welche Lizenzoptionen stehen für GroupDocs.Annotation für .NET zur Verfügung?
 GroupDocs.Annotation für .NET bietet verschiedene Lizenzierungsoptionen, darunter temporäre Lizenzen für Testzwecke und kommerzielle Lizenzen für Produktionsumgebungen. Besuchen Sie die Kaufseite[Hier](https://purchase.groupdocs.com/buy) für mehr Details.