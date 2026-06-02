---
categories:
- PDF Processing
date: '2026-05-26'
description: Dowiedz się, jak stworzyć system przeglądu dokumentów przy użyciu GroupDocs
  Annotation for .NET. Przewodnik krok po kroku obejmuje konfigurację, typy adnotacji,
  optymalizację wydajności oraz rozwiązywanie problemów dla programistów C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Utwórz system przeglądu dokumentów: PDF Annotation .NET Guide'
type: docs
url: /pl/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Utwórz system przeglądu dokumentów: Przewodnik po adnotacjach PDF w .NET

Jeśli potrzebujesz **systemu przeglądu dokumentów**, który pozwala użytkownikom dodawać komentarze, podświetlenia i kształty do plików PDF bezpośrednio z aplikacji .NET, trafiłeś we właściwe miejsce. GroupDocs.Annotation dla .NET eliminuje problemy związane z niskopoziomową obsługą PDF, jednocześnie dając precyzyjną kontrolę nad każdym typem adnotacji. W tym przewodniku zobaczysz, jak skonfigurować bibliotekę, dodać adnotacje typu obszar, elipsa i tekst, filtrować to, co zostaje zapisane, oraz utrzymać wysoką wydajność nawet przy plikach o setkach stron.

## Szybkie odpowiedzi
- **Jaka biblioteka obsługuje adnotacje PDF w .NET?** GroupDocs.Annotation for .NET.  
- **Czy mogę programowo dodawać podświetlenia, okręgi i komentarze?** Tak – użyj obiektów AreaAnnotation, EllipseAnnotation i TextAnnotation.  
- **Czy wymagana jest licencja do produkcji?** Ważna licencja GroupDocs jest obowiązkowa przy każdej produkcyjnej implementacji.  
- **Jak duży PDF może być przetwarzany?** Do 500 MB może być obsłużone bez wczytywania całego pliku do pamięci.  
- **Czy to pomoże mi stworzyć system przeglądu dokumentów?** Zdecydowanie – możesz zapisywać partiami, filtrować i wersjonować adnotacje dla recenzentów.

## Czym jest system przeglądu dokumentów?
System **przeglądu dokumentów** to rozwiązanie programowe, które pozwala wielu interesariuszom na adnotowanie, komentowanie i zatwierdzanie plików PDF w skoordynowanym przepływie pracy. Centralizuje opinie, śledzi zmiany i często eksportuje czystą wersję do ostatecznej akceptacji.

## Dlaczego używać GroupDocs Annotation dla .NET do stworzenia systemu przeglądu dokumentów?
GroupDocs Annotation obsługuje **ponad 30 typów adnotacji**, przetwarza pliki PDF o rozmiarze do **500 MB** i działa na **.NET Framework 4.6.1+**, **.NET Core 2.0+** oraz **.NET 6+**. Jego API pozwala dodawać, usuwać i filtrować adnotacje bez ingerencji w wewnętrzną strukturę PDF, co przyspiesza rozwój i zmniejsza liczbę błędów.

## Wymagania wstępne i konfiguracja środowiska

Before writing any code, make sure your development environment meets the following criteria:

- **IDE:** Visual Studio 2019 lub nowszy, lub VS Code z rozszerzeniem C#.  
- **Target Framework:** .NET Framework 4.6.1 + lub .NET Core 2.0 + (zalecamy .NET 6 dla nowych projektów).  
- **NuGet Access:** Możliwość instalacji pakietów z nuget.org.  
- **Sample PDFs:** Co najmniej jeden wielostronicowy PDF do testowania umieszczania adnotacji.  
- **Memory & Disk:** Minimum 4 GB RAM oraz wystarczająco wolnego miejsca na dysku dla plików tymczasowych (przetwarzanie adnotacji może generować tymczasowe strumienie).

### Zalecane praktyki programistyczne
- Trzymaj rozwiązanie pod kontrolą wersji (Git), aby móc cofać zmiany związane z adnotacjami.  
- Używaj dedykowanego folderu **Annotations** w projekcie do przechowywania plików konfiguracyjnych i kluczy licencyjnych.  
- Włącz **nullable reference types** (`<Nullable>enable</Nullable>`), aby wcześnie wykrywać potencjalne błędy związane z odwołaniami null.

## Rozpoczęcie: Instalacja GroupDocs.Annotation

### Metody instalacji

**Opcja 1: Konsola Menedżera Pakietów NuGet**  
Uruchom następujące polecenie w konsoli Menedżera Pakietów:  

`Install-Package GroupDocs.Annotation`

**Opcja 2: .NET CLI (zalecane dla rozwoju wieloplatformowego)**  
Wykonaj w terminalu:  

`dotnet add package GroupDocs.Annotation`

**Opcja 3: Interfejs Menedżera Pakietów w Visual Studio**  
- Kliknij prawym przyciskiem myszy projekt → **Manage NuGet Packages**  
- Wyszukaj **GroupDocs.Annotation**  
- Kliknij **Install** przy najnowszej stabilnej wersji

Wszystkie trzy metody instalują ten sam plik binarny; wybierz tę, która pasuje do Twojego przepływu pracy.

### Konfiguracja licencji

GroupDocs wymaga ważnej licencji do wszelkiego użycia produkcyjnego. Masz trzy opcje:

- **Free Trial:** 30‑dniowa ocena z pełnym zestawem funkcji.  
- **Temporary License:** Rozszerzona ocena dla rozwoju i testów.  
- **Commercial License:** Nieograniczone użycie w środowiskach produkcyjnych.

Klasa `License` ładuje i stosuje plik licencyjny GroupDocs, aby włączyć pełną funkcjonalność. Licencję możesz uzyskać na [Strona zakupu GroupDocs](https://purchase.groupdocs.com/buy). Po otrzymaniu pliku `.lic`, umieść go w folderze, który aplikacja może odczytać i wskaż go klasie `License` podczas uruchamiania.

### Weryfikacja początkowej konfiguracji

Utwórz mały program konsolowy, który wczytuje PDF i wypisuje liczbę stron na konsolę. Jeśli program uruchomi się bez wyjątków, biblioteka jest poprawnie zainstalowana i licencjonowana.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Uwaga:** Powyższy kod służy wyłącznie do ilustracji; nie musisz dodawać blokowanego kodu w ostatecznym artykule, ale wbudowany fragment pokazuje dokładne użycie API.

Jeśli zobaczysz wydrukowaną liczbę stron, jesteś gotowy, aby rozpocząć dodawanie rzeczywistych adnotacji.

## Główna implementacja: Dodawanie adnotacji do PDF

### Definicja kotwicy – Annotator

Klasa `Annotator` jest punktem wejścia dla wszystkich operacji adnotacji PDF w GroupDocs.Annotation dla .NET. Ładuje PDF do pamięci, udostępnia metody do dodawania, edytowania i pobierania adnotacji oraz obsługuje zapisywanie zmodyfikowanego dokumentu.

### Jak dodać adnotacje typu obszar i elipsa?

Wczytaj PDF za pomocą `new Annotator(...)`, utwórz obiekty `AreaAnnotation` i `EllipseAnnotation`, ustaw ich współrzędne i dodaj je do kolekcji annotatora. Na koniec wywołaj `Save`, aby zapisać zmiany. Ten przepływ pracy pozwala programowo podświetlać sekcje (obszar) lub otaczać ważne grafiki (elipsa) w jednej, atomowej operacji.

#### Krok 1: Inicjalizacja Annotatora
```csharp
var annotator = new Annotator("input.pdf");
```

#### Krok 2: Utwórz AreaAnnotation
`AreaAnnotation` reprezentuje prostokątny obszar podświetlenia na stronie PDF.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Krok 3: Utwórz EllipseAnnotation
`EllipseAnnotation` reprezentuje adnotację w kształcie elipsy na stronie PDF.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Krok 4: Dodaj adnotacje zbiorczo
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Wskazówka:** Dodawanie adnotacji w liście i wywołanie `Add` raz zmniejsza obciążenie I/O, szczególnie gdy trzeba wstawić dziesiątki znaczników na wielu stronach.

### Jak zapisać wybrane adnotacje?

`SaveOptions` konfiguruje sposób zapisu adnotowanego PDF, w tym które typy adnotacji mają być uwzględnione. GroupDocs.Annotation pozwala filtrować, które typy adnotacji są zapisywane do pliku wyjściowego. Utwórz instancję `SaveOptions`, ustaw kolekcję `AnnotationTypes` na typy, które chcesz zachować, i przekaż opcje do `Save`. To idealne rozwiązanie do generowania PDF tylko dla recenzentów lub usuwania tymczasowych notatek przed archiwizacją.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Scenariusze implementacji w rzeczywistych projektach

### Scenariusz 1: Przepływ pracy przeglądu dokumentów
Wielu recenzentów dodaje adnotacje **Area**, **Ellipse** i **Text**. Po rundzie przeglądu generujesz trzy PDF:
1. Pełna wersja ze wszystkimi komentarzami.  
2. Wersja tylko dla recenzentów (filtruje wewnętrzne notatki).  
3. Czysta wersja do ostatecznej akceptacji (zachowuje tylko podświetlenia).

### Scenariusz 2: Automatyczne generowanie raportów
Twój backend przetwarza codzienne raporty sprzedaży, automatycznie podświetlając kluczowe wskaźniki adnotacjami typu area oraz otaczając wykresy odstające adnotacjami typu ellipse. Wygenerowane PDF są następnie wysyłane e‑mailem do interesariuszy bez żadnej ręcznej interwencji.

### Scenariusz 3: Współpraca nad dokumentami prawnymi
Kancelarie prawne często muszą oddzielić komentarze partnerów od notatek młodszych współpracowników. Poprzez oznaczanie adnotacji niestandardowymi metadanymi i użycie selektywnego zapisu, możesz wygenerować PDF do przeglądu przez partnera, który ukrywa uwagi juniorów, upraszczając kontrolę wersji.

## Optymalizacja wydajności w środowisku produkcyjnym

### Jak zarządzać pamięcią przy adnotowaniu dużych PDF?

`LoadOptions` umożliwia określenie, w jaki sposób PDF jest ładowany, np. zakresy stron lub hasła. Gdy PDF przekracza 100 MB, unikaj wczytywania całego pliku, używając konstruktora `LoadOptions`, który przyjmuje zakres stron. Przetwarzaj strony partiami, zwalniaj każdą instancję `Annotator` za pomocą bloku `using` i usuwaj pliki tymczasowe po każdej partii. Takie podejście utrzymuje szczytowe zużycie pamięci poniżej 200 MB nawet przy dokumentach o 500 stronach.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Najlepsze praktyki zarządzania pamięcią
- **Zawsze otaczaj `Annotator` blokiem `using`**, aby zapewnić zwolnienie zasobów niezarządzanych.  
- **Przetwarzaj adnotacje partiami**: zbierz wszystkie adnotacje dla dokumentu, a następnie wywołaj `Add` raz.  
- **Unikaj ładowania pełnych PDF** gdy potrzebujesz zmodyfikować tylko podzbiór stron; użyj `LoadOptions.PageNumbers`.

### Strategie obsługi dużych plików
1. **Przetwarzanie stronowo** – Ładuj, adnotuj i zapisuj jedną stronę na raz.  
2. **Wyjście strumieniowe** – Kieruj metodę `Save` do `MemoryStream`, aby uniknąć pośrednich zapisów na dysku.  
3. **Czyszczenie plików tymczasowych** – Usuń wszystkie pliki tymczasowe utworzone przez annotator po każdej operacji.

### Rozważania przy przetwarzaniu równoległym
- **Bezpieczeństwo wątków:** Instancje `Annotator` nie są bezpieczne wątkowo. Twórz osobną instancję dla każdego wątku.  
- **Ograniczanie zasobów:** Ogranicz liczbę jednoczesnych zadań do liczby rdzeni CPU, aby zapobiec ich przeciążeniu.  
- **Async API:** `SaveAsync` zapisuje adnotowany dokument asynchronicznie, zwracając `Task`, co jest przydatne w środowiskach ASP.NET Core.

## Rozwiązywanie typowych problemów

### Problem 1: Błędy „File Not Found”
**Bezpośrednia odpowiedź:** Zweryfikuj, że ścieżka pliku przekazywana do `new Annotator(...)` jest absolutna lub poprawnie względna względem uruchamianego zestawu, oraz upewnij się, że proces aplikacji ma uprawnienia odczytu do tej lokalizacji. Jeśli plik znajduje się w udziale sieciowym, zamapuj udział lub użyj ścieżek UNC.

**Typowe rozwiązania:**  
- Użyj `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Przyznaj tożsamości puli aplikacji IIS uprawnienia odczytu/zapisu w folderze.

### Problem 2: Adnotacje pojawiają się w niewłaściwych miejscach
**Bezpośrednia odpowiedź:** Upewnij się, że używasz tego samego systemu współrzędnych (pochodzenie w lewym górnym rogu) oraz że DPI strony odpowiada podanym wartościom. Pobierz rozmiar strony za pomocą `annotator.GetPageInfo(pageNumber)` i oblicz współrzędne względem tego rozmiaru.

**Typowe rozwiązania:**  
- Pomnóż współrzędne przez współczynnik skalowania strony, jeśli PDF został utworzony z niestandardowym DPI.  
- Sprawdź ponownie, czy nie mieszane są jednostki punktów (1/72 cala) z pikselami.

### Problem 3: Problemy z wydajnością przy dużych plikach
**Bezpośrednia odpowiedź:** Przejdź na ładowanie zakresu stron, przetwarzaj adnotacje partiami i szybko zwalniaj każdą instancję `Annotator`. Włącz także opcję `MemoryCache` w `LoadOptions`, aby ponownie wykorzystywać bufory w trakcie operacji.

**Typowe rozwiązania:**  
- Ustaw `LoadOptions.UseMemoryCache = true`.  
- Przetwarzaj pliki asynchronicznie przy użyciu `await annotator.SaveAsync(...)`.

### Problem 4: Błędy związane z licencją
**Bezpośrednia odpowiedź:** Umieść plik `.lic` w folderze, który aplikacja może odczytać, i wywołaj `License license = new License(); license.SetLicense("path/to/license.lic");` przed jakimkolwiek innym wywołaniem GroupDocs. Zweryfikuj, czy wersja licencji odpowiada wersji biblioteki, której używasz.

**Typowe rozwiązania:**  
- Sprawdź, czy plik licencji nie jest uszkodzony (porównaj rozmiar pliku).  
- Upewnij się, że nie mieszają się licencja próbna i komercyjna w tym samym środowisku.

## Zaawansowane wskazówki i najlepsze praktyki

### Zarządzanie kolorami
Spójne kolory poprawiają czytelność dla recenzentów. Zdefiniuj paletę (np. Żółty dla podświetleń, Czerwony dla krytycznych problemów) i przechowuj ją w statycznej klasie pomocniczej. Pamiętaj o używaniu kolorów o wysokim kontraście dla dostępności oraz o dodaniu strony legendy w PDF jako odniesienia.

### Wzorce obsługi błędów
Otaczaj wszystkie wywołania adnotacji blokami try‑catch, które konkretnie przechwytują `GroupDocs.Annotation.Exceptions.AnnotationException`. Zaloguj komunikat wyjątku, stos wywołań oraz nazwę PDF, aby ułatwić debugowanie.

### Strategie testowania
- **Unit Tests:** Użyj małego PDF o znanych wymiarach, dodaj adnotację i sprawdź, czy `GetAnnotations()` zwraca oczekiwane współrzędne.  
- **Integration Tests:** Uruchom pełny przepływ pracy na PDF od 1 do 200 stron i zweryfikuj, że czas przetwarzania pozostaje poniżej 5 sekund dla plików poniżej 50 MB.  
- **Load Tests:** Symuluj 50 równoczesnych żądań adnotacji przy użyciu narzędzia takiego jak k6 lub Apache JMeter i monitoruj zużycie CPU/pamięci.

## Najczęściej zadawane pytania

**Q: Jak obsłużyć PDFy o różnych rozmiarach stron?**  
A: GroupDocs automatycznie odczytuje wymiary każdej strony. Przy pozycjonowaniu adnotacji zawsze pobieraj `annotator.GetPageInfo(pageNumber)` i obliczaj współrzędne na podstawie szerokości i wysokości tej strony.

**Q: Czy mogę adnotować PDFy chronione hasłem?**  
A: Tak. Użyj konstruktora `LoadOptions`, który przyjmuje ciąg hasła, np. `new LoadOptions { Password = "secret" }`, i przekaż go do konstruktora `Annotator`.

**Q: Jaka jest maksymalna liczba adnotacji, które mogę dodać do jednego PDF?**  
A: Nie ma sztywnego limitu, ale wydajność spada po kilku tysiącach adnotacji. Dla bardzo dużych zestawów adnotacji grupuj je w logiczne sekcje i przetwarzaj każdą sekcję osobno.

**Q: Jak usunąć konkretne adnotacje programowo?**  
A: Pobierz `Id` adnotacji za pomocą `GetAnnotations()`, a następnie wywołaj `Delete(id)` lub utwórz instancję `SaveOptions`, która wyklucza niechciany `AnnotationType`.

**Q: Czy mogę dostosować wygląd adnotacji poza kolorami?**  
A: Oczywiście. Możesz ustawić przezroczystość, grubość obramowania, styl przerywania oraz nawet osadzić własne ikony SVG dla adnotacji typu stamp.

**Q: Co się stanie, jeśli spróbuję adnotować zeskanowany (oparty na obrazie) PDF?**  
A: Adnotacje będą renderowane jako obiekty nakładkowe na obraz strony. Nie modyfikują one danych rastrowych, więc PDF pozostaje przeszukiwalny, jeśli istnieją warstwy OCR.

**Q: Jak obsłużyć bardzo duże PDFy, nie wyczerpując pamięci?**  
A: Przetwarzaj dokument strona po stronie przy użyciu `LoadOptions.PageNumbers`, natychmiast zwalniaj każdą instancję `Annotator` po użyciu i włącz zapisy strumieniowe do `MemoryStream`, aby uniknąć skoków zapisu na dysku.

## Integracja z aplikacjami ASP.NET

Kiedy udostępniasz funkcjonalność adnotacji przez API webowe, zachowaj następujący wzorzec:

1. **Kontroler otrzymuje strumień PDF** od klienta.  
2. **Waliduj rozmiar pliku** (odrzuć > 200 MB, chyba że masz specjalne przetwarzanie).  
3. **Utwórz `Annotator` w bloku `using`**, aby zapewnić zwolnienie zasobów.  
4. **Zastosuj adnotacje** na podstawie ładunku JSON opisującego typ adnotacji, współrzędne i tekst.  
5. **Zapisz w lokalizacji tymczasowej**, a następnie strumieniuj wynik z powrotem do klienta z odpowiednim nagłówkiem `Content‑Disposition`.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Dodatkowe zasoby
- [Strona zakupu GroupDocs](https://purchase.groupdocs.com/buy)  
- [Kup GroupDocs](https://purchase.groupdocs.com/buy)  
- [Dokumentacja GroupDocs Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Referencja API GroupDocs](https://reference.groupdocs.com/annotation/net/)  
- [Najnowsze wydania](https://releases.groupdocs.com/annotation/net/)  
- [Wypróbuj GroupDocs za darmo](https://releases.groupdocs.com/annotation/net/)  
- [Żądanie tymczasowej licencji](https://purchase.groupdocs.com/temporary-license/)  
- [Forum GroupDocs](https://forum.groupdocs.com/c/annotation/)

## Zakończenie i kolejne kroki

Masz teraz **kompletną, gotową do produkcji mapę drogową** do budowy **systemu przeglądu dokumentów** opartego na GroupDocs.Annotation dla .NET. Nauczyłeś się, jak skonfigurować bibliotekę, dodać adnotacje typu area, ellipse i text, filtrować zapisy oraz utrzymać niskie zużycie pamięci nawet przy ogromnych PDF.

**Kolejne działania, które możesz podjąć już dziś:**  
1. **Eksperymentuj** z dodatkowymi typami adnotacji, takimi jak `ArrowAnnotation` i `StampAnnotation`.  
2. **Zintegruj** przepływ pracy z istniejącym API ASP.NET Core lub aplikacją desktopową WPF.  
3. **Zbadaj** pełną referencję API, aby odkryć zaawansowane funkcje, takie jak wersjonowanie adnotacji i niestandardowe metadane.  
4. **Dołącz** do forum społeczności GroupDocs, aby uzyskać wsparcie od innych i być na bieżąco z nowymi wydaniami.

---
**Ostatnia aktualizacja:** 2026-05-26  
**Testowano z:** GroupDocs.Annotation 23.11 dla .NET  
**Autor:** GroupDocs  

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Powiązane samouczki

- [Samouczek GroupDocs Annotation .NET – Kompletny przewodnik po zarządzaniu dokumentami](/annotation/net/annotation-management/)  
- [Samouczki podglądu dokumentów .NET – Kompletny przewodnik GroupDocs.Annotation](/annotation/net/document-preview/)  
- [Samouczek licencji metrowanej GroupDocs Annotation – Kompletny przewodnik konfiguracji .NET](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)