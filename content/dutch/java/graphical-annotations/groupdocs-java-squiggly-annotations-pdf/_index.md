---
categories:
- Java Development
date: '2026-05-16'
description: Leer hoe je annotation replies java maakt met GroupDocs.Annotation. Beheers
  PDF annotation in Java met praktische voorbeelden, prestatie‑tips en best practices.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF Annotation Handleiding
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Java PDF Annotation Library: maak annotation reply java'
type: docs
url: /nl/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF-annotatielibrary: annotatie‑antwoord maken in Java

Als je **create annotation reply java** voor PDF's moet maken — of je nu een contract‑reviewportaal, een e‑learning‑systeem of een bulk‑verwerkingspipeline bouwt — laat deze gids je precies zien hoe je dit doet met GroupDocs.Annotation voor Java. We lopen de installatie, het maken van een squiggly‑annotatie, het threaden van antwoorden en het afstemmen van de prestaties door, zodat je een betrouwbare oplossing kunt leveren in dagen, niet weken.

## Snelle antwoorden
- **Wat is het primaire doel van GroupDocs.Annotation?** Het maakt programmatische creatie, wijziging en extractie van PDF‑annotaties in Java mogelijk.  
- **Hoe voeg ik een squiggly‑annotatie toe?** Instantieer `SquigglyAnnotation`, stel de geometrie en stijl in, en roep vervolgens `annotator.add(...)` aan.  
- **Kan ik antwoorden aan een annotatie koppelen?** Ja — maak `Reply`‑objecten aan, stel auteur en tekst in, en koppel ze aan de bovenliggende annotatie.  
- **Heb ik een licentie nodig voor productie?** Absoluut; zonder een geldige licentie zal de output watermerken bevatten.  
- **Is het geschikt voor batchverwerking?** Ja — gebruik try‑with‑resources om elk document te openen, te annoteren en te sluiten, waardoor het geheugenverbruik laag blijft.

## Waarom Java‑ontwikkelaars PDF‑annotatielibraries nodig hebben

Handmatig PDF's markeren is tijdrovend en foutgevoelig, vooral wanneer je honderden contracten of examenpapieren moet beoordelen. Een Java PDF‑annotatielibrary automatiseert dit werk, waardoor je highlights, squiggly‑onderstrepingen en getagde opmerkingen direct in het bestand kunt embedden. Het resultaat is een doorzoekbaar, draagbaar document dat alle markeringen behoudt zonder een aparte viewer nodig te hebben.

**Wat je in deze gids zult beheersen**
- Het installeren en licentiëren van GroupDocs.Annotation in een Maven‑project  
- Het bouwen van squiggly‑annotaties die eruitzien als native Word‑onderstrepingen  
- Het toevoegen van getagde antwoorden aan elke annotatie voor collaboratieve beoordeling  
- Het optimaliseren van geheugen‑ en CPU‑gebruik bij het verwerken van grote PDF's  
- Het implementeren van de oplossing in Spring Boot, micro‑services of desktop‑apps  

Of je nu een juridisch document‑review‑systeem, een educatieve beoordelings‑tool of een geautomatiseerde kwaliteits‑controlpipeline bouwt, de onderstaande technieken geven je een productie‑klare basis.

## Wat is create annotation reply java?

`create annotation reply java` is het programmatische proces van het koppelen van een commentaarthread (een Reply) aan een bestaande PDF‑annotatie met Java. Replies laten meerdere beoordelaars een specifieke markering bespreken zonder het document te verlaten, waardoor naadloze, in‑place samenwerking mogelijk is. Deze mogelijkheid maakt van een statische PDF een interactief discussiewerkblad, waarbij context en audit‑trails direct in het bestand behouden blijven.

## Vereisten: uw omgeving gereed maken

Voordat we in de code duiken, controleer dat je ontwikkelwerkstation aan de volgende specificaties voldoet:

- **JDK** 8 of hoger (JDK 11 + wordt aanbevolen voor betere garbage‑collection‑prestaties)  
- **Maven** of **Gradle** voor afhankelijkheidsbeheer (voorbeelden gebruiken Maven)  
- Een IDE met Maven‑ondersteuning (IntelliJ IDEA, Eclipse of VS Code)  
- Minimaal **2 GB** vrij RAM voor de IDE en testuitvoeringen  
- Voorbeeld‑PDF‑bestanden voor experimenten (je kunt eenvoudige PDF's genereren met elke PDF‑editor)

GroupDocs.Annotation draait volledig in‑process; er zijn geen externe PDF‑viewers of native libraries vereist.

## GroupDocs.Annotation voor Java instellen

Het integreren van de library is een proces van enkele stappen, maar een paar verborgen valkuilen kunnen runtime‑fouten veroorzaken als je ze mist.

### Maven‑afhankelijkheidsconfiguratie

Voeg de repository en afhankelijkheid toe aan je `pom.xml`. Plaats het `<repositories>`‑element **voor** `<dependencies>` zodat Maven het artefact kan resolven.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **Pro tip:** Controleer de GroupDocs releases‑pagina voor de nieuwste versie. Nieuwe releases bevatten vaak ondersteuning voor opkomende PDF‑standaarden en prestatie‑verbeteringen.

### Licentie‑instelling (Niet overslaan!)

GroupDocs.Annotation vereist een licentiebestand voor productiegebruik. Zonder deze zal elke gegenereerde PDF een watermerk bevatten.

1. **Gratis proefversie** – Volledige functionaliteit voor 30 dagen, ideaal voor evaluatie.  
2. **Tijdelijke licentie** – Goed voor ontwikkeling en interne tests.  
3. **Volledige licentie** – Vereist voor elke commerciële implementatie.

Plaats het `GroupDocs.Annotation.lic`‑bestand in je resources‑map en laad het bij opstarten:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Veelvoorkomende valkuil:** Het vergeten van de licentiestap resulteert in watermerk‑PDF's en API‑aanroepen die stil falen. Valideer de licentie altijd vroeg in je opstartroutine.

## Volledige implementatiegids: Squiggly‑annotaties toevoegen

Hieronder vind je een stap‑voor‑stap walkthrough die laat zien hoe je **create annotation reply java** kunt uitvoeren terwijl je een squiggly‑annotatie bouwt. Elke stap bevat een beknopte uitleg, zodat je de “waarom” achter elke regel begrijpt.

### Stap 1: Importeer alle vereiste klassen

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` is het toegangspunt voor alle document‑niveau operaties.  
- `Point` vertegenwoordigt een coördinaat op een pagina (X en Y gemeten vanaf de linkerbovenhoek).  
- `SquigglyAnnotation` definieert de golvende onderstreping die wordt gebruikt om fouten te markeren.  
- `Reply` bewaart getagde opmerkingen die aan een annotatie zijn gekoppeld.  
- `SaveOptions` laat je het uitvoerformaat en compressie regelen.

### Stap 2: Maak en configureer je Squiggly‑annotatie

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation is een klasse die een golvende onderstreping maakt die wordt gebruikt om fouten in een PDF te markeren.

- **Coördinatensysteem**: Punten beginnen bij de linkerbovenhoek. De twee punten hierboven tekenen een horizontale golvende lijn van (100, 200) naar (300, 200).  
- **Opacity** 0.7 betekent dat de annotatie 70 % ondoorzichtig is, waardoor onderliggende tekst leesbaar blijft.

### Stap 3: Voeg interactieve antwoorden toe (optioneel maar krachtig)

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

`Reply` is een klasse die een commentaarthread vertegenwoordigt die aan een annotatie is gekoppeld.

- Replies creëren een **getagde discussie** direct op de annotatie, wat de ervaring van moderne PDF‑beoordelaars nabootst.  
- Elke reply slaat auteur‑informatie en een tijdstempel op, die je later kunt filteren of weergeven in een UI.

### Stap 4: Pas de annotatie toe en sla het document op

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- De **try‑with‑resources**‑construct sluit automatisch de `Annotator`, waardoor bestands‑handles en native buffers worden vrijgegeven.  
- `save` schrijft de aangepaste PDF naar `output.pdf`.  

> **Geheugennotitie:** De `Annotator` laadt alleen de pagina's die je aanraakt. Voor PDF's met honderden pagina's houdt deze aanpak het heap‑gebruik onder 150 MB op een typische server.

## Geavanceerde configuratie‑opties

### Aanpassen van annotatie‑uiterlijk

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** bepaalt de lijndikte (in points).  
- **ARGB**‑formaat bevat een alfakanaal voor transparantie.

### Annotaties nauwkeurig positioneren

Het correct krijgen van coördinaten kan lastig zijn bij PDF's met verschillende paginagroottes. Volg deze systematische aanpak:

1. **Open de PDF in een viewer** (bijv. Adobe Acrobat) en noteer de liniaalwaarden voor het doelgebied.  
2. **Vertaal liniaalwaarden** naar points (1 point = 1/72 inch).  
3. **Gebruik `annotator.getPageInfo(pageIndex)`** om de paginabreedte en -hoogte op te halen, en bereken vervolgens relatieve posities.

## Veelvoorkomende problemen en oplossingen

### Probleem: Annotaties verschijnen niet

**Meest waarschijnlijke oorzaken**
- Punten liggen buiten de paginagrenzen  
- Licentie niet geladen (watermerk verbergt annotatie)  
- Verkeerd paginanummer (pagina's zijn nul‑gebaseerd in de API)  

**Oplossingschecklist**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Probleem: Slechte prestaties bij grote bestanden

Het laden van een PDF van 500 pagina's in het geheugen kan je service vertragen. Verminder dit door:

- **Één pagina per keer verwerken** – open het document, annoteer één pagina, sla op, en ga dan naar de volgende.  
- **Streaming** – gebruik de streaming‑API van `Annotator` om volledige document‑buffering te vermijden.  
- **Caching** – sla vaak geraadpleegde PDF's op in een snelle cache (bijv. Redis) en annoteer de gecachte kopie.

### Probleem: Kleurwaarden werken niet

GroupDocs verwacht **ARGB** (Alpha, Red, Green, Blue) in plaats van gewone RGB. Een ARGB‑waarde van `0xFFFF0000` betekent volledig ondoorzichtig rood. Als je `0xFF0000` opgeeft, interpreteert de library dit onjuist, wat resulteert in een zwarte annotatie.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Prestatietips

### Geheugenbeheer

Wanneer je tientallen PDF's in een batch‑taak annoteert, wikkel elk bestand in een eigen try‑with‑resources‑blok:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Dit patroon garandeert dat native buffers na elke iteratie worden vrijgegeven, waardoor **OutOfMemoryError** bij langdurige processen wordt voorkomen.

### Optimalisatie van batchverwerking

Voor omgevingen met hoge doorvoer, overweeg parallelle streams gecombineerd met een begrensde thread‑pool:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Bounded pool** voorkomt een explosie van threads, terwijl parallelle streams de CPU‑kernen bezet houden.

### Overwegingen m.b.t. bestandsgrootte

Grote PDF's (> 100 MB) kunnen de prestaties verminderen. Pas deze strategieën toe:

- **Pre‑compress** de bron‑PDF met een tool zoals Ghostscript vóór annotatie.  
- **Alleen benodigde pagina's annoteren** – sla pagina's over die geen markering nodig hebben.  
- **Splits** het document in logische secties (bijv. per hoofdstuk) en verwerk elk deel onafhankelijk.

## Toepassingen in de praktijk

### Document‑reviewsystemen

Juridische kantoren moeten vaak problematische clausules markeren. Squiggly‑annotaties gecombineerd met getagde antwoorden laten meerdere advocaten een enkele alinea bespreken zonder de PDF te verlaten:

- **Advocaat A** voegt een rode squiggly‑onderstreping toe onder een clausule en schrijft “Onduidelijke formulering”.  
- **Advocaat B** reageert “Voeg definitie toe voor ‘material breach’”.  
- De volledige discussie blijft ingebed, doorzoekbaar en controleerbaar.

### Integratie met bestaande systemen

GroupDocs.Annotation werkt soepel met populaire Java‑frameworks:

- **Spring Boot** – exposeer een REST‑endpoint `/api/annotate` dat een PDF‑multipart‑upload accepteert, annotaties toevoegt, en het resultaat terugstuurt.  
- **JSF** – bind annotatie‑acties aan UI‑componenten voor on‑the‑fly markering in een web‑view.  
- **Microservices** – de kleine footprint van de library (< 15 MB) maakt het mogelijk om deze met Docker te containerizen en horizontaal te schalen.

### Workflow‑automatisering

Combineer annotatie met andere GroupDocs‑producten (bijv. GroupDocs.Signature) om end‑to‑end‑pipelines te bouwen:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Wanneer squiggly‑annotaties gebruiken versus alternatieven

| Gebruikssituatie | Aanbevolen annotatie |
|------------------|----------------------|
| Spelling- of grammaticafouten markeren | **Squiggly** – visuele aanwijzing vergelijkbaar met tekstverwerkers |
| Belangrijke secties markeren zonder een fout te impliceren | **Highlight** – doorschijnende overlay |
| Gedetailleerde feedback geven | **Text** of **Comment** – vrij‑formaat notitie‑vak |
| Een document goedkeuren of afwijzen | **Stamp** – “Approved” of “Rejected” badge |

## Conclusie

Je hebt nu een volledige, productie‑klare handleiding voor **create annotation reply java** met GroupDocs.Annotation. Door de API te beheersen, licenties te verwerken en de bovenstaande prestatietips toe te passen, kun je:
- Fout‑markering automatiseren over duizenden PDF's  
- Collaboratieve, getagde discussies binnen het bestand mogelijk maken  
- Het geheugenverbruik laag houden, zelfs bij het verwerken van enorme documenten  

**Volgende stappen**
1. Experimenteer met andere annotatietypen (highlights, stamps, text).  
2. Bouw een REST‑service die PDF's ontvangt, annoteert en het resultaat teruggeeft.  
3. Verken de extractie‑API (`annotator.get()`) om bestaande opmerkingen op te halen voor analytics.  

De kracht van programmatische PDF‑annotatie ligt in het vermogen om saaie handmatige markering te vervangen door herhaalbare, controleerbare code. Of je nu een niche legal‑tech‑product bouwt of een algemene document‑workflow‑engine, de technieken in deze gids geven je een solide basis om vooruit te gaan.

## Veelgestelde vragen

**Q: Wat maakt GroupDocs.Annotation beter dan andere Java PDF‑libraries?**  
A: GroupDocs.Annotation richt zich uitsluitend op annotatie‑workflows, biedt meer dan 30 annotatietypen, getagde antwoorden, en native ondersteuning voor meer dan 50 bestandsformaten, terwijl de geheugen‑footprint onder 200 MB blijft voor PDF's van 500 pagina's.

**Q: Kan ik deze library gebruiken met Spring Boot‑applicaties?**  
A: Absoluut. Maak een `@RestController` die de `Annotator`‑service injecteert, multipart‑uploads verwerkt, en de geannoteerde PDF terugstreamt naar de client. Vergeet niet een thread‑pool te configureren voor gelijktijdige verzoeken.

**Q: Hoe ga ik om met documenten met verschillende paginagroottes?**  
A: Vraag de afmetingen van elke pagina op via `annotator.getPageInfo(pageIndex)` en bereken relatieve coördinaten (bijv. percentages) in plaats van vaste point‑waarden. Dit zorgt ervoor dat annotaties correct verschijnen op A4, Letter en aangepaste paginagroottes.

**Q: Is er een manier om bestaande annotaties uit PDF's te extraheren?**  
A: Ja. Roep `annotator.get()` aan om een collectie van alle annotaties op te halen, en iterereer vervolgens om eigenschappen zoals auteur, commentaar en geometrie te lezen. Dit is nuttig voor migratie‑ of analytics‑scenario's.

**Q: Wat is de beste aanpak voor het omgaan met annotatie‑permissies in multi‑user systemen?**  
A: Implementeer authenticatie op applicatielaag, sla de gebruikers‑ID op met elke `Reply`, en handhaaf bedrijfsregels (bijv. alleen de auteur of een admin kan een reply bewerken of verwijderen). De API zelf handhaaft geen permissies, waardoor je volledige flexibiliteit hebt.

**Q: Hoe optimaliseer ik het geheugenverbruik bij het verwerken van honderden PDF's?**  
A: Gebruik try‑with‑resources voor elk document, verwerk pagina's individueel, en overweeg een begrensde thread‑pool om gelijktijdig geheugenverbruik te beperken. Het monitoren van de JVM‑heap met tools zoals VisualVM helpt je de `-Xmx`‑instelling fijn af te stemmen.

**Laatst bijgewerkt:** 2026-05-16  
**Getest met:** GroupDocs.Annotation 25.2 for Java  
**Auteur:** GroupDocs  

**Aanvullende bronnen**
- [GroupDocs.Annotation voor Java Documentatie](https://docs.groupdocs.com/annotation/java/)
- [Complete API-referentie](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## Gerelateerde tutorials

- [Java PDF Annotatielibrary Tutorial](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Annotatie‑antwoorden verwijderen Java - Beheer antwoorden per ID met GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [PDF‑annotaties bewerken Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)