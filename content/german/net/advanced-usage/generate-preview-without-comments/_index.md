---
title: Vorschau ohne Kommentare generieren
linktitle: Vorschau ohne Kommentare generieren
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET Dokumentanmerkungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren.
type: docs
weight: 14
url: /de/net/advanced-usage/generate-preview-without-comments/
---
## Einführung
GroupDocs.Annotation für .NET ist ein leistungsstarkes Tool, mit dem Entwickler Annotationsfunktionen nahtlos in ihre .NET-Anwendungen integrieren können. Unabhängig davon, ob Sie an einem Dokumentenmanagementsystem, einer Kollaborationsplattform oder einer anderen Anwendung arbeiten, die Funktionen zur Dokumentanmerkung erfordert, bietet GroupDocs.Annotation einen umfassenden Satz an Tools zur Verbesserung der Funktionalität Ihrer Anwendung.
## Voraussetzungen
Bevor Sie GroupDocs.Annotation für .NET verwenden, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
### 1. Installieren Sie GroupDocs.Annotation für .NET
 Zunächst müssen Sie GroupDocs.Annotation für .NET herunterladen und installieren. Den Download-Link finden Sie hier[Hier](https://releases.groupdocs.com/annotation/net/). Befolgen Sie die Installationsanweisungen in der Dokumentation, um einen reibungslosen Einrichtungsprozess zu gewährleisten.
### 2. Erwerben Sie eine Lizenz
 GroupDocs.Annotation für .NET erfordert für die kommerzielle Nutzung eine Lizenz. Sie können eine Lizenz erwerben bei[Hier](https://purchase.groupdocs.com/buy) oder entscheiden Sie sich für eine temporäre Lizenz[Hier](https://purchase.groupdocs.com/temporary-license/) zu Testzwecken.
### 3. Vertrautheit mit .NET Framework
Grundkenntnisse des .NET Framework und der Programmiersprache C# sind für die effektive Nutzung von GroupDocs.Annotation für .NET unerlässlich.

## Namespaces importieren
Nachdem Sie nun die Voraussetzungen eingerichtet haben, importieren wir die erforderlichen Namespaces in Ihre .NET-Anwendung.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Befolgen Sie diese Schritt-für-Schritt-Anleitung, um mit GroupDocs.Annotation für .NET eine Vorschau ohne Kommentare zu erstellen:
## Schritt 1: Annotator initialisieren
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Schritt 2: Vorschauoptionen konfigurieren
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Schritt 3: Geben Sie das Vorschauformat und die Seitenzahlen an
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Schritt 4: Deaktivieren Sie die Darstellung von Kommentaren
```csharp
    previewOptions.RenderComments = false;
```
## Schritt 5: Vorschau erstellen
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Sobald Sie diese Schritte ausgeführt haben, kann Ihre .NET-Anwendung eine Vorschau der angegebenen Seiten aus dem Dokument generieren, ohne Kommentare darzustellen.

## Abschluss
Dank GroupDocs.Annotation für .NET war die Integration von Anmerkungsfunktionen in Ihre .NET-Anwendungen noch nie so einfach. Wenn Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Dokumentanmerkungsfunktionen nahtlos in Ihre Anwendungen integrieren und so die Zusammenarbeit und Dokumentenverwaltung verbessern.
## FAQs
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, DOCX, PPTX, XLSX und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen, die mit GroupDocs.Annotation für .NET generiert wurden?
Ja, GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen, mit denen Sie das Erscheinungsbild von Anmerkungen an die Anforderungen Ihrer Anwendung anpassen können.
### Unterstützt GroupDocs.Annotation für .NET die Zusammenarbeit mehrerer Benutzer?
Ja, GroupDocs.Annotation für .NET bietet kollaborative Anmerkungsfunktionen, die es mehreren Benutzern ermöglichen, Dokumente gleichzeitig zu kommentieren.
### Ist technischer Support für GroupDocs.Annotation für .NET verfügbar?
 Ja, technischer Support für GroupDocs.Annotation für .NET ist über verfügbar[Hilfeforum](https://forum.groupdocs.com/c/annotation/10).
### Kann ich GroupDocs.Annotation für .NET vor dem Kauf kostenlos testen?
 Ja, Sie können die Funktionen von GroupDocs.Annotation für .NET erkunden, indem Sie die kostenlose Testversion herunterladen[Hier](https://releases.groupdocs.com/).