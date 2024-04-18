---
title: Fügen Sie dem Dokument eine Pfeilanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Pfeilanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Pfeilanmerkungen zu Ihren Dokumenten hinzufügen. Verbessern Sie mühelos die Klarheit und Interaktivität von Dokumenten.
type: docs
weight: 11
url: /de/net/unlocking-annotation-power/add-arrow-annotation/
---
## Einführung
In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens von Pfeilanmerkungen zu Ihren Dokumenten mithilfe von GroupDocs.Annotation für .NET. Pfeilanmerkungen sind nützlich, um die Richtung anzugeben oder auf bestimmte Elemente innerhalb eines Dokuments hinzuweisen.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1.  GroupDocs.Annotation für .NET: Installieren Sie die GroupDocs.Annotation-Bibliothek für .NET. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie über eine Entwicklungsumgebung für die .NET-Entwicklung verfügen, einschließlich Visual Studio oder einer anderen bevorzugten IDE.

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces importieren, um auf die erforderlichen Klassen und Methoden für die Annotation zuzugreifen.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Annotator initialisieren
Initialisieren Sie den Annotator, indem Sie den Dateipfad des Eingabedokuments angeben.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Schritt 2: Pfeilanmerkung erstellen
Erstellen Sie eine Instanz der ArrowAnnotation-Klasse und definieren Sie deren Eigenschaften wie Position, Nachricht, Deckkraft, Stiftfarbe, Stil, Breite usw.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
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
## Schritt 3: Anmerkung hinzufügen
 Fügen Sie die Pfeilanmerkung mit dem Dokument zum Dokument hinzu`Add` Methode des Annotators.
```csharp
	annotator.Add(arrow);
```
## Schritt 4: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
	annotator.Save(outputPath);
}
```
## Schritt 5: Bestätigung anzeigen
Zeigt eine Bestätigungsmeldung an, die das erfolgreiche Speichern des Dokuments anzeigt.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Jetzt haben Sie mit GroupDocs.Annotation für .NET erfolgreich eine Pfeilanmerkung zu Ihrem Dokument hinzugefügt.

## Abschluss
In diesem Tutorial haben wir den Prozess des Hinzufügens von Pfeilanmerkungen zu Dokumenten mithilfe von GroupDocs.Annotation für .NET behandelt. Wenn Sie diese Schritte befolgen, können Sie Ihre Dokumente mit klaren Richtungshinweisen aufwerten und sie so informativer und ansprechender machen.
## FAQs
### Kann ich das Erscheinungsbild der Pfeilanmerkung anpassen?
Ja, Sie können verschiedene Eigenschaften wie Farbe, Stil, Breite und Deckkraft an Ihre Vorlieben und Dokumentanforderungen anpassen.
### Ist GroupDocs.Annotation mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, DOCX, PPTX, XLSX und mehr.
### Kann ich Anmerkungen programmgesteuert mit GroupDocs.Annotation hinzufügen?
Ja, GroupDocs.Annotation bietet APIs, mit denen Sie Anmerkungen programmgesteuert zu Dokumenten hinzufügen, bearbeiten und entfernen können.
### Bietet GroupDocs.Annotation eine kostenlose Testversion an?
 Ja, Sie können GroupDocs.Annotation kostenlos testen, indem Sie es herunterladen von[Hier](https://releases.groupdocs.com/).
### Wo erhalte ich technischen Support für GroupDocs.Annotation?
Für technischen Support und Unterstützung können Sie das GroupDocs.Annotation-Forum besuchen[Hier](https://forum.groupdocs.com/c/annotation/10).