---
categories:
- Advanced Usage
date: '2026-04-06'
description: Erfahren Sie, wie Sie Anmerkungen nach Version in GroupDocs.Annotation .NET
  mithilfe von Versionsschlüsseln abrufen. Schritt‑für‑Schritt‑Tutorial mit Codebeispielen
  und bewährten Methoden.
keywords:
- retrieve annotations by version
- version key
- GroupDocs.Annotation .NET
lastmod: '2026-04-06'
linktitle: Liste der Anmerkungen mit Versionsschlüssel abrufen
second_title: GroupDocs.Annotation .NET API
tags:
- groupdocs-annotation
- version-control
- document-annotations
- dotnet-api
title: Anmerkungen nach Version in GroupDocs.Annotation .NET abrufen
type: docs
url: /de/net/advanced-usage/get-list-annotations-version-key/
weight: 18
---

# Wie man eine Liste von Anmerkungen mit Versionsschlüssel in GroupDocs.Annotation .NET abruft

In diesem Tutorial lernen Sie **wie man Anmerkungen nach Version abruft** mit GroupDocs.Annotation für .NET. Das Verwalten verschiedener Anmerkungs‑Versionen ist eine häufige Herausforderung beim Aufbau kollaborativer Dokument‑Workflows, und der hier gezeigte Ansatz ermöglicht es Ihnen, genau zu bestimmen, welche Anmerkungen zu einer bestimmten Dokumentversion gehören.

## Schnelle Antworten
- **Was bedeutet „Anmerkungen nach Version abrufen“?** Es bedeutet, nur die Anmerkungen abzurufen, die mit einem bestimmten Versionsschlüssel gespeichert wurden.  
- **Welcher API‑Aufruf wird verwendet?** `Annotator.GetVersion(string versionKey)`.  
- **Benötige ich eine spezielle Lizenz?** Für den Produktionseinsatz ist eine gültige GroupDocs.Annotation‑Lizenz erforderlich.  
- **Wird es für alle Dateitypen unterstützt?** Ja – PDF, DOCX, XLSX, PPTX und viele weitere.  
- **Kann ich die Ergebnisse filtern?** Absolut – Sie können nach Anmerkungstyp, Autor oder Datum nach dem Abruf filtern.

## Warum die versionsbasierte Anmerkungsabfrage wichtig ist

Bevor wir in den Code eintauchen, sollten wir verstehen, wann Sie diese Funktionalität tatsächlich benötigen:

- **Dokumenten‑Review‑Workflows**: Verfolgen, welche Anmerkungen zu bestimmten Review‑Runden gehören  
- **Audit‑Trails**: Einhaltung sicherstellen, indem die Anmerkungshistorie über Dokumentversionen hinweg erhalten bleibt  
- **Kollaboratives Bearbeiten**: Mehrere Benutzer können gleichzeitig an verschiedenen Dokumentversionen arbeiten  
- **Change‑Management**: Bei Bedarf zu vorherigen Anmerkungszuständen zurückkehren  

Stellen Sie es sich wie Git für Ihre Dokumenten‑Anmerkungen vor – Sie können jederzeit nachverfolgen, was sich wann geändert hat.

## Was bedeutet „Anmerkungen nach Version abrufen“?

Das Abrufen von Anmerkungen nach Version ist der Vorgang, den Anmerkungsspeicher nach einem bestimmten **Versionsschlüssel** abzufragen. Der Versionsschlüssel ist ein vom Entwickler definierter Bezeichner (z. B. `v1.0`, `review‑round‑2`), der Anmerkungen gruppiert und das Isolieren von Änderungen, die während einer bestimmten Dokumentiteration vorgenommen wurden, erleichtert.

## Voraussetzungen für die Einrichtung von GroupDocs.Annotation .NET

Bevor Sie mit dem Abrufen von Anmerkungen nach Versionsschlüssel beginnen können, benötigen Sie eine geeignete Entwicklungsumgebung. Das benötigen Sie (und einige häufige Stolperfallen, die Sie vermeiden sollten):

### 1. Einrichtung der .NET‑Entwicklungsumgebung

Sie benötigen eine funktionierende .NET‑Entwicklungsumgebung. Das bedeutet nicht nur, dass Visual Studio installiert sein muss – Sie benötigen auch die richtige SDK‑Version.

#### Einrichtung des .NET SDK
1. Besuchen Sie die .NET‑Website und laden Sie die neueste Version des .NET SDK herunter.  
2. Befolgen Sie die für Ihr Betriebssystem bereitgestellten Installationsanweisungen.  
3. Überprüfen Sie die Installation, indem Sie ein Befehlsfenster öffnen und `dotnet --version` eingeben.

**Pro‑Tipp**: Wenn Sie in einer Teamumgebung arbeiten, fixieren Sie Ihre .NET‑SDK‑Version in einer `global.json`‑Datei, um „funktioniert auf meinem Rechner“-Probleme zu vermeiden.

### 2. Installation von GroupDocs.Annotation

Die Installation von GroupDocs.Annotation ist unkompliziert, es gibt jedoch je nach Projektsetup mehrere Möglichkeiten.

#### Installation über den NuGet Package Manager
1. Öffnen Sie Ihr Projekt in Visual Studio.  
2. Klicken Sie im Solution Explorer mit der rechten Maustaste auf Ihr Projekt und wählen Sie **Manage NuGet Packages**.  
3. Suchen Sie nach **GroupDocs.Annotation** und installieren Sie die neueste verfügbare Version.

**Wichtig**: Überprüfen Sie stets die Mindest‑.NET‑Version‑Anforderungen des Pakets im Vergleich zum Ziel‑Framework Ihres Projekts. Nicht übereinstimmende Versionen sind eine häufige Ursache für Laufzeitfehler.

## Wichtige Namespaces für Anmerkungs‑Operationen

Bevor Sie mit Anmerkungen arbeiten können, müssen Sie die richtigen Namespaces importieren. Das benötigen Sie:

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Annotation.Models.AnnotationModels;
```

**Hinweis**: Der Namespace `GroupDocs.Annotation.Models.AnnotationModels` enthält alle Anmerkungstypen, mit denen Sie arbeiten werden. Überspringen Sie diesen Import nicht, sonst erhalten Sie verwirrende Kompilierfehler.

## Schritt‑für‑Schritt‑Anleitung: Anmerkungen nach Versionsschlüssel abrufen

Jetzt zum Hauptteil – das eigentliche Abrufen der Anmerkungen. Der Prozess umfasst zwei zentrale Schritte, die nahtlos zusammenarbeiten.

### Schritt 1: Initialisieren des Annotator‑Objekts

Zuerst müssen Sie das `Annotator`‑Objekt mit Ihrem Ziel‑Dokument initialisieren. Dadurch wird die Verbindung zwischen Ihrem Code und dem annotierten Dokument hergestellt.

```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Annotation operations will be performed here
}
```

**Wichtige Punkte zu diesem Schritt**  
- Der Dateipfad kann absolut oder relativ zum Arbeitsverzeichnis Ihrer Anwendung sein.  
- GroupDocs.Annotation unterstützt mehrere Dokumentformate (PDF, DOCX, XLSX, PPTX und mehr).  
- Die `using`‑Anweisung sorgt für die korrekte Ressourcenfreigabe – immer verwenden!

### Schritt 2: Anmerkungen mit Ihrem Versionsschlüssel abrufen

Sobald Ihr Annotator initialisiert ist, erfolgt das Abrufen von Anmerkungen für eine bestimmte Version mit nur einem Methodenaufruf:

```csharp
List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
```

Dies gibt eine Liste aller Anmerkungen zurück, die dem angegebenen Versionsschlüssel zugeordnet sind. Sie können dann durch diese Liste iterieren, Anmerkungen nach Typ filtern oder andere benötigte Operationen ausführen.

**Was Sie mit den Ergebnissen tun können**  
- Anmerkungen nach Typ filtern (Kommentare, Hervorhebungen, Stempel usw.)  
- Metadaten der Anmerkungen extrahieren (Autor, Erstellungsdatum, Änderungsverlauf)  
- Anmerkungen in verschiedene Formate exportieren  
- Anmerkungen auf neue Dokumentversionen anwenden  

## Häufige Probleme und Lösungen

Selbst bei einfachem Code können typische Herausforderungen auftreten. Hier sind die häufigsten Probleme und deren Lösungen:

### Versionsschlüssel nicht gefunden
**Problem**: Ihr Versionsschlüssel liefert keine Anmerkungen.  
**Lösung**: Überprüfen Sie, ob die Anmerkungen tatsächlich mit diesem spezifischen Versionsschlüssel gespeichert wurden. Versionsschlüssel sind case‑sensitive.

### Leistung bei großen Anmerkungs‑Sätzen
**Problem**: Das Abrufen von Anmerkungen dauert zu lange bei Dokumenten mit Hunderten von Anmerkungen.  
**Lösung**: Erwägen Sie die Implementierung von Pagination oder das Filtern von Anmerkungen nach Datumsbereich oder Anmerkungstyp vor dem Abruf.

### Speicherverwaltung
**Problem**: Ihre Anwendung verbraucht übermäßig viel Speicher beim Verarbeiten mehrerer versionierter Dokumente.  
**Lösung**: Entsorgen Sie `Annotator`‑Objekte stets ordnungsgemäß (verwenden Sie `using`‑Anweisungen) und erwägen Sie die Verarbeitung von Dokumenten in Stapeln statt alle auf einmal.

## Best Practices für das Versionsmanagement

Um das Beste aus der versionsbasierten Anmerkungsabfrage herauszuholen, folgen Sie diesen bewährten Strategien:

### 1. Konsistente Versionsbenennung
Verwenden Sie ein klares, konsistentes Benennungsschema für Ihre Versionsschlüssel. Erwägen Sie Muster wie:

- `v1.0`, `v1.1`, `v2.0` für Haupt‑/Nebenversionen  
- `review-round-1`, `review-round-2` für Review‑Zyklen  
- `2025-01-02-draft`, `2025-01-05-final` für datumsbasierte Versionen  

### 2. Verfolgung von Versions‑Metadaten
Speichern Sie zusätzliche Metadaten zusammen mit Ihren Versionsschlüsseln:

- Erstellungszeitstempel  
- Autorinformationen  
- Versionsbeschreibung oder Änderungsnotizen  
- Beziehungen zu übergeordneten Versionen  

### 3. Aufräum‑Strategie
Implementieren Sie eine Strategie zur Verwaltung alter Versionen, um Speicheraufblähungen zu verhindern:

- Versionen, die älter als ein bestimmtes Datum sind, archivieren  
- Die Anzahl der Versionen pro Dokument begrenzen  
- Anmerkungsdaten für die Langzeitspeicherung komprimieren  

## Erweiterte Implementierungsszenarien

Hier sind einige Praxis‑Muster, denen Sie begegnen könnten:

### Vergleich von Anmerkungen über Versionen hinweg
```csharp
using (Annotator annotator = new Annotator("document.pdf"))
{
    var v1Annotations = annotator.GetVersion("v1.0");
    var v2Annotations = annotator.GetVersion("v2.0");
    
    // Compare annotation sets to identify changes
    // Implementation depends on your specific comparison logic
}
```

### Stapelverarbeitung mehrerer Versionen
Wenn Sie mehrere Versionen effizient verarbeiten müssen, sollten Sie Ihre Vorgänge stapeln, um den Ressourcenaufwand zu reduzieren. Durchlaufen Sie eine Sammlung von Versionsschlüsseln und verwenden Sie nach Möglichkeit ein einzelnes `Annotator`‑Objekt erneut.

## FAQ

### Kann ich mit GroupDocs.Annotation für .NET Dokumente außer PDFs annotieren?
Absolut! GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter Word (DOCX), Excel (XLSX), PowerPoint (PPTX) und viele Bildformate. Die Versionsschlüssel‑Funktionalität funktioniert bei allen unterstützten Formaten konsistent.

### Wie gehe ich mit Fällen um, in denen ein Versionsschlüssel nicht existiert?
Die Methode `GetVersion()` gibt eine leere Liste zurück, wenn der angegebene Versionsschlüssel nicht existiert. Prüfen Sie immer, ob die zurückgegebene Liste Elemente enthält, bevor Sie sie verarbeiten. Sie können außerdem try‑catch‑Blöcke implementieren, um mögliche Ausnahmen elegant zu behandeln.

### Gibt es einen Performance‑Einfluss bei Dokumenten mit vielen Versionen?
Die Leistung hängt von der Anzahl der Anmerkungen pro Version ab, nicht von der Anzahl der Versionen selbst. Die Anmerkungen jeder Version werden separat gespeichert, sodass das Abrufen einer Version keine Daten anderer Versionen lädt. Dokumente mit Hunderten von Anmerkungen pro Version können jedoch Pagination‑Strategien erfordern.

### Kann ich Anmerkungen aus mehreren Versionen gleichzeitig abrufen?
Obwohl die Methode `GetVersion()` jeweils nur eine Version abruft, können Sie sie problemlos mehrmals hintereinander aufrufen. Für Bulk‑Operationen sollten Sie einen eigenen Caching‑Mechanismus implementieren, um wiederholte Dateizugriffe zu vermeiden.

### Gibt es eine kostenlose Testversion von GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET erhalten, indem Sie die [Website](https://releases.groupdocs.com/annotation/net/) besuchen. Die Testversion enthält den vollen Funktionsumfang mit einigen Nutzungseinschränkungen.

### Wie kann ich Support für Probleme oder Fragen zu GroupDocs.Annotation erhalten?
Sie können Support erhalten, indem Sie das GroupDocs.Annotation‑Forum besuchen oder das Support‑Team direkt kontaktieren. Das Community‑Forum ist besonders hilfreich für Implementierungsfragen und Best Practices.

### Kann ich eine temporäre Lizenz für GroupDocs.Annotation zu Testzwecken erwerben?
Ja, temporäre Lizenzen können zum Testen und Evaluieren des Produkts erworben werden. Dies ist besonders nützlich für Proof‑of‑Concept‑Projekte oder verlängerte Evaluierungszeiträume.

### Wo finde ich umfassende Dokumentation für GroupDocs.Annotation für .NET?
Sie können die auf der GroupDocs‑Website verfügbare Dokumentation für detaillierte Anleitungen zur Nutzung des Produkts [hier]( https://tutorials.groupdocs.com/annotation/net/) einsehen. Die Dokumentation enthält API‑Referenzen, Code‑Beispiele und fortgeschrittene Anwendungsszenarien.

## Häufig gestellte Fragen

**F: Beeinflusst das Abrufen von Anmerkungen nach Version das Originaldokument?**  
**A:** Nein. Die Methode `GetVersion()` ist schreibgeschützt; sie verändert die Quelldatei nicht.

**F: Kann ich die Versionsfilterung mit anderen Abfrageparametern kombinieren?**  
**A:** Ja. Nach dem Abrufen der Liste können Sie sie im Speicher weiter nach Autor, Anmerkungstyp oder Datum filtern.

**F: Wie werden Versionsschlüssel intern gespeichert?**  
**A:** Versionsschlüssel werden als Teil der Metadaten jeder Anmerkung gespeichert, was eine schnelle Suche ohne Durchsuchen der gesamten Anmerkungssammlung ermöglicht.

**F: Ist es möglich, einen Versionsschlüssel nach dem Speichern von Anmerkungen umzubenennen?**  
**A:** Ein direktes Umbenennen wird nicht unterstützt; Sie müssten die Anmerkungen programmgesteuert in einen neuen Versionsschlüssel kopieren.

**F: Was passiert, wenn ich eine Dokumentversionsdatei lösche?**  
**A:** Das Löschen des zugrunde liegenden Dokuments entfernt alle zugehörigen Anmerkungen, einschließlich derjenigen, die an Versionsschlüssel gebunden sind. Stellen Sie sicher, dass Sie benötigte Versionen vor dem Entfernen sichern.

## Ziel‑Keywords

**Primäres Schlüsselwort (HÖCHSTE PRIORITÄT):**  
retrieve annotations by version

**Sekundäre Schlüsselwörter (UNTERSTÜTZEND):**  
(Not specified)

---

**Zuletzt aktualisiert:** 2026-04-06  
**Getestet mit:** GroupDocs.Annotation 2.0 für .NET (zum Zeitpunkt des Schreibens aktuell)  
**Autor:** GroupDocs