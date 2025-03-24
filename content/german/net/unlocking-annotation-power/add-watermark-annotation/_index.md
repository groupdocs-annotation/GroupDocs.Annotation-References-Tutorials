---
title: Fügen Sie dem Dokument eine Wasserzeichenanmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Wasserzeichenanmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET mühelos Wasserzeichenanmerkungen zu Ihren Dokumenten hinzufügen. Verbessern Sie die Klarheit und Sicherheit von Dokumenten.
weight: 28
url: /de/net/unlocking-annotation-power/add-watermark-annotation/
---
## Einführung
In diesem Tutorial führen wir den Prozess des Hinzufügens einer Wasserzeichenanmerkung zu einem Dokument mithilfe von GroupDocs.Annotation für .NET durch. Wasserzeichenanmerkungen sind nützlich, um den Status eines Dokuments anzuzeigen, es als vertraulich zu kennzeichnen oder andere relevante Informationen hinzuzufügen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  GroupDocs.Annotation für .NET: Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem System installiert ist.
3. Grundkenntnisse in C#: Um die Codebeispiele zu verstehen und umzusetzen, sind Kenntnisse der Programmiersprache C# erforderlich.

## Namespaces importieren

Bevor wir mit dem Codieren beginnen, importieren wir die erforderlichen Namespaces:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Lassen Sie uns nun den Prozess des Hinzufügens einer Wasserzeichenanmerkung in mehrere Schritte unterteilen:

## Schritt 1: Ausgabepfad definieren

 Zuerst müssen wir den Ausgabepfad definieren, in dem das mit Anmerkungen versehene Dokument gespeichert wird. Wir werden das verwenden`Path` Klasse von`System.IO` Namespace, um den Ausgabeverzeichnispfad mit dem Dateinamen zu kombinieren.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Schritt 2: Annotator initialisieren

Als Nächstes initialisieren wir den Annotator, indem wir den Pfad des Eingabedokuments angeben. Dadurch können wir dem Dokument Anmerkungen hinzufügen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier angezeigt
}
```

## Schritt 3: Erstellen Sie eine Wasserzeichenanmerkung

Erstellen wir nun ein Wasserzeichen-Anmerkungsobjekt mit den gewünschten Eigenschaften wie Winkel, Position, Text, Schriftfarbe, Deckkraft usw.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Schritt 4: Wasserzeichenanmerkung hinzufügen

 Jetzt fügen wir die Wasserzeichenanmerkung mithilfe von zum Dokument hinzu`Add` Methode des Annotatorobjekts.

```csharp
annotator.Add(watermark);
```

## Schritt 5: Dokument speichern

Abschließend speichern wir das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.

```csharp
annotator.Save(outputPath);
```

## Abschluss

In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine Wasserzeichenanmerkung hinzufügt. Wasserzeichenanmerkungen sind ein wertvolles Werkzeug, um Dokumente mit relevanten Informationen zu kennzeichnen oder ihren Status anzuzeigen.

## FAQs

### F: Kann ich das Erscheinungsbild der Wasserzeichenanmerkung anpassen?

A: Ja, Sie können verschiedene Eigenschaften wie Text, Schriftgröße, Farbe, Deckkraft, Position usw. anpassen, um das Wasserzeichen an Ihre Anforderungen anzupassen.

### F: Ist GroupDocs.Annotation für .NET mit verschiedenen Dokumentformaten kompatibel?

A: Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und Bildformate.

### F: Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?

A: Absolut, GroupDocs.Annotation ermöglicht es Ihnen, mehrere Anmerkungen unterschiedlicher Art zu einem einzelnen Dokument hinzuzufügen und so ein umfassendes Dokument-Markup zu ermöglichen.

### F: Bietet GroupDocs.Annotation Unterstützung für kollaborative Anmerkungen?

A: Ja, GroupDocs.Annotation erleichtert das gemeinsame Annotieren, indem es Benutzern das Hinzufügen von Kommentaren, Antworten und Anmerkungen ermöglicht und so eine effektive Zusammenarbeit zwischen Teammitgliedern fördert.

### F: Gibt es eine Testversion für GroupDocs.Annotation für .NET?

 A: Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).