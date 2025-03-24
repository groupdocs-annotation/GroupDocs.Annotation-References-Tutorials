---
title: Laden benutzerdefinierter Schriftarten
linktitle: Laden benutzerdefinierter Schriftarten
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie benutzerdefinierte Schriftarten nahtlos in GroupDocs.Annotation für .NET laden, um Dokumentanmerkungen zu verbessern. Befolgen Sie unsere Schritt-für-Schritt-Anleitung für eine einfache Integration.
weight: 20
url: /de/net/advanced-usage/loading-custom-fonts/
---

# Laden benutzerdefinierter Schriftarten

## Einführung
GroupDocs.Annotation für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, mühelos Anmerkungsfunktionen zu ihren .NET-Anwendungen hinzuzufügen. Eine der wichtigsten Funktionen ist die Möglichkeit, benutzerdefinierte Schriftarten zu laden, was eine verbesserte Anpassung und Flexibilität bei der Dokumentanmerkung ermöglicht.
## Voraussetzungen
Bevor Sie mit dem Tutorial fortfahren, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/annotation/net/).
2. .NET-Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine Arbeitsumgebung für die .NET-Entwicklung eingerichtet haben.
3. Zugriff auf benutzerdefinierte Schriftarten: Bereiten Sie die benutzerdefinierten Schriftarten vor, die Sie in Ihre Anwendung laden möchten.

## Namespaces importieren
Importieren Sie in Ihrem .NET-Projekt die erforderlichen Namespaces für die Verwendung von GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Annotator-Objekt instanziieren
 Erstellen Sie eine Instanz von`Annotator` Klasse, indem Sie den Pfad zum Eingabe-PDF-Dokument zusammen mit den benutzerdefinierten Schriftartenverzeichnissen angeben:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Hier finden Sie Ihren Code für weitere Vorgänge
}
```
## Schritt 2: Vorschauoptionen konfigurieren
Definieren Sie die Vorschauoptionen, um festzulegen, wie die Dokumentvorschauen generiert werden. Sie können Optionen wie Vorschauformat, Seitenzahlen usw. festlegen:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Schritt 3: Dokumentvorschauen erstellen
 Nutzen Sie die`GeneratePreview` Methode der`Document` Eigenschaft zum Generieren von Vorschauen mit benutzerdefinierten Schriftarten:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Schritt 4: Ausgabepfad anzeigen
Zeigen Sie abschließend eine Meldung an, die die erfolgreiche Generierung der Dokumentvorschau zusammen mit dem Ausgabeverzeichnispfad angibt:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass das Laden benutzerdefinierter Schriftarten in GroupDocs.Annotation für .NET Entwicklern die Flexibilität bietet, Dokumentanmerkungen entsprechend ihren Anforderungen anzupassen. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie benutzerdefinierte Schriftarten nahtlos in Ihre .NET-Anwendungen integrieren und das Anmerkungserlebnis für Benutzer verbessern.
## FAQs
### Kann ich mehrere benutzerdefinierte Schriftarten gleichzeitig laden?
 Ja, Sie können beim Instanziieren mehrere Schriftartenverzeichnisse angeben`Annotator` Objekt.
### Gibt es Einschränkungen hinsichtlich der unterstützten Schriftarten?
GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Schriftarten, einschließlich TrueType-Schriftarten (.ttf) und OpenType-Schriftarten (.otf).
### Kann ich die geladenen Schriftarten zur Laufzeit dynamisch ändern?
Ja, Sie können die Schriftartenverzeichnisse dynamisch ändern und die Dokumentanmerkungen nach Bedarf neu laden.
### Unterstützt GroupDocs.Annotation die Einbettung von Schriftarten in Ausgabedokumenten?
Ja, Sie können benutzerdefinierte Schriftarten in die Ausgabedokumente einbetten, um eine konsistente Darstellung auf verschiedenen Plattformen sicherzustellen.
### Gibt es eine Möglichkeit, die Schriftartenlizenzierung innerhalb der Anwendung zu verwalten?
GroupDocs.Annotation bietet Optionen zum Verwalten der Schriftartenlizenzierung, einschließlich temporärer Lizenzen für Evaluierungszwecke.