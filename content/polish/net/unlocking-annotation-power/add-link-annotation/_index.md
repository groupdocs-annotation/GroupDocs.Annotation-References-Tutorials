---
"description": "Dowiedz się, jak dodawać adnotacje linków do dokumentów za pomocą Groupdocs.Annotation dla .NET. Bezproblemowo usprawniaj współpracę i interaktywność."
"linktitle": "Dodaj adnotację linku do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację linku do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-link-annotation/"
"weight": 16
---

# Dodaj adnotację linku do dokumentu

## Wstęp
Groupdocs.Annotation for .NET to potężna biblioteka, która umożliwia deweloperom łatwą integrację kompleksowych funkcjonalności adnotacji z aplikacjami .NET. Jedną z kluczowych funkcji, jakie oferuje, jest możliwość dodawania adnotacji linków do dokumentów, co usprawnia współpracę i interaktywność.
## Wymagania wstępne
Zanim rozpoczniesz proces dodawania adnotacji linków, upewnij się, że spełnione są następujące wymagania wstępne:
- Podstawowa znajomość języka programowania C#.
- Zainstalowano bibliotekę Groupdocs.Annotation dla platformy .NET.
- Uzyskaj dostęp do dokumentu, który chcesz opisać.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw, aby wykorzystać Groupdocs.Annotation dla funkcjonalności .NET. Dzięki temu Twoja aplikacja będzie mogła uzyskać dostęp do klas i metod wymaganych do adnotowania dokumentów.
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
## Krok 2: Zainicjuj Adnotator
Utwórz instancję `Annotator` klasę, podając ścieżkę do dokumentu, który chcesz adnotować.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```
## Krok 3: Utwórz adnotację łącza
Zdefiniuj `LinkAnnotation` obiekt i określ jego właściwości, takie jak wiadomość, krycie, numer strony, kolor tła, punkty, odpowiedzi i adres URL.
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
    Url = "https://www.google.com"
};
```
## Krok 4: Dodaj adnotację
Dodaj utworzoną adnotację łącza do dokumentu za pomocą `Add` metoda instancji adnotatora.
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
Podsumowując, wykonując powyższe kroki, możesz bezproblemowo dodawać adnotacje linków do dokumentów za pomocą Groupdocs.Annotation dla .NET. To usprawnia współpracę nad dokumentami i zapewnia użytkownikom funkcje interaktywne.
## Najczęściej zadawane pytania
### Czy Groupdocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi typami dokumentów?
Groupdocs.Annotation dla platformy .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Word, Excel i inne.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować różne właściwości adnotacji, takie jak kolor, krycie i rozmiar, do swoich potrzeb.
### Czy Groupdocs.Annotation dla platformy .NET oferuje funkcje współpracy w czasie rzeczywistym?
Tak, Groupdocs.Annotation dla platformy .NET oferuje funkcje współpracy w czasie rzeczywistym, pozwalające wielu użytkownikom na jednoczesne adnotowanie dokumentów.
### Czy dla produktów Groupdocs dostępna jest pomoc techniczna?
Tak, pomoc techniczna dla produktów Groupdocs jest dostępna na forum i w dziale pomocy technicznej [Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy mogę wypróbować Groupdocs.Annotation dla platformy .NET przed zakupem?
Tak, możesz skorzystać z bezpłatnej wersji próbnej Groupdocs.Annotation dla platformy .NET, aby zapoznać się z jej funkcjami przed dokonaniem zakupu[Tutaj](https://purchase.groupdocs.com/temporary-license/).