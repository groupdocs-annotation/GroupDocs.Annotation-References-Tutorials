---
"description": "Dowiedz się, jak dodawać adnotacje odległości do dokumentów za pomocą GroupDocs.Annotation dla .NET. Bezproblemowo usprawnij współpracę i komunikację."
"linktitle": "Dodaj adnotację odległości do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację odległości do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Dodaj adnotację odległości do dokumentu

## Wstęp
W tym samouczku dowiesz się, jak dodać adnotację odległości do dokumentu za pomocą GroupDocs.Annotation dla .NET. Wykonaj następujące kroki, aby wykonać zadanie:
## Wymagania wstępne

Zanim przejdziesz dalej, upewnij się, że spełnione są następujące wymagania wstępne:

- Biblioteka GroupDocs.Annotation dla platformy .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Annotation dla platformy .NET z [ten link](https://releases.groupdocs.com/annotation/net/).
- Dokument do adnotacji: Przygotuj dokument (np. PDF), do którego chcesz dodać adnotację dotyczącą odległości.
- Środowisko programistyczne: Skonfiguruj środowisko programistyczne za pomocą programu Visual Studio lub innego wybranego środowiska IDE.

## Importuj przestrzenie nazw

Zanim zaczniesz, upewnij się, że w kodzie uwzględniłeś niezbędne przestrzenie nazw. Te przestrzenie nazw są niezbędne do uzyskania dostępu do wymaganych klas i metod.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Krok 1: Zainicjuj Adnotator

Zacznij od zainicjowania `Annotator` obiekt zawierający ścieżkę do dokumentu, który chcesz adnotować.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```

## Krok 2: Utwórz adnotację odległości

Teraz utwórz `DistanceAnnotation` obiekt i skonfigurować jego właściwości, takie jak wymiary pola, komunikat, krycie, kolor pióra itp.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
    }
};
```

## Krok 3: Dodaj adnotację

Dodaj utworzoną adnotację odległości do dokumentu za pomocą `Add` metoda obiektu adnotatora.

```csharp
annotator.Add(distance);
```

## Krok 4: Zapisz dokument

Zapisz dokument z adnotacjami w wybranym miejscu w systemie.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Krok 5: Wyświetl potwierdzenie

Na koniec wyświetl komunikat potwierdzający pomyślne zapisanie dokumentu z adnotacjami.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek

Dodawanie adnotacji odległości do dokumentów za pomocą GroupDocs.Annotation dla .NET to prosty proces. Postępując zgodnie z krokami opisanymi w tym samouczku, możesz wzbogacić swoje dokumenty o cenne adnotacje, ułatwiając lepszą współpracę i komunikację.

## Najczęściej zadawane pytania

### P: Czy mogę dostosować wygląd adnotacji dotyczącej odległości?

O: Tak, możesz dostosować różne właściwości, takie jak kolor, krycie, styl linii itp., aby dopasować je do swoich wymagań.

### P: Czy GroupDocs.Annotation obsługuje adnotacje w różnych typach dokumentów?

O: Tak, GroupDocs.Annotation obsługuje adnotacje w szerokiej gamie formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i innych.

### P: Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation?

O: Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Annotation z [ten link](https://releases.groupdocs.com/).

### P: Gdzie mogę znaleźć dokumentację GroupDocs.Annotation dla platformy .NET?

A: Możesz zapoznać się ze szczegółową dokumentacją dostępną [Tutaj](https://tutorials.groupdocs.com/annotation/net/).

### P: W jaki sposób mogę uzyskać pomoc lub wsparcie dotyczące GroupDocs.Annotation?

A: Możesz szukać wsparcia i pomocy na forum społeczności GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).