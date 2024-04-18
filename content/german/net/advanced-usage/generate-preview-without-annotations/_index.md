---
title: Vorschau ohne Anmerkungen generieren
linktitle: Vorschau ohne Anmerkungen generieren
second_title: GroupDocs.Annotation .NET-API
description: Verbessern Sie die Zusammenarbeit und Kommentierung von Dokumenten in .NET-Anwendungen mit GroupDocs.Annotation für .NET. Mit dieser leistungsstarken Bibliothek können Sie Dokumente ganz einfach mit Anmerkungen versehen, markieren und überprüfen.
type: docs
weight: 13
url: /de/net/advanced-usage/generate-preview-without-annotations/
---
## Einführung
Im heutigen digitalen Zeitalter ist eine effiziente Zusammenarbeit an Dokumenten der Schlüssel zu Produktivität und Erfolg. Unabhängig davon, ob Sie an einem Projekt mit Teammitgliedern arbeiten, die über die ganze Welt verstreut sind, oder mit Kunden an wichtigen Verträgen zusammenarbeiten, ist die Möglichkeit, Dokumente nahtlos zu kommentieren und zu überprüfen, von entscheidender Bedeutung. Mit GroupDocs.Annotation für .NET können Sie Ihre Zusammenarbeit an Dokumenten auf die nächste Ebene heben und eine einfache Annotation, Markierung und Überprüfung direkt in Ihren .NET-Anwendungen ermöglichen.
## Voraussetzungen
Bevor Sie mit GroupDocs.Annotation für .NET in die Welt der Dokumentannotation eintauchen, müssen Sie einige Voraussetzungen erfüllen:
### 1. Installieren Sie GroupDocs.Annotation für .NET
 Zunächst müssen Sie GroupDocs.Annotation für .NET herunterladen und installieren. Den Download-Link finden Sie hier[Hier](https://releases.groupdocs.com/annotation/net/). Befolgen Sie die bereitgestellten Installationsanweisungen, um die Bibliothek in Ihrer .NET-Umgebung einzurichten.
### 2. Erwerben Sie eine Lizenz (optional)
Während GroupDocs.Annotation für .NET eine kostenlose Testversion anbietet, sollten Sie den Erwerb einer Lizenz in Betracht ziehen, um vollen Zugriff auf seine Funktionen zu erhalten. Sie können eine Lizenz erwerben[Hier](https://purchase.groupdocs.com/buy) oder fordern Sie eine temporäre Lizenz an[Hier](https://purchase.groupdocs.com/temporary-license/) zu Testzwecken.
### 3. Vertrautheit mit C#- und .NET-Entwicklung
Um GroupDocs.Annotation für .NET optimal nutzen zu können, ist es hilfreich, über grundlegende Kenntnisse der C#- und .NET-Entwicklung zu verfügen. Dadurch können Sie die Bibliothek nahtlos in Ihre bestehenden Anwendungen und Arbeitsabläufe integrieren.
### 4. Installieren Sie einen PDF-Viewer
Da GroupDocs.Annotation für .NET mit PDF-Dokumenten funktioniert, muss auf Ihrem System ein PDF-Viewer installiert sein, um eine Vorschau der mit Anmerkungen versehenen Dokumente anzuzeigen. Der Adobe Acrobat Reader oder ein anderer PDF-Viewer reicht aus.

## Namespaces importieren
Bevor Sie mit dem Kommentieren von Dokumenten beginnen können, müssen Sie die erforderlichen Namespaces in Ihr .NET-Projekt importieren. Dadurch können Sie auf die von GroupDocs.Annotation für .NET bereitgestellten Klassen und Methoden zugreifen.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Nachdem Sie nun alles eingerichtet haben, erstellen wir eine Vorschau eines Dokuments ohne Anmerkungen. Befolgen Sie diese Schritte, um dies zu erreichen:
## Schritt 1: Annotator initialisieren
 Erstellen Sie zunächst eine Instanz von`Annotator` -Klasse und übergibt den Pfad zu dem Dokument, das Sie mit Anmerkungen versehen möchten.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Schritt 2: Vorschauoptionen konfigurieren
Konfigurieren Sie anschließend die Vorschauoptionen entsprechend Ihren Anforderungen. Sie können die Seitenzahlen angeben, die Sie in die Vorschau aufnehmen möchten, das Vorschauformat (z. B. PNG) und ob Anmerkungen gerendert werden sollen.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## Schritt 3: Vorschau erstellen
 Generieren Sie abschließend die Vorschau mithilfe von`GeneratePreview` Methode der`Document` Klasse und übergibt die konfigurierten Vorschauoptionen.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Wenn Sie diese einfachen Schritte befolgen, können Sie mit GroupDocs.Annotation für .NET eine Vorschau eines Dokuments ohne Anmerkungen erstellen.

## Abschluss
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET eine leistungsstarke Lösung für die Zusammenarbeit und Annotation von Dokumenten innerhalb von .NET-Anwendungen bietet. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie Dokumentanmerkungsfunktionen nahtlos in Ihre Projekte integrieren und so die Zusammenarbeit und Produktivität verbessern.
## FAQs
### F: Kann ich GroupDocs.Annotation für .NET mit anderen Dokumentformaten als PDF verwenden?
Ja, GroupDocs.Annotation für .NET unterstützt eine Vielzahl von Dokumentformaten, darunter DOCX, XLSX, PPTX und mehr.
### F: Ist GroupDocs.Annotation für .NET mit .NET Core kompatibel?
Ja, GroupDocs.Annotation für .NET ist sowohl mit .NET Framework- als auch mit .NET Core-Umgebungen kompatibel.
### F: Bietet GroupDocs.Annotation für .NET anpassbare Anmerkungstools?
Ja, GroupDocs.Annotation für .NET bietet eine Reihe von Anmerkungstools, die an Ihre spezifischen Anforderungen angepasst werden können.
### F: Kann ich GroupDocs.Annotation für .NET in meine Webanwendungen integrieren?
Ja, GroupDocs.Annotation für .NET kann sowohl in Desktop- als auch in Webanwendungen integriert werden und bietet nahtlose Funktionen für die Zusammenarbeit an Dokumenten.
### F: Gibt es ein Community-Forum, in dem ich Unterstützung und Hilfe zu GroupDocs.Annotation für .NET erhalten kann?
 Ja, Sie finden Unterstützung und Hilfe im GroupDocs.Annotation-Forum[Hier](https://forum.groupdocs.com/c/annotation/10).