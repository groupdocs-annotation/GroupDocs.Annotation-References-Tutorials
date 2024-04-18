---
title: Dodaj adnotację łącza do dokumentu
linktitle: Dodaj adnotację łącza do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje do łączy do dokumentów za pomocą Groupdocs.Annotation dla .NET. Bez wysiłku usprawnij współpracę i interaktywność.
type: docs
weight: 16
url: /pl/net/unlocking-annotation-power/add-link-annotation/
---
## Wstęp
Groupdocs.Annotation dla .NET to potężna biblioteka, która umożliwia programistom bezproblemową integrację kompleksowych funkcji adnotacji z aplikacjami .NET. Jedną z kluczowych funkcji, jakie oferuje, jest możliwość dodawania adnotacji do linków do dokumentów, co poprawia współpracę i interaktywność.
## Warunki wstępne
Zanim przystąpisz do procesu dodawania adnotacji do linków, upewnij się, że spełniasz następujące wymagania wstępne:
- Podstawowa znajomość języka programowania C#.
- Zainstalowano bibliotekę Groupdocs.Annotation dla .NET.
- Dostęp do dokumentu, do którego chcesz dodać adnotacje.

## Importuj przestrzenie nazw
Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw, aby móc korzystać z funkcjonalności Groupdocs.Annotation for .NET. Dzięki temu aplikacja może uzyskać dostęp do klas i metod wymaganych do dodawania adnotacji do dokumentów.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Ustaw ścieżkę wyjściową
Zdefiniuj ścieżkę, w której chcesz zapisać dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Utwórz instancję`Annotator` class, podając ścieżkę dokumentu, do którego chcesz dodać adnotację.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
## Krok 3: Utwórz adnotację łącza
 Zdefiniuj`LinkAnnotation` obiekt i określ jego właściwości, takie jak wiadomość, przezroczystość, numer strony, kolor tła, punkty, odpowiedzi i adres URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    Url = "https://www.google.com”
};
```
## Krok 4: Dodaj adnotację
 Dodaj utworzoną adnotację łącza do dokumentu za pomocą`Add` metoda instancji adnotatora.
```csharp
annotator.Add(link);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Poinformuj użytkownika o pomyślnym zapisaniu dokumentu z adnotacjami.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
Podsumowując, wykonując powyższe kroki, możesz bezproblemowo dodawać adnotacje do linków do dokumentów za pomocą Groupdocs.Annotation dla .NET. Usprawnia to współpracę nad dokumentami i zapewnia użytkownikom interaktywne funkcje.
## Często zadawane pytania
### Czy Groupdocs.Annotation for .NET jest kompatybilny ze wszystkimi typami dokumentów?
Groupdocs.Annotation dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Word, Excel i inne.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować różne właściwości adnotacji, takie jak kolor, przezroczystość i rozmiar, do własnych wymagań.
### Czy Groupdocs.Annotation dla .NET oferuje funkcje współpracy w czasie rzeczywistym?
Tak, Groupdocs.Annotation dla .NET udostępnia funkcje współpracy w czasie rzeczywistym, umożliwiające wielu użytkownikom jednoczesne dodawanie adnotacji do dokumentów.
### Czy dostępna jest pomoc techniczna dla produktów Groupdocs?
 Tak, pomoc techniczna dla produktów Groupdocs jest dostępna za pośrednictwem forum i wsparcia[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy przed zakupem mogę wypróbować Groupdocs.Annotation dla .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej Groupdocs.Annotation dla .NET, aby zapoznać się z jej funkcjami przed dokonaniem zakupu[Tutaj](https://purchase.groupdocs.com/temporary-license/).