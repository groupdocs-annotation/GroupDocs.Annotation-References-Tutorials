---
title: Dokument von URL laden
linktitle: Dokument von URL laden
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie PDF-Dokumente mit GroupDocs.Annotation für .NET programmgesteuert mit Anmerkungen versehen. Schritt-für-Schritt-Anleitung mit Codebeispielen.
type: docs
weight: 15
url: /de/net/document-loading-essentials/load-document-from-url/
---
## Einführung
GroupDocs.Annotation für .NET ist eine funktionsreiche Bibliothek, die es Entwicklern ermöglicht, ihren .NET-Anwendungen mühelos Annotationsfunktionen hinzuzufügen. Mit GroupDocs.Annotation können Sie PDF-Dokumente programmgesteuert mit Anmerkungen versehen, sodass Benutzer Text hervorheben, Kommentare hinzufügen, Formen zeichnen und mehr können. Dieses Tutorial führt Sie durch die Schritte zum Laden eines Dokuments von einer URL, zum Hinzufügen von Anmerkungen und zum Speichern des mit Anmerkungen versehenen Dokuments mithilfe von GroupDocs.Annotation für .NET.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Entwicklungscomputer installiert ist.
2.  GroupDocs.Annotation für .NET: Laden Sie GroupDocs.Annotation für .NET von herunter und installieren Sie es[Webseite](https://releases.groupdocs.com/annotation/net/).
3. Grundkenntnisse in C#: Machen Sie sich mit der Programmiersprache C# vertraut.
4. Internetverbindung: Sie benötigen eine Internetverbindung, um auf externe Ressourcen zuzugreifen und Beispieldateien herunterzuladen.

## Namespaces importieren
Importieren wir zunächst die erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Schritt 1: Dokument von URL laden
Gehen Sie folgendermaßen vor, um ein PDF-Dokument über eine URL mit Anmerkungen zu versehen:
### Schritt 1.1: Ausgabepfad definieren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Schritt 1.2: URL angeben
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Schritt 1.3: Dokument laden
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Fügen Sie hier Anmerkungen hinzu
    annotator.Save(outputPath);
}
```
## Schritt 2: Anmerkungen hinzufügen
Fügen wir nun dem geladenen Dokument Anmerkungen hinzu. In diesem Beispiel fügen wir eine Bereichsanmerkung hinzu:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Schritt 3: Kommentiertes Dokument speichern
Speichern Sie abschließend das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man PDF-Dokumente mit GroupDocs.Annotation für .NET mit Anmerkungen versehen kann. Wenn Sie der Schritt-für-Schritt-Anleitung folgen, können Sie Anmerkungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren und Benutzern eine effektive Zusammenarbeit an PDF-Dateien ermöglichen.

## FAQs
### Ist GroupDocs.Annotation für .NET mit allen .NET-Frameworks kompatibel?
Ja, GroupDocs.Annotation für .NET ist mit verschiedenen .NET-Frameworks kompatibel, einschließlich .NET Framework, .NET Core und .NET Standard.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen, mit denen Sie das Erscheinungsbild und Verhalten von Anmerkungen entsprechend Ihren Anforderungen ändern können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation für .NET?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET herunterladen[Webseite](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Annotation für .NET?
 Wenn Sie auf technische Probleme stoßen oder Fragen zu GroupDocs.Annotation für .NET haben, können Sie sich an die wenden[Hilfeforum](https://forum.groupdocs.com/c/annotation/10).
### Wo kann ich eine Lizenz für GroupDocs.Annotation für .NET erwerben?
 Sie können eine Lizenz für GroupDocs.Annotation für .NET bei erwerben[Kaufseite](https://purchase.groupdocs.com/buy).