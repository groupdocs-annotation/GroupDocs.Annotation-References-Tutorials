---
categories:
- Java Development
date: '2026-03-30'
description: Naučte se, jak pomocí GroupDocs.Annotation přidat v Javě anotaci typu
  přeškrtnutí. Podrobný návod krok za krokem s ukázkami kódu, tipy na řešení problémů
  a osvědčené postupy pro označování dokumentů.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Přidání přeškrtnuté anotace – Java tutoriál s GroupDocs
type: docs
url: /cs/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Přidání přeškrtnuté anotace Java – Kompletní průvodce GroupDocs

Už jste někdy přemýšleli nad dokumentem a říkali si: „Potřebuji přeškrtnout tento text, ale nemohu jen tak vzít červené pero“? Nejste sami. Ať už vytváříte systém pro revizi dokumentů, navrhujete workflow úprav, nebo jen potřebujete označit text ke smazání ve své Java aplikaci, **add strikeout annotation java** je nezbytná dovednost. V tomto tutoriálu projdeme vše, co potřebujete vědět, abyste implementovali funkci přeškrtnutí textu, která skutečně funguje v produkci.

## Rychlé odpovědi
- **Jaká knihovna podporuje přeškrtnuté anotace v Javě?** GroupDocs.Annotation for Java  
- **Jaké primární klíčové slovo bych měl cílit pro SEO?** add strikeout annotation java  
- **Potřebuji licenci pro spuštění ukázkového kódu?** Bezplatná zkušební verze nebo dočasná licence funguje pro vývoj; pro produkci je vyžadována plná licence.  
- **Mohu to použít s PDF, DOCX a PPTX soubory?** Ano – GroupDocs.Annotation podporuje všechny hlavní formáty dokumentů.  
- **Jaká verze Javy je požadována?** JDK 8 nebo vyšší (doporučeno JDK 11+).  

## Co je add strikeout annotation java?
Přeškrtnutá anotace nakreslí čáru přes vybraný text, vizuálně naznačující, že obsah by měl být odstraněn nebo ignorován. Jedná se o ne‑destruktivní způsob, jak navrhnout smazání, přičemž originální text zůstává zachován pro auditní záznamy nebo kolaborativní revize.

## Proč používat přeškrtnuté anotace v Java aplikacích?
- **Procesy revize dokumentů** – recenzenti mohou označit nechtěný text bez změny zdroje.  
- **Spolupráce při úpravách** – členové týmu okamžitě vidí navrhovaná smazání.  
- **Právní a soulad** – udržujte jasný auditní záznam změn.  
- **Migrace obsahu** – označte zastaralé sekce před přesunem obsahu mezi systémy.  

## Předpoklady a nastavení prostředí
Budete potřebovat následující předtím, než se ponoříte do kódu:

- **Java Development Kit (JDK)** 8+ (JDK 11+ doporučeno)  
- **Maven nebo Gradle** pro správu závislostí  
- **IDE** – IntelliJ IDEA, Eclipse nebo VS Code s rozšířeními pro Javu  
- **GroupDocs.Annotation knihovna** – v příkladech použijeme verzi 25.2  

*Užitečné:* základní znalost Java anotací a práce s PDF.

## Nastavení GroupDocs.Annotation pro Java

### Maven konfigurace, která skutečně funguje
Přidejte repozitář a závislost do vašeho `pom.xml` přesně tak, jak je uvedeno:

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

### Zajištění licence
GroupDocs nabízí několik licenčních možností:

- **Free trial** – ideální pro testování (není vyžadována kreditní karta)  
- **Temporary license** – ideální pro vývoj a testování  
- **Full license** – vyžadována pro produkční použití; viz [stránka nákupu](https://purchase.groupdocs.com/buy)

> **Pro tip:** Začněte s bezplatnou zkušební verzí, abyste prozkoumali API, a poté přejděte na dočasnou licenci, až budete připraveni vytvořit reálnou funkci.

### Rychlé ověření nastavení
Spusťte tento minimální program, abyste ověřili, že se knihovna načte správně:

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

Pokud konzole vypíše zprávu o úspěchu bez chyb, jste připraveni přidávat přeškrtnuté anotace.

## Jak přidat přeškrtnutou anotaci Java

Níže je kompletní, produkčně připravená implementace rozdělená do jasných kroků.

### Krok 1 – Inicializace anotátoru
Vytvořte instanci `Annotator`, která ukazuje na zdrojový dokument:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Proč je to důležité:** Použití absolutní nebo správně rozpoznané relativní cesty zabraňuje výjimkám „soubor nenalezen“.

### Krok 2 – (Volitelné) Připravit odpovědi na komentáře
Přidání odpovědí činí anotaci kolaborativní:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Tyto komentáře se zobrazí, když uživatel najede kurzorem na přeškrtnutí.

### Krok 3 – Definovat oblast přeškrtnutí
Určete obdélník, který obklopuje text, který chcete přeškrtnout:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Tip pro souřadnice:** Počátek (0,0) je levý horní roh stránky; X roste doprava, Y roste dolů. Použijte PDF prohlížeč, který zobrazuje souřadnice, pro doladění těchto hodnot.

### Krok 4 – Konfigurace přeškrtnuté anotace
Nastavte vzhled, číslo stránky a připojte komentáře:

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

*Poznámka o barvě:* `65535` odpovídá žluté v celočíselném RGB formátu. Změňte hodnotu pro použití jiných barev.

### Krok 5 – Aplikovat anotaci a uložit
Přidejte anotaci do dokumentu a zapište výstupní soubor:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Krok 6 – Vyčistit zdroje (kritické!)
Vždy uvolněte anotátor, aby se uvolnily nativní zdroje:

```java
if (annotator != null) {
    annotator.dispose();
}
```

V produkci zabalte použití do bloku try‑with‑resources nebo konstrukce `try/finally`.

## Časté problémy a jak je opravit

| Problém | Symptom | Řešení |
|---------|---------|--------|
| **File Not Found** | `Annotator` vyhodí výjimku | Použijte absolutní cesty, ověřte oprávnění ke čtení, ujistěte se, že žádný jiný proces soubor neblokuje |
| **Wrong Coordinates** | Přeškrtnutí se zobrazuje mimo zamýšlený text | Znovu zkontrolujte souřadnicový systém PDF prohlížeče; podle toho upravte body |
| **Annotation Invisible** | Po uložení není viditelné přeškrtnutí | Zvyšte `opacity` (např. `0.9`), ověřte `pageNumber` (číslování od 0), ujistěte se, že body tvoří správný obdélník |
| **OutOfMemoryError** | Aplikace spadne při velkých PDF | Zvyšte haldu JVM (`-Xmx2048m`), zpracovávejte dokumenty po dávkách, vždy volejte `dispose()` |

## Nejlepší postupy výkonu pro produkci

### Správa paměti
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

### Strategie dávkového zpracování
Když potřebujete anotovat desítky nebo stovky souborů:

- Zpracovávejte 10‑20 dokumentů na dávku.  
- Zaznamenávejte úspěch/neúspěch pro každý soubor.  
- Znovu inicializujte `Annotator` pro každý dokument, aby nedocházelo k únikům paměti.  

### Tipy pro cachování
- Cachujte často používané šablony dokumentů.  
- Ukládejte předem vypočítané mapy souřadnic pro standardní rozvržení.  

## Reálné příklady použití

1. **Systémy revize dokumentů** – Editoři navrhují smazání bez změny původní smlouvy.  
2. **Právní úpravy** – Právníci sledují odstranění klauzulí při zachování původního znění pro audit.  
3. **Akademické recenze** – Recenzenti označují sekce k odstranění a přidávají vložené komentáře.  
4. **Migrace obsahu** – Během migrací CMS přeškrtnutí zvýrazňují zastaralý text, který je třeba nahradit.  

## Pokročilá přizpůsobení

### Vlastní stylování
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Přidání metadat
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Kontrolní seznam pro řešení problémů
- ✅ Můžete otevřít zdrojový soubor ručně?  
- ✅ Jsou všechny GroupDocs závislosti přítomny v classpath?  
- ✅ Tvoří body platný obdélník?  
- ✅ Je číslo stránky správné (0‑based)?  
- ✅ Je dostatek paměti haldy?  
- ✅ Máte oprávnění k zápisu do výstupní složky?  
- ✅ Je formát dokumentu podporován (PDF, DOCX, PPTX, atd.)?  

## Často kladené otázky

**Q: Mohu použít GroupDocs.Annotation uvnitř služby Spring Boot?**  
A: Ano. Přidejte Maven závislost, injektujte servisní třídu, která vytváří `Annotator`, a spravujte její životní cyklus pomocí Spring bean scopes.

**Q: Které formáty dokumentů podporují přeškrtnuté anotace?**  
A: PDF, DOCX, PPTX a mnoho dalších formátů podporovaných GroupDocs.Annotation. PDF nabízí nejpřesnější práci se souřadnicemi.

**Q: Jak zacházet s dokumenty s různými velikostmi stránek?**  
A: Získejte rozměry stránky pomocí `annotator.getPageInfo(pageNumber)` a podle toho škálujte své souřadnice.

**Q: Je možné upravit nebo smazat existující přeškrtnutou anotaci?**  
A: Rozhodně. Použijte `annotator.getAnnotations(pageNumber)` pro načtení, poté `annotator.update(updatedAnnotation)` nebo `annotator.delete(annotationId)`.

**Q: Jaký je dopad na výkon při přidávání mnoha anotací?**  
A: Přidání stovek anotací je obecně v pořádku, ale sledujte využití paměti. Pro velmi velké sady anotací zvažte stránkování zobrazení nebo lazy‑loading anotací na vyžádání.

## Závěr
Nyní máte kompletní, produkčně připravený průvodce k **add strikeout annotation java** pomocí GroupDocs.Annotation. Začněte jednoduchým ověřovacím příkladem, poté rozšiřte na dávkové zpracování, vlastní stylování a obohacení metadat. Pamatujte na pečlivé testování souřadnic, odpovědné řízení zdrojů a výběr správného licenčního modelu pro vaše prostředí.

Připraveni na další průzkum? Prohlédněte si další typy anotací – zvýraznění, poznámku, obrázek, šipku a vodoznak – a vytvořte plnohodnotný balík pro spolupráci na dokumentech.

---

**Poslední aktualizace:** 2026-03-30  
**Testováno s:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Další zdroje**
- [Dokumentace GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Příručka API reference](https://reference.groupdocs.com/annotation/java/)
- [Stáhnout nejnovější verzi](https://releases.groupdocs.com/annotation/java/)
- [Zakoupit plnou licenci](https://purchase.groupdocs.com/buy)
- [Spustit bezplatnou zkušební verzi](https://releases.groupdocs.com/annotation/java/)
- [Získat dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)
- [Komunitní fórum podpory](https://forum.groupdocs.com/c/annotation/)