---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu Dokumenten hinzufügen. Verbessern Sie Ihr Dokumentenmanagement mit leistungsstarken Anmerkungsfunktionen."
"linktitle": "Bildanmerkung zum Dokument hinzufügen (Remote-Pfad)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Bildanmerkung zum Dokument hinzufügen (Remote-Pfad)"
"url": "/de/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Bildanmerkung zum Dokument hinzufügen (Remote-Pfad)

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET Bildanmerkungen zu einem Dokument hinzufügen. Diese Bibliothek bietet leistungsstarke Tools zum programmgesteuerten Kommentieren verschiedener Dokumenttypen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:
1. GroupDocs.Annotation für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von [Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine funktionierende Entwicklungsumgebung für die .NET-Entwicklung eingerichtet haben.
3. Dokument: Bereiten Sie das Dokument vor, das Sie kommentieren möchten. Für dieses Tutorial gehen wir davon aus, dass Sie ein PDF-Dokument mit dem Namen `input.pdf`.
4. Bild für Anmerkung: Wählen Sie das Bild aus, das Sie für Anmerkungen verwenden möchten. Halten Sie die Bild-URL oder den lokalen Pfad bereit.

## Namespaces importieren
Bevor wir mit dem Codieren beginnen, importieren wir die erforderlichen Namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Schritt 1: Ausgabepfad festlegen
Definieren Sie zunächst den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Erstellen Sie eine Instanz des `Annotator` Klasse und geben Sie das Eingabedokument an.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier eingefügt
}
```
## Schritt 3: Bildanmerkungen hinzufügen
Fügen wir nun die Bildanmerkung zum Dokument hinzu. Wir legen die Eigenschaften der Bildanmerkung fest, z. B. Position, Deckkraft, Seitenzahl und Bildpfad.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Geben Sie die Position der Anmerkung an
    CreatedOn = DateTime.Now, // Legen Sie das Erstellungsdatum fest
    Opacity = 0.7, // Deckkraft einstellen (0 bis 1)
    PageNumber = 0, // Geben Sie die Seitenzahl an
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Geben Sie die URL des Bildes an
};
annotator.Add(image); // Bildanmerkung hinzufügen
```
## Schritt 4: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 5: Ausgabepfad anzeigen
Informieren Sie den Benutzer über den erfolgreichen Dokumentspeichervorgang und zeigen Sie den Ausgabepfad an.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu einem Dokument hinzufügen. Mit diesen Schritten können Sie Ihre Dokumentenverwaltungsanwendungen um leistungsstarke Anmerkungsfunktionen erweitern.
## Häufig gestellte Fragen
### Kann GroupDocs.Annotation mit anderen Dokumentformaten außer PDF verwendet werden?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Ist GroupDocs.Annotation mit .NET Core kompatibel?
Ja, GroupDocs.Annotation ist sowohl mit .NET Framework als auch mit .NET Core kompatibel.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, Sie können das Erscheinungsbild von Anmerkungen, beispielsweise Farbe, Deckkraft und Größe, anpassen.
### Unterstützt GroupDocs.Annotation kollaborative Anmerkungsfunktionen?
Ja, GroupDocs.Annotation bietet kollaborative Anmerkungsfunktionen für die Echtzeit-Zusammenarbeit an Dokumenten.
### Gibt es eine Testversion zum Testen?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation erhalten von [Hier](https://releases.groupdocs.com/).