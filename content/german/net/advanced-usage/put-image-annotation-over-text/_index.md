---
title: Platzieren Sie Bildanmerkungen über Text
linktitle: Platzieren Sie Bildanmerkungen über Text
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation Bildanmerkungen über Text in .NET hinzufügen, um eine effiziente Dokumentenverwaltung und Zusammenarbeit zu ermöglichen.
weight: 21
url: /de/net/advanced-usage/put-image-annotation-over-text/
---
## Einführung
In der Welt der .NET-Entwicklung bietet GroupDocs.Annotation eine leistungsstarke Lösung zum Hinzufügen von Anmerkungen zu Dokumenten und macht die Zusammenarbeit und Dokumentenverwaltung effizienter. Eine häufige Anforderung besteht darin, Bildanmerkungen über Text zu platzieren, was mit GroupDocs.Annotation für .NET nahtlos bewerkstelligt werden kann.
## Voraussetzungen
Bevor Sie mit GroupDocs.Annotation für .NET beginnen, Bildanmerkungen über Text zu platzieren, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung ein, z. B. Visual Studio oder eine andere .NET-IDE.
3. Dokument- und Bilddateien: Bereiten Sie die Dokumentdatei (PDF, DOCX usw.) und die Bilddatei vor, die Sie für Anmerkungen verwenden möchten.
4. Grundlegendes Verständnis von C#: Um die in diesem Tutorial bereitgestellten Codefragmente zu implementieren, sind Kenntnisse der Programmiersprache C# erforderlich.

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
Definieren Sie zunächst den Ausgabepfad, in dem das mit Anmerkungen versehene Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Schritt 2: Annotator initialisieren
 Initialisieren Sie die`Annotator` Objekt durch Angabe des Eingabedokumentpfads:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```
## Schritt 3: Bildanmerkung erstellen
 Erstelle ein`ImageAnnotation` Objekt mit den gewünschten Eigenschaften wie Boxabmessungen, Deckkraft, Seitenzahl, Bildpfad und Z-Index:
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
 Fügen Sie die Bildanmerkung mithilfe von zum Dokument hinzu`Add` Methode der`Annotator` Objekt:
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
Zusammenfassend lässt sich sagen, dass das Hinzufügen von Bildanmerkungen zu Text in .NET-Anwendungen mithilfe von GroupDocs.Annotation ein unkomplizierter Vorgang ist. Wenn Sie der Schritt-für-Schritt-Anleitung in diesem Tutorial folgen, können Sie Dokumente effizient mit Anmerkungen versehen und die Funktionen für die Zusammenarbeit und Dokumentenverwaltung in Ihren .NET-Projekten verbessern.
## FAQs
### Kann ich andere Dokumente als PDFs mit Anmerkungen versehen?
Ja, GroupDocs.Annotation unterstützt verschiedene Dokumentformate wie DOCX, XLSX, PPTX und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Wie erhalte ich Unterstützung für GroupDocs.Annotation?
 Unterstützung erhalten Sie im GroupDocs.Annotation-Community-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).
### Benötige ich zu Testzwecken eine temporäre Lizenz?
 Ja, Sie können eine temporäre Lizenz erhalten von[Hier](https://purchase.groupdocs.com/temporary-license/) zu Testzwecken.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, GroupDocs.Annotation bietet verschiedene Optionen zum Anpassen des Erscheinungsbilds von Anmerkungen wie Farbe, Deckkraft, Schriftgröße usw.