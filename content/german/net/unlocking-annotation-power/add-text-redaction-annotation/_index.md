---
title: Fügen Sie dem Dokument eine Textredaktionsanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Textredaktionsanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Textredaktionsanmerkungen zu PDF-Dokumenten hinzufügen. Schützen Sie vertrauliche Informationen mühelos.
weight: 23
url: /de/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# Fügen Sie dem Dokument eine Textredaktionsanmerkung hinzu

## Einführung
Das Hinzufügen einer Textredaktionsanmerkung zu einem Dokument kann ein entscheidender Schritt bei der sicheren Verwaltung sensibler Informationen sein. GroupDocs.Annotation für .NET bietet eine robuste Lösung, um dies nahtlos zu erreichen. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess des Hinzufügens einer Textredaktionsanmerkung zu Ihrem Dokument.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1.  GroupDocs.Annotation für .NET: Stellen Sie sicher, dass Sie die GroupDocs.Annotation für .NET-Bibliothek installiert haben. Sie können es hier herunterladen[Webseite](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit einer .NET-kompatiblen IDE wie Visual Studio ein.

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
## Schritt 1: Ausgabepfad definieren
Definieren Sie den Ausgabepfad, in dem Sie das mit Anmerkungen versehene Dokument speichern möchten. Stellen Sie sicher, dass es zugänglich und beschreibbar ist.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Initialisieren Sie den Annotator mit dem Eingabedokumentpfad. Ersetzen`"input.pdf"` mit dem Pfad zu Ihrem Dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```
## Schritt 3: Erstellen Sie eine Textredaktionsanmerkung
 Ein ... kreieren`TextRedactionAnnotation`Objekt mit den erforderlichen Eigenschaften wie z`PageNumber`, `FontColor` , Und`Points`. Passen Sie die Anmerkung entsprechend Ihren Anforderungen an.
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
Fügen Sie die erstellte Anmerkung mit dem Annotator zum Dokument hinzu und speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Schritt 5: Überprüfen Sie die Ausgabe
Bestätigen Sie abschließend, dass das Dokument erfolgreich im angegebenen Ausgabepfad gespeichert wurde.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir den Prozess des Hinzufügens einer Textredaktionsanmerkung zu einem Dokument mithilfe von GroupDocs.Annotation für .NET durchlaufen. Mit diesen Schritten können Sie vertrauliche Informationen in Ihren Dokumenten jetzt sicher verwalten.
## FAQs
### Kann ich das Erscheinungsbild der Textredaktionsanmerkung anpassen?
Ja, Sie können verschiedene Eigenschaften wie Schriftfarbe, Füllfarbe und Deckkraft an Ihre Anforderungen anpassen.
### Gibt es vor dem Kauf eine Testversion?
 Ja, Sie können über die auf eine kostenlose Testversion zugreifen[Webseite](https://releases.groupdocs.com/).
### Wie kann ich Unterstützung erhalten, wenn ich auf Probleme stoße?
 Unterstützung erhalten Sie im GroupDocs.Annotation-Community-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).
### Benötige ich zu Testzwecken eine temporäre Lizenz?
 Ja, Sie können eine temporäre Lizenz bei der erhalten[Kaufseite](https://purchase.groupdocs.com/temporary-license/)zum Prüfen.
### Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?
Absolut, mit GroupDocs.Annotation können Sie einem einzelnen Dokument verschiedene Arten von Anmerkungen und mehrere Instanzen hinzufügen.