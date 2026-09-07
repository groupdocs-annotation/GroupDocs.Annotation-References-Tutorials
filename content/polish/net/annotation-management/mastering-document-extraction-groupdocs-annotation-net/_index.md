---
categories:
- Document Processing
date: '2026-06-01'
description: Dowiedz się, jak wyodrębnić c# pdf page count, uzyskać file type i odczytać
  file properties c# przy użyciu GroupDocs.Annotation .NET. Zawiera praktyczny code
  i tips.
keywords:
- c# pdf page count
- c# get file type
- read file properties c#
- c# read document size
lastmod: '2026-06-01'
linktitle: Wyodrębnij informacje o dokumencie C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  headline: c# pdf page count – Extract Document Info with GroupDocs
  type: TechArticle
- description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  name: c# pdf page count – Extract Document Info with GroupDocs
  steps:
  - name: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
    text: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
  - name: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
    text: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
  - name: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
    text: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
  - name: Clone the sample project and run the provided placeholders with real files.
    text: Clone the sample project and run the provided placeholders with real files.
  - name: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
    text: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
  - name: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
    text: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports over 50 document formats, including PDF,
      DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.
    question: What document formats does GroupDocs.Annotation support for information
      extraction?
  - answer: '`GetDocumentInfo()` provides core metadata like file type, page count,
      and size. For custom properties such as author or creation date, combine GroupDocs.Annotation
      with GroupDocs.Metadata or use the native file format’s property APIs.'
    question: Can I extract custom metadata or properties from documents?
  - answer: Provide the password when creating the `Annotator` instance, e.g., `new
      Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.
    question: How do I handle password‑protected documents?
  - answer: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption
      stays low even for multi‑hundred‑page PDFs.
    question: Is there a way to extract document information without loading the entire
      file into memory?
  - answer: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator`
      per request and dispose of it promptly.
    question: Can I use this in a web application or multi‑threaded environment?
  type: FAQPage
tags:
- csharp
- document-extraction
- groupdocs
- dotnet
title: c# pdf page count – Wyodrębnij informacje o dokumencie z GroupDocs
type: docs
url: /pl/net/annotation-management/mastering-document-extraction-groupdocs-annotation-net/
weight: 1
---

# c# pdf page count – Pobieranie informacji o dokumencie za pomocą GroupDocs.Annotation

## Wprowadzenie

Czy kiedykolwiek patrzyłeś na stos dokumentów i zastanawiałeś się, co tak naprawdę w nich jest, nie otwierając każdego z osobna? Nie jesteś w tym sam. Niezależnie od tego, czy budujesz system zarządzania dokumentami, przetwarzasz pliki prawne, czy po prostu starasz się uporządkować cyfrowe zasoby firmy, znajomość **extract document information in C#** — w tym **c# pdf page count** — może być prawdziwym przełomem.

Ręczne sprawdzanie właściwości plików jest czasochłonne i podatne na błędy. Dzięki **GroupDocs.Annotation for .NET** możesz zautomatyzować cały proces i w kilku linijkach kodu uzyskać typ pliku, liczbę stron, rozmiar dokumentu i wiele innych. Ten tutorial wyjaśnia, dlaczego jest to ważne, jak skonfigurować bibliotekę oraz krok po kroku przedstawia kod gotowy do użycia.

## Szybkie odpowiedzi
- **Co wyodrębnia GroupDocs.Annotation?** Typ pliku, liczbę stron, rozmiar oraz podstawowe metadane.  
- **Ile formatów jest obsługiwanych?** Ponad 50 formatów wejściowych i wyjściowych, w tym PDF, DOCX, XLSX, PPTX oraz popularne typy obrazów.  
- **Czy mogę uzyskać c# pdf page count bez ładowania całego pliku?** Tak — `GetDocumentInfo()` odczytuje jedynie nagłówek potrzebny do określenia liczby stron.  
- **Czy potrzebna jest licencja do rozwoju?** Darmowa wersja próbna wystarczy do testów; pełna licencja jest wymagana w produkcji.  
- **Czy API jest bezpieczne wątkowo dla aplikacji webowych?** Absolutnie — wystarczy prawidłowo zwalniać instancje `Annotator`.

## Co to jest c# pdf page count?
**c# pdf page count** to całkowita liczba stron zgłaszana przez plik PDF po zapytaniu przez API. Korzystając z GroupDocs.Annotation, otrzymujesz tę wartość natychmiast za pomocą metody `GetDocumentInfo()` bez renderowania całego dokumentu. Liczba ta jest wyprowadzana z wewnętrznej struktury PDF, co pozwala podejmować decyzje o przetwarzaniu, przechowywaniu lub wyświetlaniu bez otwierania pliku w przeglądarce. Jest to szczególnie przydatne przy walidacji wsadowej, kontrolach zgodności i podglądach UI, gdzie limity stron mają znaczenie.

## Dlaczego wyodrębniać informacje o dokumencie za pomocą GroupDocs.Annotation?
GroupDocs.Annotation obsługuje **ponad 50 formatów dokumentów** i potrafi przetwarzać pliki wielostronicowe bez ładowania ich w całości do pamięci, dostarczając metadane w mniej niż 200 ms na typowym serwerze. Ta szybkość i szeroki zakres formatów czynią go idealnym rozwiązaniem dla automatyzacji na dużą skalę, kontroli zgodności i inteligentnej klasyfikacji treści.

## Wymagania wstępne i konfiguracja

### Czego potrzebujesz
- Visual Studio 2019 lub nowsze (wersja Community w zupełności wystarczy)  
- .NET Framework 4.6.1+ **lub** .NET Core 2.0+  
- Podstawowa znajomość C# oraz NuGet  

### Instalacja GroupDocs.Annotation
Dodanie biblioteki do projektu jest proste. Wybierz preferowaną metodę:

**Opcja 1: Package Manager Console (zalecane)**
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Opcja 2: .NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Opcja 3: Package Manager UI**  
Jeśli wolisz klikać zamiast pisać, po prostu wyszukaj „GroupDocs.Annotation” w menedżerze pakietów NuGet i zainstaluj najnowszą wersję.

### Uzyskanie licencji
1. **Rozpocznij od wersji próbnej**: Pobierz z [strony GroupDocs](https://releases.groupdocs.com/annotation/net/) – bez zobowiązań.  
2. **Potrzebujesz więcej czasu?** Uzyskaj [tymczasową licencję](https://purchase.groupdocs.com/temporary-license/) na wydłużoną ocenę.  
3. **Gotowy do wdrożenia?** [Kup pełną licencję](https://purchase.groupdocs.com/buy), gdy będziesz gotowy do produkcji.  

> **Pro tip:** Wersja próbna zawiera znak wodny, ale jest idealna do nauki i testowania kodu.

Najświeższe zmiany znajdziesz w [notatkach o wydaniu](https://releases.groupdocs.com/annotation/net/).

## Jak uzyskać c# pdf page count za pomocą GroupDocs.Annotation?

**Annotator** to główna klasa, która ładuje dokument i udostępnia funkcje anotacji oraz metadane.  
Załaduj swój PDF przy pomocy `new Annotator("file.pdf")` i wywołaj `GetDocumentInfo()` – właściwość `PageCount` zwraca dokładną liczbę stron w zaledwie dwóch linijkach kodu. **GetDocumentInfo()** zwraca obiekt **DocumentInfo** zawierający metadane takie jak liczba stron, typ pliku i rozmiar. Metoda odczytuje jedynie niezbędne dane nagłówka, więc nawet duże PDF-y są obsługiwane wydajnie.

### Podstawowa konfiguracja i ładowanie dokumentu
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Initialize the annotator with a document path
        using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
        {
            Console.WriteLine("Document loaded successfully!");
            // We'll add the extraction code here next
        }
    }
}
```  

### Wyodrębnianie metadanych dokumentu
**DocumentInfo** kapsułkuje wyodrębnione właściwości pliku, ułatwiając ich odczyt i wykorzystanie w aplikacji.  
```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    // Extract document info
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    // Always check if info was retrieved successfully
    if (info == null || info.PageCount == 0)
    {
        throw new Exception("Unexpected document information!");
    }

    // Display the extracted information
    Console.WriteLine($"\
File type: {info.FileType}\
Number of pages: {info.PageCount}\
Document size: {info.Size} bytes.");
    
    // Convert size to more readable format
    string readableSize = FormatFileSize(info.Size);
    Console.WriteLine($"Document size (formatted): {readableSize}");
}

// Helper method to format file size
static string FormatFileSize(long bytes)
{
    string[] suffixes = { "B", "KB", "MB", "GB", "TB" };
    int counter = 0;
    decimal number = bytes;
    
    while (Math.Round(number / 1024) >= 1)
    {
        number /= 1024;
        counter++;
    }
    
    return string.Format("{0:n1}{1}", number, suffixes[counter]);
}
```  

### Rozszerzone wyświetlanie informacji
Jeśli potrzebujesz dodatkowego kontekstu — np. czy dokument przekracza określony próg rozmiaru — możesz rozbudować podstawowy przykład o dodatkowe sprawdzenia i logikę biznesową.

```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    if (info == null)
    {
        Console.WriteLine("Could not retrieve document information.");
        return;
    }

    // Comprehensive info display
    Console.WriteLine("=== Document Information ===");
    Console.WriteLine($"File Type: {info.FileType}");
    Console.WriteLine($"Page Count: {info.PageCount}");
    Console.WriteLine($"Size: {FormatFileSize(info.Size)}");
    
    // Additional checks you might want to perform
    if (info.PageCount > 100)
    {
        Console.WriteLine("⚠️  Large document detected - consider batch processing");
    }
    
    if (info.Size > 10 * 1024 * 1024) // 10MB
    {
        Console.WriteLine("⚠️  Large file size - may impact processing time");
    }
    
    Console.WriteLine("=== Analysis Complete ===");
}
```  

## Typowe problemy i rozwiązania

### Problem 1: Błąd „File Not Found”
**Bezpośrednia odpowiedź:** Upewnij się, że ścieżka do pliku jest absolutna lub prawidłowo osadzona względem katalogu bazowego aplikacji oraz że proces ma uprawnienia do odczytu.  

```csharp
string documentPath = @"C:\Documents\test.pdf";

// Always check if file exists first
if (!File.Exists(documentPath))
{
    Console.WriteLine($"File not found: {documentPath}");
    return;
}

try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        // Your code here
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```  

### Problem 2: Nieobsługiwany format pliku
**Bezpośrednia odpowiedź:** Sprawdź, czy rozszerzenie pliku znajduje się wśród ponad 50 obsługiwanych formatów; w przeciwnym razie przekonwertuj go na wspierany typ przed wywołaniem `GetDocumentInfo()`.  

```csharp
try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        if (info == null)
        {
            Console.WriteLine("Unsupported file format or corrupted document");
            return;
        }
        
        // Process the info
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine($"File type not supported: {ex.Message}");
}
```  

### Problem 3: Problemy z pamięcią przy dużych dokumentach
**Bezpośrednia odpowiedź:** Wprowadź sprawdzanie rozmiaru przed ładowaniem i używaj instrukcji `using`, aby zagwarantować zwolnienie instancji `Annotator`, co zapobiega wyciekom pamięci.  

```csharp
const long MAX_FILE_SIZE = 50 * 1024 * 1024; // 50MB limit

FileInfo fileInfo = new FileInfo(documentPath);
if (fileInfo.Length > MAX_FILE_SIZE)
{
    Console.WriteLine("File too large for processing");
    return;
}

// Use proper disposal patterns
using (Annotator annotator = new Annotator(documentPath))
{
    // Process quickly and dispose
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    // Handle info immediately
}
// Annotator is automatically disposed here
```  

## Praktyczne zastosowania

### Integracja z systemem zarządzania dokumentami
Gdy użytkownik przesyła plik, najpierw wyodrębnij jego metadane, aby zdecydować o miejscu przechowywania, strategii indeksacji lub wymaganym procesie zatwierdzania.

```csharp
public class DocumentProcessor
{
    public DocumentMetadata ProcessUpload(string filePath)
    {
        using (Annotator annotator = new Annotator(filePath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            return new DocumentMetadata
            {
                FileName = Path.GetFileName(filePath),
                FileType = info.FileType.ToString(),
                PageCount = info.PageCount,
                FileSizeBytes = info.Size,
                ProcessedDate = DateTime.UtcNow,
                Category = DetermineCategory(info)
            };
        }
    }
    
    private string DetermineCategory(IDocumentInfo info)
    {
        // Business logic for automatic categorization
        if (info.FileType.ToString().Contains("Pdf"))
        {
            return info.PageCount > 20 ? "Legal Document" : "Standard Document";
        }
        
        return "Other";
    }
}
```  

### Analiza wsadowa dokumentów
Przetwarzaj folder plików w zadaniu w tle, rejestrując liczbę stron i typ każdego dokumentu w celach raportowych.

```csharp
public void AnalyzeDocumentFolder(string folderPath)
{
    string[] supportedExtensions = { ".pdf", ".docx", ".xlsx", ".pptx" };
    
    foreach (string file in Directory.GetFiles(folderPath))
    {
        if (!supportedExtensions.Contains(Path.GetExtension(file).ToLower()))
            continue;
            
        try
        {
            using (Annotator annotator = new Annotator(file))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                Console.WriteLine($"{Path.GetFileName(file)}: {info.FileType}, {info.PageCount} pages");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to process {file}: {ex.Message}");
        }
    }
}
```  

### Zgodność i walidacja
Branże regulowane często wymagają, aby dokumenty nie przekraczały określonej liczby stron lub rozmiaru. Wykorzystaj wyodrębnione metadane do automatycznego odrzucania niezgodnych uploadów.

```csharp
public bool ValidateDocument(string filePath, DocumentRequirements requirements)
{
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        // Check file type
        if (requirements.AllowedTypes != null && 
            !requirements.AllowedTypes.Contains(info.FileType.ToString()))
        {
            return false;
        }
        
        // Check page count limits
        if (info.PageCount < requirements.MinPages || 
            info.PageCount > requirements.MaxPages)
        {
            return false;
        }
        
        // Check file size
        if (info.Size > requirements.MaxSizeBytes)
        {
            return false;
        }
        
        return true;
    }
}
```  

## Wskazówki optymalizacji wydajności

### 1. Implementacja pamięci podręcznej
Cache'uj wyniki `DocumentInfo` dla często używanych plików, aby uniknąć powtarzających się operacji I/O.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _infoCache = 
    new Dictionary<string, IDocumentInfo>();

public IDocumentInfo GetDocumentInfoCached(string filePath)
{
    string fileHash = GetFileHash(filePath);
    
    if (_infoCache.ContainsKey(fileHash))
    {
        return _infoCache[fileHash];
    }
    
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        _infoCache[fileHash] = info;
        return info;
    }
}
```  

### 2. Asynchroniczne przetwarzanie wielu dokumentów
Wykorzystaj `Task.Run` lub async streams do równoczesnego przetwarzania wielu plików bez blokowania głównego wątku.

```csharp
public async Task<List<DocumentMetadata>> ProcessDocumentsAsync(string[] filePaths)
{
    var tasks = filePaths.Select(async path =>
    {
        return await Task.Run(() =>
        {
            using (Annotator annotator = new Annotator(path))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                return new DocumentMetadata(path, info);
            }
        });
    });
    
    return (await Task.WhenAll(tasks)).ToList();
}
```  

### 3. Najlepsze praktyki zarządzania pamięcią
- Zawsze otaczaj `Annotator` blokiem `using`.  
- Przetwarzaj dokumenty w partiach, a nie wszystkie naraz.  
- Dla plików większych niż 100 MB rozważ najpierw strumieniowe zapisanie ich na dysk, a dopiero potem odczyt metadanych.  

## Przewodnik rozwiązywania problemów

### Problemy związane z licencją
**License** to obiekt rejestrujący plik aktywacyjny produktu w bibliotece GroupDocs. Upewnij się, że plik licencyjny znajduje się w katalogu głównym aplikacji i że obiekt `License` jest zainicjowany przed jakimikolwiek wywołaniami GroupDocs.  

```csharp
// Set license before using any GroupDocs functionality
License license = new License();
license.SetLicense("path/to/your/license.lic");

// Or use stream for embedded licenses
using (Stream stream = Assembly.GetExecutingAssembly().GetManifestResourceStream("YourApp.license.lic"))
{
    license.SetLicense(stream);
}
```  

### Problemy z wydajnością
**Bezpośrednia odpowiedź:** Profiluj aplikację, ogranicz rozmiar plików do 100 MB dla przetwarzania w czasie rzeczywistym i włącz cache'owanie przy wielokrotnych odczytach.  

### Problemy specyficzne dla platformy
**Bezpośrednia odpowiedź:** Używaj `Path.Combine` do budowania ścieżek wieloplatformowych; Windows używa backslashy, a Linux forward slashy.  

```csharp
// Use Path.Combine for cross-platform compatibility
string documentPath = Path.Combine(baseDirectory, "documents", fileName);
```  

### Obsługa dokumentów zabezpieczonych hasłem
**Bezpośrednia odpowiedź:** Przekaż hasło do konstruktora `Annotator` lub ustaw je poprzez `LoadOptions` przed wywołaniem `GetDocumentInfo()`.  

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-document.pdf", loadOptions))
{
    // Extract information normally
}
```  

### Aktualizacja GroupDocs.Annotation
**Bezpośrednia odpowiedź:** Uruchom `dotnet add package GroupDocs.Annotation --version <latest>` lub użyj interfejsu NuGet Package Manager UI, aby pobrać najnowszą wersję.  

```shell
Update-Package GroupDocs.Annotation
```  

## Najczęściej zadawane pytania

**P: Jakie formaty dokumentów obsługuje GroupDocs.Annotation przy wyodrębnianiu informacji?**  
O: GroupDocs.Annotation obsługuje ponad 50 formatów, w tym PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF, pliki CAD i wiele innych.

**P: Czy mogę wyodrębnić niestandardowe metadane lub właściwości z dokumentów?**  
O: `GetDocumentInfo()` dostarcza podstawowe metadane takie jak typ pliku, liczba stron i rozmiar. Aby uzyskać niestandardowe właściwości, np. autora lub datę utworzenia, połącz GroupDocs.Annotation z GroupDocs.Metadata lub użyj natywnych API formatu pliku.

**P: Jak obsłużyć dokumenty zabezpieczone hasłem?**  
O: Podaj hasło przy tworzeniu instancji `Annotator`, np. `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.

**P: Czy istnieje sposób na wyodrębnienie informacji o dokumencie bez ładowania całego pliku do pamięci?**  
O: Tak — `GetDocumentInfo()` odczytuje jedynie nagłówek pliku, więc zużycie pamięci pozostaje niskie nawet przy wielostronicowych PDF-ach.

**P: Czy mogę używać tego w aplikacji webowej lub środowisku wielowątkowym?**  
O: Absolutnie. GroupDocs.Annotation jest bezpieczny wątkowo; wystarczy tworzyć nowy `Annotator` dla każdego żądania i odpowiednio go zwalniać.

## Podsumowanie i kolejne kroki

Masz teraz kompletną, gotową do produkcji metodę wyodrębniania **c# pdf page count**, typu pliku i rozmiaru przy użyciu GroupDocs.Annotation. Dowiedziałeś się, jak skonfigurować bibliotekę, pobrać metadane, radzić sobie z typowymi problemami i optymalizować wydajność w scenariuszach dużej skali.

**Następne działania:**  
1. Sklonuj projekt przykładowy i uruchom dostarczone szablony z rzeczywistymi plikami.  
2. Zbadaj dodatkowe funkcje GroupDocs.Annotation, takie jak renderowanie anotacji i porównywanie dokumentów.  
3. Zintegruj wyodrębnianie metadanych z istniejącym pipeline'em uploadu, aby automatyzować klasyfikację i walidację.

Pamiętaj, solidne przetwarzanie dokumentów zaczyna się od wiarygodnych metadanych. Dzięki GroupDocs.Annotation możesz budować inteligentniejsze, szybsze i bardziej skalowalne rozwiązania.

---

**Ostatnia aktualizacja:** 2026-06-01  
**Testowano z:** GroupDocs.Annotation 25.4.0 (najnowsza)  
**Autor:** GroupDocs  

**Linki kluczowe:**  
- **[Dokumentacja](https://docs.groupdocs.com/annotation/net/)**  
- **[Referencja API](https://reference.groupdocs.com/annotation/net/)**  
- **[Pobierz najnowszą wersję](https://releases.groupdocs.com/annotation/net/)**  
- **[Zakup licencji](https://purchase.groupdocs.com/buy)**  
- **[Pobierz wersję próbną](https://releases.groupdocs.com/annotation/net/)**  
- **[Żądanie licencji tymczasowej](https://purchase.groupdocs.com/temporary-license/)**  
- **[Forum wsparcia społeczności](https://forum.groupdocs.com/c/annotation/)**  

## Powiązane tutoriale

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)  
- [PDF Page Dimensions .NET - Extract Width & Height with C#](/annotation/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/)  
- [GroupDocs.Annotation .NET Tutorial: Extract & Save Specific PDF Pages](/annotation/net/annotation-management/groupdocs-annotation-dotnet-page-range-management/)