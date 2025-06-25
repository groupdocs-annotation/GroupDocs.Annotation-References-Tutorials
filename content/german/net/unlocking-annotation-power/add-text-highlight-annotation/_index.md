---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Texthervorhebungen zu Dokumenten hinzufügen. Verbessern Sie die Zusammenarbeit und Produktivität mit dieser umfassenden Lösung."
"linktitle": "Texthervorhebungsanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Texthervorhebungsanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Texthervorhebungsanmerkung zum Dokument hinzufügen

## Einführung
Im Bereich Dokumentenmanagement und Zusammenarbeit erweist sich GroupDocs.Annotation für .NET als robuste Lösung, die Entwicklern die nahtlose Integration von Texthervorhebungen in ihre Anwendungen ermöglicht. Dieses Tutorial bietet eine umfassende Anleitung zum Hinzufügen von Texthervorhebungen zu Dokumenten mit GroupDocs.Annotation für .NET. Durch Schritt-für-Schritt-Anleitungen und detaillierte Erklärungen lernen Sie, die Möglichkeiten dieser leistungsstarken Bibliothek optimal zu nutzen.
## Voraussetzungen
Bevor Sie sich mit der Implementierung von Texthervorhebungsanmerkungen befassen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. Umgebungseinrichtung: Lassen Sie eine geeignete Entwicklungsumgebung für die .NET-Entwicklung konfigurieren.
2. Installation von GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET von der bereitgestellten [Download-Link](https://releases.groupdocs.com/annotation/net/).
3. Vertrautheit mit C#: Grundlegende Kenntnisse der Programmiersprache C#.
4. Zu kommentierendes Dokument: Bereiten Sie ein Dokument (z. B. PDF) vor, das Sie kommentieren möchten.

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
#Lassen Sie uns nun den Vorgang des Hinzufügens von Texthervorhebungsanmerkungen in mehrere Schritte unterteilen:
## Schritt 1: Ausgabepfad definieren
Geben Sie den Ausgabepfad an, in dem das kommentierte Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Erstellen Sie eine Instanz des `Annotator` Klasse, wobei der Dateiname des Dokuments als Parameter übergeben wird:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Schritt 3: Hervorhebungsanmerkung erstellen
Instanziieren Sie ein `HighlightAnnotation` Objekt und konfigurieren Sie seine Eigenschaften:
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
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET einen optimierten Ansatz zum Einfügen von Texthervorhebungen in Dokumente bietet. Mit den in diesem Tutorial beschriebenen Schritten können Entwickler die Zusammenarbeit an Dokumenten und die Produktivität in ihren Anwendungen nahtlos verbessern.
## Häufig gestellte Fragen
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation für .NET unterstützt verschiedene Dokumentformate, darunter PDF, Word, Excel und mehr. Die vollständige Liste finden Sie in der Dokumentation.
### Können Anmerkungen an spezifische Anforderungen angepasst werden?
Ja, Entwickler haben die volle Kontrolle über die Eigenschaften und das Erscheinungsbild von Anmerkungen und können diese an unterschiedliche Anforderungen anpassen.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können die Funktionen von GroupDocs.Annotation für .NET erkunden, indem Sie auf die kostenlose Testversion über die bereitgestellte [Link](https://releases.groupdocs.com/).
### Wie erhalte ich Support bei Problemen oder Fragen zu GroupDocs.Annotation für .NET?
Für Support und Hilfe können Sie das GroupDocs.Annotation-Forum besuchen. [Hier](https://forum.groupdocs.com/c/annotation/10).
### Welche Lizenzierungsoptionen sind für GroupDocs.Annotation für .NET verfügbar?
GroupDocs.Annotation für .NET bietet verschiedene Lizenzoptionen, darunter temporäre Lizenzen für Testzwecke und kommerzielle Lizenzen für Produktionsumgebungen. Besuchen Sie die Kaufseite. [Hier](https://purchase.groupdocs.com/buy) für weitere Details.