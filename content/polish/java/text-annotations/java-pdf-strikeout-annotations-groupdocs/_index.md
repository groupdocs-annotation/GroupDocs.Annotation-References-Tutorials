---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Dowiedz się, jak dodać adnotacje przekreślenia do plików PDF w Javie
  przy użyciu GroupDocs. Ten samouczek krok po kroku obejmuje konfigurację, kod, rozwiązywanie
  problemów oraz wskazówki dotyczące wydajności.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Przewodnik po przekreślaniu tekstu PDF w Javie
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
title: Jak dodać adnotacje przekreślenia do plików PDF w Javie – Kompletny przewodnik
  GroupDocs
type: docs
url: /pl/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Jak dodać adnotacje przekreślenia do plików PDF w Javie

Czy kiedykolwiek potrzebowałeś przekreślić tekst w pliku PDF programowo? Niezależnie od tego, czy budujesz system przeglądu dokumentów, tworzysz przepływ pracy edycji, czy po prostu musisz oznaczyć tekst do usunięcia, **how to add strikeout** adnotacje w Javie to praktyczna umiejętność, która oszczędza czas i zmniejsza ręczną pracę. W tym obszernym przewodniku odkryjesz wszystko, co musisz wiedzieć, aby wdrożyć adnotacje przekreślenia przy użyciu GroupDocs.Annotation dla Javy, od konfiguracji projektu po optymalizację wydajności.

## Szybkie odpowiedzi
- **Jaki jest pierwszy krok?** Dodaj zależność GroupDocs.Annotation Maven do swojego `pom.xml`.  
- **Jak utworzyć przekreślenie?** Instantiate `Annotator`, define `StrikeoutAnnotation` with points, set color/opacity, then call `addAnnotation`.  
- **Czy mogę dodać komentarze?** Yes, attach a `Comment` object to the annotation for collaboration.  
- **Co zrobić, jeśli adnotacja jest nieprawidłowo umieszczona?** Adjust the coordinate points; PDF uses a bottom‑left origin system.  
- **Czy istnieje limit rozmiaru dokumentu?** GroupDocs processes multi‑hundred‑page PDFs without loading the entire file into memory.

## Co oznacza „how to add strikeout” w adnotacjach PDF?
Wyrażenie „how to add strikeout” odnosi się do procesu programowego rysowania linii przez wybrany tekst w dokumencie PDF przy użyciu API adnotacji. W Javie GroupDocs.Annotation udostępnia dedykowaną klasę `StrikeoutAnnotation`, która obsługuje renderowanie, stylizację i trwałość znaków przekreślenia.

## Dlaczego używać GroupDocs do przekreśleń PDF w Javie?
GroupDocs.Annotation obsługuje **ponad 50 formatów wejściowych i wyjściowych** — w tym PDF, DOCX, XLSX, PPTX, HTML oraz popularne typy obrazów — więc nie jesteś ograniczony do jednego typu pliku. Dostarcza wysokopoziomowe API, które abstrahuje niskopoziomową strukturę PDF, automatycznie obsługując osadzanie czcionek, renderowanie stron i trwałość adnotacji, co pozwala programistom skupić się na logice biznesowej, a nie na wewnętrznych szczegółach PDF.

## Wymagania wstępne i konfiguracja

### Niezbędne wymagania
- **Java Development Kit (JDK):** Wersja 8 lub nowsza (zalecany JDK 11+ dla optymalnej kolekcji śmieci).  
- **GroupDocs.Annotation for Java:** Zintegrowany przez Maven (zobacz fragment Maven poniżej).  
- **IDE:** IntelliJ IDEA, Eclipse lub dowolny edytor kompatybilny z Javą.

### Konfiguracja zależności Maven
Dodaj następujący blok zależności do swojego `pom.xml`:

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

**Pro Tip:** Zawsze sprawdzaj najnowszą wersję na stronie wydań GroupDocs; nowsze wydania dodają funkcje i naprawiają błędy, które mogą wpływać na renderowanie adnotacji.

### Uzyskanie licencji
GroupDocs.Annotation wymaga ważnej licencji do użytku produkcyjnego. Masz trzy opcje:

- **Free Trial:** Pobierz z [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License:** Poproś o klucz deweloperski na [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Full License:** Kup na produkcję na [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Wersja próbna dodaje subtelną znak wodny, więc zaplanuj testy odpowiednio.

## Przewodnik krok po kroku

### Zrozumienie podstawowych komponentów
Poniższe definicje zapewniają szybki model mentalny:

- **Annotator:** Główny obiekt API, który ładuje PDF i udostępnia metody adnotacji.  
- **StrikeoutAnnotation:** Reprezentuje wizualną linię przekreślenia oraz opcje jej stylizacji.  
- **Point:** Para współrzędnych (X, Y), określająca, gdzie linia zaczyna się i kończy.  
- **Comment:** Opcjonalny tekst dołączony do adnotacji w celu współpracy.

### Krok 1: Konfiguracja ścieżek plików
Zdefiniuj lokalizacje swojego źródłowego PDF oraz pliku docelowego. Nieprawidłowe ścieżki są częstym źródłem błędów „File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Upewnij się, że katalog wyjściowy istnieje i jest zapisywalny; GroupDocs nie utworzy automatycznie brakujących folderów.

### Krok 2: Inicjalizacja Annotatora
Utwórz instancję `Annotator`, która ładuje PDF do pamięci.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** Biblioteka parsuje strukturę PDF, buduje wewnętrzną reprezentację i przygotowuje płótno adnotacji na każdej stronie. Dla plików o setkach stron ten krok może zająć kilka sekund.

### Krok 3: Dodawanie komentarzy (opcjonalne, ale zalecane)
`Comment` to klasa reprezentująca notatkę tekstową dołączoną do adnotacji, umożliwiającą współpracownikom wyjaśnienie przyczyny przekreślenia.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Używaj komentarzy, aby wyjaśnić, dlaczego tekst jest usuwany — jest to szczególnie przydatne w procesach przeglądu prawnego lub redakcyjnego.

### Krok 4: Definiowanie współrzędnych adnotacji
Obiekty `Point` przechowują pary współrzędnych X‑Y, które definiują dokładną lokalizację adnotacji na stronie PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** Współrzędne PDF zaczynają się w lewym dolnym rogu (0,0). Przykład tworzy poziomą linię od (80,730) do (240,730) na docelowej stronie.

**Finding the Right Coordinates:** Wielu programistów tworzy pomocniczą funkcję, która konwertuje procenty szerokości/wysokości strony na punkty bezwzględne, co sprawia, że kod jest odporny na różne rozmiary stron.

### Krok 5: Tworzenie adnotacji przekreślenia
`StrikeoutAnnotation` kapsułkuje wizualną linię, jej właściwości stylu takie jak kolor i przezroczystość oraz wszelkie powiązane metadane dla znaku przekreślenia.

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

**Color Values:** `fontColor` używa dziesiętnych wartości RGB (np. 65535 dla jasnego żółtego). Skorzystaj z konwertera online, jeśli potrzebujesz odcieni specyficznych dla marki.

**Opacity Recommendation:** Przezroczystość `0.7` (70 %) zapewnia wyraźną wskazówkę wizualną, jednocześnie pozostawiając podstawowy tekst czytelnym.

### Krok 6: Zastosowanie adnotacji
`addAnnotation` to metoda `Annotator`, która rejestruje przygotowaną adnotację w dokumencie, aby została wyrenderowana i zapisana.

```java
annotator.add(strikeout);
```

### Krok 7: Zapis i sprzątanie
`dispose()` zwalnia zasoby natywne trzymane przez instancję `Annotator`, zapobiegając wyciekom pamięci po zakończeniu przetwarzania.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Wywołanie `dispose()` zwalnia zasoby natywne i zapobiega wyciekom pamięci przy przetwarzaniu partii plików PDF.

## Typowe problemy i jak je rozwiązać

### Problem 1: Błędy „File Not Found”
**Symptoms:** Wyrzucony wyjątek podczas konstrukcji `Annotator`.  
**Solution:** Zweryfikuj zarówno ścieżki wejściowe, jak i wyjściowe oraz potwierdź, że aplikacja ma uprawnienia do odczytu/zapisu.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problem 2: Przekreślenie pojawia się w niewłaściwym miejscu
**Symptoms:** Linia nie pokrywa się z zamierzonym tekstem.  
**Solution:** Pamiętaj, że współrzędne Y w PDF rosną w górę. Użyj narzędzia do debugowania wizualnego lub wydrukuj wymiary strony, aby dokładnie dostroić punkty.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problem 3: Adnotacja niewidoczna
**Symptoms:** Po zapisaniu nie pojawia się żadne przekreślenie.  
**Possible Causes & Fixes:**  
- **Opacity too low:** Tymczasowo ustaw przezroczystość na `1.0`, aby zweryfikować widoczność.  
- **Color blending:** Użyj koloru o wysokim kontraście, takiego jak czerwony (`255`).  
- **Incorrect page index:** Numery stron zaczynają się od zera; upewnij się, że celujesz w właściwą stronę.

### Problem 4: Problemy z pamięcią przy dużych plikach
**Symptoms:** `OutOfMemoryError` lub spowolniona wydajność.  
**Solutions:**  
- Przetwarzaj dokumenty w mniejszych partiach.  
- Użyj API strumieniowego, jeśli jest dostępne.  
- Zawsze wywołuj `dispose()` po każdym dokumencie.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Zastosowania w rzeczywistych scenariuszach

### Przegląd dokumentów prawnych
Kancelarie prawne oznaczają kontrakty przekreśleniami, aby wskazać usunięte klauzule, zachowując jednocześnie ślad audytu.

### Redakcja prac akademickich
Profesorowie używają przekreśleń, aby zasugerować usunięcia podczas recenzji, pozostawiając oryginalny tekst widoczny w kontekście.

### Systemy zarządzania treścią
Platformy wydawnicze automatycznie oznaczają sekcje naruszające politykę przekreśleniami przed ręczną moderacją.

### Kontrola wersji dokumentów
Przedsiębiorstwa traktują adnotacje przekreślenia jako „markery usunięcia” w przepływie pracy kontroli wersji skoncentrowanej na dokumentach, podobnie jak różnice w kodzie.

## Wskazówki optymalizacji wydajności

### Strategia przetwarzania wsadowego
Podczas obsługi wielu plików PDF, w miarę możliwości ponownie używaj jednej instancji `Annotator` i przetwarzaj pliki w równoległych wątkach.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Najlepsze praktyki zarządzania pamięcią
- Wywołaj `dispose()` na każdym `Annotator`.  
- Ogranicz jednoczesne ładowanie dokumentów, aby uniknąć obciążenia sterty.  
- Monitoruj zużycie pamięci JVM przy użyciu narzędzi takich jak VisualVM.

### Buforowanie współrzędnych
Jeśli stosujesz ten sam układ adnotacji w wielu plikach, buforuj obiekty `Point`, aby uniknąć ponownego obliczania.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Zaawansowane opcje dostosowywania

### Dynamiczny wybór koloru
Wybieraj kolory w czasie wykonywania na podstawie reguł biznesowych (np. czerwony dla krytycznych usunięć, żółty dla wstępnych).

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

### Wieloliniowe przekreślenia
Utwórz serię par `Point`, aby narysować linię zygzakowatą przecinającą kilka linii tekstu.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Lista kontrolna rozwiązywania problemów
1. **File Permissions:** Zweryfikuj dostęp do odczytu/zapisu.  
2. **Library Version:** Upewnij się, że używasz wspieranej wersji GroupDocs.Annotation.  
3. **License Status:** Potwierdź, że plik licencji jest prawidłowo odwołany.  
4. **PDF Compatibility:** Sprawdź, czy PDF nie jest uszkodzony i mieści się w obsługiwanych limitach rozmiaru.  
5. **Coordinate Validation:** Upewnij się, że wszystkie punkty znajdują się w granicach strony.  
6. **Heap Space:** Zwiększ pamięć JVM `-Xmx`, jeśli przetwarzasz bardzo duże pliki.

## Najczęściej zadawane pytania

**Q: Czy mogę przekreślić tekst obejmujący wiele linii?**  
A: Tak. Utwórz kilka obiektów `Point`, które odzwierciedlają żądaną ścieżkę; adnotacja podąży za podanym polilinią.

**Q: Co się stanie, jeśli podam współrzędne poza granicami strony?**  
A: Adnotacja zostanie przycięta i może stać się niewidoczna. Zawsze weryfikuj współrzędne względem szerokości i wysokości strony.

**Q: Czy mogę usunąć adnotacje przekreślenia po ich dodaniu?**  
A: Oczywiście. Użyj metody `removeAnnotation` z ID adnotacji lub przefiltruj po typie, aby usunąć je programowo.

**Q: Czy istnieje limit liczby adnotacji, które mogę dodać do jednego PDF?**  
A: GroupDocs nie narzuca sztywnego limitu, ale wydajność może spadać po kilku tysiącach adnotacji. Rozważ paginację lub podsumowanie adnotacji przy bardzo dużych zestawach.

**Q: Jak pracować z PDF‑ami zabezpieczonymi hasłem?**  
A: Przekaż hasło do konstruktora `Annotator`. Biblioteka odszyfruje dokument w pamięci przed zastosowaniem jakichkolwiek adnotacji.

**Q: Jak mogę obsługiwać PDF‑y o różnych rozmiarach i orientacjach stron?**  
A: Pobierz wymiary każdej strony za pomocą `annotator.getPageInfo(pageNumber)` i oblicz współrzędne względem tych wymiarów, aby zapewnić spójne rozmieszczenie.

## Zakończenie
Masz teraz kompletną, gotową do produkcji rozwiązanie dla **how to add strikeout** adnotacji do plików PDF w Javie przy użyciu GroupDocs.Annotation. Opanowując obsługę ścieżek plików, obliczanie współrzędnych i zarządzanie zasobami, możesz wbudować tę funkcjonalność w narzędzia przeglądu dokumentów, pipeline’y treści lub dowolną aplikację opartą na Javie, która potrzebuje precyzyjnego wizualnego feedbacku.

**Kolejne kroki**
1. Sklonuj przykładowy projekt i uruchom go na próbce PDF.  
2. Eksperymentuj z różnymi kolorami, przezroczystościami i tekstami komentarzy.  
3. Zintegruj przepływ pracy adnotacji z istniejącą usługą przetwarzania dokumentów.  
4. Poznaj powiązane typy adnotacji — podświetlenia, notatki samoprzylepne i adnotacje kształtów — aby poszerzyć zestaw narzędzi do manipulacji PDF.

Gotowy na więcej? Zanurz się w oficjalnej dokumentacji, aby uzyskać głębsze informacje o API.

## Dodatkowe zasoby
- [Dokumentacja GroupDocs](https://docs.groupdocs.com/annotation/java/) - Ogólna dokumentacja bibliotek GroupDocs  
- [Dokumentacja GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/) - Pełna referencja API  
- [Przewodnik referencyjny API](https://reference.groupdocs.com/annotation/java/) - Szczegóły metoda po metodzie  
- [Pobierz najnowszą wersję](https://releases.groupdocs.com/annotation/java/) - Utrzymuj swoją bibliotekę w najnowszej wersji  
- [Kup licencję](https://purchase.groupdocs.com/buy) - Licencjonowanie gotowe do produkcji  
- [Pobierz wersję próbną](https://releases.groupdocs.com/annotation/java/) - Oceń przed zakupem  
- [Wniosek o licencję tymczasową](https://purchase.groupdocs.com/temporary-license/) - Testowanie w środowisku deweloperskim  
- [Forum wsparcia](https://forum.groupdocs.com/c/annotation/) - Pomoc społeczności i oficjalne wsparcie  

---

**Ostatnia aktualizacja:** 2026-05-21  
**Testowano z:** GroupDocs.Annotation 23.12 for Java  
**Autor:** GroupDocs

## Powiązane samouczki
- [Dodaj adnotację PDF w Javie – Kompletny przewodnik GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Samouczek adnotacji PDF w Javie – Kompletny przewodnik po podświetlaniu PDF](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [Jak dodać strzałkę do PDF w Javie – Kompletny samouczek GroupDocs](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)