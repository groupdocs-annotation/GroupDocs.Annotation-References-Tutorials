---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Textredaktionen in PDF-Dokumente einfügen. Schützen Sie vertrauliche Informationen mühelos."
"linktitle": "Textredaktionsanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Textredaktionsanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# Textredaktionsanmerkung zum Dokument hinzufügen

## Einführung
Das Hinzufügen einer Textredaktion zu einem Dokument kann ein entscheidender Schritt für die sichere Verwaltung vertraulicher Informationen sein. GroupDocs.Annotation für .NET bietet eine robuste Lösung für die nahtlose Umsetzung. In diesem Tutorial führen wir Sie Schritt für Schritt durch das Hinzufügen einer Textredaktion zu Ihrem Dokument.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1. GroupDocs.Annotation für .NET: Stellen Sie sicher, dass Sie die Bibliothek GroupDocs.Annotation für .NET installiert haben. Sie können sie von der [Webseite](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit einer .NET-kompatiblen IDE wie Visual Studio ein.

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
## Schritt 1: Ausgabepfad definieren
Definieren Sie den Ausgabepfad, in dem Sie das kommentierte Dokument speichern möchten. Stellen Sie sicher, dass der Pfad zugänglich und beschreibbar ist.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den Annotator mit dem Eingabedokumentpfad. Ersetzen Sie `"input.pdf"` mit dem Pfad zu Ihrem Dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier eingefügt
}
```
## Schritt 3: Textredaktionsanmerkung erstellen
Erstellen Sie ein `TextRedactionAnnotation` Objekt mit den erforderlichen Eigenschaften wie `PageNumber`, `FontColor`, Und `Points`. Passen Sie die Anmerkung Ihren Anforderungen entsprechend an.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Schritt 4: Anmerkung hinzufügen und speichern
Fügen Sie die erstellte Anmerkung mithilfe des Annotators zum Dokument hinzu und speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Schritt 5: Ausgabe prüfen
Bestätigen Sie abschließend, dass das Dokument erfolgreich im angegebenen Ausgabepfad gespeichert wurde.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir den Prozess des Hinzufügens einer Textredaktionsanmerkung zu einem Dokument mithilfe von GroupDocs.Annotation für .NET erläutert. Mit diesen Schritten können Sie vertrauliche Informationen in Ihren Dokumenten sicher verwalten.
## Häufig gestellte Fragen
### Kann ich das Erscheinungsbild der Textredaktionsanmerkung anpassen?
Ja, Sie können verschiedene Eigenschaften wie Schriftfarbe, Füllfarbe und Deckkraft an Ihre Anforderungen anpassen.
### Gibt es vor dem Kauf eine Testversion?
Ja, Sie können auf eine kostenlose Testversion zugreifen von der [Webseite](https://releases.groupdocs.com/).
### Wie erhalte ich Unterstützung, wenn Probleme auftreten?
Sie erhalten Unterstützung im GroupDocs.Annotation-Community-Forum [Hier](https://forum.groupdocs.com/c/annotation/10).
### Benötige ich zu Testzwecken eine temporäre Lizenz?
Ja, Sie können eine vorläufige Lizenz erhalten von der [Kaufseite](https://purchase.groupdocs.com/temporary-license/) zum Testen.
### Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?
Auf jeden Fall. Mit GroupDocs.Annotation können Sie einem einzelnen Dokument verschiedene Arten von Anmerkungen und mehrere Instanzen hinzufügen.