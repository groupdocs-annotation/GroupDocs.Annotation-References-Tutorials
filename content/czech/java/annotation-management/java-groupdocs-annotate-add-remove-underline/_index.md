---
"date": "2025-05-06"
"description": "Naučte se, jak přidávat a odebírat podtržené anotace v dokumentech Java pomocí GroupDocs.Annotation. Vylepšete si správu dokumentů s tímto podrobným průvodcem."
"title": "Přidání a odebrání podtržených anotací v Javě pomocí GroupDocs – Komplexní průvodce"
"url": "/cs/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Jak implementovat Javu: Přidání a odebrání podtržených anotací pomocí GroupDocs

## Zavedení

Vylepšujete svůj systém správy dokumentů programově přidáváním nebo odebíráním anotací? Tento tutoriál vás provede používáním výkonné knihovny GroupDocs.Annotation v Javě k přidávání a odebírání podtržených anotací z dokumentů, jako jsou PDF.

**Co se naučíte:**
- Inicializujte třídu Annotator.
- Přidejte podtrženou anotaci s komentáři pomocí GroupDocs.Annotation pro Javu.
- Odebrání všech anotací z dokumentu.
- Nakonfigurujte si prostředí tak, aby efektivně používalo GroupDocs.Annotation.

Pojďme se podívat, jak lze tyto funkce využít ve vašich projektech. Než začnete, ujistěte se, že máte splněny nezbytné předpoklady.

## Předpoklady

### Požadované knihovny a závislosti
Abyste mohli tento tutoriál efektivně sledovat, ujistěte se, že máte:
- **GroupDocs.Annotation pro Javu**Doporučuje se verze 25.2 nebo novější.
- **Vývojová sada pro Javu (JDK)**Je vyžadována verze 8 nebo vyšší.

### Požadavky na nastavení prostředí
Ujistěte se, že vaše vývojové prostředí obsahuje IDE, jako je IntelliJ IDEA nebo Eclipse, a nástroj pro sestavení, jako je Maven.

### Předpoklady znalostí
Základní znalost programování v Javě, zejména práce s knihovnami přes Maven, bude výhodou.

## Nastavení GroupDocs.Annotation pro Javu

Chcete-li začít používat GroupDocs.Annotation ve svých projektech Java, postupujte podle těchto kroků nastavení:

**Konfigurace Mavenu:**
Přidejte následující konfiguraci do svého `pom.xml` soubor pro stažení a integraci GroupDocs.Annotation.

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

**Získání licence:**
Začněte stažením bezplatné zkušební verze nebo získáním dočasné licence od GroupDocs, abyste si mohli prozkoumat všechny možnosti jejich knihovny. Pro produkční použití je nutné zakoupit licenci.

## Průvodce implementací

### Funkce 1: Inicializace anotátoru a přidání podtržené anotace

Tato část vás provede inicializací `Annotator` třídu a přidání podtržené anotace do dokumentu.

#### Přehled
Přidávání anotací pomáhá zvýraznit konkrétní části dokumentu. Zde se zaměřujeme na podtržení textu s komentáři pro objasnění nebo zpětnou vazbu.

#### Postupná implementace

**1. Inicializace anotátoru**
Vytvořte `Annotator` objekt a načtěte soubor PDF.

```java
import com.groupdocs.annotation.Annotator;

// Vložte dokument, který chcete anotovat
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Vytvořte komentáře s odpověďmi**
Definujte komentáře spojené s podtrženou anotací.

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

**3. Definujte body pro podtrženou anotaci**
Nastavte souřadnice pro určení místa, kde se má podtržení zobrazit.

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

**4. Vytvořte a nakonfigurujte podtrženou anotaci**
Vytvořte podtrženou anotaci a nastavte její vlastnosti, jako je barva, krytí a komentáře.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Žlutá ve formátu ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Uložte anotovaný dokument**
Uložte změny do nového souboru.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Tipy pro řešení problémů
- Ujistěte se, že všechny souřadnice bodů jsou v rámci hranic dokumentu.
- Ověřte, že `outputPath` Adresář existuje a je zapisovatelný.

### Funkce 2: Uložení dokumentu bez anotací

Tato část popisuje, jak odstranit všechny anotace z dříve anotovaného dokumentu.

#### Přehled
Pro účely sdílení nebo archivace může být nutné uložit čistou verzi dokumentu bez jakýchkoli poznámek.

#### Postupná implementace

**1. Inicializace anotátoru s anotovaným dokumentem**
Načtěte dokument, který obsahuje existující anotace.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Konfigurace možností ukládání pro odstranění anotací**
Určete, že do výstupního souboru nemají být ukládány žádné anotace.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Uložte dokument bez anotací**
Definujte cestu pro vyčištěný dokument a uložte jej.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Praktické aplikace

Zde je několik reálných scénářů, kde mohou být tyto funkce prospěšné:
1. **Kontrola dokumentů**Zvýraznění a komentování částí smlouvy nebo zprávy k přezkoumání.
2. **Vzdělávací nástroje**Anotace učebnic s poznámkami nebo opravami pro studenty.
3. **Kolaborativní editace**Sdílení anotovaných návrhů mezi členy týmu za účelem zpětné vazby.
4. **Právní dokumentace**Podtrhávání klíčových ustanovení v právních dokumentech během diskusí.
5. **Marketingové materiály**Zvýraznění důležitých informací v brožurách před distribucí.

## Úvahy o výkonu
Při práci s GroupDocs.Annotation zvažte tyto tipy pro optimalizaci výkonu:
- **Správa paměti**Řádně zlikvidujte `Annotator` objekty k uvolnění zdrojů.
- **Dávkové zpracování**Pokud anotujete více dokumentů, zpracovávejte je dávkově, abyste efektivně řídili zátěž systému.
- **Alokace zdrojů**Ujistěte se, že vaše prostředí má dostatek paměti a výpočetního výkonu pro zpracování velkých souborů.

## Závěr
Naučili jste se, jak přidávat a odebírat podtržené anotace pomocí GroupDocs.Annotation pro Javu. Tento tutoriál se zabýval inicializací třídy Annotator, konfigurací anotací s komentáři a ukládáním dokumentů bez jakýchkoli anotací. 

Pro další zkoumání zvažte integraci těchto funkcí do vašich stávajících systémů správy dokumentů nebo experimentujte s jinými typy anotací poskytovanými službou GroupDocs.

## Sekce Často kladených otázek
1. **Jak nakonfiguruji více podtržených anotací v jednom spuštění?**
   - Vytvořit více `UnderlineAnnotation` objekty a přidávat je postupně pomocí `annotator.add()` metoda.
2. **Mohu pomocí této knihovny anotovat obrázky v PDF souborech?**
   - Ano, GroupDocs.Annotation podporuje anotaci obrázků v dokumentech, jako jsou PDF.
3. **Jaké formáty souborů podporuje GroupDocs.Annotation?**
   - Podporuje různé formáty dokumentů včetně PDF, Wordu, Excelu a dalších.