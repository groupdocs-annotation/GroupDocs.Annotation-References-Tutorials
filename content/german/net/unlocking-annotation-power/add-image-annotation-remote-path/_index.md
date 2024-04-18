---
title: Bildanmerkung zum Dokument hinzufügen (Remote-Pfad)
linktitle: Bildanmerkung zum Dokument hinzufügen (Remote-Pfad)
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Bildanmerkungen zu Dokumenten hinzufügen. Verbessern Sie die Dokumentenverwaltung mit leistungsstarken Anmerkungsfunktionen.
type: docs
weight: 15
url: /de/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Einführung
In diesem Tutorial führen wir den Prozess des Hinzufügens von Bildanmerkungen zu einem Dokument mithilfe von GroupDocs.Annotation für .NET durch. Diese Bibliothek bietet leistungsstarke Tools zum programmgesteuerten Kommentieren verschiedener Dokumenttypen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Annotation für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie über eine funktionierende Entwicklungsumgebung für die .NET-Entwicklung verfügen.
3.  Dokument: Bereiten Sie das Dokument vor, das Sie mit Anmerkungen versehen möchten. Für dieses Tutorial gehen wir davon aus, dass Sie ein PDF-Dokument mit dem Namen haben`input.pdf`.
4. Bild für Anmerkung: Wählen Sie das Bild aus, das Sie für die Anmerkung verwenden möchten. Stellen Sie sicher, dass Sie die Bild-URL oder den lokalen Pfad bereit haben.

## Namespaces importieren
Bevor wir mit dem Codieren beginnen, importieren wir die erforderlichen Namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Schritt 1: Ausgabepfad festlegen
Definieren Sie zunächst den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Erstellen Sie eine Instanz von`Annotator` Klasse und geben Sie das Eingabedokument an.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```
## Schritt 3: Bildanmerkung hinzufügen
Fügen wir nun die Bildanmerkung zum Dokument hinzu. Wir legen die Eigenschaften der Bildanmerkung wie Position, Deckkraft, Seitenzahl und Bildpfad fest.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Geben Sie die Position der Anmerkung an
    CreatedOn = DateTime.Now, // Legen Sie das Erstellungsdatum fest
    Opacity = 0.7, // Deckkraft einstellen (0 bis 1)
    PageNumber = 0, // Geben Sie die Seitenzahl an
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Geben Sie die URL des Bildes an
};
annotator.Add(image); // Fügen Sie die Bildanmerkung hinzu
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
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET Bildanmerkungen zu einem Dokument hinzufügt. Wenn Sie diese Schritte befolgen, können Sie Ihre Dokumentenverwaltungsanwendungen mit leistungsstarken Anmerkungsfunktionen erweitern.
## FAQs
### Kann GroupDocs.Annotation neben PDF auch mit anderen Dokumentformaten verwendet werden?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate, darunter Word, Excel, PowerPoint und mehr.
### Ist GroupDocs.Annotation mit .NET Core kompatibel?
Ja, GroupDocs.Annotation ist sowohl mit .NET Framework als auch .NET Core kompatibel.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, Sie können das Erscheinungsbild von Anmerkungen wie Farbe, Deckkraft und Größe anpassen.
### Unterstützt GroupDocs.Annotation Funktionen für kollaborative Anmerkungen?
Ja, GroupDocs.Annotation bietet kollaborative Anmerkungsfunktionen für die Zusammenarbeit an Dokumenten in Echtzeit.
### Gibt es eine Testversion zum Testen?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation unter erhalten[Hier](https://releases.groupdocs.com/).