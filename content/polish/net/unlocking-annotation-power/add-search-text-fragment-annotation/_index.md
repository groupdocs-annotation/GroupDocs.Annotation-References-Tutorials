---
"description": "Poznaj możliwości narzędzia GroupDocs.Annotation dla platformy .NET i bez trudu dodaj funkcje adnotacji dokumentów do swoich aplikacji."
"linktitle": "Dodaj adnotację fragmentu tekstu wyszukiwania do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację fragmentu tekstu wyszukiwania do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Dodaj adnotację fragmentu tekstu wyszukiwania do dokumentu

## Wstęp
W dziedzinie rozwoju .NET GroupDocs.Annotation wyróżnia się jako potężne narzędzie do bezproblemowego adnotowania dokumentów. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero wkraczasz w świat .NET, ten kompleksowy samouczek przeprowadzi Cię przez podstawy korzystania z GroupDocs.Annotation dla .NET, od importowania przestrzeni nazw po opanowanie zawiłości dodawania adnotacji fragmentów tekstu wyszukiwania do dokumentów.
## Wstęp
GroupDocs.Annotation for .NET umożliwia programistom łatwe włączanie funkcji adnotacji dokumentów do swoich aplikacji. Dzięki intuicyjnemu interfejsowi API i solidnym funkcjom programiści mogą adnotować różne formaty dokumentów, w tym pliki PDF, dokumenty Microsoft Office, obrazy i inne.
## Wymagania wstępne
Zanim przejdziesz do GroupDocs.Annotation dla platformy .NET, upewnij się, że spełnione są następujące wymagania wstępne:

## Importuj przestrzenie nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod GroupDocs.Annotation w swoim projekcie .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Zacznij od zdefiniowania ścieżki wyjściowej, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj Adnotator
Następnie zainicjuj instancję `Annotator` klasę, podając ścieżkę do dokumentu, który chcesz adnotować:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz adnotację fragmentu tekstu wyszukiwania
Utwórz `SearchTextFragment` obiekt o pożądanych właściwościach, takich jak tekst do wyszukania, rozmiar czcionki, rodzina czcionek, kolor czcionki i kolor tła:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Krok 4: Dodaj adnotację
Dodaj do dokumentu adnotację utworzonego fragmentu tekstu wyszukiwania za pomocą `Add` metoda adnotatora:
```csharp
annotator.Add(searchText);
```
## Krok 5: Zapisz dokument z adnotacjami
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Poinformuj użytkownika, że dokument został pomyślnie zapisany:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
Podsumowując, GroupDocs.Annotation dla .NET upraszcza proces dodawania adnotacji do dokumentów, usprawniając współpracę i procesy przeglądu dokumentów. Postępując zgodnie z krokami opisanymi w tym przewodniku, możesz bezproblemowo zintegrować możliwości adnotacji dokumentów z aplikacjami .NET.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym pliki PDF, dokumenty pakietu Microsoft Office, obrazy i inne.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście! GroupDocs.Annotation zapewnia rozbudowane opcje dostosowywania adnotacji, umożliwiając dostosowanie właściwości, takich jak rozmiar czcionki, kolor i styl.
### Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation?
Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Annotation, aby zapoznać się z jej funkcjami i możliwościami przed dokonaniem zakupu [Tutaj](https://releases.groupdocs.com/)..
### Gdzie mogę znaleźć pomoc dotyczącą GroupDocs.Annotation?
Aby uzyskać pomoc i wsparcie dotyczące GroupDocs.Annotation, możesz odwiedzić witrynę GroupDocs [forum](https://forum.groupdocs.com/c/annotation/10) poświęcony zapytaniom i dyskusjom związanym z adnotacjami.
### Jak uzyskać tymczasową licencję na GroupDocs.Annotation?
Możesz nabyć tymczasową licencję na GroupDocs.Annotation za pośrednictwem GroupDocs [strona internetowa](https://purchase.groupdocs.com/temporary-license/), co pozwoli Ci w pełni ocenić produkt.