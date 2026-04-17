---
categories:
- Java Development
date: '2026-03-30'
description: Leer hoe u een doorstreepte annotatie in Java kunt toevoegen met GroupDocs.Annotation.
  Stapsgewijze handleiding met codevoorbeelden, tips voor probleemoplossing en best
  practices voor documentmarkering.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Voeg doorstreepte annotatie toe Java-tutorial met GroupDocs
type: docs
url: /nl/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Voeg doorstreepte annotatie Java toe - Complete GroupDocs-gids

Heb je ooit naar een document gekeken en gedacht: “Ik moet deze tekst doorstrepen, maar ik kan niet zomaar een rode pen pakken”? Je bent niet de enige. Of je nu een documentreview‑systeem bouwt, een bewerkingsworkflow maakt, of gewoon tekst moet markeren voor verwijdering in je Java‑applicatie, **add strikeout annotation java** is een essentiële vaardigheid. In deze tutorial lopen we alles door wat je moet weten om tekstdoorstrepingsfunctionaliteit te implementeren die echt in productie werkt.

## Snelle antwoorden
- **Welke bibliotheek ondersteunt doorstreepte annotaties in Java?** GroupDocs.Annotation for Java  
- **Welk primair trefwoord moet ik targeten voor SEO?** add strikeout annotation java  
- **Heb ik een licentie nodig om de voorbeeldcode uit te voeren?** Een gratis proefversie of tijdelijke licentie werkt voor ontwikkeling; een volledige licentie is vereist voor productie.  
- **Kan ik dit gebruiken met PDF-, DOCX- en PPTX‑bestanden?** Ja – GroupDocs.Annotation ondersteunt alle belangrijke documentformaten.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger (JDK 11+ aanbevolen).

## Wat is add strikeout annotation java?
Een doorstreepte annotatie trekt een lijn door geselecteerde tekst, waardoor visueel wordt aangegeven dat de inhoud moet worden verwijderd of genegeerd. Het is een niet‑destructieve manier om verwijderingen voor te stellen terwijl de oorspronkelijke tekst intact blijft voor audit‑trails of collaboratieve beoordelingen.

## Waarom doorstreepte annotaties gebruiken in Java‑applicaties?
- **Documentreview‑workflows** – reviewers kunnen ongewenste tekst markeren zonder de bron te wijzigen.  
- **Collaboratieve bewerking** – teamleden zien voorgestelde verwijderingen direct.  
- **Juridisch en compliance** – houd een duidelijke audit‑trail van wijzigingen bij.  
- **Contentmigratie** – markeer verouderde secties voordat je inhoud tussen systemen verplaatst.  

## Vereisten en omgeving configuratie
Je hebt het volgende nodig voordat je in de code duikt:

- **Java Development Kit (JDK)** 8+ (JDK 11+ aanbevolen)  
- **Maven of Gradle** voor afhankelijkheidsbeheer  
- **IDE** – IntelliJ IDEA, Eclipse of VS Code met Java‑extensies  
- **GroupDocs.Annotation‑bibliotheek** – we gebruiken versie 25.2 in de voorbeelden  

*Handig om te hebben:* basiskennis van Java‑annotaties en PDF‑verwerking.

## GroupDocs.Annotation instellen voor Java

### Maven‑configuratie die echt werkt
Voeg de repository en afhankelijkheid toe aan je `pom.xml` precies zoals weergegeven:

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

### Je licentie regelen
GroupDocs biedt verschillende licentieopties:

- **Gratis proefversie** – perfect voor testen (geen creditcard vereist)  
- **Tijdelijke licentie** – ideaal voor ontwikkeling en staging  
- **Volledige licentie** – vereist voor productie; zie de [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** Begin met de gratis proefversie om de API te verkennen, schakel vervolgens over op een tijdelijke licentie wanneer je klaar bent om een real‑world functie te bouwen.

### Snelle sanity‑check configuratie
Voer dit minimale programma uit om te verifiëren dat de bibliotheek correct wordt geladen:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Als de console het succesbericht zonder fouten afdrukt, ben je klaar om doorstreepte annotaties toe te voegen.

## Hoe add strikeout annotation java toe te voegen

Hieronder vind je een volledige, productie‑klare implementatie, opgesplitst in duidelijke stappen.

### Stap 1 – Initialiseer de Annotator
Maak een `Annotator`‑instantie die naar het bron‑document wijst:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Waarom dit belangrijk is:** Het gebruik van een absoluut of correct opgeloste relatieve pad voorkomt “file not found”‑exceptions.

### Stap 2 – (Optioneel) Bereid reactie‑commentaren voor
Het toevoegen van reacties maakt de annotatie collaboratief:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Deze commentaren verschijnen wanneer een gebruiker over de doorstreping hovert.

### Stap 3 – Definieer het doorstreepte gebied
Specificeer de rechthoek die de tekst die je wilt doorstrepen omsluit:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Coördinatentip:** Oorsprong (0,0) is de linkerbovenhoek van de pagina; X groeit naar rechts, Y groeit naar beneden. Gebruik een PDF‑viewer die coördinaten toont om deze waarden fijn af te stemmen.

### Stap 4 – Configureer de doorstreepte annotatie
Stel uiterlijk, paginanummer en voeg de commentaren toe:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Kleurnotitie:* `65535` komt overeen met geel in integer RGB‑formaat. Verander de waarde om andere kleuren te gebruiken.

### Stap 5 – Pas de annotatie toe en sla op
Voeg de annotatie toe aan het document en schrijf het uitvoerbestand weg:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Stap 6 – Ruim bronnen op (Kritisch!)
Disposeer altijd de annotator om native bronnen vrij te geven:

```java
if (annotator != null) {
    annotator.dispose();
}
```

In productie, wikkel het gebruik in een try‑with‑resources‑blok of een `try/finally`‑constructie.

## Veelvoorkomende problemen en hoe ze op te lossen

| Probleem | Symptoom | Oplossing |
|----------|----------|-----------|
| **Bestand niet gevonden** | `Annotator` gooit een uitzondering | Gebruik absolute paden, controleer leesrechten, zorg dat geen ander proces het bestand vergrendelt |
| **Verkeerde coördinaten** | Doorstreping verschijnt op een andere plek dan de beoogde tekst | Controleer het coördinatensysteem van de PDF‑viewer; pas de punten dienovereenkomstig aan |
| **Annotatie onzichtbaar** | Geen zichtbare doorstreping na opslaan | Verhoog `opacity` (bijv. `0.9`), controleer `pageNumber` (0‑gebaseerd), zorg dat punten een juiste rechthoek vormen |
| **OutOfMemoryError** | Applicatie crasht bij grote PDF's | Verhoog de JVM‑heap (`-Xmx2048m`), verwerk documenten in batches, roep altijd `dispose()` aan |

## Prestatie‑best practices voor productie

### Geheugenbeheer
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Batch‑verwerkingsstrategie
Wanneer je tientallen of honderden bestanden moet annoteren:

- Verwerk 10‑20 documenten per batch.  
- Log succes/failure voor elk bestand.  
- Initialiseer de `Annotator` opnieuw voor elk document om geheugenlekken te voorkomen.  

### Caching‑tips
- Cache vaak gebruikte documenttemplates.  
- Sla vooraf berekende coördinatenkaarten op voor standaard lay‑outs.  

## Praktijkvoorbeelden

1. **Documentreview‑systemen** – Editors stellen verwijderingen voor zonder het originele contract te wijzigen.  
2. **Juridische amendementen** – Juristen volgen clausuleverwijderingen terwijl de originele bewoording voor audit behouden blijft.  
3. **Academische peer review** – Reviewers markeren secties voor verwijdering en voegen inline commentaren toe.  
4. **Contentmigratie** – Tijdens CMS‑migraties markeren doorstrepingen verouderde tekst die vervangen moet worden.  

## Geavanceerde aanpassing

### Aangepaste styling
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Metadata toevoegen
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Checklist voor probleemoplossing
- ✅ Kun je het bronbestand handmatig openen?  
- ✅ Zijn alle GroupDocs‑afhankelijkheden aanwezig in de classpath?  
- ✅ Vormen de punten een geldige rechthoek?  
- ✅ Is het paginanummer correct (0‑gebaseerd)?  
- ✅ Is er voldoende heap‑geheugen?  
- ✅ Heb je schrijfrechten voor de doelmap?  
- ✅ Wordt het documentformaat ondersteund (PDF, DOCX, PPTX, enz.)?  

## Veelgestelde vragen

**Q: Kan ik GroupDocs.Annotation gebruiken binnen een Spring Boot‑service?**  
A: Ja. Voeg de Maven‑afhankelijkheid toe, injecteer een service‑klasse die de `Annotator` maakt, en beheer de levenscyclus met Spring‑bean‑scopes.

**Q: Welke documentformaten ondersteunen doorstreepte annotaties?**  
A: PDF, DOCX, PPTX, en vele andere formaten ondersteund door GroupDocs.Annotation. PDF biedt de meest precieze coördinatenafhandeling.

**Q: Hoe ga ik om met documenten met verschillende paginagroottes?**  
A: Haal de paginadimensies op via `annotator.getPageInfo(pageNumber)` en schaal je coördinaten dienovereenkomstig.

**Q: Is het mogelijk om een bestaande doorstreepte annotatie te bewerken of te verwijderen?**  
A: Absoluut. Gebruik `annotator.getAnnotations(pageNumber)` om op te halen, vervolgens `annotator.update(updatedAnnotation)` of `annotator.delete(annotationId)`.

**Q: Wat is de prestatie‑impact van het toevoegen van veel annotaties?**  
A: Het toevoegen van honderden annotaties is over het algemeen geen probleem, maar houd het geheugenverbruik in de gaten. Voor zeer grote annotatiesets, overweeg paginering van de weergave of lazy‑loading van annotaties op aanvraag.

## Conclusie
Je hebt nu een volledige, productie‑klare gids voor **add strikeout annotation java** met behulp van GroupDocs.Annotation. Begin met het eenvoudige sanity‑check‑voorbeeld, schaal vervolgens op naar batch‑verwerking, aangepaste styling en metadata‑verrijking. Vergeet niet de coördinaten zorgvuldig te testen, bronnen verantwoord te beheren en het juiste licentiemodel voor je omgeving te kiezen.

Klaar om meer te verkennen? Bekijk andere annotatietypen—highlight, note, image, arrow en watermark—om een volledige document‑samenwerkingssuite te bouwen.

---

**Laatst bijgewerkt:** 2026-03-30  
**Getest met:** GroupDocs.Annotation 25.2 for Java  
**Auteur:** GroupDocs  

**Aanvullende bronnen**
- [GroupDocs Annotation Documentatie](https://docs.groupdocs.com/annotation/java/)
- [API Referentiehandleiding](https://reference.groupdocs.com/annotation/java/)
- [Download nieuwste versie](https://releases.groupdocs.com/annotation/java/)
- [Volledige licentie kopen](https://purchase.groupdocs.com/buy)
- [Gratis proefversie starten](https://releases.groupdocs.com/annotation/java/)
- [Tijdelijke licentie verkrijgen](https://purchase.groupdocs.com/temporary-license/)
- [Community‑ondersteuningsforum](https://forum.groupdocs.com/c/annotation/)