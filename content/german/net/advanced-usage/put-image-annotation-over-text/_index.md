---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation Bildanmerkungen über Text in .NET hinzufügen, um ein effizientes Dokumentenmanagement und eine effiziente Zusammenarbeit zu ermöglichen."
"linktitle": "Bildanmerkungen über Text legen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Bildanmerkungen über Text legen"
"url": "/de/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Bildanmerkungen über Text legen

## Einführung
In der .NET-Entwicklung bietet GroupDocs.Annotation eine leistungsstarke Lösung zum Hinzufügen von Anmerkungen zu Dokumenten und optimiert so die Zusammenarbeit und das Dokumentenmanagement. Häufig wird das Einfügen von Bildanmerkungen in Text gefordert, was mit GroupDocs.Annotation für .NET problemlos möglich ist.
## Voraussetzungen
Bevor Sie mit dem Einfügen von Bildanmerkungen über Text mithilfe von GroupDocs.Annotation für .NET beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von [Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung ein, beispielsweise Visual Studio oder eine andere .NET-IDE.
3. Dokument- und Bilddateien: Bereiten Sie die Dokumentdatei (PDF, DOCX usw.) und die Bilddatei vor, die Sie für Anmerkungen verwenden möchten.
4. Grundlegende Kenntnisse in C#: Um die in diesem Tutorial bereitgestellten Codeausschnitte zu implementieren, sind Kenntnisse der Programmiersprache C# erforderlich.

## Namespaces importieren
Bevor Sie mit dem Annotationsprozess fortfahren, stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Schritt 1: Ausgabepfad definieren
Definieren Sie zunächst den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den `Annotator` Objekt, indem Sie den Pfad des Eingabedokuments angeben:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier eingefügt
}
```
## Schritt 3: Bildanmerkung erstellen
Erstellen Sie ein `ImageAnnotation` Objekt mit den gewünschten Eigenschaften wie Kastenabmessungen, Deckkraft, Seitenzahl, Bildpfad und Z-Index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Schritt 4: Anmerkung hinzufügen
Fügen Sie die Bildanmerkung zum Dokument hinzu, indem Sie `Add` Methode der `Annotator` Objekt:
```csharp
annotator.Add(image);
```
## Schritt 5: Kommentiertes Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad:
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Zeigen Sie eine Erfolgsmeldung mit dem Pfad zum kommentierten Dokument an:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass das Hinzufügen von Bildanmerkungen über Text in .NET-Anwendungen mit GroupDocs.Annotation ein unkomplizierter Vorgang ist. Mit der Schritt-für-Schritt-Anleitung in diesem Tutorial können Sie Dokumente effizient kommentieren und die Zusammenarbeit sowie das Dokumentenmanagement in Ihren .NET-Projekten verbessern.
## Häufig gestellte Fragen
### Kann ich andere Dokumente als PDFs mit Anmerkungen versehen?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate wie DOCX, XLSX, PPTX und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
Ja, Sie können eine kostenlose Testversion herunterladen von [Hier](https://releases.groupdocs.com/).
### Wie erhalte ich Support für GroupDocs.Annotation?
Sie erhalten Unterstützung im GroupDocs.Annotation-Community-Forum [Hier](https://forum.groupdocs.com/c/annotation/10).
### Benötige ich zu Testzwecken eine temporäre Lizenz?
Ja, Sie können eine vorläufige Lizenz erhalten von [Hier](https://purchase.groupdocs.com/temporary-license/) zu Testzwecken.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, GroupDocs.Annotation bietet verschiedene Optionen zum Anpassen des Erscheinungsbilds von Anmerkungen wie Farbe, Deckkraft, Schriftgröße usw.