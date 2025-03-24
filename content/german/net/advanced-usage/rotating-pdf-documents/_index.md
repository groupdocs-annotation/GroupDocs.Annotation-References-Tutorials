---
title: Rotierende PDF-Dokumente
linktitle: Rotierende PDF-Dokumente
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie PDF-Dokumente mühelos mit Groupdocs.Annotation für .NET drehen. Verbessern Sie die Effizienz des Dokumentenmanagements.
weight: 22
url: /de/net/advanced-usage/rotating-pdf-documents/
---
## Einführung
Das Rotieren von PDF-Dokumenten kann eine entscheidende Aufgabe sein, wenn es um Dateien geht, die anders angezeigt oder verarbeitet werden müssen. In diesem Tutorial erfahren Sie Schritt für Schritt, wie Sie PDF-Dokumente mit Groupdocs.Annotation für .NET drehen.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  Groupdocs.Annotation for .NET-Bibliothek: Stellen Sie sicher, dass Sie die Groupdocs.Annotation for .NET-Bibliothek heruntergeladen und installiert haben. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).
2. Grundkenntnisse der C#-Programmierung: In diesem Tutorial wird davon ausgegangen, dass Sie über grundlegende Kenntnisse der Programmiersprache C# und der Arbeit mit .NET-Bibliotheken verfügen.

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren, um auf die von der Groupdocs.Annotation-Bibliothek bereitgestellten Funktionen zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Laden Sie das PDF-Dokument
 Laden Sie zunächst das PDF-Dokument, das Sie drehen möchten, mit`Annotator` Klasse.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Schritt 2: Legen Sie die Rotation fest und verarbeiten Sie die Seiten
Geben Sie den Drehwinkel und die Seiten an, die Sie drehen möchten. In diesem Beispiel drehen wir die erste Seite um 90 Grad im Uhrzeigersinn.
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
Informieren Sie den Benutzer darüber, dass das Dokument erfolgreich gedreht wurde.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Abschluss
Das Rotieren von PDF-Dokumenten ist ein grundlegender Vorgang und wird mit Groupdocs.Annotation für .NET einfach und effizient. Wenn Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie PDF-Dateien ganz einfach entsprechend Ihren Anforderungen drehen.
## FAQs
### Kann ich mit Groupdocs.Annotation für .NET mehrere Seiten in einem PDF-Dokument drehen?
 Ja, Sie können mehrere zu drehende Seiten angeben, indem Sie die anpassen`ProcessPages` Eigentum entsprechend.
### Ist Groupdocs.Annotation für .NET mit allen Versionen des .NET Frameworks kompatibel?
Groupdocs.Annotation für .NET unterstützt eine Vielzahl von .NET Framework-Versionen und gewährleistet so die Kompatibilität mit den meisten Entwicklungsumgebungen.
### Bietet Groupdocs.Annotation für .NET Optionen zum Drehen von PDF-Dokumenten in verschiedene Richtungen?
Ja, Sie können PDF-Dokumente je nach Ihren Anforderungen im Uhrzeigersinn, gegen den Uhrzeigersinn oder in benutzerdefinierten Winkeln drehen.
### Kann ich Groupdocs.Annotation für .NET in mein bestehendes Dokumentenmanagementsystem integrieren?
Absolut, Groupdocs.Annotation für .NET bietet nahtlose Integrationsoptionen, sodass Sie die Dokumentverwaltungsfunktionen mühelos erweitern können.
### Gibt es eine Testversion für Groupdocs.Annotation für .NET?
 Ja, Sie können eine kostenlose Testversion von erhalten[Hier](https://releases.groupdocs.com/).