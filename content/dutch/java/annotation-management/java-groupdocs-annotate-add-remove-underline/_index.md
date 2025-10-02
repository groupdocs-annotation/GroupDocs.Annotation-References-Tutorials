---
"date": "2025-05-06"
"description": "Leer hoe u onderstreepte aantekeningen kunt toevoegen en verwijderen in Java-documenten met GroupDocs.Annotation. Verbeter uw documentbeheer met deze gedetailleerde handleiding."
"title": "Onderstrepingsannotaties toevoegen en verwijderen in Java met behulp van GroupDocs&#58; een uitgebreide handleiding"
"url": "/nl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Java implementeren: onderstrepingsannotaties toevoegen en verwijderen met GroupDocs

## Invoering

Wilt u uw documentbeheersysteem verbeteren door programmatisch annotaties toe te voegen of te verwijderen? Deze tutorial begeleidt u bij het gebruik van de krachtige GroupDocs.Annotation-bibliotheek in Java om onderstreepte annotaties toe te voegen en te verwijderen uit documenten zoals pdf's.

**Wat je leert:**
- Initialiseer de Annotator-klasse.
- Voeg een onderstreepte aantekening met opmerkingen toe met behulp van GroupDocs.Annotation voor Java.
- Verwijder alle aantekeningen uit een document.
- Configureer uw omgeving om GroupDocs.Annotation efficiënt te gebruiken.

Laten we eens kijken hoe deze functionaliteiten in uw projecten kunnen worden benut. Zorg ervoor dat u aan de nodige vereisten voldoet voordat u begint.

## Vereisten

### Vereiste bibliotheken en afhankelijkheden
Om deze tutorial effectief te kunnen volgen, moet u het volgende doen:
- **GroupDocs.Annotatie voor Java**: Versie 25.2 of hoger wordt aanbevolen.
- **Java-ontwikkelingskit (JDK)**: Versie 8 of hoger is vereist.

### Vereisten voor omgevingsinstellingen
Zorg ervoor dat uw ontwikkelomgeving een IDE zoals IntelliJ IDEA of Eclipse en een buildtool zoals Maven bevat.

### Kennisvereisten
Een basiskennis van Java-programmering, met name het werken met bibliotheken via Maven, is nuttig.

## GroupDocs.Annotation instellen voor Java

Om GroupDocs.Annotation in uw Java-projecten te gebruiken, volgt u deze installatiestappen:

**Maven-configuratie:**
Voeg de volgende configuratie toe aan uw `pom.xml` bestand om GroupDocs.Annotation te downloaden en te integreren.

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

**Licentieverwerving:**
Begin met het downloaden van een gratis proefversie of neem een tijdelijke licentie van GroupDocs om alle mogelijkheden van hun bibliotheek te ontdekken. Voor productiegebruik is de aanschaf van een licentie vereist.

## Implementatiegids

### Functie 1: Annotator initialiseren en onderstrepingsannotatie toevoegen

In deze sectie wordt u begeleid bij het initialiseren van de `Annotator` klasse en het toevoegen van een onderstreepte aantekening aan uw document.

#### Overzicht
Het toevoegen van annotaties helpt om specifieke delen van een document te markeren. Hier richten we ons op het onderstrepen van tekst met opmerkingen ter verduidelijking of feedback.

#### Stapsgewijze implementatie

**1. Initialiseer Annotator**
Maak een `Annotator` object en laad uw PDF-bestand.

```java
import com.groupdocs.annotation.Annotator;

// Laad het document dat u wilt annoteren
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Maak opmerkingen met antwoorden**
Definieer opmerkingen die bij de onderstreepte aantekening horen.

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

**3. Definieer punten voor onderstrepingsannotatie**
Stel coördinaten in om te bepalen waar de onderstreping moet verschijnen.

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

**4. Onderstrepingsannotatie maken en configureren**
Maak de onderstrepingsannotatie en stel de eigenschappen in, zoals kleur, dekking en opmerkingen.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Geel in ARGB-formaat
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Sla het geannoteerde document op**
Sla uw wijzigingen op in een nieuw bestand.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Tips voor probleemoplossing
- Zorg ervoor dat alle coördinaten voor punten binnen de documentgrenzen vallen.
- Controleer of de `outputPath` map bestaat en schrijfbaar is.

### Functie 2: Document opslaan zonder aantekeningen

In dit gedeelte wordt beschreven hoe u alle aantekeningen uit een eerder geannoteerd document verwijdert.

#### Overzicht
Mogelijk moet u een schone versie van uw document opslaan zonder aantekeningen, zodat u het kunt delen of archiveren.

#### Stapsgewijze implementatie

**1. Initialiseer Annotator met het geannoteerde document**
Laad het document met bestaande annotaties.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configureer opslagopties om aantekeningen te verwijderen**
Geef aan dat er geen annotaties in het uitvoerbestand moeten worden opgeslagen.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Sla het document op zonder aantekeningen**
Definieer het pad voor het opgeschoonde document en sla het op.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Praktische toepassingen

Hier zijn enkele praktijkscenario's waarin deze functies nuttig kunnen zijn:
1. **Documentbeoordeling**: Het markeren en becommentariëren van delen van een contract of rapport ter beoordeling.
2. **Educatieve hulpmiddelen**: Aantekeningen of correcties in leerboeken aanbrengen voor studenten.
3. **Samenwerkend bewerken**: Geannoteerde concepten delen met teamleden voor feedback.
4. **Juridische documentatie**: Het onderstrepen van belangrijke clausules in juridische documenten tijdens discussies.
5. **Marketingmaterialen**: Belangrijke informatie benadrukken in brochures voordat deze worden verspreid.

## Prestatieoverwegingen
Houd bij het werken met GroupDocs.Annotation rekening met de volgende tips om de prestaties te optimaliseren:
- **Geheugenbeheer**: Op de juiste manier weggooien `Annotator` objecten om bronnen vrij te maken.
- **Batchverwerking**:Als u meerdere documenten van aantekeningen voorziet, kunt u deze in batches verwerken om de systeembelasting effectief te beheren.
- **Toewijzing van middelen**: Zorg ervoor dat uw omgeving voldoende geheugen en verwerkingskracht heeft om grote bestanden te verwerken.

## Conclusie
Je hebt geleerd hoe je onderstreepte annotaties kunt toevoegen en verwijderen met GroupDocs.Annotation voor Java. Deze tutorial behandelde het initialiseren van de Annotator-klasse, het configureren van annotaties met opmerkingen en het opslaan van documenten zonder annotaties. 

Als u de mogelijkheden verder wilt verkennen, kunt u overwegen deze functies te integreren in uw bestaande documentbeheersystemen of te experimenteren met andere annotatietypen die GroupDocs biedt.

## FAQ-sectie
1. **Hoe configureer ik meerdere onderstrepingsannotaties in één keer?**
   - Meerdere maken `UnderlineAnnotation` objecten en voeg ze sequentieel toe met behulp van de `annotator.add()` methode.
2. **Kan ik afbeeldingen in PDF's annoteren met deze bibliotheek?**
   - Ja, GroupDocs.Annotation ondersteunt het annoteren van afbeeldingen in documenten zoals PDF's.
3. **Welke bestandsformaten ondersteunt GroupDocs.Annotation?**
   - Het ondersteunt verschillende documentformaten, waaronder PDF, Word, Excel en meer.