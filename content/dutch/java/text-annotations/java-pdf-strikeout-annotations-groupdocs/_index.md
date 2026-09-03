---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Leer hoe u strike‑out annotaties kunt toevoegen aan PDF's in Java met
  behulp van GroupDocs. Deze stapsgewijze tutorial behandelt installatie, code, probleemoplossing
  en prestatie‑tips.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF Tekst Strikeout Gids
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Hoe strike‑out annotaties toe te voegen aan PDF's in Java – Complete GroupDocs-gids
type: docs
url: /nl/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Hoe Strikeout-annotaties toe te voegen aan PDF's in Java

Heb je ooit tekst in een PDF programmatisch moeten doorstrepen? Of je nu een documentreview‑systeem bouwt, een bewerkingsworkflow maakt, of gewoon tekst wilt markeren voor verwijdering, **hoe strikeout‑annotaties** toe te voegen in Java is een praktische vaardigheid die tijd bespaart en handmatig werk vermindert. In deze uitgebreide gids ontdek je alles wat je moet weten om strikeout‑annotaties te implementeren met GroupDocs.Annotation voor Java, van projectconfiguratie tot prestatie‑optimalisatie.

## Snelle antwoorden
- **Wat is de eerste stap?** Voeg de GroupDocs.Annotation Maven‑dependency toe aan je `pom.xml`.  
- **Hoe maak ik een strikeout?** Instantieer `Annotator`, definieer `StrikeoutAnnotation` met punten, stel kleur/doorzichtigheid in, en roep vervolgens `addAnnotation` aan.  
- **Kan ik opmerkingen toevoegen?** Ja, koppel een `Comment`‑object aan de annotatie voor samenwerking.  
- **Wat als de annotatie op de verkeerde plaats staat?** Pas de coördinatenpunten aan; PDF gebruikt een oorsprongsysteem links‑onder.  
- **Is er een limiet aan de documentgrootte?** GroupDocs verwerkt PDF's van honderden pagina's zonder het volledige bestand in het geheugen te laden.

## Wat betekent “how to add strikeout” in PDF‑annotatie?
De uitdrukking “how to add strikeout” verwijst naar het proces waarbij programmatically een lijn door geselecteerde tekst in een PDF‑document wordt getekend met behulp van een annotatie‑API. In Java biedt GroupDocs.Annotation een speciale `StrikeoutAnnotation`‑klasse die het renderen, stijlen en bewaren van strikeout‑markeringen afhandelt.

## Waarom GroupDocs gebruiken voor Java PDF‑Strikeout?
GroupDocs.Annotation ondersteunt **50+ invoer‑ en uitvoerformaten**—inclusief PDF, DOCX, XLSX, PPTX, HTML en gangbare afbeeldingsformaten—zodat je niet vastzit aan één bestandstype. Het biedt een high‑level API die de low‑level PDF‑structuur abstraheert, automatisch lettertype‑embedding, paginarendering en annotatie‑persistentie afhandelt, waardoor ontwikkelaars zich kunnen richten op de businesslogica in plaats van PDF‑internals.

## Voorvereisten en installatie‑eisen

### Essentiële vereisten
- **Java Development Kit (JDK):** Versie 8 of later (JDK 11+ aanbevolen voor optimale garbage‑collection).  
- **GroupDocs.Annotation voor Java:** Geïntegreerd via Maven (zie het Maven‑fragment hieronder).  
- **IDE:** IntelliJ IDEA, Eclipse of een andere Java‑compatibele editor.

### Maven‑dependencies configuratie
Voeg het volgende dependency‑blok toe aan je `pom.xml`:

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

**Pro tip:** Controleer altijd de nieuwste versie op de GroupDocs‑releasepagina; nieuwere releases voegen functies toe en verhelpen bugs die de weergave van annotaties kunnen beïnvloeden.

### Je licentie regelen
GroupDocs.Annotation vereist een geldige licentie voor productiegebruik. Je hebt drie opties:

- **Gratis proefversie:** Download van [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Tijdelijke licentie:** Vraag een ontwikkelingssleutel aan via [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Volledige licentie:** Aanschaf voor productie via [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

De proefversie voegt een subtiele watermerk toe, plan je tests dus dienovereenkomstig.

## Stapsgewijze implementatie‑gids

### De kerncomponenten begrijpen
De volgende definities geven je een snel mentaal model:

- **Annotator:** Het primaire API‑object dat een PDF laadt en annotatiemethoden beschikbaar maakt.  
- **StrikeoutAnnotation:** Vertegenwoordigt de visuele strikeout‑lijn en de bijbehorende stijlopties.  
- **Point:** Een coördinatenpaar (X, Y) dat de bibliotheek vertelt waar de lijn begint en eindigt.  
- **Comment:** Optionele tekst die aan een annotatie wordt gekoppeld voor samenwerking.

### Stap 1: Bestands‑paden instellen
Definieer de locaties van je bron‑PDF en het doelbestand. Onjuiste paden zijn een veelvoorkomende oorzaak van “File Not Found”‑fouten.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Veelgemaakte fout:** Zorg ervoor dat de uitvoermap bestaat en schrijfbaar is; GroupDocs maakt ontbrekende mappen niet automatisch aan.

### Stap 2: De Annotator initialiseren
Maak een `Annotator`‑instance die de PDF in het geheugen laadt.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**Wat gebeurt er hier?** De bibliotheek parseert de PDF‑structuur, bouwt een interne representatie en bereidt een paginagebaseerd annotatie‑canvas voor. Voor bestanden met honderden pagina's kan deze stap enkele seconden duren.

### Stap 3: Opmerkingen toevoegen (optioneel maar aanbevolen)
`Comment` is een klasse die een tekstuele notitie vertegenwoordigt die aan een annotatie is gekoppeld, zodat medewerkers de reden voor de strikeout kunnen uitleggen.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Praktische tip:** Gebruik opmerkingen om te verduidelijken waarom tekst wordt verwijderd—dit is vooral nuttig in juridische of redactionele review‑workflows.

### Stap 4: Annotatie‑coördinaten definiëren
`Point`‑objecten slaan X‑Y‑coördinatenparen op die de exacte locatie van een annotatie op een PDF‑pagina bepalen.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coördinatensysteem uitgelegd:** PDF‑coördinaten beginnen in de linker‑onderhoek (0,0). Het voorbeeld maakt een horizontale lijn van (80,730) naar (240,730) op de doelpagina.

**De juiste coördinaten vinden:** Veel ontwikkelaars maken een helper die percentages van de paginabreedte/‑hoogte omzet naar absolute punten, waardoor de code robuust blijft voor verschillende paginagroottes.

### Stap 5: De Strikeout‑annotatie maken
`StrikeoutAnnotation` omvat de visuele lijn, stijl‑eigenschappen zoals kleur en doorzichtigheid, en eventuele metadata voor een strikeout‑markering.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Kleurwaarden:** De `fontColor` gebruikt decimale RGB‑waarden (bijv. 65535 voor fel geel). Gebruik een online converter als je merk‑specifieke tinten nodig hebt.

**Doorzichtigheids‑aanbeveling:** Een doorzichtigheid van `0.7` (70 %) biedt een duidelijk visueel signaal terwijl de onderliggende tekst leesbaar blijft.

### Stap 6: De annotatie toepassen
`addAnnotation` is een methode van de `Annotator` die de voorbereide annotatie registreert bij het document zodat deze wordt gerenderd en opgeslagen.

```java
annotator.add(strikeout);
```

### Stap 7: Opslaan en opruimen
`dispose()` vrijgeeft native resources die door de `Annotator`‑instance worden gehouden, waardoor geheugenlekken worden voorkomen nadat de verwerking is voltooid.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Opmerking over geheugenbeheer:** Het aanroepen van `dispose()` bevrijdt native resources en voorkomt geheugenlekken bij het batch‑verwerken van PDF's.

## Veelvoorkomende problemen en hoe ze op te lossen

### Probleem 1: “File Not Found”‑fouten
**Symptomen:** Exception gegooid tijdens `Annotator`‑constructie.  
**Oplossing:** Controleer zowel de invoer‑ als uitvoer‑paden en bevestig dat de applicatie lees‑/schrijfrechten heeft.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Probleem 2: Strikeout verschijnt op de verkeerde locatie
**Symptomen:** De lijn komt niet overeen met de beoogde tekst.  
**Oplossing:** Onthoud dat PDF‑Y‑coördinaten omhoog toenemen. Gebruik een visueel debug‑tool of print de paginadimensies om de punten fijn af te stellen.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Probleem 3: Annotatie niet zichtbaar
**Symptomen:** Na opslaan verschijnt er geen strikeout.  
**Mogelijke oorzaken & oplossingen:**
- **Doorzichtigheid te laag:** Zet tijdelijk de doorzichtigheid op `1.0` om zichtbaarheid te verifiëren.  
- **Kleurvermenging:** Gebruik een hoog‑contrastkleur zoals rood (`255`).  
- **Onjuist paginanummer:** Pagina‑indexen beginnen bij nul; zorg dat je de juiste pagina target.

### Probleem 4: Geheugenproblemen met grote bestanden
**Symptomen:** `OutOfMemoryError` of trage prestaties.  
**Oplossingen:**  
- Verwerk documenten in kleinere batches.  
- Gebruik de streaming‑API indien beschikbaar.  
- Roep altijd `dispose()` aan na elk document.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Praktische toepassingen en use‑cases

### Juridische documentreview
Advocaten annoteren contracten met strikeouts om verwijderde clausules aan te geven terwijl ze een audit‑trail behouden.

### Academische paper‑redactie
Professoren gebruiken strikeouts om verwijderingen voor te stellen tijdens peer review, waarbij de originele tekst zichtbaar blijft voor context.

### Content‑managementsystemen
Publicatieplatforms markeren automatisch secties die in strijd zijn met beleid met strikeouts vóór handmatige moderatie.

### Versiebeheer voor documenten
Ondernemingen behandelen strikeout‑annotaties als “verwijderingsmarkeringen” in een document‑gecentreerde versie‑control workflow, vergelijkbaar met code‑diffs.

## Tips voor prestatie‑optimalisatie

### Batch‑verwerkingsstrategie
Wanneer je veel PDF's verwerkt, hergebruik dan een enkele `Annotator`‑instance waar mogelijk en verwerk bestanden in parallelle threads.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Best practices voor geheugenbeheer
- Roep `dispose()` aan op elke `Annotator`.  
- Beperk gelijktijdige document‑loads om heap‑druk te vermijden.  
- Monitor JVM‑geheugengebruik met tools zoals VisualVM.

### Coördinaten‑caching
Als je dezelfde annotatielay‑out op meerdere bestanden toepast, cache dan de `Point`‑objecten om herberekening te vermijden.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Geavanceerde aanpassingsopties

### Dynamische kleurselectie
Kies kleuren tijdens runtime op basis van bedrijfsregels (bijv. rood voor kritieke verwijderingen, geel voor voorlopige).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Meerdere lijnen strikeout
Maak een reeks `Point`‑paren om een zig‑zag‑lijn te tekenen die meerdere tekstregels doorkruist.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Checklist voor probleemoplossing
1. **Bestandsrechten:** Controleer lees‑/schrijftoegang.  
2. **Bibliotheekversie:** Zorg dat je een ondersteunde GroupDocs.Annotation‑release gebruikt.  
3. **Licentiestatus:** Bevestig dat het licentiebestand correct wordt gerefereerd.  
4. **PDF‑compatibiliteit:** Controleer of de PDF niet corrupt is en binnen de ondersteunde grootte‑limieten valt.  
5. **Coördinatenvalidatie:** Zorg dat alle punten binnen de paginagrenzen liggen.  
6. **Heap‑ruimte:** Verhoog JVM‑`-Xmx` bij verwerking van zeer grote bestanden.

## Veelgestelde vragen

**V: Kan ik tekst over meerdere regels strikeouten?**  
A: Ja. Maak meerdere `Point`‑objecten die het gewenste pad volgen; de annotatie volgt de opgegeven polyline.

**V: Wat gebeurt er als ik coördinaten buiten de paginagrenzen opgeef?**  
A: De annotatie wordt bijgesneden en kan onzichtbaar worden. Valideer altijd coördinaten tegen de breedte en hoogte van de pagina.

**V: Kan ik strikeout‑annotaties verwijderen nadat ik ze heb toegevoegd?**  
A: Absoluut. Gebruik de `removeAnnotation`‑methode met de ID van de annotatie of filter op type om ze programmatisch te verwijderen.

**V: Is er een limiet aan het aantal annotaties dat ik aan één PDF kan toevoegen?**  
A: GroupDocs legt geen harde limiet, maar de prestaties kunnen afnemen na duizenden annotaties. Overweeg paginering of samenvatten van annotaties voor zeer grote sets.

**V: Hoe werk ik met wachtwoord‑beveiligde PDF's?**  
A: Geef het wachtwoord door aan de `Annotator`‑constructor. De bibliotheek zal het document in het geheugen ontsleutelen voordat annotaties worden toegepast.

**V: Hoe ga ik om met PDF's met verschillende paginagroottes en -oriëntaties?**  
A: Haal de afmetingen van elke pagina op via `annotator.getPageInfo(pageNumber)` en bereken coördinaten relatief ten opzichte van die afmetingen om consistente plaatsing te garanderen.

## Conclusie
Je beschikt nu over een volledige, productieklare oplossing voor **hoe strikeout‑annotaties** toe te voegen aan PDF's in Java met GroupDocs.Annotation. Door het beheer van bestands‑paden, coördinatenberekening en resource‑management te beheersen, kun je deze functionaliteit integreren in documentreview‑tools, content‑pipelines of elke Java‑gebaseerde applicatie die precieze visuele feedback vereist.

**Volgende stappen**
1. Clone het voorbeeldproject en voer het uit tegen een voorbeeld‑PDF.  
2. Experimenteer met verschillende kleuren, doorzichtigheden en opmerkingsteksten.  
3. Integreer de annotatie‑workflow in je bestaande document‑verwerkingsservice.  
4. Verken gerelateerde annotatietypen—highlights, sticky notes en vorm‑annotaties—om je PDF‑manipulatie‑toolkit uit te breiden.

Klaar voor meer? Duik in de officiële documentatie voor diepere API‑inzichten.

## Aanvullende bronnen

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Algemene documentatie voor GroupDocs‑bibliotheken  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Complete API‑referentie  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Methode‑voor‑methode details  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Houd je bibliotheek up‑to‑date  
- [Purchase License](https://purchase.groupdocs.com/buy) - Productieklaar licentiëren  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Evalueren vóór aankoop  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Ontwikkelingstesten  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Community‑hulp en officiële support  

---

**Laatst bijgewerkt:** 2026-05-21  
**Getest met:** GroupDocs.Annotation 23.12 for Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)