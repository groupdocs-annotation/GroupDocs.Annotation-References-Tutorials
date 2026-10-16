---
date: '2026-10-16'
description: Dowiedz się, jak zapisać PDF bez adnotacji w Javie, opanuj zarządzanie
  pamięcią PDF w Javie oraz dodawaj podkreślone adnotacje za pomocą GroupDocs.Annotation.
  Przewodnik krok po kroku.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Adnotacje dokumentów w Javie z GroupDocs
og_description: Dowiedz się, jak zapisać PDF bez adnotacji w Javie, opanuj zarządzanie
  pamięcią PDF w Javie oraz dodawaj podkreślone adnotacje za pomocą GroupDocs.Annotation.
  Przewodnik krok po kroku.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Jak zapisać PDF bez adnotacji w Javie przy użyciu GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Jak zapisać PDF bez adnotacji w Javie przy użyciu GroupDocs
type: docs
url: /pl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Jak zapisać PDF bez adnotacji w Javie przy użyciu GroupDocs

Jeśli potrzebujesz **zapisać PDF bez adnotacji**, a jednocześnie chcesz dodawać współpracujące podkreślenia, jesteś we właściwym miejscu. Wielu programistów Java ma problem z utrzymaniem czystej wersji dokumentu do ostatecznej dystrybucji, szczególnie gdy ten sam plik jest używany w iteracyjnych przeglądach. W tym samouczku nauczysz się, jak wygenerować czysty PDF, efektywnie zarządzać pamięcią i stosować podkreślenia z komentarzami przy użyciu GroupDocs.Annotation. Po zakończeniu zrozumiesz kompletny przepływ pracy — od wczytania PDF po stworzenie finalnej kopii bez znaków wodnych — oraz wskazówki najlepszych praktyk przy budowaniu solidnego **java document review system**.

## Szybkie odpowiedzi
- **Jak dodać podkreślenie?** Użyj `UnderlineAnnotation` z `annotator.add()`, a następnie zapisz dokument.  
- **Jak mogę zapisać PDF bez adnotacji?** Załaduj plik z adnotacjami, ustaw `AnnotationType.NONE` w `SaveOptions` i zapisz nową kopię.  
- **Jakie biblioteki są wymagane?** GroupDocs.Annotation v25.2 (lub nowsza) oraz jej repozytorium Maven.  
- **Czy potrzebna jest licencja do produkcji?** Tak — zastosuj ważną licencję GroupDocs, aby uniknąć znaków wodnych.  
- **Czy mogę efektywnie przetwarzać wiele dokumentów?** Umieść każdy `Annotator` w bloku try‑with‑resources i zwolnij zasoby po każdym pliku.

## Jak zapisać PDF bez adnotacji w Javie?

Załaduj źródłowy PDF przy użyciu `Annotator`, skonfiguruj `SaveOptions`, aby wykluczyć wszystkie typy adnotacji, i wywołaj `save()`, aby zapisać czystą kopię. Ta operacja nie modyfikuje oryginalnego pliku, więc zachowujesz zarówno wersję z adnotacjami dla recenzentów, jak i nieskażoną wersję do dystrybucji. Proces używa strumieniowania, co oznacza, że cały dokument nigdy nie znajduje się w całości w pamięci — kluczowe przy dużych PDF‑ach.

## Co oznacza zapis PDF bez adnotacji?

`save pdf without annotations` odnosi się do eksportu dokumentu PDF przy jednoczesnym usunięciu wszystkich obiektów adnotacji (podświetlenia, komentarze, pieczątki, podkreślenia itp.). Powstały plik zawiera wyłącznie oryginalną treść i układ, co czyni go odpowiednim do archiwizacji prawnej, publikacji publicznej lub przechowywania.

## Dlaczego tworzyć czyste pliki PDF w systemie przeglądu dokumentów Java?

Czysta wersja eliminuje znaczniki recenzentów, komentarze i podświetlenia, dając wypolerowany dokument gotowy dla klientów, regulatorów lub publikacji publicznej. Redukuje także rozmiar pliku średnio o 30 % i zapobiega przypadkowemu ujawnieniu wewnętrznych notatek — kluczowe w przepływach pracy prawnych i zgodności. GroupDocs.Annotation może usunąć wszystkie obiekty adnotacji w jednym przebiegu, obsługując PDF‑y do 500 MB bez ładowania całego pliku do pamięci.

## Wymagania wstępne i konfiguracja środowiska

### Wymagania przed rozpoczęciem

**Wymagania środowiska programistycznego**  
- Java Development Kit (JDK) 8 lub wyższy (zalecany JDK 11+)  
- Maven 3.6+ lub Gradle 6.0+ do zarządzania zależnościami  
- IDE, takie jak IntelliJ IDEA, Eclipse lub VS Code z rozszerzeniami Java  
- Co najmniej 2 GB dostępnej pamięci RAM (przetwarzanie dokumentów może być intensywne pod względem pamięci)

**Wymagania wiedzy**  
Powinieneś być zaznajomiony z podstawowymi koncepcjami Javy — inicjalizacją obiektów, wywoływaniem metod i zależnościami Maven. Wcześniejsze doświadczenie z bibliotekami zewnętrznymi przyspieszy wdrożenie.

**Dokumenty testowe**  
Przygotuj kilka przykładowych PDF‑ów. PDF‑y oparte na tekście działają najlepiej; zeskanowane obrazy mogą wymagać OCR przed adnotacją.

### Konfiguracja Maven: dodanie GroupDocs do projektu

Dodaj następującą zależność do swojego `pom.xml`. Ten krok sprawia trudności wielu programistom przy pierwszej próbie, ponieważ identyfikatory grupy i artefaktu muszą być dokładnie zgodne.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Important:** Version 25.2 is the latest stable release at the time of writing. Check the GroupDocs repository regularly for newer versions that include bug fixes and performance improvements.

### Konfiguracja licencji (nie pomijaj tego)

**For development/testing** – Download the free trial from the GroupDocs website. The trial includes all features but adds a watermark to processed documents.

**For production** – Purchase a license and apply it during application startup. Without a valid license, production builds will be limited and watermarked.

## Przewodnik implementacji: dodawanie podkreśleń

### Zrozumienie przepływu pracy z adnotacjami

Zanim przejdziemy do kodu, przyjrzyjmy się czterostopniowemu przepływowi, który zachodzi, gdy **annotate PDF in Java**:

1. **Wczytywanie dokumentu** – `Annotator` odczytuje plik do pamięci.  
2. **Tworzenie adnotacji** – Zdefiniuj właściwości takie jak pozycja, styl i komentarze.  
3. **Zastosowanie adnotacji** – Biblioteka wstawia adnotację do struktury PDF.  
4. **Zapisywanie dokumentu** – Zapisz zmodyfikowany plik, opcjonalnie zachowując oryginał.

Proces jest niedestrukcyjny; plik źródłowy pozostaje nienaruszony, chyba że go nadpiszesz.

### Krok 1: zainicjalizuj annotator i wczytaj dokument

`Annotator` jest głównym punktem wejścia w GroupDocs.Annotation do wczytywania i modyfikacji dokumentów PDF. Abstrahuje obsługę systemu plików, zarządzanie strumieniami i alokację zasobów natywnych.

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

**Pro tip:** Use absolute paths while developing to avoid “file not found” errors. In production, consider loading resources from the classpath or a cloud storage bucket.

### Krok 2: tworzenie komentarzy i odpowiedzi (część współpracy)

Obiekty `Comment` reprezentują wątkowaną dyskusję dołączoną do adnotacji. Każdy komentarz może mieć autora, znacznik czasu i opcjonalne odpowiedzi, umożliwiając pełną konwersację wokół konkretnego oznaczenia.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Real‑world use:** Reviewers can discuss a specific clause by adding threaded replies, keeping the conversation tied to the exact annotation.

### Krok 3: definiowanie współrzędnych adnotacji (poprawne pozycjonowanie)

`Point` definiuje pojedynczą współrzędną w przestrzeni PDF (mierzoną w punktach, gdzie 72 punkty = 1 cal). Cztery punkty są wymagane dla podkreślenia: dwa dla linii początkowej i dwa dla linii końcowej.

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

**Coordinate system:**  
- Punkty 1 i 2 definiują górną krawędź podkreślenia.  
- Punkty 3 i 4 definiują dolną krawędź.  
- Różnica Y (730 vs 650) kontroluje grubość.

### Krok 4: tworzenie i konfigurowanie podkreślenia

`UnderlineAnnotation` jest konkretną klasą reprezentującą podkreślenie. Dziedziczy po bazowej klasie `Annotation` i dodaje właściwości specyficzne dla podkreśleń, takie jak grubość linii i styl.

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

**Color & opacity tips:**  
- `FontColor` używa ARGB; `65535` (0x00FFFF) daje jasny żółty.  
- Dla czerwonego użyj `16711680` (0xFF0000); dla niebieskiego `255` (0x0000FF).  
- Wartości przezroczystości między 0.5 a 0.8 zapewniają dobrą czytelność bez zasłaniania tekstu.

### Krok 5: zapisywanie dokumentu z adnotacjami

`SaveOptions` pozwala kontrolować format wyjściowy, czy wstawiać adnotacje oraz jak obsługiwać metadane. Ustawienie `AnnotationType.NONE` instruuje bibliotekę, aby usunęła wszystkie obiekty adnotacji, co jest kluczem do **save PDF without annotations**.

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

**Memory management:** The `dispose()` call releases native resources and prevents memory leaks—critical when processing many files in a batch.

## Usuwanie adnotacji: tworzenie czystych wersji dokumentu

Czasami potrzebujesz wersji PDF **bez żadnych adnotacji** — na przykład przy dostarczaniu ostatecznie zatwierdzonego kontraktu. GroupDocs ułatwia to zadanie.

### Zrozumienie opcji usuwania adnotacji

Możesz:  
- Usuwanie **wszystkich** adnotacji (najczęstsze)  
- Usuwanie określonych typów (np. tylko podświetlenia)  
- Usuwanie adnotacji według autora lub strony  

### Krok po kroku usuwanie adnotacji

**Krok 1: wczytaj wcześniej oznaczony dokument**

`Annotator` ponownie działa jako loader; odczyta plik, który nadal zawiera obiekty adnotacji.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Krok 2: skonfiguruj opcje zapisu dla czystego wyniku**

`SaveOptions` provides a fluent API to specify that no annotation types should be written to the output file.

```java
Annotator annotator = new Annotator(outputPath);
```

**Krok 3: zapisz czystą wersję**

Calling `save()` with the configured options writes a PDF that contains only the original content.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

This produces a **clean PDF** file that contains no annotation objects, perfect for final distribution.

## Typowe problemy i rozwiązania

### Problem 1: błąd „Document not found”

Make sure the file path is correct and that the application has read permissions. Using `Path.of()` with absolute paths eliminates most ambiguities.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problem 2: Adnotacje pojawiają się w niewłaściwych miejscach

PDF coordinate origin is at the bottom‑left corner. Verify that your Y‑values increase upward and that you account for page rotation.

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

### Problem 3: Problemy z pamięcią przy dużych dokumentach

GroupDocs.Annotation streams content and never loads the entire file into heap memory. However, you must still call `dispose()` and consider increasing the JVM heap (`-Xmx`) for files larger than 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 4: Problemy z licencjonowaniem w produkcji

If the license file is missing or the path is incorrect, the library falls back to trial mode, adding a watermark to every page. Place the license file in a location that is on the classpath and load it early in your application lifecycle.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Najlepsze praktyki wydajnościowe dla aplikacji produkcyjnych

### Strategie zarządzania pamięcią

GroupDocs.Annotation processes PDFs in a streaming fashion, which allows it to handle files up to 500 MB without loading the whole document into memory. Still, follow these guidelines:

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Rozważania dotyczące wątków

GroupDocs.Annotation is **not thread‑safe** by default. If your application processes documents concurrently:

- **Nigdy nie udostępniaj** instancji `Annotator` pomiędzy wątkami.  
- **Synchronizuj** dostęp do plików lub użyj mechanizmu blokady.  
- Rozważ **puli** obiektów `Annotator`, jeśli potrzebujesz wysokiej przepustowości.

### Strategie buforowania

- Buforuj często używane szablony adnotacji.  
- Ponownie używaj kolekcji `Point` dla typowych zestawów współrzędnych.  
- Trzymaj **szablon PDF** w pamięci, jeśli wielokrotnie adnotujesz ten sam dokument bazowy.

## Najlepsze praktyki zarządzania pamięcią PDF w Javie

Efektywne użycie pamięci jest niezbędne przy obsłudze dużych PDF‑ów lub przetwarzaniu wielu plików w partii. Oto kilka praktycznych zaleceń:

- **Używaj try‑with‑resources** dla każdego `Annotator`, aby zapewnić zwolnienie zasobów.  
- **Zwiększaj stertę JVM** (`-Xmx`) tylko w razie potrzeby; monitoruj użycie za pomocą narzędzi profilujących.  
- **Przetwarzaj dokumenty kolejno** gdy to możliwe, zwalniając pamięć po każdym pliku.  
- **Unikaj wielokrotnego ładowania tego samego PDF**; ponownie używaj tego samego strumienia, jeśli musisz go czytać wielokrotnie.

Stosowanie tych praktyk pomaga utrzymać aplikację responsywną i zapobiega awariom z powodu braku pamięci podczas intensywnych zadań adnotacyjnych.

## Praktyczne zastosowania i przypadki użycia

### Systemy przeglądu dokumentów

- **Przegląd prawny:** Podkreśl klauzule umowy i dodaj komentarze dotyczące ryzyka.  
- **Audyt zgodności:** Podświetl problematyczne sekcje w sprawozdaniach finansowych.  
- **Recenzja akademicka:** Profesorowie podkreślają fragmenty wymagające wyjaśnienia.

### Platformy edukacyjne

- **Narzędzia do adnotacji dla studentów:** Pozwalają uczniom podkreślać kluczowe pojęcia w e‑bookach.  
- **Feedback nauczyciela:** Dostarczaj komentarze w miejscu bezpośrednio na przesłanych zadaniach.

### Procesy zapewnienia jakości

- **Przegląd dokumentacji technicznej:** Inżynierowie podkreślają sekcje wymagające aktualizacji.  
- **Procedury operacyjne:** Inspektorzy bezpieczeństwa podkreślają krytyczne kroki.

### Systemy zarządzania treścią

- **Workflow redakcyjny:** Redaktorzy podkreślają tekst wymagający weryfikacji faktów.  
- **Kontrola wersji:** Śledź historię adnotacji w kolejnych wersjach dokumentu.

## Zaawansowane wskazówki dla profesjonalnej implementacji

### Niestandardowe style adnotacji

Możesz rozszerzyć wygląd podkreślenia, ustawiając własne wzory kresek, zakończenia linii i poziomy przezroczystości. Przydaje się, gdy trzeba odróżnić role recenzentów (np. prawnika vs. inżyniera).

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

### Metadane adnotacji do śledzenia

Każda adnotacja może zawierać słownik metadanych definiowany przez użytkownika. Przechowuj identyfikatory, znaczniki czasu lub stan przepływu pracy, aby zintegrować się z zewnętrznymi systemami śledzenia.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integracja z systemami zarządzania użytkownikami

Mapuj właściwość `author` obiektu `Comment` do identyfikatorów użytkowników w Twojej aplikacji. To umożliwia stylizację zależną od roli oraz generowanie ścieżki audytu.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Rozwiązywanie problemów w produkcji

### Monitorowanie wydajności

Śledź te metryki w produkcji:  
- **Użycie sterty** – upewnij się, że wywołano `dispose()`.  
- **Czas przetwarzania na dokument** – loguj znaczniki czasu przed i po `annotator.save()`.  
- **Wskaźnik błędów** – przechwytuj wyjątki i kategoryzuj je.

### Typowe pułapki w produkcji

- **Blokowanie plików** – upewnij się, że przesłane pliki są zamknięte przed adnotacją.  
- **Jednoczesne edycje** – wdroż optymistyczne blokowanie lub sprawdzanie wersji.  
- **Duże pliki (> 50 MB)** – zwiększ limit czasu JVM i rozważ API strumieniowe.

### Najlepsze praktyki obsługi błędów

Wrap all annotation calls in try‑catch blocks, log the full stack trace, and re‑throw a custom `AnnotationException` with a user‑friendly message. This pattern simplifies debugging and provides clear feedback to API consumers.

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

## Najczęściej zadawane pytania

**Q: How do I annotate multiple areas of text in a single operation?**  
A: Create several `UnderlineAnnotation` objects with different coordinates and add them sequentially using `annotator.add()`.

**Q: Can I annotate images within PDF documents?**  
A: Yes. Use the same coordinate system, ensuring the points lie inside the image bounds.

**Q: What file formats besides PDF does GroupDocs.Annotation support?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats such as JPEG, PNG, TIFF.

**Q: How do I handle very large documents without running out of memory?**  
A: Process documents one at a time, increase the JVM heap (`-Xmx`), and always dispose of `Annotator` instances promptly.

**Q: Is it possible to extract existing annotations from a document?**  
A: Yes. Use `annotator.get()` to retrieve all annotations, then filter by type, author, or page as needed.

---

**Ostatnia aktualizacja:** 2026-10-16  
**Testowano z:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

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

## Powiązane samouczki

- [Utwórz czysty PDF w Javie: podkreślenia z GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edytuj adnotacje PDF w Javie – kompletny samouczek GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Adnotuj PDFy GroupDocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)