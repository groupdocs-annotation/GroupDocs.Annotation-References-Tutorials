---
"date": "2025-05-06"
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET prägnante und relevante Dokumentvorschauen aus bestimmten Arbeitsblattspalten erstellen. Ideal für optimierte Arbeitsabläufe in der Datenanalyse und im IT-Management."
"title": "Generieren Sie gezielte Excel-Tabellenvorschauen mit GroupDocs.Annotation .NET"
"url": "/de/net/document-preview/groupdocs-annotation-net-create-previews-worksheet-columns/"
"weight": 1
---

# Generieren Sie gezielte Excel-Tabellenvorschauen mit GroupDocs.Annotation .NET
## Handbuch zur Dokumentvorschau
### Einführung
Möchten Sie die Übersichtlichkeit Ihrer Dokumentenverarbeitung verbessern, indem Sie sich auf bestimmte Datenpunkte konzentrieren? Ob Entwickler, der Datenanalysetools erstellt, IT-Experte, der Dokumente verwaltet, oder jemand, der Arbeitsabläufe optimieren möchte – gezielte Dokumentvorschauen sparen Zeit und steigern die Effizienz. Dieses Tutorial führt Sie durch die Verwendung von GroupDocs.Annotation für .NET, um Vorschauen aus ausgewählten Arbeitsblattspalten zu generieren und so präzise und relevante Ergebnisse zu gewährleisten.

#### Was Sie lernen werden:
- So richten Sie GroupDocs.Annotation für .NET ein
- Erstellen von Vorschauen mit angegebenen Arbeitsblattspalten
- Konfigurieren von Vorschauoptionen für eine optimale Ausgabe
- Praktische Anwendungen dieser Funktion in realen Szenarien

Lassen Sie uns zunächst die erforderlichen Voraussetzungen überprüfen, bevor Sie mit der Implementierung dieser Lösung beginnen.
## Voraussetzungen
Bevor Sie mit der Implementierung beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

### Erforderliche Bibliotheken und Versionen:
- **GroupDocs.Annotation für .NET**: Version 25.4.0 oder höher ist erforderlich.

### Anforderungen für die Umgebungseinrichtung:
- Eine Entwicklungsumgebung mit installiertem .NET Framework oder .NET Core.

### Erforderliche Kenntnisse:
- Grundlegende Kenntnisse der C#-Programmierung
- Vertrautheit mit Datei-E/A-Operationen in .NET
## Einrichten von GroupDocs.Annotation für .NET
Um zu beginnen, müssen Sie die Bibliothek GroupDocs.Annotation installieren. So können Sie dies mit verschiedenen Paketmanagern tun:

**NuGet-Paket-Manager-Konsole**
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET-CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Schritte zum Lizenzerwerb:
- **Kostenlose Testversion**: Laden Sie eine Testversion herunter von der [GroupDocs-Website](https://releases.groupdocs.com/annotation/net/) um Funktionen zu testen.
- **Temporäre Lizenz**: Erhalten Sie eine temporäre Lizenz für den vollen Zugriff während der Entwicklung unter [Seite „Temporäre Lizenz“](https://purchase.groupdocs.com/temporary-license/).
- **Kaufen**: Für den Produktionseinsatz erwerben Sie eine Lizenz über die [GroupDocs-Kaufseite](https://purchase.groupdocs.com/buy).
### Grundlegende Initialisierung und Einrichtung mit C#:
So können Sie Ihre Umgebung einrichten, um mit GroupDocs.Annotation für .NET zu arbeiten.
```csharp
using System;
using GroupDocs.Annotation;
// Initialisieren Sie das Annotator-Objekt mit einem Dokumentpfad.
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";
Annotator annotator = new Annotator(inputFilePath);
```
Nachdem Sie nun alles eingerichtet haben, können wir mit der Generierung von Vorschauen aus bestimmten Arbeitsblattspalten fortfahren.
## Implementierungshandbuch
Diese Anleitung führt Sie durch die Implementierung der Funktion zum Generieren von Dokumentvorschauen mit angegebenen Arbeitsblattspalten. Jeder Abschnitt konzentriert sich auf einen bestimmten Aspekt des Implementierungsprozesses.
### Erstellen einer Dokumentvorschau aus bestimmten Arbeitsblattspalten
**Überblick**Mit dieser Funktion können Entwickler Dokumentvorschauen erstellen, die nur ausgewählte Spalten aus einem Excel-Arbeitsblatt enthalten, wodurch sowohl die Leistung als auch die Relevanz verbessert werden.
#### Schritt 1: Vorschauoptionen definieren
Beginnen Sie mit der Einrichtung Ihres `PreviewOptions`. Dadurch wird bestimmt, wie und wo Ihre Vorschaudateien gespeichert werden.
```csharp
using System.IO;
using GroupDocs.Annotation.Options;
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY";
PreviewOptions previewOptions = new PreviewOptions(pageNumber => 
    new FileStream(Path.Combine(outputDirectoryPath, $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose());
```
**Erläuterung**: Der `PreviewOptions` Der Konstruktor benötigt zwei Delegaten. Der erste gibt den Dateipfad für das Vorschaubild jeder Seite an. Der zweite stellt sicher, dass Streams nach der Verwendung ordnungsgemäß entsorgt werden.
#### Schritt 2: Arbeitsblattspalten angeben
Wählen Sie aus, welche Spalten Ihres Arbeitsblatts Sie in die Vorschau einbeziehen möchten, indem Sie sie hinzufügen zu `WorksheetColumns`.
```csharp
// Fügen Sie bestimmte Spalten aus Sheet1 ein.
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1\