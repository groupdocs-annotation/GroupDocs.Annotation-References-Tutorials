---
categories:
- Java Development
date: '2026-05-16'
description: Dowiedz się, jak tworzyć odpowiedzi na adnotacje w Java przy użyciu GroupDocs.Annotation.
  Opanuj adnotacje PDF w Java dzięki praktycznym przykładom, wskazówkom dotyczącym
  wydajności i najlepszym praktykom.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Samouczek Java PDF Annotation
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
title: 'Java PDF Annotation Library: tworzenie odpowiedzi na adnotację w Java'
type: docs
url: /pl/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Biblioteka Java do adnotacji PDF: tworzenie odpowiedzi na adnotację w Java

Jeśli potrzebujesz **create annotation reply java** dla plików PDF — niezależnie od tego, czy tworzysz portal do przeglądu umów, system e‑learningowy, czy potok przetwarzania wsadowego — ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu GroupDocs.Annotation dla Javy. Przejdziemy przez konfigurację, tworzenie adnotacji typu squiggly, wątkowanie odpowiedzi oraz optymalizację wydajności, abyś mógł dostarczyć niezawodne rozwiązanie w ciągu dni, a nie tygodni.

## Szybkie odpowiedzi
- **Jaki jest główny cel GroupDocs.Annotation?** Umożliwia programowe tworzenie, modyfikację i wyodrębnianie adnotacji PDF w Javie.  
- **Jak dodać adnotację squiggly?** Utwórz instancję `SquigglyAnnotation`, ustaw jej geometrię i styl, a następnie wywołaj `annotator.add(...)`.  
- **Czy mogę dołączyć odpowiedzi do adnotacji?** Tak — utwórz obiekty `Reply`, ustaw autora i tekst, i powiąż je z adnotacją nadrzędną.  
- **Czy potrzebuję licencji do produkcji?** Zdecydowanie tak; bez ważnej licencji wyjściowy plik będzie zawierał znaki wodne.  
- **Czy nadaje się do przetwarzania wsadowego?** Tak — użyj try‑with‑resources, aby otworzyć każdy dokument, dodać adnotacje i zamknąć go, utrzymując niskie zużycie pamięci.

## Dlaczego programiści Java potrzebują bibliotek do adnotacji PDF

Ręczne oznaczanie plików PDF jest czasochłonne i podatne na błędy, szczególnie gdy trzeba przeglądać setki umów lub arkuszy egzaminacyjnych. Biblioteka Java do adnotacji PDF automatyzuje tę pracę, pozwalając osadzać podświetlenia, faliste podkreślenia i wątkowane komentarze bezpośrednio w pliku. Efektem jest przeszukiwalny, przenośny dokument, który zachowuje wszystkie adnotacje bez potrzeby osobnego przeglądarki.

**Co opanujesz w tym przewodniku**
- Instalacja i licencjonowanie GroupDocs.Annotation w projekcie Maven  
- Tworzenie adnotacji squiggly wyglądających jak natywne podkreślenia w Wordzie  
- Dodawanie wątkowanych odpowiedzi do dowolnej adnotacji w celu współpracy przy przeglądzie  
- Optymalizacja zużycia pamięci i CPU przy przetwarzaniu dużych plików PDF  
- Wdrażanie rozwiązania w Spring Boot, mikro‑serwisach lub aplikacjach desktopowych  

Niezależnie od tego, czy budujesz system przeglądu dokumentów prawnych, narzędzie do oceniania edukacyjnego, czy zautomatyzowany potok kontroli jakości, poniższe techniki zapewnią Ci gotową do produkcji bazę.

## Co to jest create annotation reply java?

`create annotation reply java` to programowy proces dołączania wątku komentarzy (Reply) do istniejącej adnotacji PDF przy użyciu Javy. Odpowiedzi pozwalają wielu recenzentom dyskutować o konkretnym oznaczeniu bez opuszczania dokumentu, umożliwiając płynną, w‑miejscu współpracę. Ta funkcja zamienia statyczny PDF w interaktywną platformę dyskusyjną, zachowując kontekst i ścieżki audytu bezpośrednio w pliku.

## Wymagania wstępne: Przygotowanie środowiska

Zanim przejdziemy do kodu, sprawdź, czy Twoja stacja robocza spełnia poniższe wymagania:

- **JDK** 8 lub wyższy (zalecany JDK 11 + dla lepszej wydajności garbage‑collection)  
- **Maven** lub **Gradle** do zarządzania zależnościami (przykłady używają Maven)  
- IDE z obsługą Maven (IntelliJ IDEA, Eclipse lub VS Code)  
- Co najmniej **2 GB** wolnej pamięci RAM dla IDE i testów  
- Przykładowe pliki PDF do eksperymentów (możesz wygenerować proste PDF w dowolnym edytorze PDF)

GroupDocs.Annotation działa w pełni w procesie; nie są wymagane zewnętrzne przeglądarki PDF ani biblioteki natywne.

## Konfiguracja GroupDocs.Annotation dla Javy

Integracja biblioteki to proces kilku kroków, ale kilka ukrytych pułapek może powodować błędy w czasie wykonywania, jeśli je pominiesz.

### Konfiguracja zależności Maven

Dodaj repozytorium i zależność do swojego `pom.xml`. Umieść element `<repositories>` **przed** `<dependencies>`, aby Maven mógł rozwiązać artefakt.

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

> **Wskazówka:** Sprawdź stronę wydań GroupDocs, aby uzyskać najnowszą wersję. Nowe wydania często zawierają wsparcie dla nowych standardów PDF i ulepszenia wydajności.

### Konfiguracja licencji (nie pomijaj tego!)

GroupDocs.Annotation wymaga pliku licencji do użytku produkcyjnego. Bez niego każdy wygenerowany PDF będzie zawierał znak wodny.

1. **Free Trial** – Pełny zestaw funkcji na 30 dni, idealny do oceny.  
2. **Temporary License** – Dobra do rozwoju i testów wewnętrznych.  
3. **Full License** – Wymagana przy każdej komercyjnej implementacji.  

Umieść plik `GroupDocs.Annotation.lic` w folderze resources i załaduj go podczas uruchamiania:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Częsty problem:** Zapomnienie o kroku licencji skutkuje znakami wodnymi w PDF i cichymi niepowodzeniami wywołań API. Zawsze weryfikuj licencję na początku procedury uruchamiania.

## Kompletny przewodnik implementacji: Dodawanie adnotacji squiggly

Poniżej znajduje się krok po kroku przewodnik, który pokazuje, jak **create annotation reply java** podczas tworzenia adnotacji squiggly. Każdy krok zawiera zwięzłe wyjaśnienie, abyś zrozumiał „dlaczego” każdej linii.

### Krok 1: Import wszystkich wymaganych klas

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` jest punktem wejścia dla wszystkich operacji na poziomie dokumentu.  
- `Point` reprezentuje współrzędną na stronie (X i Y mierzone od lewego górnego rogu).  
- `SquigglyAnnotation` definiuje falistą podkreślenie używaną do zaznaczania błędów.  
- `Reply` przechowuje wątkowane komentarze dołączone do adnotacji.  
- `SaveOptions` pozwala kontrolować format wyjścia i kompresję.

### Krok 2: Utwórz i skonfiguruj swoją adnotację Squiggly

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

SquigglyAnnotation to klasa tworząca falistą podkreślenie używaną do zaznaczania błędów w PDF.

- **System współrzędnych**: Punkty zaczynają się w lewym górnym rogu. Dwa powyższe punkty rysują poziomą falistą linię od (100, 200) do (300, 200).  
- **Opacity** 0.7 oznacza, że adnotacja jest w 70 % nieprzezroczysta, pozwalając na czytelność tekstu pod nią.

### Krok 3: Dodaj interaktywne odpowiedzi (opcjonalne, ale potężne)

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

Reply to klasa reprezentująca wątek komentarzy dołączony do adnotacji.

- Odpowiedzi tworzą **wątkowaną dyskusję** bezpośrednio na adnotacji, odzwierciedlając doświadczenie współczesnych recenzentów PDF.  
- Każda odpowiedź przechowuje informacje o autorze i znacznik czasu, które możesz później filtrować lub wyświetlać w interfejsie.

### Krok 4: Zastosuj adnotację i zapisz dokument

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- Konstrukcja **try‑with‑resources** automatycznie zamyka `Annotator`, zwalniając uchwyty plików i natywne bufory.  
- `save` zapisuje zmodyfikowany PDF do `output.pdf`.  

> **Uwaga o pamięci:** `Annotator` ładuje tylko strony, które modyfikujesz. Dla PDF‑ów o setkach stron, takie podejście utrzymuje zużycie sterty poniżej 150 MB na typowym serwerze.

## Zaawansowane opcje konfiguracji

### Dostosowywanie wyglądu adnotacji

Możesz precyzyjnie dostroić styl wizualny, aby pasował do wytycznych Twojej marki:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** kontroluje grubość linii (w punktach).  
- **ARGB** format zawiera kanał alfa dla przejrzystości.

### Precyzyjne pozycjonowanie adnotacji

Otrzymanie prawidłowych współrzędnych może być trudne w PDF‑ach o różnych rozmiarach stron. Postępuj zgodnie z tym systematycznym podejściem:

1. **Otwórz PDF w przeglądarce** (np. Adobe Acrobat) i zanotuj wartości linijki dla docelowego obszaru.  
2. **Przelicz wartości linijki** na punkty (1 punkt = 1/72 cala).  
3. **Użyj `annotator.getPageInfo(pageIndex)`** aby pobrać szerokość i wysokość strony, a następnie obliczyć pozycje względne.

## Typowe problemy i rozwiązania

### Problem: Adnotacje nie pojawiają się

**Najbardziej prawdopodobne przyczyny**
- Punkty leżą poza granicami strony  
- Licencja nie została załadowana (znak wodny ukrywa adnotację)  
- Nieprawidłowy numer strony (strony są numerowane od zera w API)  

**Lista kontrolna rozwiązania**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Problem: Słaba wydajność przy dużych plikach

Ładowanie 500‑stronnicowego PDF‑a do pamięci może spowolnić usługę. Zminimalizuj to, stosując:

- **Przetwarzanie jednej strony na raz** – otwórz dokument, adnotuj jedną stronę, zapisz, a następnie przejdź do kolejnej.  
- **Streaming** – użyj API strumieniowego `Annotator`, aby uniknąć buforowania całego dokumentu.  
- **Cache** – przechowuj często używane PDF‑y w szybkim cache (np. Redis) i adnotuj kopię z cache.

### Problem: Wartości kolorów nie działają

GroupDocs oczekuje **ARGB** (Alpha, Red, Green, Blue) zamiast zwykłego RGB. Wartość ARGB `0xFFFF0000` oznacza w pełni nieprzezroczystą czerwień. Jeśli podasz `0xFF0000`, biblioteka interpretuje to niepoprawnie, co skutkuje czarną adnotacją.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Najlepsze praktyki wydajnościowe

### Zarządzanie pamięcią

Gdy adnotujesz dziesiątki PDF‑ów w zadaniu wsadowym, opakuj każdy plik w osobny blok try‑with‑resources:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Ten wzorzec zapewnia zwolnienie natywnych buforów po każdej iteracji, zapobiegając **OutOfMemoryError** w długotrwałych procesach.

### Optymalizacja przetwarzania wsadowego

Dla środowisk o wysokiej przepustowości rozważ równoległe strumienie połączone z ograniczoną pulą wątków:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Bounded pool** zapobiega wybuchowi wątków, a równoległe strumienie utrzymują procesory w użyciu.

### Rozważania dotyczące rozmiaru pliku

Duże PDF‑y (> 100 MB) mogą obniżać wydajność. Zastosuj następujące strategie:

- **Pre‑compress** źródłowy PDF przy użyciu narzędzia takiego jak Ghostscript przed adnotacją.  
- **Adnotuj tylko potrzebne strony** – pomijaj strony, które nie wymagają adnotacji.  
- **Podziel** dokument na logiczne sekcje (np. rozdział po rozdziale) i przetwarzaj każdy fragment niezależnie.

## Zastosowania w rzeczywistych projektach

### Systemy przeglądu dokumentów

Firmy prawnicze często muszą oznaczać problematyczne klauzule. Faliste adnotacje połączone z wątkowanymi odpowiedziami pozwalają wielu prawnikom dyskutować o jednym paragrafie bez opuszczania PDF:

- **Lawyer A** dodaje czerwone squiggly pod klauzulą i pisze „Niejasne sformułowanie”.  
- **Lawyer B** odpowiada „Dodaj definicję ‘material breach’”.  
- Cała dyskusja pozostaje osadzona, przeszukiwalna i audytowalna.

### Integracja z istniejącymi systemami

GroupDocs.Annotation współpracuje płynnie z popularnymi frameworkami Java:

- **Spring Boot** – udostępnij endpoint REST `/api/annotate`, który przyjmuje wieloczęściowy upload PDF, dodaje adnotacje i zwraca wynik w strumieniu.  
- **JSF** – powiąż akcje adnotacji z komponentami UI dla adnotacji w locie w widoku webowym.  
- **Mikroserwisy** – mały rozmiar biblioteki (< 15 MB) pozwala konteneryzować ją przy użyciu Docker i skalować poziomo.

### Automatyzacja przepływu pracy

Połącz adnotacje z innymi produktami GroupDocs (np. GroupDocs.Signature), aby zbudować kompleksowe potoki:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Kiedy używać adnotacji Squiggly vs. alternatyw

| Przypadek użycia | Zalecana adnotacja |
|------------------|--------------------|
| Oznaczanie błędów ortograficznych lub gramatycznych | **Squiggly** – wizualna wskazówka podobna do edytorów tekstu |
| Podświetlanie ważnych sekcji bez sugerowania błędu | **Highlight** – przezroczysta nakładka |
| Dostarczanie szczegółowej informacji zwrotnej | **Text** lub **Comment** – notatka w formie wolnego tekstu |
| Zatwierdzanie lub odrzucanie dokumentu | **Stamp** – etykieta „Approved” lub „Rejected” |

## Zakończenie

Masz teraz kompletny, gotowy do produkcji przepis na **create annotation reply java** przy użyciu GroupDocs.Annotation. Opanowując API, obsługując licencjonowanie i stosując powyższe wskazówki wydajnościowe, możesz:

- Automatyzować oznaczanie błędów w tysiącach PDF‑ów  
- Umożliwić współpracę i wątkowane dyskusje wewnątrz samego pliku  
- Utrzymać niskie zużycie pamięci nawet przy przetwarzaniu ogromnych dokumentów  

**Kolejne kroki**
1. Eksperymentuj z innymi typami adnotacji (highlight, stamp, text).  
2. Zbuduj usługę REST, która przyjmuje PDF‑y, adnotuje je i zwraca wynik.  
3. Zbadaj API ekstrakcji (`annotator.get()`), aby pobrać istniejące komentarze do analiz.  

Moc programowej adnotacji PDF polega na możliwości zastąpienia żmudnego ręcznego oznaczania powtarzalnym, audytowalnym kodem. Niezależnie od tego, czy tworzysz niszowy produkt legal‑tech, czy ogólnego przeznaczenia silnik przepływu dokumentów, techniki w tym przewodniku zapewniają solidną podstawę do dalszego rozwoju.

## Najczęściej zadawane pytania

**P: Co sprawia, że GroupDocs.Annotation jest lepszy od innych bibliotek Java PDF?**  
O: GroupDocs.Annotation koncentruje się wyłącznie na przepływach pracy z adnotacjami, oferując ponad 30 typów adnotacji, wątkowane odpowiedzi i natywne wsparcie dla ponad 50 formatów plików, przy jednoczesnym utrzymaniu zużycia pamięci poniżej 200 MB dla PDF‑ów o 500 stronach.

**P: Czy mogę używać tej biblioteki w aplikacjach Spring Boot?**  
O: Zdecydowanie tak. Utwórz `@RestController`, który wstrzykuje usługę `Annotator`, przetwarza wieloczęściowe uploady i strumieniuje adnotowany PDF z powrotem do klienta. Pamiętaj o skonfigurowaniu puli wątków dla równoczesnych żądań.

**P: Jak obsługiwać dokumenty o różnych rozmiarach stron?**  
O: Pobierz wymiary każdej strony za pomocą `annotator.getPageInfo(pageIndex)` i oblicz współrzędne względne (np. procenty) zamiast twardo kodować wartości w punktach. To zapewnia prawidłowe wyświetlanie adnotacji na stronach A4, Letter i o niestandardowych rozmiarach.

**P: Czy istnieje sposób na wyodrębnienie istniejących adnotacji z PDF‑ów?**  
O: Tak. Wywołaj `annotator.get()`, aby pobrać kolekcję wszystkich adnotacji, a następnie iteruj, aby odczytać właściwości takie jak autor, komentarz i geometria. Jest to przydatne w scenariuszach migracji lub analiz.

**P: Jaki jest najlepszy sposób obsługi uprawnień do adnotacji w systemach wieloużytkownikowych?**  
O: Zaimplementuj uwierzytelnianie na warstwie aplikacji, przechowuj identyfikator użytkownika w każdym `Reply` i egzekwuj reguły biznesowe (np. tylko autor lub administrator może edytować lub usuwać odpowiedź). Same API nie wymusza uprawnień, dając pełną elastyczność.

**P: Jak zoptymalizować zużycie pamięci przy przetwarzaniu setek PDF‑ów?**  
O: Używaj try‑with‑resources dla każdego dokumentu, przetwarzaj strony indywidualnie i rozważ ograniczoną pulę wątków, aby ograniczyć jednoczesne zużycie pamięci. Monitorowanie sterty JVM przy użyciu narzędzi takich jak VisualVM pomaga precyzyjnie dostroić ustawienie `-Xmx`.

**Ostatnia aktualizacja:** 2026-05-16  
**Testowano z:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Dodatkowe zasoby**

- [Dokumentacja GroupDocs.Annotation dla Javy](https://docs.groupdocs.com/annotation/java/)  
- [Pełna referencja API](https://reference.groupdocs.com/annotation/java/)

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

## Powiązane samouczki

- [Samouczek biblioteki Java PDF Annotation](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)  
- [Usuwanie odpowiedzi adnotacji w Java – zarządzanie odpowiedziami po ID z GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)  
- [Edycja adnotacji PDF w Java – kompletny samouczek GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)