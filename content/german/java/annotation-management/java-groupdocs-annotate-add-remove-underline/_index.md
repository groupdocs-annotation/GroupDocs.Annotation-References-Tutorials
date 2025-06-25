---
"date": "2025-05-06"
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation Unterstreichungen in Java-Dokumenten hinzufügen und entfernen. Optimieren Sie Ihr Dokumentenmanagement mit dieser ausführlichen Anleitung."
"title": "Hinzufügen und Entfernen von Unterstreichungsanmerkungen in Java mithilfe von GroupDocs – Ein umfassender Leitfaden"
"url": "/de/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
"weight": 1
---

# So implementieren Sie Java: Hinzufügen und Entfernen von Unterstreichungsanmerkungen mit GroupDocs

## Einführung

Möchten Sie Ihr Dokumentenmanagementsystem verbessern, indem Sie programmgesteuert Anmerkungen hinzufügen oder entfernen? Dieses Tutorial führt Sie durch die Verwendung der leistungsstarken GroupDocs.Annotation-Bibliothek in Java, um unterstrichene Anmerkungen aus Dokumenten wie PDFs hinzuzufügen und zu entfernen.

**Was Sie lernen werden:**
- Initialisieren Sie die Annotator-Klasse.
- Fügen Sie mithilfe von GroupDocs.Annotation für Java eine Unterstreichungsanmerkung mit Kommentaren hinzu.
- Entfernen Sie alle Anmerkungen aus einem Dokument.
- Konfigurieren Sie Ihre Umgebung für die effiziente Nutzung von GroupDocs.Annotation.

Lassen Sie uns untersuchen, wie Sie diese Funktionen in Ihren Projekten nutzen können. Stellen Sie sicher, dass Sie die notwendigen Voraussetzungen erfüllt haben, bevor Sie beginnen.

## Voraussetzungen

### Erforderliche Bibliotheken und Abhängigkeiten
Um diesem Tutorial effektiv folgen zu können, stellen Sie sicher, dass Sie über Folgendes verfügen:
- **GroupDocs.Annotation für Java**: Version 25.2 oder höher wird empfohlen.
- **Java Development Kit (JDK)**: Version 8 oder höher ist erforderlich.

### Anforderungen für die Umgebungseinrichtung
Stellen Sie sicher, dass Ihre Entwicklungsumgebung eine IDE wie IntelliJ IDEA oder Eclipse und ein Build-Tool wie Maven enthält.

### Voraussetzungen
Grundkenntnisse in der Java-Programmierung, insbesondere im Umgang mit Bibliotheken über Maven, sind von Vorteil.

## Einrichten von GroupDocs.Annotation für Java

Um GroupDocs.Annotation in Ihren Java-Projekten zu verwenden, befolgen Sie diese Einrichtungsschritte:

**Maven-Konfiguration:**
Fügen Sie die folgende Konfiguration zu Ihrem `pom.xml` Datei zum Herunterladen und Integrieren von GroupDocs.Annotation.

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Lizenzerwerb:**
Laden Sie zunächst eine kostenlose Testversion herunter oder erwerben Sie eine temporäre Lizenz von GroupDocs, um den vollen Funktionsumfang der Bibliothek zu nutzen. Für den produktiven Einsatz ist der Erwerb einer Lizenz erforderlich.

## Implementierungshandbuch

### Funktion 1: Annotator initialisieren und Unterstreichungsanmerkungen hinzufügen

Dieser Abschnitt führt Sie durch die Initialisierung des `Annotator` Klasse und fügen Sie Ihrem Dokument eine Unterstreichungsanmerkung hinzu.

#### Überblick
Durch das Hinzufügen von Anmerkungen können bestimmte Teile eines Dokuments hervorgehoben werden. Hier konzentrieren wir uns auf das Unterstreichen von Text mit Kommentaren zur Erläuterung oder für Feedback.

#### Schrittweise Implementierung

**1. Annotator initialisieren**
Erstellen Sie ein `Annotator` Objekt und laden Sie Ihre PDF-Datei.

```java
import com.groupdocs.annotation.Annotator;

// Laden Sie das Dokument, das Sie kommentieren möchten
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Erstellen Sie Kommentare mit Antworten**
Definieren Sie Kommentare, die mit der unterstrichenen Anmerkung verknüpft sind.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Definieren Sie Punkte für die Unterstreichungsanmerkung**
Legen Sie Koordinaten fest, um zu bestimmen, wo die Unterstreichung erscheinen soll.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Erstellen und Konfigurieren von Unterstreichungsanmerkungen**
Erstellen Sie die Unterstreichungsanmerkung und legen Sie ihre Eigenschaften wie Farbe, Deckkraft und Kommentare fest.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Gelb im ARGB-Format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Speichern Sie das kommentierte Dokument**
Speichern Sie Ihre Änderungen in einer neuen Datei.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Tipps zur Fehlerbehebung
- Stellen Sie sicher, dass alle Koordinaten der Punkte innerhalb der Dokumentgrenzen liegen.
- Überprüfen Sie, ob die `outputPath` Verzeichnis existiert und ist beschreibbar.

### Funktion 2: Dokument ohne Anmerkungen speichern

In diesem Abschnitt wird beschrieben, wie Sie alle Anmerkungen aus einem zuvor mit Anmerkungen versehenen Dokument entfernen.

#### Überblick
Möglicherweise müssen Sie zum Teilen oder Archivieren eine saubere Version Ihres Dokuments ohne Anmerkungen speichern.

#### Schrittweise Implementierung

**1. Initialisieren Sie Annotator mit dem kommentierten Dokument**
Laden Sie das Dokument mit vorhandenen Anmerkungen.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Konfigurieren Sie die Speicheroptionen zum Entfernen von Anmerkungen**
Geben Sie an, dass in der Ausgabedatei keine Anmerkungen gespeichert werden sollen.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Speichern Sie das Dokument ohne Anmerkungen**
Legen Sie den Pfad für das bereinigte Dokument fest und speichern Sie es.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Praktische Anwendungen

Hier sind einige reale Szenarien, in denen diese Funktionen von Vorteil sein können:
1. **Dokumentenprüfung**: Hervorheben und Kommentieren von Abschnitten eines Vertrags oder Berichts zur Überprüfung.
2. **Lehrmittel**: Kommentieren von Lehrbüchern mit Notizen oder Korrekturen für Studierende.
3. **Gemeinsame Bearbeitung**: Teilen Sie kommentierte Entwürfe unter den Teammitgliedern, um Feedback zu erhalten.
4. **Rechtliche Dokumentation**: Unterstreichen wichtiger Klauseln in Rechtsdokumenten während Diskussionen.
5. **Marketingmaterialien**: Hervorheben wichtiger Informationen in Broschüren vor der Verteilung.

## Überlegungen zur Leistung
Beachten Sie beim Arbeiten mit GroupDocs.Annotation diese Tipps zur Leistungsoptimierung:
- **Speicherverwaltung**: Entsorgen Sie ordnungsgemäß `Annotator` Objekte, um Ressourcen freizugeben.
- **Stapelverarbeitung**: Wenn Sie mehrere Dokumente mit Anmerkungen versehen, verarbeiten Sie diese stapelweise, um die Systemlast effektiv zu verwalten.
- **Ressourcenzuweisung**: Stellen Sie sicher, dass Ihre Umgebung über ausreichend Arbeitsspeicher und Verarbeitungsleistung für die Verarbeitung großer Dateien verfügt.

## Abschluss
Sie haben gelernt, wie Sie mit GroupDocs.Annotation für Java Unterstreichungsanmerkungen hinzufügen und entfernen. Dieses Tutorial behandelte die Initialisierung der Annotator-Klasse, die Konfiguration von Anmerkungen mit Kommentaren und das Speichern von Dokumenten ohne Anmerkungen. 

Erwägen Sie zur weiteren Erkundung die Integration dieser Funktionen in Ihre vorhandenen Dokumentenverwaltungssysteme oder das Experimentieren mit anderen von GroupDocs bereitgestellten Anmerkungstypen.

## FAQ-Bereich
1. **Wie konfiguriere ich mehrere Unterstreichungsanmerkungen in einem einzigen Lauf?**
   - Erstellen Sie mehrere `UnderlineAnnotation` Objekte und fügen Sie sie nacheinander hinzu, indem Sie `annotator.add()` Verfahren.
2. **Kann ich mit dieser Bibliothek Bilder in PDFs mit Anmerkungen versehen?**
   - Ja, GroupDocs.Annotation unterstützt das Kommentieren von Bildern in Dokumenten wie PDFs.
3. **Welche Dateiformate unterstützt GroupDocs.Annotation?**
   - Es unterstützt verschiedene Dokumentformate, darunter PDF, Word, Excel und mehr.