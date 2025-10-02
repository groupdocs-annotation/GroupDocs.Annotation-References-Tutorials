---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Dokumentverarbeitung."
"linktitle": "Bildanmerkung zum Dokument hinzufügen (lokaler Pfad)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Bildanmerkung zum Dokument hinzufügen (lokaler Pfad)"
"url": "/de/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Bildanmerkung zum Dokument hinzufügen (lokaler Pfad)

## Einführung
GroupDocs.Annotation für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler verschiedene Arten von Anmerkungen programmgesteuert zu Dokumenten hinzufügen können. In diesem Tutorial erfahren Sie, wie Sie Bildanmerkungen über einen lokalen Pfad zu einem Dokument hinzufügen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Grundkenntnisse der Programmiersprache C#.
2. Visual Studio ist auf Ihrem System installiert.
3. GroupDocs.Annotation für die in Ihrem Projekt installierte .NET-Bibliothek oder Tutorialsd.
4. Ein Eingabedokument (z. B. PDF) und eine Bilddatei zur Kommentierung.
## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihre C#-Datei importieren. Diese Namespaces ermöglichen den Zugriff auf die Klassen und Methoden, die für die Arbeit mit GroupDocs.Annotation erforderlich sind.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Schritt 1: Ausgabepfad definieren
Definieren Sie den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den Annotator, indem Sie den Pfad zum Eingabedokument angeben.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Hier kommt der Anmerkungscode hin
}
```
## Schritt 3: Bildanmerkung erstellen
Erstellen Sie eine Instanz des `ImageAnnotation` Klasse und geben Sie ihre Eigenschaften wie Position, Deckkraft, Seitenzahl und Bildpfad an.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Schritt 4: Anmerkung hinzufügen
Fügen Sie die erstellte Bildanmerkung dem Dokument hinzu, indem Sie `Add` Methode des Annotators.
```csharp
annotator.Add(image);
```
## Schritt 5: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Ausgabepfad anzeigen
Zeigen Sie eine Meldung an, die das erfolgreiche Speichern des Dokuments und den Speicherort der Ausgabedatei angibt.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu einem Dokument hinzufügen. Mit diesen einfachen Schritten können Sie Ihre Dokumentverarbeitung mit leistungsstarken Anmerkungsfunktionen verbessern.
## Häufig gestellte Fragen
### Kann ich andere Dokumente als PDF mit Anmerkungen versehen?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Ist GroupDocs.Annotation mit .NET Core kompatibel?
Ja, GroupDocs.Annotation ist sowohl mit .NET Framework als auch mit .NET Core kompatibel.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Natürlich können Sie das Aussehen, die Größe, die Farbe und andere Eigenschaften von Anmerkungen Ihren Anforderungen entsprechend anpassen.
### Bietet GroupDocs.Annotation Unterstützung für die gemeinsame Kommentierung?
Ja, GroupDocs.Annotation bietet kollaborative Anmerkungsfunktionen, die es mehreren Benutzern ermöglichen, Dokumente gleichzeitig mit Anmerkungen zu versehen.
### Wo finde ich zusätzliche Hilfe oder Unterstützung?
Sie können das GroupDocs.Annotation-Forum besuchen, um Hilfe und Unterstützung von der Community zu erhalten.