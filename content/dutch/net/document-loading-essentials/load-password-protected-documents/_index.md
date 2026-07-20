---
categories:
- Document Security
date: '2026-07-20'
description: Annoteer wachtwoordbeveiligde PDF veilig met GroupDocs.Annotation voor
  .NET. Volg stap‑voor‑stap instructies om versleutelde bestanden te laden, te annoteren
  en veilig op te slaan.
keywords:
- annotate password protected pdf
- real time pdf collaboration
- groupdocs annotation .net
- secure pdf annotation
lastmod: '2026-07-20'
linktitle: Laad wachtwoordbeveiligde documenten
og_description: Annoteer wachtwoordbeveiligde PDF met GroupDocs.Annotation voor .NET,
  waarmee veilige realtime samenwerking mogelijk wordt. Leer hoe je versleutelde documenten
  kunt laden, annoteren en efficiënt opslaan.
og_image_alt: Guide showing how to annotate password protected PDF using GroupDocs.Annotation
  in .NET
og_title: Annoteren van wachtwoordbeveiligde PDF met GroupDocs.Annotation
schemas:
- author: GroupDocs
  dateModified: '2026-07-20'
  description: Annotate password protected PDF securely with GroupDocs.Annotation
    for .NET. Follow step‑by‑step instructions to load, annotate, and save encrypted
    files safely.
  headline: Annotate Password Protected PDF with GroupDocs.Annotation
  type: TechArticle
- description: Annotate password protected PDF securely with GroupDocs.Annotation
    for .NET. Follow step‑by‑step instructions to load, annotate, and save encrypted
    files safely.
  name: Annotate Password Protected PDF with GroupDocs.Annotation
  steps:
  - name: Configure Output Path and Load Options
    text: 'LoadOptions specifies how a document should be opened, including password
      for encrypted files. This first step is more important than it might initially
      appear. Here''s what''s happening: **Output Path Configuration**: We''re defining
      where the annotated document will be saved. The `Path.Combine` metho'
  - name: Initialize the Annotator with Security Context
    text: 'Annotator is the main class that handles loading, annotating, and saving
      documents in GroupDocs.Annotation. This step creates the core annotation object,
      but there''s more happening under the hood than meets the eye: **Resource Management**:
      The `using` statement ensures that the `Annotator` object i'
  - name: Create and Configure Annotations
    text: 'AreaAnnotation represents a rectangular highlight annotation that can be
      placed on a page. Here''s where we actually create the annotation that will
      be applied to our protected document: **Annotation Type Selection**: We''re
      using an `AreaAnnotation`, which creates a rectangular highlight over a speci'
  - name: Save the Annotated Document Securely
    text: 'Saving an annotated password‑protected document maintains the original
      security settings. This seemingly simple line of code handles several complex
      operations: **Encryption Preservation**: When saving an annotated password‑protected
      document, GroupDocs.Annotation maintains the original security set'
  - name: Provide User Feedback
    text: 'While this might seem like a minor detail, providing clear feedback to
      users is essential for a good user experience: **Success Confirmation**: Users
      need to know that their operation completed successfully, especially when working
      with sensitive documents. **File Location**: By displaying the exact'
  type: HowTo
- questions:
  - answer: Yes, it supports over 30 formats—including PDF, DOCX, XLSX, PPTX, and
      image files—and handles password protection consistently across all of them.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Absolutely. You can control color, opacity, border style, font, and size
      for each annotation type, allowing you to match your application's branding
      or highlight specific review notes.
    question: Can I customize the appearance of annotations created with GroupDocs.Annotation
      for .NET?
  - answer: Yes, you can download a free trial version of GroupDocs.Annotation for
      .NET from [here](https://releases.groupdocs.com/). The trial version allows
      you to evaluate the product's full functionality, including password‑protected
      document handling, before making a purchase.
    question: Is there a trial version available for GroupDocs.Annotation for .NET?
  - answer: If you have any questions or encounter issues, you can visit the support
      forum [here](https://forum.groupdocs.com/c/annotation/10) to seek assistance
      from the community and the GroupDocs support team.
    question: How can I get support for GroupDocs.Annotation for .NET?
  - answer: Yes, GroupDocs.Annotation integrates with real‑time collaboration solutions,
      enabling multiple users to view and annotate the same encrypted PDF simultaneously
      while preserving security.
    question: Does the library support real‑time PDF collaboration?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- password-protection
- document-annotation
- security
- authentication
title: Annoteren van wachtwoordbeveiligde PDF met GroupDocs.Annotation
type: docs
url: /nl/net/document-loading-essentials/load-password-protected-documents/
weight: 17
---

# Annoteren van wachtwoordbeveiligde PDF

Werken met gevoelige documenten vereist meer dan alleen basisannotatie‑mogelijkheden—je hebt robuuste beveiligingsmaatregelen nodig die de functionaliteit niet in gevaar brengen. Als je te maken hebt met vertrouwelijke contracten, juridische documenten of eigendomsrechten, ben je waarschijnlijk de uitdaging tegengekomen om wachtwoordbeveiligde bestanden te annoteren terwijl je de beveiligingsintegriteit behoudt.

GroupDocs.Annotation for .NET maakt programmatische annotatie van vele documentformaten mogelijk, inclusief versleutelde PDF's, binnen .NET‑applicaties. Of je nu een documentbeheersysteem, samenwerkingsplatform of compliance‑tool bouwt, deze gids laat zien hoe je wachtwoordbeveiligde PDF's veilig kunt laden en annoteren zonder gevoelige informatie bloot te stellen.

Het beste? Je kunt enterprise‑niveau beveiliging behouden terwijl je realtime samenwerking en documentreviewprocessen mogelijk maakt. Laten we duiken in hoe je deze krachtige combinatie van beveiliging en functionaliteit kunt implementeren in je .NET‑applicaties.

## Snelle Antwoorden
- **Welke bibliotheek behandelt PDF-annotatie?** GroupDocs.Annotation for .NET.
- **Kan ik versleutelde PDF's annoteren?** Ja—geef simpelweg het wachtwoord op via `LoadOptions`.
- **Wordt realtime samenwerking ondersteund?** De bibliotheek werkt met realtime PDF‑samenwerkingsplatformen.
- **Heb ik een licentie nodig?** Een geldige GroupDocs.Annotation‑licentie is vereist voor productie.
- **Welke .NET‑versies zijn compatibel?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.

## Wat is GroupDocs.Annotation voor .NET?
GroupDocs.Annotation voor .NET is een bibliotheek die programmatische annotatie van vele documentformaten mogelijk maakt, inclusief versleutelde PDF's, binnen .NET‑applicaties. Het biedt een uniforme API voor het toevoegen van markeringen, opmerkingen, stempels en aangepaste vormen, terwijl de originele bestandsbeveiliging behouden blijft.

## Waarom annotatie van wachtwoordbeveiligde documenten belangrijk is?
Het laden, annoteren en opslaan van versleutelde PDF's zonder de encryptie te breken is essentieel voor compliance‑gedreven industrieën. Het zorgt ervoor dat vertrouwelijke informatie gedurende de hele levenscyclus beschermd blijft, voldoet aan audit‑vereisten, en stelt gedistribueerde teams in staat samen te werken zonder ruwe gegevens bloot te stellen. In gereguleerde sectoren kan het behouden van encryptie terwijl review‑notities worden toegevoegd, de compliance‑kosten met tot 30 % verlagen en handmatige her‑encryptiestappen verminderen.

## Voorvereisten

Voordat je duikt in het annoteren van wachtwoordbeveiligde PDF's met GroupDocs.Annotation voor .NET, laten we ervoor zorgen dat alles correct is ingesteld. Maak je geen zorgen—het installatieproces is eenvoudig, en ik zal je door elke vereiste leiden.

### 1. Installeer GroupDocs.Annotation voor .NET

Allereerst moet je de GroupDocs.Annotation voor .NET‑bibliotheek downloaden en installeren. Je kunt de downloadlink vinden [hier](https://releases.groupdocs.com/annotation/net/). Voor andere releases, bezoek de hoofd‑releasespagina [hier](https://releases.groupdocs.com/).

**Pro Tip**: Als je NuGet Package Manager gebruikt (wat ik ten zeerste aanbeveel), kun je het direct via Visual Studio installeren of via de Package Manager Console met een eenvoudige opdracht. Deze aanpak zorgt ervoor dat je altijd de nieuwste compatibele versie krijgt en automatische afhankelijkheids‑resolutie.

### 2. Verkrijg een licentie of gebruik een tijdelijke licentie

GroupDocs.Annotation voor .NET vereist een geldige licentie om de volledige functionaliteit te ontgrendelen, vooral bij het werken met wachtwoordbeveiligde documenten. Je hebt hier twee opties:

- **Koop een volledige licentie** via de GroupDocs‑website [hier](https://purchase.groupdocs.com/buy) voor productiegebruik
- **Vraag een tijdelijke licentie** aan voor evaluatiedoeleinden [hier](https://purchase.groupdocs.com/temporary-license/)

**Belangrijke Opmerking**: De tijdelijke licentie is perfect voor test‑ en ontwikkelingsfasen. Het geeft je toegang tot alle functies zonder functionele beperkingen, zodat je de bibliotheek grondig kunt evalueren voordat je een aankoopbeslissing neemt.

### 3. Vertrouwdheid met C# en .NET‑ontwikkeling

Een basisbegrip van de programmeertaal C# en .NET‑ontwikkeling is essentieel om GroupDocs.Annotation voor .NET effectief te gebruiken. Als je deze gids leest, heb je waarschijnlijk al de benodigde achtergrond, maar dit is waar je vertrouwd mee moet zijn:

- Basis C#‑syntaxis en object‑georiënteerde programmeerconcepten
- Begrip van `using`‑statements en disposable‑objecten
- Vertrouwdheid met bestands‑I/O‑operaties
- Basiskennis van exception‑handling

Als je nieuw bent in C# of .NET, laat je dan niet ontmoedigen! De codevoorbeelden in deze gids zijn goed gedocumenteerd en stap‑voor‑stap uitgelegd.

## Importeer Vereiste Namespaces

Voordat je begint met het annoteren van documenten, zorg ervoor dat je de vereiste namespaces importeert in je C#‑project. Deze stap is cruciaal omdat het je naadloos toegang geeft tot alle klassen en methoden die GroupDocs.Annotation voor .NET biedt.

`System` en `System.IO` bieden basis‑.NET‑functionaliteit voor bestandsoperaties.  
`GroupDocs.Annotation.Models` bevat kern‑annotatiemodelklassen.  
`GroupDocs.Annotation.Models.AnnotationModels` huisvest specifieke annotatietypen zoals `AreaAnnotation`.  
`GroupDocs.Annotation.Options` biedt configuratie‑opties voor het laden en verwerken van documenten.

```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## Stapsgewijze Implementatiegids

Nu de vereisten op hun plaats zijn en de benodigde namespaces zijn geïmporteerd, lopen we de daadwerkelijke implementatie door. We behandelen vijf hoofd stappen, waarbij we zowel het **hoe** als het **waarom** achter elke beslissing uitleggen.

### Stap 1: Configureer Uitvoerpad en Load‑Options

LoadOptions specificeert hoe een document moet worden geopend, inclusief wachtwoord voor versleutelde bestanden.

```csharp
// Define where the annotated file will be saved
string outputPath = Path.Combine(Environment.CurrentDirectory, "AnnotatedDocument.pdf");

// Set up load options with the document password
var loadOptions = new LoadOptions { Password = "yourPasswordHere" };
```

Deze eerste stap is belangrijker dan het op het eerste gezicht lijkt. Dit gebeurt:

**Uitvoerpadconfiguratie**: We definiëren waar het geannoteerde document wordt opgeslagen. De `Path.Combine`‑methode zorgt voor cross‑platform compatibiliteit (werkt op Windows, Linux en macOS). Door `Path.GetExtension` te gebruiken, behouden we automatisch het originele bestandsformaat—of het nu PDF, DOCX of een ander ondersteund formaat is.

**Load‑Options‑instelling**: Het `LoadOptions`‑object is waar de magie gebeurt voor wachtwoordbeveiligde documenten. De wachtwoord‑eigenschap vertelt GroupDocs.Annotation hoe het document moet worden gedecodeerd en de inhoud moet benaderen.

**Beveiligingsoverweging**: In productie‑applicaties moet je nooit wachtwoorden hard‑coderen zoals in dit voorbeeld. Haal wachtwoorden in plaats daarvan op uit veilige opslag, omgevingsvariabelen, of gebruikersinvoer met juiste validatie.

### Stap 2: Initialiseert de Annotator met Beveiligingscontext

Annotator is de hoofdklasse die het laden, annoteren en opslaan van documenten in GroupDocs.Annotation afhandelt.

```csharp
using (var annotator = new Annotator("protected.pdf", loadOptions))
{
    // Annotation logic will go here
}
```

Deze stap creëert het kern‑annotatie‑object, maar er gebeurt meer onder de motorkap dan je zou denken:

**Resourcebeheer**: De `using`‑statement zorgt ervoor dat het `Annotator`‑object correct wordt vrijgegeven na gebruik. Dit is cruciaal bij wachtwoordbeveiligde documenten omdat het ervoor zorgt dat gedecrypteerde inhoud niet langer in het geheugen blijft dan nodig.

**Documentladen**: Wanneer je het pad van het beveiligde document en de load‑options doorgeeft, probeert GroupDocs.Annotation onmiddellijk het document te decoderen en in het geheugen te laden. Als het wachtwoord onjuist is, krijg je op dit punt een uitzondering—wat eigenlijk goed is voor beveiligingsvalidatie.

**Geheugensecurity**: De bibliotheek behandelt de gedecrypteerde documentinhoud op een veilige manier en wist automatisch gevoelige gegevens uit het geheugen wanneer het object wordt vrijgegeven.

### Stap 3: Maak en Configureer Annotaties

AreaAnnotation vertegenwoordigt een rechthoekige markeer‑annotatie die op een pagina kan worden geplaatst.

```csharp
var area = new AreaAnnotation
{
    PageNumber = 1,
    Rectangle = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535 // Bright yellow
};
annotator.Add(area);
```

Hier maken we daadwerkelijk de annotatie die op ons beveiligde document wordt toegepast:

**Selectie van Annotatietype**: We gebruiken een `AreaAnnotation`, die een rechthoekige markering over een specifiek gebied van het document creëert. Dit is slechts één van de vele beschikbare annotatietypen—je kunt ook tekstannotaties, sticky notes, pijlen of aangepaste vormen gebruiken.

**Positionering en Grootte**: De parameters `Rectangle(100, 100, 100, 100)` definiëren de positie en grootte van de annotatie:
- Eerste twee getallen (100, 100): X‑ en Y‑coördinaten van de linkerbovenhoek
- Laatste twee getallen (100, 100): Breedte en hoogte van de annotatie

**Visuele Styling**: De eigenschap `BackgroundColor` gebruikt een numerieke kleurwaarde. In dit geval vertegenwoordigt 65535 een felgele kleur. Je kunt dit aanpassen aan de branding van je applicatie of gebruikersvoorkeuren.

**Toevoegen aan Document**: De methode `annotator.Add(area)` past de annotatie toe op het geladen document. Je kunt meerdere annotaties achter elkaar toevoegen indien nodig.

### Stap 4: Sla het Geannoteerde Document Veilig op

Het opslaan van een geannoteerd wachtwoordbeveiligd document behoudt de oorspronkelijke beveiligingsinstellingen.

```csharp
annotator.Save(outputPath);
```

Deze ogenschijnlijk eenvoudige regel code behandelt verschillende complexe bewerkingen:

**Behoud van Encryptie**: Bij het opslaan van een geannoteerd wachtwoordbeveiligd document behoudt GroupDocs.Annotation de oorspronkelijke beveiligingsinstellingen. Het uitvoerdocument blijft versleuteld met dezelfde wachtwoordbeveiliging.

**Metadata‑integratie**: Annotaties worden direct in de documentstructuur ingebed, niet opgeslagen als aparte overlay‑bestanden. Dit zorgt ervoor dat annotaties behouden blijven, zelfs als het document wordt verplaatst of gedeeld.

**Formaatconsistentie**: Het opgeslagen document behoudt zijn oorspronkelijke formaat terwijl de nieuwe annotaties worden geïntegreerd. PDF‑bestanden blijven PDF's, Word‑documenten blijven DOCX, enzovoort.

### Stap 5: Geef Gebruikersfeedback

Hoewel dit misschien een klein detail lijkt, is het geven van duidelijke feedback aan gebruikers essentieel voor een goede gebruikerservaring:

```csharp
Console.WriteLine($"Document annotated successfully. Saved to: {outputPath}");
```

**Bevestiging van Succes**: Gebruikers moeten weten dat hun bewerking succesvol is afgerond, vooral bij het werken met gevoelige documenten.

**Bestandslocatie**: Door het exacte uitvoerpad weer te geven, weten gebruikers precies waar ze hun geannoteerde document kunnen vinden.

**Foutafhandeling**: In productie‑applicaties moet je dit hele proces omhullen met try‑catch‑blokken om mogelijke uitzonderingen op een nette manier af te handelen.

## Beveiligingsbest Practices

Bij het werken met wachtwoordbeveiligde documenten moet beveiliging je hoogste prioriteit hebben. Hier zijn essentiële praktijken om te implementeren:

### Veilige Wachtwoordafhandeling
- Gebruik veilige configuratie‑beheer
- Implementeer juiste encryptie voor opgeslagen referenties  
- Overweeg het gebruik van Windows Credential Store of vergelijkbare veilige opslagmechanismen
- Valideer wachtwoordsterkte en implementeer juiste authenticatiestromen

### Geheugenbeheer
Wachtwoordbeveiligde documenten bevatten gevoelige gegevens die zorgvuldig moeten worden behandeld:
- Gebruik altijd `using`‑statements om correcte resource‑vrijgave te garanderen
- Vermijd het langer dan nodig in het geheugen houden van gedecrypteerde inhoud
- Overweeg het implementeren van geheugen‑scrubbing technieken voor zeer gevoelige applicaties

### Toegangscontrole
Implementeer juiste autorisatiecontroles:
- Verifieer gebruikersrechten voordat documenttoegang wordt verleend
- Log alle pogingen tot documenttoegang voor auditdoeleinden
- Overweeg het implementeren van role‑based access control (RBAC)

## Veelvoorkomende Problemen en Probleemoplossing

Werken met wachtwoordbeveiligde documenten kan unieke uitdagingen met zich meebrengen. Hier zijn de meest voorkomende problemen die je kunt tegenkomen en hoe je ze oplost:

### Authenticatiefouten
**Probleem**: “Invalid password” of authenticatiefouten  
**Oplossingen**:
- Controleer of het wachtwoord correct is en niet is gewijzigd
- Controleer op coderingsproblemen (vooral bij speciale tekens)
- Zorg ervoor dat het document niet corrupt is of een niet‑ondersteunde encryptie gebruikt

### Prestatieoverwegingen
**Probleem**: Trage laadtijden voor versleutelde documenten  
**Oplossingen**:
- Cache gedecrypteerde inhoud wanneer passend (met juiste beveiligingsmaatregelen)
- Implementeer asynchrone lading voor grote documenten
- Optimaliseer geheugengebruik door resources tijdig vrij te geven

### Compatibiliteitsproblemen
**Probleem**: Bepaalde documenttypes of encryptiemethoden worden niet ondersteund  
**Oplossingen**:
- Controleer de GroupDocs.Annotation‑documentatie voor ondersteunde formaten
- Werk bij naar de nieuwste bibliotheekversie voor verbeterde compatibiliteit
- Overweeg documentconversie voor niet‑ondersteunde encryptiemethoden

## Praktijkvoorbeelden van Implementatie

Inzicht in wanneer en hoe je wachtwoordbeveiligde PDF‑annotatie in echte applicaties gebruikt, kan je helpen betere architecturale beslissingen te nemen:

### Juridische Documentreview
Advocatenkantoren moeten vaak samenwerken aan vertrouwelijke zaakbestanden terwijl ze het advocaat‑cliënt‑privilege behouden. Annotaties stellen teamleden in staat opmerkingen en feedback toe te voegen zonder de documentbeveiliging in gevaar te brengen.

### Gezondheidszorg Compliance
HIPAA‑compliant applicaties vereisen dat annotaties op patiëntendocumenten versleuteld blijven. GroupDocs.Annotation zorgt ervoor dat medische dossiers gedurende het review‑proces beschermd blijven.

### Financiële Diensten
Bank- en investeringsbedrijven gebruiken wachtwoordbeveiligde annotaties voor gevoelige financiële documenten, waardoor regelgeving wordt nageleefd terwijl noodzakelijke samenwerking mogelijk wordt gemaakt.

## Tips voor Prestatie‑optimalisatie
Om de beste prestaties te behalen bij het werken met wachtwoordbeveiligde documenten:
1. **Batchverwerking**: Bij het annoteren van meerdere beveiligde documenten, hergebruik de `Annotator`‑instance waar mogelijk.
2. **Geheugenbeheer**: Houd het geheugengebruik in de gaten, vooral bij grote documenten.
3. **Asynchrone Operaties**: Overweeg het implementeren van async/await‑patronen voor een betere gebruikerservaring.
4. **Caching‑strategie**: Voor vaak geraadpleegde documenten, implementeer veilige caching‑mechanismen.

## Conclusie

Wachtwoordbeveiligde PDF‑annotatie met GroupDocs.Annotation voor .NET biedt de perfecte balans tussen beveiliging en functionaliteit. Door de implementatiegids en beveiligingsbest practices uit dit artikel te volgen, kun je robuuste applicaties bouwen die gevoelige documenten verwerken terwijl ze effectieve samenwerking mogelijk maken.

De belangrijkste conclusie is dat je geen concessies aan beveiliging hoeft te doen om krachtige annotatiefuncties mogelijk te maken. Met een juiste implementatie kunnen je applicaties enterprise‑niveau beveiliging behouden en gebruikers de samenwerkings‑tools bieden die ze nodig hebben.

Of je nu een documentbeheersysteem, compliance‑platform of samenwerkingswerkruimte bouwt, GroupDocs.Annotation voor .NET biedt je de basis om veilige, functie‑rijke oplossingen te creëren die je gebruikers zullen waarderen.

Vergeet niet je implementatie grondig te testen met verschillende documenttypes en encryptiemethoden om compatibiliteit met je specifieke use‑cases te waarborgen. De investering in een juiste setup en beveiligingsmaatregelen zal zich uitbetalen in gebruikersvertrouwen en applicatiebetrouwbaarheid.

## Veelgestelde Vragen

**Q: Is GroupDocs.Annotation for .NET compatibel met alle documentformaten?**  
A: Ja, het ondersteunt meer dan 30 formaten—waaronder PDF, DOCX, XLSX, PPTX en afbeeldingsbestanden—en behandelt wachtwoordbeveiliging consequent voor al deze formaten.

**Q: Kan ik het uiterlijk van annotaties die met GroupDocs.Annotation for .NET zijn gemaakt aanpassen?**  
A: Absoluut. Je kunt kleur, doorzichtigheid, randstijl, lettertype en grootte voor elk annotatietype regelen, zodat je de branding van je applicatie kunt matchen of specifieke review‑notities kunt benadrukken.

**Q: Is er een proefversie beschikbaar voor GroupDocs.Annotation for .NET?**  
A: Ja, je kunt een gratis proefversie van GroupDocs.Annotation for .NET downloaden van [here](https://releases.groupdocs.com/). De proefversie stelt je in staat de volledige functionaliteit te evalueren, inclusief het verwerken van wachtwoordbeveiligde documenten, voordat je een aankoop doet.

**Q: Hoe kan ik ondersteuning krijgen voor GroupDocs.Annotation for .NET?**  
A: Als je vragen hebt of problemen ondervindt, kun je het supportforum bezoeken [here](https://forum.groupdocs.com/c/annotation/10) om hulp te zoeken bij de community en het GroupDocs‑supportteam.

**Q: Ondersteunt de bibliotheek realtime PDF‑samenwerking?**  
A: Ja, GroupDocs.Annotation integreert met realtime‑samenwerkingsoplossingen, waardoor meerdere gebruikers hetzelfde versleutelde PDF‑document gelijktijdig kunnen bekijken en annoteren terwijl de beveiliging behouden blijft.

---

**Laatst bijgewerkt:** 2026-07-20  
**Getest met:** GroupDocs.Annotation 23.12 for .NET  
**Auteur:** GroupDocs  

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
```

```csharp
using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
```

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```

```csharp
annotator.Save(outputPath);
```

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Gerelateerde Tutorials

- [Hoe Documenten Laden .NET - Complete GroupDocs.Annotation Tutorial](/annotation/net/document-loading/)
- [Hoe Geannoteerde Documenten Opslaan in .NET - Complete GroupDocs.Annotation Gids](/annotation/net/annotation-management/mastering-document-annotation-dotnet-groupdocs/)
- [PDF Annoteren vanaf URL C# - GroupDocs.Annotation Tutorial](/annotation/net/annotation-management/annotate-pdfs-online-groupdocs-annotation-net/)