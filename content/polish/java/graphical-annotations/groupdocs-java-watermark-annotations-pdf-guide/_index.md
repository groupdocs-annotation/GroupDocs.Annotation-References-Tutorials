---
categories:
- Java PDF Processing
date: '2026-07-30'
description: Dowiedz się, jak zastosować znak wodny na wszystkich stronach dokumentów
  PDF w Javie przy użyciu GroupDocs.Annotation. Ten krok‑po‑kroku poradnik pokazuje,
  jak dodać znak wodny PDF do wielu stron, zawierając przykłady kodu, wskazówki rozwiązywania
  problemów oraz najlepsze praktyki.
keywords:
- apply watermark all pages
- pdf watermark multiple pages
- java add watermark pdf
- add pdf watermark java
lastmod: '2026-07-30'
linktitle: Przewodnik po znakach wodnych PDF w Javie
og_description: Zastosuj znak wodny na wszystkich stronach dokumentów PDF przy użyciu
  GroupDocs.Annotation dla Javy. Ten przewodnik obejmuje znak wodny PDF na wielu stronach,
  konfigurację, kod oraz rozwiązywanie problemów w zwięzłym poradniku.
og_image_alt: 'Guide: Apply watermark to all pages of a PDF using GroupDocs.Annotation
  Java'
og_title: Zastosuj znak wodny na wszystkich stronach – Przewodnik po znakach wodnych
  PDF w Javie
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  headline: Apply Watermark All Pages – Java PDF Watermark Guide
  type: TechArticle
- description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  name: Apply Watermark All Pages – Java PDF Watermark Guide
  steps:
  - name: Import the Required Classes
    text: Before you can use the API, import the essential classes. **Definition:**
      Import statements bring the needed GroupDocs.Annotation classes into the current
      Java file, allowing you to reference them without fully qualified names.
  - name: Load the PDF Document
    text: Create the `Annotator` instance that points to your source PDF. **Definition:**
      The `Annotator` constructor loads the PDF file into a manageable object, preparing
      it for annotation operations. > **Pro tip:** For PDFs larger than 50 MB, consider
      increasing the JVM heap (`-Xmx4g`) and processing files
  - name: (Optional) Prepare Reply Metadata
    text: If you need to attach comments or approval notes to the watermark, create
      a `Reply` object. **Definition:** `Reply` stores user‑generated comments that
      accompany an annotation, useful for audit trails.
  - name: Configure the Watermark Appearance
    text: Set the visual properties such as text, color, rotation, size, and opacity.
      **Definition:** The following setters customize the watermark’s look and placement
      on each page.
  - name: Loop Through All Pages and Apply the Watermark
    text: To **apply watermark all pages**, iterate over the document’s page count
      and assign the annotation to each page. **Definition:** `annotator.getPageCount()`
      returns the total number of pages, enabling a loop that creates a separate `WatermarkAnnotation`
      per page.
  - name: Save the Watermarked PDF
    text: Finally, write the changes to a new file. The original PDF remains untouched.
      **Definition:** `annotator.save("output.pdf")` persists all added annotations
      into a new PDF file. That’s the complete flow for **apply watermark all pages**
      using GroupDocs.Annotation for Java.
  type: HowTo
- questions:
  - answer: Loop over the document’s page count, clone a configured `WatermarkAnnotation`
      for each page, set `setPageNumber(i)`, and add it with `annotator.add()`.
    question: How do I add watermarks to multiple pages in a PDF?
  - answer: GroupDocs.Annotation uses fonts installed on the host OS. Specify a font
      family that exists on the server; the library falls back to a default if the
      font isn’t found.
    question: Can I use custom fonts for my watermarks?
  - answer: Between **0.3** and **0.7** provides a balance—visible enough to be noticed
      but still allows underlying content to be read.
    question: What opacity setting works best for professional watermarks?
  - answer: Increase the JVM heap (`-Xmx4g` or more), process files one at a time,
      and always call `dispose()` after each document to free native resources.
    question: How should I handle very large PDF files?
  - answer: 'Yes—retrieve annotations with `annotator.get()`, filter for `WatermarkAnnotation`,
      then edit or delete as needed:'
    question: Is it possible to remove or modify existing watermarks?
  type: FAQPage
tags:
- java pdf watermark
- groupdocs annotation
- document security
- apply watermark all pages
- pdf processing
title: Zastosuj znak wodny na wszystkich stronach – Przewodnik po znakach wodnych
  PDF w Javie
type: docs
url: /pl/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/
weight: 1
---

# Zastosuj znak wodny na wszystkich stronach – Przewodnik po znakach wodnych PDF w Javie

W tym obszernej poradniku dowiesz się **jak zastosować znak wodny na wszystkich stronach** dokumentu PDF przy użyciu Javy i GroupDocs.Annotation. Niezależnie od tego, czy musisz chronić poufne raporty, oznaczyć marketingowe PDF‑y, czy dodać pieczęć „CONFIDENTIAL” na całym pliku, poniższe kroki przeprowadzą Cię przez wszystko — od konfiguracji Maven po zaawansowaną personalizację — abyś mógł wdrożyć niezawodne rozwiązanie w kilka minut.

## Szybkie odpowiedzi
- **Jaka biblioteka może dodać znak wodny PDF na wielu stronach w Javie?** GroupDocs.Annotation for Java.  
- **Czy potrzebuję licencji?** Yes, a free trial works for development; a full license is required for production.  
- **Czy mogę dodać znak wodny na wszystkich stronach jednocześnie?** Yes – create a watermark annotation for each page in a loop.  
- **Jaka wersja Javy jest wymagana?** JDK 8+ (JDK 11+ recommended).  
- **Jak kontrolować krycie?** Use `setOpacity(double)` where 0.0 is fully transparent and 1.0 is fully opaque.

## Dlaczego potrzebujesz znaków wodnych PDF (i jak Java to ułatwia)

Czy kiedykolwiek martwiłeś się, że poufny PDF może zostać udostępniony bez Twojej zgody? Albo potrzebowałeś szybkiego sposobu na oznaczenie każdej strony broszury sprzedażowej? Dodawanie znaków wodnych programowo eliminuje ręczną pracę, zapewnia spójność i wzmacnia bezpieczeństwo dokumentu. Z Javą i GroupDocs.Annotation — jedną z najsolidniejszych **java add watermark pdf** bibliotek — uzyskasz precyzyjną kontrolę nad położeniem, obrotem, kolorem i kryciem, jednocześnie efektywnie obsługując duże pliki.

**Co opanujesz po przeczytaniu tego przewodnika:**
- Konfigurowanie GroupDocs.Annotation dla znaków wodnych w Javie  
- Tworzenie własnych adnotacji znaków wodnych, które stosują się do **wszystkich stron**  
- Obsługa dużych plików PDF bez wyczerpywania pamięci  
- Rozwiązywanie typowych problemów i optymalizacja wydajności  

## Czym jest znak wodny PDF i dlaczego używać go na wielu stronach?

Znak wodny PDF to nakładka, która pojawia się nad treścią dokumentu, nie zmieniając podstawowego tekstu ani obrazów. Dodanie znaku wodnego do **wszystkich stron** zapewnia, że każda strona zawiera tę samą markę lub informację poufności, zapobiegając przypadkowemu rozpowszechnianiu nieoznaczonych stron.

## Wymagania wstępne

### Niezbędne wymagania
- **Środowisko Java:** JDK 8 lub wyższy (zalecany JDK 11+), Maven 3.6+, dowolne IDE (IntelliJ, Eclipse, VS Code).  
- **Wymagania wiedzy:** Podstawowa składnia Javy, operacje I/O na plikach, zarządzanie zależnościami Maven.  
- **Uprawnienia projektu:** Dostęp do zapisu w katalogu wyjściowym oraz wystarczająca ilość RAM dla dużych PDF‑ów (≥ 4 GB zalecane dla plików powyżej 200 stron).

## Konfigurowanie środowiska znaków wodnych PDF w Javie

### Dodawanie GroupDocs.Annotation do projektu

Najpierw dodaj artefakt Maven GroupDocs.Annotation. Ta zależność pobiera wszystkie wymagane pliki binarne i biblioteki tranzytywne.

**Definicja:** Element Maven `<dependency>` deklaruje bibliotekę GroupDocs.Annotation dla Twojego projektu, umożliwiając kompilatorowi odnalezienie plików JAR podczas budowania.  

```xml
<!-- Maven dependency for GroupDocs.Annotation -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```
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

**Wskazówka:** Zawsze używaj najnowszej wydanej wersji (przykład pokazuje 25.2, najnowszą w 2025 roku), aby korzystać z poprawek błędów i ulepszeń wydajności.

### Uzyskanie licencji

Potrzebujesz ważnej licencji do wdrożeń produkcyjnych. Wybierz opcję, która pasuje do Twojego harmonogramu:

1. **Bezpłatna wersja próbna:** Idealna do rozwoju i testów. Pobierz z [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
2. **Licencja tymczasowa:** Pełny zestaw funkcji do oceny. Uzyskaj ją ze [Strony licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/)  
3. **Pełna licencja:** Wymagana do użytku komercyjnego. Zakup przez [Stronę zakupu GroupDocs](https://purchase.groupdocs.com/buy)

### Podstawowa konfiguracja, która naprawdę działa

Po dodaniu zależności i uzyskaniu pliku licencji, zainicjalizuj obiekt `Annotator`. Obiekt ten ładuje PDF do pamięci i udostępnia API do tworzenia adnotacji.

**Definicja:** `Annotator` jest głównym punktem wejścia GroupDocs.Annotation; zarządza ładowaniem PDF, tworzeniem adnotacji i zapisywaniem.  

```java
// Initialize Annotator with a license and input PDF
Annotator annotator = new Annotator("input.pdf", "GroupDocs.Annotation.lic");
```
```java
import com.groupdocs.annotation.Annotator;

public class WatermarkSetup {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
        Annotator annotator = new Annotator(inputFilePath);
        
        // Your watermark code goes here...
        // Always remember to dispose!
        annotator.dispose();
    }
}
```

**Typowy błąd, którego należy unikać:** Zapomnienie wywołania `annotator.dispose()` po przetworzeniu; może to powodować wycieki pamięci, szczególnie przy obsłudze wielu dokumentów w partii.

## Jak zastosować znak wodny na wszystkich stronach w Javie

Aby dodać znak wodny do każdej strony, tworzysz `WatermarkAnnotation`, ustawiasz jego właściwości wizualne, a następnie dodajesz osobną instancję tej adnotacji do każdej strony w pętli. Pętla używa liczby stron dokumentu, przypisuje właściwy numer strony i na końcu zapisuje zmodyfikowany PDF.

### Zrozumienie adnotacji znaków wodnych

`WatermarkAnnotation` reprezentuje warstwę nakładki, która może zawierać tekst, niestandardowe kolory, obrót i krycie. W przeciwieństwie do prostego dodania tekstu, jest przechowywana jako adnotacja, co umożliwia jej późniejsze usunięcie lub edycję.

**Definicja:** `WatermarkAnnotation` jest klasą w GroupDocs.Annotation, która kapsułkuje wszystkie właściwości wizualne nakładki znaku wodnego.  

```java
WatermarkAnnotation watermark = new WatermarkAnnotation();
```
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.WatermarkAnnotation;
import java.util.ArrayList;
import java.util.Calendar;
```

### Krok 1: Importowanie wymaganych klas

Zanim będziesz mógł używać API, zaimportuj niezbędne klasy.

**Definicja:** Instrukcje importu wprowadzają potrzebne klasy GroupDocs.Annotation do bieżącego pliku Java, umożliwiając odwoływanie się do nich bez pełnych nazw kwalifikowanych.  

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.annotation.WatermarkAnnotation;
import com.groupdocs.annotation.models.common.Rectangle;
import com.groupdocs.annotation.models.annotation.Reply;
```
```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/AddWatermarkAnnotation.pdf";

final Annotator annotator = new Annotator(inputFilePath);
```

### Krok 2: Załadowanie dokumentu PDF

Utwórz instancję `Annotator`, która wskazuje na Twój źródłowy PDF.

**Definicja:** Konstruktor `Annotator` ładuje plik PDF do zarządzalnego obiektu, przygotowując go do operacji adnotacji.  

```java
Annotator annotator = new Annotator("sample.pdf");
```
```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```

> **Wskazówka:** Dla PDF‑ów większych niż 50 MB rozważ zwiększenie sterty JVM (`-Xmx4g`) i przetwarzanie plików kolejno, aby utrzymać niskie zużycie pamięci.

### Krok 3: (Opcjonalnie) Przygotowanie metadanych odpowiedzi

Jeśli musisz dołączyć komentarze lub notatki zatwierdzające do znaku wodnego, utwórz obiekt `Reply`.

**Definicja:** `Reply` przechowuje generowane przez użytkownika komentarze towarzyszące adnotacji, przydatne w ścieżkach audytu.  

```java
Reply reply = new Reply();
reply.setComment("Confidential – Internal Use Only");
```
```java
ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

WatermarkAnnotation watermark = new WatermarkAnnotation();
watermark.setAngle(75.0); // Set the angle of the watermark.
watermark.setBox(new Rectangle(200, 200, 100, 50)); // Define position and size with a rectangle.
watermark.setCreatedOn(Calendar.getInstance().getTime());
watermark.setText("Watermark");
watermark.setFontColor(65535); // Yellow color in ARGB format
watermark.setFontSize(12.0);
watermark.setMessage("This is a watermark annotation");
watermark.setOpacity(0.7);
watermark.setPageNumber(0);
watermark.setReplies(replies);
```

### Krok 4: Konfiguracja wyglądu znaku wodnego

Ustaw właściwości wizualne, takie jak tekst, kolor, obrót, rozmiar i krycie.

**Definicja:** Poniższe settery dostosowują wygląd i położenie znaku wodnego na każdej stronie.  

```java
watermark.setText("CONFIDENTIAL");
watermark.setAngle(75.0);                     // Diagonal orientation
watermark.setBox(new Rectangle(200, 200, 300, 100)); // Position & size
watermark.setFontColor(65535);               // Yellow (ARGB)
watermark.setOpacity(0.7);                   // 70% opacity
watermark.setReply(reply);                   // Attach the optional reply
```
```java
annotator.add(watermark);
annotator.save(outputPath);
annotator.dispose();
```

### Krok 5: Przejdź przez wszystkie strony i zastosuj znak wodny

Aby **zastosować znak wodny na wszystkich stronach**, iteruj po liczbie stron dokumentu i przypisz adnotację do każdej strony.

**Definicja:** `annotator.getPageCount()` zwraca całkowitą liczbę stron, umożliwiając pętlę tworzącą osobny `WatermarkAnnotation` dla każdej strony.  

```java
int pageCount = annotator.getPageCount();
for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation pageWatermark = watermark.clone(); // Duplicate settings
    pageWatermark.setPageNumber(i);                       // Zero‑based index
    annotator.add(pageWatermark);                         // Add to current page
}
```
```java
// Get total page count first
int pageCount = annotator.getDocument().getPages().size();

for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation watermark = new WatermarkAnnotation();
    // Reuse the same configuration or customize per page
    watermark.setAngle(45.0);
    watermark.setText("CONFIDENTIAL");
    watermark.setFontColor(16711680); // Red
    watermark.setOpacity(0.3);
    watermark.setFontSize(24.0);
    watermark.setBox(new Rectangle(100, 300, 400, 100));
    watermark.setPageNumber(i);
    annotator.add(watermark);
}
annotator.save(outputPath);
annotator.dispose();
```

### Krok 6: Zapisz PDF z znakiem wodnym

Na koniec zapisz zmiany do nowego pliku. Oryginalny PDF pozostaje niezmieniony.

**Definicja:** `annotator.save("output.pdf")` zapisuje wszystkie dodane adnotacje do nowego pliku PDF.  

```java
annotator.save("output_watermarked.pdf");
annotator.dispose(); // Release resources
```
```java
// Better error handling approach
try {
    File inputFile = new File(inputFilePath);
    if (!inputFile.exists()) {
        throw new FileNotFoundException("Input PDF not found: " + inputFilePath);
    }
    
    Annotator annotator = new Annotator(inputFilePath);
    // ... your watermark code
} catch (Exception e) {
    System.err.println("Error processing PDF: " + e.getMessage());
}
```

To pełny przepływ dla **zastosowania znaku wodnego na wszystkich stronach** przy użyciu GroupDocs.Annotation dla Javy.

## Typowe problemy i jak je naprawić

### Błędy „Plik nie znaleziony”

```java
// Example of handling missing file paths
File inputFile = new File("nonexistent.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Input PDF not found at: " + inputFile.getAbsolutePath());
}
```
```java
WatermarkAnnotation confidentialWatermark = new WatermarkAnnotation();
confidentialWatermark.setAngle(45.0);
confidentialWatermark.setText("CONFIDENTIAL");
confidentialWatermark.setFontColor(16711680); // Red
confidentialWatermark.setOpacity(0.3); // Subtle but visible
confidentialWatermark.setFontSize(24.0);
confidentialWatermark.setBox(new Rectangle(100, 300, 400, 100));
```

- Sprawdź ścieżki bezwzględne i upewnij się, że plik istnieje.  
- Sprawdź uprawnienia odczytu/zapisu w katalogach wejściowym i wyjściowym.  
- Utwórz folder wyjściowy wcześniej, jeśli nie istnieje.

### Problemy z pamięcią przy dużych PDF‑ach

- Zawsze wywołuj `annotator.dispose()` po przetworzeniu.  
- Przetwarzaj PDF‑y pojedynczo; unikaj równoległych strumieni, chyba że biblioteka jest potwierdzona jako bezpieczna wątkowo.  
- Zwiększ stertę JVM (`-Xmx4g` lub wyższą) dla plików powyżej 200 stron.

### Pozycjonowanie znaku wodnego nie jest zgodne z oczekiwaniami

- Punkt początkowy współrzędnych PDF to **lewy dolny**; odpowiednio dostosuj wartości `Rectangle`.  
- Testuj różne rozmiary stron (A4 vs. Letter), ponieważ wymiary wpływają na pozycjonowanie.  
- Użyj `setOpacity(0.5)`, jeśli znak wodny jest zbyt słaby na tłustych tłach.

### Problemy z kolorem czcionki

GroupDocs.Annotation oczekuje wartości całkowitych ARGB. Popularne kolory:
- Czerwony: `16711680`  
- Niebieski: `255`  
- Zielony: `65280`  
- Czarny: `0`  
- Biały: `16777215`  
- Żółty: `65535` (użyty w przykładzie)

## Praktyczne zastosowania znaków wodnych PDF w Javie

### Ochrona dokumentów biznesowych

```java
// Apply a corporate logo watermark across all pages of a contract
watermark.setText("© Acme Corp – Confidential");
```
```java
WatermarkAnnotation brandWatermark = new WatermarkAnnotation();
brandWatermark.setText("© YourCompany 2025");
brandWatermark.setFontColor(0); // Black
brandWatermark.setOpacity(0.6);
brandWatermark.setFontSize(10.0);
brandWatermark.setBox(new Rectangle(400, 50, 150, 30));
```

### Branding materiałów marketingowych

```java
// Use a semi‑transparent brand slogan as a watermark
watermark.setText("Acme Marketing 2026");
watermark.setOpacity(0.4);
```
```java
WatermarkAnnotation versionWatermark = new WatermarkAnnotation();
versionWatermark.setText("DRAFT - v2.1");
versionWatermark.setFontColor(255); // Blue
versionWatermark.setOpacity(0.8);
versionWatermark.setBox(new Rectangle(50, 750, 100, 30));
```

### Kontrola wersji dokumentów

```java
// Append version number dynamically
watermark.setText("Version 3.2 – Reviewed");
```
```java
public void processMultiplePDFs(List<String> pdfPaths) {
    for (String path : pdfPaths) {
        Annotator annotator = null;
        try {
            annotator = new Annotator(path);
            // Add your watermark logic here
            annotator.save(path.replace(".pdf", "_watermarked.pdf"));
        } finally {
            if (annotator != null) {
                annotator.dispose(); // Always dispose, even if exceptions occur
            }
        }
    }
}
```

## Wskazówki dotyczące optymalizacji wydajności

### Najlepsze praktyki zarządzania pamięcią

```java
// Explicitly release resources after each document
annotator.dispose();
System.gc(); // Hint to the JVM (optional)
```
```java
public class WatermarkTemplates {
    public static WatermarkAnnotation createConfidentialWatermark() {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setAngle(45.0);
        watermark.setText("CONFIDENTIAL");
        watermark.setFontColor(16711680);
        watermark.setOpacity(0.3);
        watermark.setFontSize(24.0);
        return watermark;
    }
    
    public static WatermarkAnnotation createBrandWatermark(String companyName) {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setText("© " + companyName + " 2025");
        watermark.setFontColor(0);
        watermark.setOpacity(0.6);
        watermark.setFontSize(10.0);
        return watermark;
    }
}
```

- Przetwarzaj dokumenty kolejno, aby utrzymać niski rozmiar sterty.  
- Używaj wskaźnika postępu dla zadań wsadowych, aby monitorować zużycie pamięci.  
- Unikaj ładowania całego PDF‑a do pamięci, gdy potrzebny jest znak wodny tylko na wybranym zestawie stron; biblioteka obsługuje ładowanie na poziomie stron.

### Wskazówki dotyczące organizacji kodu

- Zamknij tworzenie znaku wodnego w metodzie pomocniczej: `createWatermark(String text, double opacity, int angle)`.  
- Trzymaj konfigurację (kolory, czcionki, krycie) w zewnętrznym pliku właściwości, aby łatwo dostosowywać ją w różnych środowiskach.

## Najczęściej zadawane pytania

**P: Jak dodać znaki wodne do wielu stron w PDF?**  
A: Loop over the document’s page count, clone a configured `WatermarkAnnotation` for each page, set `setPageNumber(i)`, and add it with `annotator.add()`.

**P: Czy mogę używać własnych czcionek w moich znakach wodnych?**  
A: GroupDocs.Annotation uses fonts installed on the host OS. Specify a font family that exists on the server; the library falls back to a default if the font isn’t found.

**P: Jakie ustawienie krycia jest najlepsze dla profesjonalnych znaków wodnych?**  
A: Between **0.3** and **0.7** provides a balance—visible enough to be noticed but still allows underlying content to be read.

**P: Jak postępować z bardzo dużymi plikami PDF?**  
A: Increase the JVM heap (`-Xmx4g` or more), process files one at a time, and always call `dispose()` after each document to free native resources.

**P: Czy można usunąć lub zmodyfikować istniejące znaki wodne?**  
A: Yes—retrieve annotations with `annotator.get()`, filter for `WatermarkAnnotation`, then edit or delete as needed:  

```java
List<AnnotationBase> watermarks = annotator.get().stream()
    .filter(a -> a instanceof WatermarkAnnotation)
    .collect(Collectors.toList());
annotator.delete(watermarks.get(0)); // Example: delete first watermark
```
```java
// Get existing annotations
List<AnnotationBase> annotations = annotator.get();
// Filter and modify as needed
```

## Dodatkowe zasoby

- **Dokumentacja:** [GroupDocs Annotation Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **Pełna referencja API:** [GroupDocs Annotation Java API](https://reference.groupdocs.com/annotation/java/)  
- **Pobierz najnowszą wersję:** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Licencjonowanie komercyjne:** [Purchase GroupDocs](https://purchase.groupdocs.com/buy)  
- **Wsparcie społeczności:** [GroupDocs Forums](https://forum.groupdocs.com/c/annotation/10)

---

**Ostatnia aktualizacja:** 2026-07-30  
**Testowano z:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---

## Powiązane samouczki

- [Załaduj PDF w Javie z GroupDocs Annotation: Przewodnik po ładowaniu dokumentów](/annotation/java/document-loading/)  
- [Dodaj adnotacje PDF w Javie – Kompletny przewodnik GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Jak dodać obraz do PDF przy użyciu Javy i GroupDocs Annotation](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)