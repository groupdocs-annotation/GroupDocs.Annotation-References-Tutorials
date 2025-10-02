---
"date": "2025-05-06"
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET effizient nur kommentierte Seiten einer PDF-Datei speichern. Optimieren Sie Dokumentenmanagement und Zusammenarbeit mit dieser ausführlichen Anleitung."
"title": "So speichern Sie kommentierte Seiten in PDF mit GroupDocs.Annotation für .NET"
"url": "/de/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# So speichern Sie kommentierte Seiten in PDF mit GroupDocs.Annotation für .NET

## Einführung

Sie haben Schwierigkeiten, bestimmte kommentierte Seiten aus Ihren PDF-Dokumenten zu speichern? Diese umfassende Anleitung zeigt, wie Sie dies mit GroupDocs.Annotation für .NET effizient erreichen. Nutzen Sie die Kommentarfunktionen, optimieren Sie Ihr Dokumentenmanagement und verbessern Sie die Zusammenarbeit, indem Sie sich auf relevante Inhalte konzentrieren.

In diesem Tutorial lernen Sie:
- Einrichten Ihrer Entwicklungsumgebung mit GroupDocs.Annotation
- Hinzufügen verschiedener Arten von Anmerkungen
- Effektives Speichern nur kommentierter Seiten

Bereit zum Start? Wir stellen sicher, dass Sie alles bereit haben.

### Voraussetzungen

Stellen Sie vor Beginn sicher, dass Sie über Folgendes verfügen:
- **.NET Framework** (Version 4.6 oder höher) oder **.NET Core/5+**
- Ein Code-Editor wie Visual Studio
- Grundkenntnisse in C# und .NET-Projekt-Setup

## Einrichten von GroupDocs.Annotation für .NET

Um GroupDocs.Annotation zu verwenden, installieren Sie es über NuGet.

**NuGet-Paket-Manager-Konsole**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET-CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Lizenzerwerb

GroupDocs bietet eine kostenlose Testversion an, um die Software umfassend zu testen. Für eine längere Nutzung erwerben Sie eine Lizenz oder fordern Sie eine befristete Lizenz an:
- **Kostenlose Testversion**: Erkunden Sie die Funktionen für einen ersten Zeitraum ohne Einschränkungen.
- **Temporäre Lizenz**: Verwenden Sie GroupDocs.Annotation vorübergehend in der Produktion.
- **Kaufen**Sichern Sie Ihren langfristigen Bedarf mit einer kommerziellen Lizenz.

Nach der Installation initialisieren Sie die Bibliothek wie folgt:

```csharp
using GroupDocs.Annotation;

// Grundlegende Einrichtung zum Laden und Kommentieren von Dokumenten
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Implementierungshandbuch

### Hinzufügen von Anmerkungen

#### Überblick

Anmerkungen helfen dabei, wichtige Bereiche in Ihrem Dokument hervorzuheben. Lassen Sie uns das Hinzufügen einer `AreaAnnotation` und ein `EllipseAnnotation`.

**Schritt 1: Bereichsanmerkung erstellen**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definieren Sie die Bereichsanmerkung
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position und Größe
    BackgroundColor = 65535,                // ARGB-Farbwert für Hervorhebung
    PageNumber = 1                          // Bestimmte Seitenzahl
};
```

Der `AreaAnnotation` markiert einen rechteckigen Bereich im Dokument. Passen Sie seine Position an (`Box`) und Hintergrundfarbe.

**Schritt 2: Ellipsenanmerkung erstellen**

```csharp
// Definieren der Ellipsenannotation
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position und Größe
    BackgroundColor = 123456,                // ARGB-Farbwert für Hervorhebung
    PageNumber = 1                           // Bestimmte Seitenzahl
};
```

Der `EllipseAnnotation` ermöglicht das Zeichnen einer ovalen Form auf dem Dokument. Passen Sie Position und Abmessungen mit dem `Box` Eigentum.

**Schritt 3: Anmerkungen hinzufügen**

```csharp
// Hinzufügen von Anmerkungen zur Annotator-Instanz
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Mithilfe der `Add` Methode, mehrere Arten von Anmerkungen einschließen. Dieser Schritt fügt sowohl die `AreaAnnotation` Und `EllipseAnnotation`.

### Nur kommentierte Seiten speichern

#### Überblick

Um nur Seiten mit Anmerkungen zu speichern, konfigurieren Sie Ihre Speicheroptionen entsprechend.

**Schritt 4: Kommentierte Seiten speichern**

```csharp
using GroupDocs.Annotation.Options;

// Richten Sie die Speicheroptionen so ein, dass nur kommentierte Seiten eingeschlossen werden
annotator.Save("path/to/output/document.pdf\