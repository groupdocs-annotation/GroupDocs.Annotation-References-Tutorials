---
"description": "Erfahren Sie, wie Sie PDF-Dokumente mit Groupdocs.Annotation für .NET mühelos drehen. Verbessern Sie die Effizienz Ihres Dokumentenmanagements."
"linktitle": "Drehen von PDF-Dokumenten"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Drehen von PDF-Dokumenten"
"url": "/de/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Drehen von PDF-Dokumenten

## Einführung
Das Drehen von PDF-Dokumenten kann eine wichtige Aufgabe sein, wenn Dateien unterschiedlich angezeigt oder verarbeitet werden müssen. In diesem Tutorial erfahren Sie Schritt für Schritt, wie Sie PDF-Dokumente mit Groupdocs.Annotation für .NET drehen.
## Voraussetzungen
Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Groupdocs.Annotation für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Bibliothek Groupdocs.Annotation für .NET heruntergeladen und installiert haben. Sie können sie hier herunterladen: [Hier](https://releases.groupdocs.com/annotation/net/).
2. Grundkenntnisse der C#-Programmierung: Dieses Lernprogramm setzt voraus, dass Sie über grundlegende Kenntnisse der Programmiersprache C# und der Arbeit mit .NET-Bibliotheken verfügen.

## Namespaces importieren
Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren, um auf die von der Bibliothek Groupdocs.Annotation bereitgestellte Funktionalität zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Laden Sie das PDF-Dokument
Laden Sie zunächst das PDF-Dokument, das Sie drehen möchten, mit dem `Annotator` Klasse.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Schritt 2: Rotation festlegen und Seiten verarbeiten
Geben Sie den Drehwinkel und die zu drehenden Seiten an. In diesem Beispiel drehen wir die erste Seite um 90 Grad im Uhrzeigersinn.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Schritt 3: Speichern Sie das gedrehte Dokument
Speichern Sie das gedrehte PDF-Dokument mit den angegebenen Änderungen.
```csharp
annotator.Save("result.pdf");
```
## Schritt 4: Bestätigung anzeigen
Informieren Sie den Benutzer, dass das Dokument erfolgreich gedreht wurde.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Abschluss
Das Drehen von PDF-Dokumenten ist eine grundlegende Aufgabe und wird mit Groupdocs.Annotation für .NET einfach und effizient. Mit den in diesem Tutorial beschriebenen Schritten können Sie PDF-Dateien ganz einfach nach Ihren Anforderungen drehen.
## Häufig gestellte Fragen
### Kann ich mit Groupdocs.Annotation für .NET mehrere Seiten in einem PDF-Dokument drehen?
Ja, Sie können mehrere Seiten zum Drehen angeben, indem Sie die `ProcessPages` Eigentum entsprechend.
### Ist Groupdocs.Annotation für .NET mit allen Versionen des .NET-Frameworks kompatibel?
Groupdocs.Annotation für .NET unterstützt eine breite Palette von .NET-Framework-Versionen und gewährleistet so die Kompatibilität für die meisten Entwicklungsumgebungen.
### Bietet Groupdocs.Annotation für .NET Optionen zum Drehen von PDF-Dokumenten in verschiedene Richtungen?
Ja, Sie können PDF-Dokumente je nach Bedarf im Uhrzeigersinn, gegen den Uhrzeigersinn oder in benutzerdefinierten Winkeln drehen.
### Kann ich Groupdocs.Annotation für .NET in mein bestehendes Dokumentenmanagementsystem integrieren?
Auf jeden Fall, Groupdocs.Annotation für .NET bietet nahtlose Integrationsoptionen, mit denen Sie die Dokumentverwaltungsfunktionen mühelos erweitern können.
### Gibt es eine Testversion für Groupdocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion erhalten von [Hier](https://releases.groupdocs.com/).