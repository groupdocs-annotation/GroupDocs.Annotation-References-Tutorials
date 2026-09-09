---
categories:
- Java Development
date: '2026-03-24'
description: Leer hoe je schone PDF‑Java‑bestanden maakt, Java‑PDF‑geheugen beheert
  en PDF in Java annoteert met GroupDocs.Annotation, met volledige codevoorbeelden
  en tips voor probleemoplossing.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Maak schone PDF Java: Onderstreepte annotaties met GroupDocs'
type: docs
url: /nl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Maak schone PDF Java: Onderstrepingsannotaties met GroupDocs

Als je **create clean PDF Java** bestanden moet maken en collaboratieve annotaties wilt toevoegen, ben je hier op de juiste plek. Heb je moeite met documentbeheer en samenwerking in je Java-toepassingen? Je bent niet de enige. Veel ontwikkelaars staan voor de uitdaging om robuuste documentannotatiefuncties te implementeren die betrouwbaar werken met verschillende bestandsformaten.

In deze gids zul je **create clean PDF Java** bestanden maken en leren hoe je **annotate PDF in Java** gebruikt met GroupDocs.Annotation. Aan het einde van deze tutorial weet je precies hoe je onderstrepingsannotaties met opmerkingen kunt toevoegen, bestaande annotaties kunt verwijderen en deze functies naadloos in je projecten kunt integreren.

**Wat je in deze gids onder de knie krijgt:**
- GroupDocs.Annotation instellen in je Java-project (op de juiste manier)  
- Onderstrepingsannotaties toevoegen met aangepaste opmerkingen en styling  
- Alle annotaties verwijderen om schone documentversies te maken  
- Veelvoorkomende problemen die ontwikkelaars tegenkomen oplossen  
- Prestaties optimaliseren voor productie‑applicaties  

Of je nu een documentreview‑systeem, een educatief platform of een collaboratief bewerkingstool bouwt, deze tutorial biedt je praktische, geteste code‑voorbeelden.

## Quick Answers
- **Hoe voeg ik een onderstrepingsannotatie toe?** Gebruik `UnderlineAnnotation` en `annotator.add()` en sla vervolgens het document op.  
- **Hoe kan ik een clean PDF Java bestand maken?** Laad het geannoteerde bestand, stel `AnnotationType.NONE` in `SaveOptions` in, en sla een nieuwe kopie op.  
- **Welke bibliotheken zijn vereist?** GroupDocs.Annotation v25.2 (of nieuwer) en de Maven‑repository.  
- **Heb ik een licentie nodig voor productie?** Ja—pas een geldige GroupDocs‑licentie toe om watermerken te vermijden.  
- **Kan ik meerdere documenten efficiënt verwerken?** Plaats elke `Annotator` in een try‑with‑resources‑blok en maak deze na elk bestand vrij.

## Hoe maak je clean PDF Java bestanden
Een clean PDF Java bestand maken betekent een versie van het document genereren **zonder annotaties** terwijl de originele inhoud behouden blijft. Dit is nuttig voor einddistributie, archivering, of wanneer je een “schone” kopie wilt delen na een review‑cyclus.

GroupDocs.Annotation maakt dit eenvoudig: laad het geannoteerde bestand, configureer `SaveOptions` om alle annotatietypen uit te sluiten, en sla het resultaat op. De stappen worden later geïllustreerd in de sectie **Removing Annotations**.

## Waarom clean PDF Java bestanden maken?
Een schone versie verwijdert beoordelingsmarkeringen, opmerkingen en markeringen, waardoor je een gepolijst document krijgt dat klaar is voor klanten, toezichthouders of openbare publicatie. Het verkleint ook de bestandsgrootte en voorkomt per ongeluk lekken van interne notities—cruciaal voor juridische en compliance‑werkstromen.

## Hoe PDF annoteren in Java met GroupDocs
GroupDocs.Annotation biedt een rijke API voor **annotate PDF in Java**. Het ondersteunt een breed scala aan annotatietypen, waaronder highlights, stempels en onderstrepingen. In deze tutorial richten we ons op onderstrepingsannotaties omdat ze vaak worden gebruikt om tekst te benadrukken terwijl ze threaded opmerkingen mogelijk maken.

## Vereisten en Omgevingsconfiguratie

### Wat je nodig hebt voordat je begint

**Development Environment Requirements:**
- Java Development Kit (JDK) 8 of hoger (JDK 11+ aanbevolen)  
- Maven 3.6+ of Gradle 6.0+ voor afhankelijkheidsbeheer  
- IDE zoals IntelliJ IDEA, Eclipse, of VS Code met Java‑extensies  
- Minimaal 2 GB beschikbaar RAM (documentverwerking kan geheugenintensief zijn)

**Knowledge Prerequisites:**
Je moet vertrouwd zijn met basis Java‑concepten—objectinitialisatie, methode‑aanroepen en Maven‑afhankelijkheden. Eerdere ervaring met externe bibliotheken versnelt de adoptie.

**Testing Documents:**
Zorg voor een paar voorbeeld‑PDF’s. Tekst‑gebaseerde PDF’s werken het beste; gescande afbeeldingen kunnen OCR vereisen vóór annotatie.

### Maven‑configuratie: GroupDocs in je project krijgen

Hier lees je hoe je je Maven‑project correct configureert (dit struikelt veel ontwikkelaars bij hun eerste poging):

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

**Belangrijk:** Versie 25.2 is de nieuwste stabiele release op het moment van schrijven. Controleer regelmatig de GroupDocs‑repository voor nieuwere versies met bug‑fixes en prestatie‑verbeteringen.

### Licentie‑configuratie (niet overslaan)

**Voor ontwikkeling/testing:**  
Download de gratis proefversie van de GroupDocs‑website. De proefversie bevat alle functies maar voegt een watermerk toe aan verwerkte documenten.

**Voor productie:**  
Koop een licentie en pas deze toe tijdens het opstarten van de applicatie. Zonder een geldige licentie zullen productie‑builds beperkt zijn.

## Implementatie‑gids: Onderstrepingsannotaties toevoegen

### Het annotatiewerkproces begrijpen

Voordat we in de code duiken, lopen we de vier‑stappen workflow door die plaatsvindt wanneer je **annotate PDF in Java**:

1. **Document laden** – `Annotator` leest het bestand in het geheugen.  
2. **Annotatie maken** – Definieer eigenschappen zoals positie, stijl en opmerkingen.  
3. **Annotatie toepassen** – De bibliotheek injecteert de annotatie in de structuur van de PDF.  
4. **Document opslaan** – Sla het gewijzigde bestand op, eventueel met behoud van het origineel.

Het proces is niet‑destructief; het bronbestand blijft onaangeroerd tenzij je het overschrijft.

### Stap 1: Initialiseer de Annotator en laad je document

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Pro‑tip:** Gebruik absolute paden tijdens ontwikkeling om “bestand niet gevonden” fouten te voorkomen. In productie, overweeg resources te laden vanaf het classpath of een cloud‑opslag‑bucket.

### Stap 2: Opmerkingen en antwoorden maken (het collaboratieve deel)

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

**Praktijkvoorbeeld:** Beoordelaars kunnen een specifieke clausule bespreken door threaded antwoorden toe te voegen, waardoor het gesprek gekoppeld blijft aan de exacte annotatie.

### Stap 3: Annotatiecoördinaten definiëren (de juiste positie bepalen)

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

**Coördinatensysteem:**  
- Punten 1 & 2 definiëren de bovenrand van de onderstreping.  
- Punten 3 & 4 definiëren de onderrand.  
- Het Y‑verschil (730 vs 650) bepaalt de dikte.

### Stap 4: De onderstrepingsannotatie maken en configureren

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Kleur‑ en doorzichtigheidstips:**  
- `FontColor` gebruikt ARGB; `65535` (0x00FFFF) geeft fel geel.  
- Voor rood, gebruik `16711680` (0xFF0000); voor blauw, `255` (0x0000FF).  
- Doorzichtigheidswaarden tussen 0.5 en 0.8 bieden goede leesbaarheid zonder de tekst te verbergen.

### Stap 5: Je geannoteerde document opslaan

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Geheugenbeheer:** De `dispose()`‑aanroep vrijgeeft native resources en voorkomt geheugenlekken—cruciaal bij het verwerken van veel bestanden in een batch.

## Annotaties verwijderen: schone documentversies maken

Soms heb je een versie van de PDF **zonder annotaties** nodig—bijvoorbeeld bij het leveren van het definitieve goedgekeurde contract. GroupDocs maakt dit eenvoudig.

### Opties voor het verwijderen van annotaties begrijpen

Je kunt:
- Verwijder **alle** annotaties (meest gebruikelijk)  
- Verwijder specifieke typen (bijv. alleen highlights)  
- Verwijder annotaties op auteur of pagina  

### Stapsgewijze annotatieverwijdering

**Step 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 2: Configure Save Options for a Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Step 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Dit produceert een **clean PDF Java** bestand dat geen annotatie‑objecten bevat, perfect voor einddistributie.

## Veelvoorkomende problemen en oplossingen

### Problem 1: “Document not found” Errors

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Problem 2: Annotations Appearing in Wrong Locations

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 3: Memory Issues with Large Documents

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problem 4: Licensing Issues in Production

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## Prestaties‑best practices voor productie‑applicaties

### Memory Management Strategies

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Threading Considerations

GroupDocs.Annotation is **not thread‑safe** by default. If your application processes documents concurrently:

- **Deel nooit** een `Annotator`‑instantie over threads.  
- **Synchroniseer** bestands‑toegang of gebruik een lock‑mechanisme.  
- Overweeg een **pool** van `Annotator`‑objecten als je hoge doorvoer nodig hebt.

### Caching Strategies

- Cache vaak gebruikte annotatiesjablonen.  
- Herbruik `Point`‑collecties voor veelvoorkomende coördinaten.  
- Houd een **template PDF** in het geheugen als je herhaaldelijk hetzelfde basisdocument annoteert.

## Java PDF geheugenbeheer‑tips

Efficiënt geheugen gebruik is essentieel wanneer je grote PDF’s verwerkt of veel bestanden in een batch verwerkt. Hier zijn een paar praktische aanbevelingen:

- **Gebruik try‑with‑resources** voor elke `Annotator` om vrijgave te garanderen.  
- **Verhoog de JVM‑heap** (`-Xmx`) alleen indien nodig; monitor gebruik met profiling‑tools.  
- **Verwerk documenten opeenvolgend** wanneer mogelijk, en maak geheugen vrij na elk bestand.  
- **Vermijd het meerdere keren laden van dezelfde PDF**; hergebruik dezelfde stream als je deze herhaaldelijk moet lezen.

Het toepassen van deze praktijken helpt je applicatie responsief te houden en voorkomt out‑of‑memory crashes tijdens zware annotatiewerkzaamheden.

## Praktische toepassingen en use‑cases

### Document Review Systems

- **Legal Review:** Onderstreep contractclausules en voeg opmerkingen over risico toe.  
- **Compliance Audits:** Markeer problematische secties in financiële overzichten.  
- **Academic Peer Review:** Professoren onderstrepen passages die verduidelijking nodig hebben.

### Educational Platforms

- **Studentannotatietools:** Laat leerlingen sleutelconcepten onderstrepen in e‑books.  
- **Docentfeedback:** Geef inline opmerkingen direct op ingediende opdrachten.

### Quality Assurance Workflows

- **Technische documentatie review:** Engineers onderstrepen secties die updates nodig hebben.  
- **Standaard operationele procedures:** Veiligheidsfunctionarissen markeren kritieke stappen.

### Content Management Systems

- **Redactionele workflow:** Editors onderstrepen tekst die fact‑checking vereist.  
- **Versiebeheer:** Volg annotatiegeschiedenis over documentrevisies.

## Geavanceerde tips voor professionele implementatie

### Custom Annotation Styles

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Annotation Metadata for Tracking

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration with User Management Systems

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Problemen oplossen in productie

### Performance Monitoring

Houd deze statistieken in de gaten in productie:

- **Heap‑gebruik** – zorg dat `dispose()` wordt aangeroepen.  
- **Verwerkingstijd per document** – log tijdstempels vóór/na `annotator.save()`.  
- **Foutpercentage** – vang uitzonderingen op en categoriseer ze.

### Common Production Gotchas

- **Bestandsvergrendeling** – zorg dat geüploade bestanden gesloten zijn vóór annotatie.  
- **Gelijktijdige bewerkingen** – implementeer optimistic locking of versiecontroles.  
- **Grote bestanden (> 50 MB)** – vergroot JVM‑timeout en overweeg streaming‑API’s.

### Error Handling Best Practices

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Conclusie

Je hebt nu alles wat je nodig hebt om **create clean PDF Java** bestanden te **annotate PDF in Java** met onderstrepingsannotaties te maken met GroupDocs.Annotation. Vergeet niet:

- Beheer resources met try‑with‑resources of expliciete `dispose()`.  
- Valideer coördinaten vroeg om verkeerd geplaatste onderstrepingen te voorkomen.  
- Implementeer robuuste foutafhandeling voor productie‑stabiliteit.  
- Maak gebruik van rolgebaseerde styling en metadata om in je workflow te passen.

Volgende stappen? Probeer andere annotatietypen toe te voegen—highlights, stempels of tekstvervangingen—om een volledig uitgeruste documentreview‑oplossing te bouwen.

## Veelgestelde vragen

**Q: Hoe annoteer ik meerdere tekstgebieden in één bewerking?**  
A: Maak meerdere `UnderlineAnnotation`‑objecten met verschillende coördinaten en voeg ze opeenvolgend toe met `annotator.add()`.

**Q: Kan ik afbeeldingen binnen PDF‑documenten annoteren?**  
A: Ja. Gebruik hetzelfde coördinatensysteem en zorg dat de punten binnen de afbeelding liggen.

**Q: Welke bestandsformaten ondersteunt GroupDocs.Annotation naast PDF?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) en beeldformaten zoals JPEG, PNG, TIFF.

**Q: Hoe ga ik om met zeer grote documenten zonder geheugen op te raken?**  
A: Verwerk documenten één voor één, vergroot de JVM‑heap (`-Xmx`) en maak `Annotator`‑instanties altijd direct vrij.

**Q: Is het mogelijk om bestaande annotaties uit een document te extraheren?**  
A: Ja. Gebruik `annotator.get()` om alle annotaties op te halen en filter vervolgens op type, auteur of pagina indien nodig.

---

**Laatst bijgewerkt:** 2026-03-24  
**Getest met:** GroupDocs.Annotation 25.2  
**Auteur:** GroupDocs  

---