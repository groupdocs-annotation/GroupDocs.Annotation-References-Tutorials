---
title: Bildanmerkung zum Dokument hinzufügen (lokaler Pfad)
linktitle: Bildanmerkung zum Dokument hinzufügen (lokaler Pfad)
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu Dokumenten hinzufügen. Erweitern Sie die Möglichkeiten der Dokumentenverarbeitung ganz einfach.
type: docs
weight: 14
url: /de/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Einführung
GroupDocs.Annotation für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler programmgesteuert verschiedene Arten von Anmerkungen zu Dokumenten hinzufügen können. In diesem Tutorial erfahren Sie, wie Sie mithilfe eines lokalen Pfads Bildanmerkungen zu einem Dokument hinzufügen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Grundkenntnisse der Programmiersprache C#.
2. Visual Studio ist auf Ihrem System installiert.
3. GroupDocs.Annotation für die .NET-Bibliothek, die in Ihrem Projekt installiert ist oder auf die verwiesen wird.
4. Ein Eingabedokument (z. B. PDF) und eine Bilddatei zur Kommentierung.
## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihre C#-Datei importieren. Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die für die Arbeit mit GroupDocs.Annotation erforderlich sind.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Schritt 1: Ausgabepfad definieren
Definieren Sie den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den Annotator, indem Sie den Pfad zum Eingabedokument angeben.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode kommt hierher
}
```
## Schritt 3: Bildanmerkung erstellen
 Erstellen Sie eine Instanz von`ImageAnnotation`Klasse und geben Sie ihre Eigenschaften wie Position, Deckkraft, Seitenzahl und Bildpfad an.
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
 Fügen Sie die erstellte Bildanmerkung mithilfe von zum Dokument hinzu`Add` Methode des Annotators.
```csharp
annotator.Add(image);
```
## Schritt 5: Dokument speichern
Speichern Sie das kommentierte Dokument im Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Ausgabepfad anzeigen
Zeigt eine Meldung an, die über das erfolgreiche Speichern des Dokuments und den Speicherort der Ausgabedatei informiert.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET Bildanmerkungen zu einem Dokument hinzufügt. Wenn Sie diese einfachen Schritte befolgen, können Sie Ihre Dokumentverarbeitungsfunktionen mit leistungsstarken Anmerkungsfunktionen erweitern.
## FAQs
### Kann ich andere Dokumente als PDF mit Anmerkungen versehen?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Ist GroupDocs.Annotation mit .NET Core kompatibel?
Ja, GroupDocs.Annotation ist sowohl mit .NET Framework als auch .NET Core kompatibel.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Selbstverständlich können Sie das Erscheinungsbild, die Größe, die Farbe und andere Eigenschaften von Anmerkungen Ihren Anforderungen entsprechend anpassen.
### Bietet GroupDocs.Annotation Unterstützung für kollaborative Anmerkungen?
Ja, GroupDocs.Annotation bietet kollaborative Anmerkungsfunktionen, die es mehreren Benutzern ermöglichen, Dokumente gleichzeitig zu kommentieren.
### Wo finde ich zusätzliche Hilfe oder Unterstützung?
Sie können das GroupDocs.Annotation-Forum besuchen, um Hilfe und Unterstützung von der Community zu erhalten.