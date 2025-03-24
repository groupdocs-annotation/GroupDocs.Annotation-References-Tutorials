---
title: Dodaj adnotację fragmentu wyszukiwania do dokumentu
linktitle: Dodaj adnotację fragmentu wyszukiwania do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Poznaj możliwości GroupDocs.Annotation dla .NET i bez wysiłku dodawaj możliwości adnotacji w dokumentach do swoich aplikacji.
weight: 20
url: /pl/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Dodaj adnotację fragmentu wyszukiwania do dokumentu

## Wstęp
W dziedzinie programowania .NET GroupDocs.Annotation wyróżnia się jako potężne narzędzie do płynnego dodawania adnotacji do dokumentów. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero wkraczasz w świat .NET, ten kompleksowy samouczek przeprowadzi Cię przez podstawy korzystania z GroupDocs.Annotation dla .NET, od importowania przestrzeni nazw po opanowanie zawiłości dodawania adnotacji fragmentów wyszukiwanego tekstu do dokumenty.
## Wstęp
GroupDocs.Annotation dla .NET umożliwia programistom łatwe włączanie funkcji adnotacji do dokumentów do swoich aplikacji. Dzięki intuicyjnemu interfejsowi API i niezawodnym funkcjom programiści mogą dodawać adnotacje do różnych formatów dokumentów, w tym plików PDF, dokumentów Microsoft Office, obrazów i innych.
## Warunki wstępne
Zanim zagłębisz się w GroupDocs.Annotation dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:

## Importuj przestrzenie nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod GroupDocs.Annotation w projekcie .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Rozpocznij od zdefiniowania ścieżki wyjściowej, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Następnie zainicjuj instancję`Annotator` class, podając ścieżkę do dokumentu, do którego chcesz dodać adnotację:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz adnotację do fragmentu wyszukiwania
 Stwórz`SearchTextFragment` obiekt o żądanych właściwościach, takich jak wyszukiwany tekst, rozmiar czcionki, rodzina czcionek, kolor czcionki i kolor tła:
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
 Dodaj adnotację utworzonego fragmentu szukanego tekstu do dokumentu za pomocą`Add` metoda adnotatora:
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
Podsumowując, GroupDocs.Annotation dla .NET upraszcza proces dodawania adnotacji do dokumentów, usprawniając procesy współpracy i przeglądu dokumentów. Wykonując kroki opisane w tym przewodniku, możesz bezproblemowo zintegrować możliwości dodawania adnotacji w dokumentach z aplikacjami .NET.
## Często zadawane pytania
### Czy GroupDocs.Annotation jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym pliki PDF, dokumenty Microsoft Office, obrazy i inne.
### Czy mogę dostosować wygląd adnotacji?
Absolutnie! GroupDocs.Annotation udostępnia szerokie opcje dostosowywania adnotacji, umożliwiając dostosowanie takich właściwości, jak rozmiar, kolor i styl czcionki.
### Czy dostępna jest bezpłatna wersja próbna GroupDocs.Annotation?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Annotation, aby zapoznać się z jej funkcjami i możliwościami przed dokonaniem zakupu[Tutaj](https://releases.groupdocs.com/)..
### Gdzie mogę znaleźć pomoc dotyczącą GroupDocs.Annotation?
 Aby uzyskać wsparcie i pomoc dotyczącą GroupDocs.Annotation, możesz odwiedzić stronę GroupDocs[forum](https://forum.groupdocs.com/c/annotation/10) przeznaczony do zapytań i dyskusji związanych z adnotacjami.
### Jak uzyskać tymczasową licencję na GroupDocs.Annotation?
 Tymczasową licencję na GroupDocs.Annotation można nabyć za pośrednictwem GroupDocs[strona internetowa](https://purchase.groupdocs.com/temporary-license/)co pozwala na pełną ocenę produktu.