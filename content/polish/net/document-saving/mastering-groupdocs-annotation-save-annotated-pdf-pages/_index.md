---
"date": "2025-05-06"
"description": "Dowiedz się, jak efektywnie zapisywać tylko adnotowane strony pliku PDF za pomocą narzędzia GroupDocs.Annotation dla platformy .NET. Ulepsz zarządzanie dokumentami i współpracę dzięki temu szczegółowemu przewodnikowi."
"title": "Jak zapisać adnotowane strony w formacie PDF za pomocą GroupDocs.Annotation dla platformy .NET"
"url": "/pl/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# Jak zapisać adnotowane strony w formacie PDF za pomocą GroupDocs.Annotation dla platformy .NET

## Wstęp

Masz problemy z zapisywaniem określonych adnotowanych stron z dokumentów PDF? Ten kompleksowy przewodnik pokazuje, jak skutecznie to osiągnąć, używając GroupDocs.Annotation dla .NET. Wykorzystując możliwości adnotacji, usprawnij zarządzanie dokumentami i popraw współpracę, koncentrując się na odpowiedniej treści.

tym samouczku dowiesz się:
- Konfigurowanie środowiska programistycznego za pomocą GroupDocs.Annotation
- Dodawanie różnych typów adnotacji
- Efektywne zapisywanie tylko adnotowanych stron

Gotowy do startu? Upewnijmy się, że masz wszystko gotowe.

### Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz następujące rzeczy:
- **.NET Framework** (wersja 4.6 lub nowsza) lub **.NET Core/5+**
- Edytor kodu, taki jak Visual Studio
- Podstawowa znajomość języka C# i konfiguracji projektu .NET

## Konfigurowanie GroupDocs.Annotation dla .NET

Aby rozpocząć korzystanie z GroupDocs.Annotation, zainstaluj go za pomocą NuGet.

**Konsola Menedżera Pakietów NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\Interfejs wiersza poleceń .NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Nabycie licencji

GroupDocs oferuje bezpłatny okres próbny, aby w pełni poznać ich oprogramowanie. W celu dłuższego użytkowania, kup licencję lub poproś o tymczasową:
- **Bezpłatna wersja próbna**:Przez pierwszy okres możesz korzystać z funkcji bez ograniczeń.
- **Licencja tymczasowa**: Tymczasowo użyj GroupDocs.Annotation w środowisku produkcyjnym.
- **Zakup**:Zabezpiecz swoje długoterminowe potrzeby dzięki licencji komercyjnej.

Po zainstalowaniu zainicjuj bibliotekę w następujący sposób:

```csharp
using GroupDocs.Annotation;

// Podstawowa konfiguracja umożliwiająca ładowanie i adnotowanie dokumentów
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Przewodnik wdrażania

### Dodawanie adnotacji

#### Przegląd

Adnotacje pomagają wyróżnić ważne obszary w dokumencie. Przyjrzyjmy się dodawaniu `AreaAnnotation` i `EllipseAnnotation`.

**Krok 1: Utwórz adnotację obszaru**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Zdefiniuj adnotację obszaru
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozycja i rozmiar
    BackgroundColor = 65535,                // Wartość koloru ARGB dla podświetlenia
    PageNumber = 1                          // Konkretny numer strony
};
```

Ten `AreaAnnotation` podświetla prostokątny obszar w dokumencie. Dostosuj jego położenie (`Box`) i kolor tła.

**Krok 2: Utwórz adnotację elipsy**

```csharp
// Zdefiniuj adnotację elipsy
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozycja i rozmiar
    BackgroundColor = 123456,                // Wartość koloru ARGB dla podświetlenia
    PageNumber = 1                           // Konkretny numer strony
};
```

Ten `EllipseAnnotation` pozwala na narysowanie owalnego kształtu na dokumencie. Dostosuj położenie i wymiary za pomocą `Box` nieruchomość.

**Krok 3: Dodaj adnotacje**

```csharp
// Dodawanie adnotacji do instancji Annotatora
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Korzystanie z `Add` metoda, obejmuje wiele typów adnotacji. Ten krok dodaje zarówno `AreaAnnotation` I `EllipseAnnotation`.

### Zapisywanie tylko adnotowanych stron

#### Przegląd

Aby zapisać tylko strony zawierające adnotacje, należy odpowiednio skonfigurować opcje zapisu.

**Krok 4: Zapisz adnotowane strony**

```csharp
using GroupDocs.Annotation.Options;

// Skonfiguruj opcje zapisywania tak, aby uwzględniały tylko strony z adnotacjami
annotator.Save("path/to/output/document.pdf\