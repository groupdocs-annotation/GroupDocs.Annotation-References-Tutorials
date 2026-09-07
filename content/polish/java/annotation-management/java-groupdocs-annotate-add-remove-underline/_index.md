---
categories:
- Java Development
date: '2026-03-24'
description: Dowiedz się, jak tworzyć czyste pliki PDF w języku Java, zarządzać pamięcią
  PDF w Javie oraz dodawać adnotacje do PDF w Javie przy użyciu GroupDocs.Annotation,
  z pełnymi przykładami kodu i wskazówkami rozwiązywania problemów.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Tworzenie czystego PDF w Javie: podkreślanie adnotacji przy użyciu GroupDocs'
type: docs
url: /pl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Utwórz czysty PDF Java: podkreślenia adnotacji z GroupDocs

Jeśli potrzebujesz **utworzyć czyste PDF Java** i dodać współpracujące adnotacje, jesteś we właściwym miejscu. Masz problemy z zarządzaniem dokumentami i współpracą w aplikacjach Java? Nie jesteś sam. Wielu programistów napotyka trudności przy wdrażaniu solidnych funkcji adnotacji dokumentów, które działają niezawodnie w różnych formatach plików.

W tym przewodniku **utworzysz czyste PDF Java** i nauczysz się **adnotować PDF w Javie** przy użyciu GroupDocs.Annotation. Po zakończeniu tutorialu będziesz dokładnie wiedział, jak dodać podkreślenia z komentarzami, usunąć istniejące adnotacje oraz zintegrować te funkcje płynnie w swoich projektach.

**Co opanujesz w tym przewodniku:**
- Konfigurację GroupDocs.Annotation w projekcie Java (właściwy sposób)  
- Dodawanie podkreśleń z własnymi komentarzami i stylizacją  
- Usuwanie wszystkich adnotacji w celu utworzenia czystych wersji dokumentu  
- Rozwiązywanie typowych problemów, z którymi spotykają się programiści  
- Optymalizację wydajności dla aplikacji produkcyjnych  

Niezależnie od tego, czy tworzysz system przeglądu dokumentów, platformę edukacyjną, czy narzędzie do współdzielonej edycji, ten tutorial zapewnia praktyczne, przetestowane przykłady kodu.

## Szybkie odpowiedzi
- **Jak dodać podkreślenie?** Użyj `UnderlineAnnotation` i `annotator.add()`, a następnie zapisz dokument.  
- **Jak utworzyć czysty PDF Java?** Załaduj plik z adnotacjami, ustaw `AnnotationType.NONE` w `SaveOptions` i zapisz nową kopię.  
- **Jakie biblioteki są wymagane?** GroupDocs.Annotation v25.2 (lub nowsza) oraz jej repozytorium Maven.  
- **Czy potrzebna jest licencja do produkcji?** Tak — zastosuj ważną licencję GroupDocs, aby uniknąć znaków wodnych.  
- **Czy mogę przetwarzać wiele dokumentów efektywnie?** Owiń każdy `Annotator` w blok try‑with‑resources i zwolnij zasoby po każdym pliku.

## Jak tworzyć czyste PDF Java
Utworzenie czystego PDF Java oznacza wygenerowanie wersji dokumentu **bez żadnych adnotacji**, przy zachowaniu oryginalnej zawartości. Jest to przydatne przy ostatecznej dystrybucji, archiwizacji lub gdy trzeba udostępnić „czystą” kopię po cyklu przeglądu.

GroupDocs.Annotation upraszcza to zadanie: załaduj plik z adnotacjami, skonfiguruj `SaveOptions`, aby wykluczyć wszystkie typy adnotacji, i zapisz wynik. Kroki są przedstawione później w sekcji **Usuwanie adnotacji**.

## Dlaczego tworzyć czyste PDF Java?
Czysta wersja eliminuje znaczniki recenzentów, komentarze i podświetlenia, dając wypolerowany dokument gotowy dla klientów, regulatorów lub publikacji publicznej. Redukuje także rozmiar pliku i zapobiega przypadkowemu ujawnieniu wewnętrznych notatek — co jest kluczowe w przepływach pracy prawnych i zgodności.

## Jak adnotować PDF w Javie przy użyciu GroupDocs
GroupDocs.Annotation oferuje bogate API do **adnotowania PDF w Javie**. Obsługuje szeroką gamę typów adnotacji, w tym podświetlenia, pieczątki i podkreślenia. W tym tutorialu skupiamy się na podkreśleniach, ponieważ są one często używane do podkreślania tekstu przy jednoczesnym umożliwieniu wątkowych komentarzy.

## Wymagania wstępne i konfiguracja środowiska

### Co będzie potrzebne przed rozpoczęciem

**Wymagania środowiska deweloperskiego:**
- Java Development Kit (JDK) 8 lub wyższy (zalecany JDK 11+)  
- Maven 3.6+ lub Gradle 6.0+ do zarządzania zależnościami  
- IDE, takie jak IntelliJ IDEA, Eclipse lub VS Code z rozszerzeniami Java  
- Co najmniej 2 GB dostępnej pamięci RAM (przetwarzanie dokumentów może być intensywne pod względem pamięci)

**Wymagania wiedzy:**
Powinieneś być zaznajomiony z podstawowymi koncepcjami Javy — inicjalizacją obiektów, wywoływaniem metod i zależnościami Maven. Doświadczenie z bibliotekami firm trzecich przyspieszy wdrożenie.

**Dokumenty testowe:**
Przygotuj kilka przykładowych plików PDF. PDF‑y oparte na tekście działają najlepiej; zeskanowane obrazy mogą wymagać OCR przed adnotacją.

### Konfiguracja Maven: Dodawanie GroupDocs do projektu

Oto jak prawidłowo skonfigurować projekt Maven (wielu programistów popełnia błąd przy pierwszej próbie):

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

**Ważne:** Wersja 25.2 jest najnowszym stabilnym wydaniem w momencie pisania. Regularnie sprawdzaj repozytorium GroupDocs pod kątem nowszych wersji zawierających poprawki błędów i ulepszenia wydajności.

### Konfiguracja licencji (nie pomijaj)

**Do rozwoju/testów:**  
Pobierz darmową wersję próbną ze strony GroupDocs. Próba zawiera wszystkie funkcje, ale dodaje znak wodny do przetwarzanych dokumentów.

**Do produkcji:**  
Kup licencję i zastosuj ją podczas uruchamiania aplikacji. Bez ważnej licencji wersje produkcyjne będą ograniczone.

## Przewodnik implementacji: Dodawanie podkreśleń

### Zrozumienie przepływu pracy adnotacji

Zanim przejdziemy do kodu, przyjrzyjmy się czterostopniowemu procesowi, który zachodzi, gdy **adnotujesz PDF w Javie**:

1. **Ładowanie dokumentu** – `Annotator` odczytuje plik do pamięci.  
2. **Tworzenie adnotacji** – definiowanie właściwości, takich jak pozycja, styl i komentarze.  
3. **Zastosowanie adnotacji** – biblioteka wstawia adnotację do struktury PDF.  
4. **Zapisywanie dokumentu** – utrwalenie zmodyfikowanego pliku, opcjonalnie zachowując oryginał.

Proces jest nie destrukcyjny; plik źródłowy pozostaje nienaruszony, chyba że go nadpiszesz.

### Krok 1: Inicjalizacja Annotatora i załadowanie dokumentu

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Wskazówka:** Używaj ścieżek bezwzględnych podczas developmentu, aby uniknąć błędów „file not found”. W produkcji rozważ ładowanie zasobów z classpath lub z chmury.

### Krok 2: Tworzenie komentarzy i odpowiedzi (część współpracy)

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

**Zastosowanie w praktyce:** Recenzenci mogą dyskutować konkretny fragment, dodając wątkowe odpowiedzi, które pozostają powiązane z daną adnotacją.

### Krok 3: Definiowanie współrzędnych adnotacji (uzyskanie właściwej pozycji)

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

**System współrzędnych:**  
- Punkty 1 i 2 definiują górną krawędź podkreślenia.  
- Punkty 3 i 4 definiują dolną krawędź.  
- Różnica w osi Y (730 vs 650) kontroluje grubość.

### Krok 4: Tworzenie i konfigurowanie adnotacji podkreślenia

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

**Wskazówki dotyczące koloru i przezroczystości:**  
- `FontColor` używa formatu ARGB; `65535` (0x00FFFF) daje jasny żółty.  
- Dla czerwonego użyj `16711680` (0xFF0000); dla niebieskiego `255` (0x0000FF).  
- Wartości przezroczystości między 0.5 a 0.8 zapewniają dobrą czytelność bez zasłaniania tekstu.

### Krok 5: Zapisywanie dokumentu z adnotacjami

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Zarządzanie pamięcią:** Wywołanie `dispose()` zwalnia zasoby natywne i zapobiega wyciekom pamięci — kluczowe przy przetwarzaniu wielu plików w partii.

## Usuwanie adnotacji: tworzenie czystych wersji dokumentu

Czasami potrzebna jest wersja PDF **bez żadnych adnotacji** — na przykład przy dostarczaniu ostatecznie zatwierdzonego kontraktu. GroupDocs umożliwia to w prosty sposób.

### Zrozumienie opcji usuwania adnotacji

Możesz:
- Usunąć **wszystkie** adnotacje (najczęstsze)  
- Usunąć konkretne typy (np. tylko podświetlenia)  
- Usunąć adnotacje według autora lub strony  

### Krok po kroku: usuwanie adnotacji

**Krok 1: Załaduj wcześniej adnotowany dokument**

```java
Annotator annotator = new Annotator(outputPath);
```

**Krok 2: Skonfiguruj opcje zapisu dla czystego wyjścia**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Krok 3: Zapisz czystą wersję**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Powoduje to utworzenie **czystego PDF Java**, który nie zawiera obiektów adnotacji, idealnego do ostatecznej dystrybucji.

## Typowe problemy i rozwiązania

### Problem 1: Błąd „Document not found”

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

### Problem 2: Adnotacje pojawiają się w niewłaściwych miejscach

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 3: Problemy z pamięcią przy dużych dokumentach

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problem 4: Problemy z licencją w produkcji

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

## Najlepsze praktyki wydajnościowe dla aplikacji produkcyjnych

### Strategie zarządzania pamięcią

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

### Rozważania dotyczące wątkowości

GroupDocs.Annotation jest **niebezpieczny wątkowo** domyślnie. Jeśli aplikacja przetwarza dokumenty równocześnie:

- **Nigdy nie udostępniaj** jednej instancji `Annotator` wielu wątkom.  
- **Synchronizuj** dostęp do plików lub użyj mechanizmu blokady.  
- Rozważ **puli** obiektów `Annotator`, jeśli potrzebujesz wysokiej przepustowości.

### Strategie buforowania

- Buforuj często używane szablony adnotacji.  
- Ponownie używaj kolekcji `Point` dla wspólnych zestawów współrzędnych.  
- Trzymaj **szablon PDF** w pamięci, jeśli wielokrotnie adnotujesz ten sam dokument bazowy.

## Wskazówki dotyczące zarządzania pamięcią w Java PDF
Efektywne wykorzystanie pamięci jest niezbędne przy obsłudze dużych PDF‑ów lub przetwarzaniu wielu plików w partii. Oto kilka praktycznych zaleceń:

- **Używaj try‑with‑resources** dla każdego `Annotator`, aby zagwarantować zwolnienie zasobów.  
- **Zwiększaj stertę JVM** (`-Xmx`) tylko w razie potrzeby; monitoruj zużycie przy pomocy narzędzi profilujących.  
- **Przetwarzaj dokumenty kolejno**, zwalniając pamięć po każdym pliku.  
- **Unikaj wielokrotnego ładowania tego samego PDF**; ponownie użyj tego samego strumienia, jeśli musisz odczytać go wielokrotnie.

Stosowanie tych praktyk pomaga utrzymać aplikację responsywną i zapobiega awariom z powodu braku pamięci podczas intensywnych obciążeń adnotacji.

## Realne zastosowania i przypadki użycia

### Systemy przeglądu dokumentów

- **Przegląd prawny:** Podkreśl klauzule umowy i dodaj komentarze dotyczące ryzyka.  
- **Audyt zgodności:** Podświetl problematyczne sekcje w sprawozdaniach finansowych.  
- **Recenzja akademicka:** Profesorowie podkreślają fragmenty wymagające wyjaśnienia.

### Platformy edukacyjne

- **Narzędzia do adnotacji dla studentów:** Umożliwiają podkreślanie kluczowych koncepcji w e‑książkach.  
- **Informacja zwrotna od nauczyciela:** Dostarcza komentarze w linii bezpośrednio na zgłoszonych zadaniach.

### Przepływy pracy zapewnienia jakości

- **Przegląd dokumentacji technicznej:** Inżynierowie podkreślają sekcje wymagające aktualizacji.  
- **Standardowe procedury operacyjne:** Inspektorzy bezpieczeństwa podkreślają krytyczne kroki.

### Systemy zarządzania treścią

- **Workflow redakcyjny:** Redaktorzy podkreślają tekst wymagający weryfikacji faktów.  
- **Kontrola wersji:** Śledź historię adnotacji w kolejnych wersjach dokumentu.

## Zaawansowane wskazówki dla profesjonalnej implementacji

### Niestandardowe style adnotacji

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadane adnotacji do śledzenia

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integracja z systemami zarządzania użytkownikami

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

## Rozwiązywanie problemów w środowisku produkcyjnym

### Monitorowanie wydajności

Obserwuj następujące metryki w produkcji:
- **Użycie sterty** – upewnij się, że wywołano `dispose()`.  
- **Czas przetwarzania na dokument** – loguj znaczniki czasu przed i po `annotator.save()`.  
- **Wskaźnik błędów** – przechwytuj wyjątki i kategoryzuj je.

### Typowe pułapki w produkcji

- **Blokowanie plików** – upewnij się, że przesłane pliki są zamknięte przed adnotacją.  
- **Równoczesne edycje** – wdroż optymistyczne blokowanie lub sprawdzanie wersji.  
- **Duże pliki (> 50 MB)** – zwiększ limit czasu JVM i rozważ API strumieniowe.

### Najlepsze praktyki obsługi błędów

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

## Podsumowanie

Masz teraz wszystkie niezbędne informacje, aby **utworzyć czyste PDF Java** i **adnotować PDF w Javie** podkreśleniami przy użyciu GroupDocs.Annotation. Pamiętaj, aby:

- Zarządzać zasobami przy pomocy try‑with‑resources lub wywoływać `dispose()`.  
- Wcześnie weryfikować współrzędne, aby uniknąć nieprawidłowych podkreśleń.  
- Implementować solidną obsługę błędów dla stabilności w produkcji.  
- Wykorzystać stylizację opartą na rolach i metadane, aby dopasować rozwiązanie do swojego workflow.

Co dalej? Spróbuj dodać inne typy adnotacji — podświetlenia, pieczątki lub zamiany tekstu — aby zbudować w pełni funkcjonalne rozwiązanie do przeglądu dokumentów.

## Najczęściej zadawane pytania

**P: Jak adnotować wiele fragmentów tekstu w jednej operacji?**  
O: Utwórz kilka obiektów `UnderlineAnnotation` z różnymi współrzędnymi i dodaj je kolejno przy użyciu `annotator.add()`.

**P: Czy mogę adnotować obrazy w dokumentach PDF?**  
O: Tak. Użyj tego samego systemu współrzędnych, upewniając się, że punkty leżą wewnątrz granic obrazu.

**P: Jakie formaty plików oprócz PDF obsługuje GroupDocs.Annotation?**  
O: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) oraz formaty obrazów takie jak JPEG, PNG, TIFF.

**P: Jak radzić sobie z bardzo dużymi dokumentami, aby nie wyczerpać pamięci?**  
O: Przetwarzaj dokumenty pojedynczo, zwiększaj stertę JVM (`-Xmx`) i zawsze szybko zwalniaj instancje `Annotator`.

**P: Czy można wyodrębnić istniejące adnotacje z dokumentu?**  
O: Tak. Użyj `annotator.get()`, aby pobrać wszystkie adnotacje, a następnie filtruj je według typu, autora lub strony.

---

**Ostatnia aktualizacja:** 2026-03-24  
**Testowane z:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---