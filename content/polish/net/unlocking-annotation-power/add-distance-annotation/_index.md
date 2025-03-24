---
title: Dodaj adnotację dotyczącą odległości do dokumentu
linktitle: Dodaj adnotację dotyczącą odległości do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje dotyczące odległości do dokumentów za pomocą GroupDocs.Annotation dla .NET. Usprawnij współpracę i komunikację bez wysiłku.
weight: 12
url: /pl/net/unlocking-annotation-power/add-distance-annotation/
---

# Dodaj adnotację dotyczącą odległości do dokumentu

## Wstęp
W tym samouczku dowiesz się, jak dodać adnotację dotyczącą odległości do dokumentu za pomocą GroupDocs.Annotation dla .NET. Wykonaj poniższe kroki, aby wykonać zadanie:
## Warunki wstępne

Przed kontynuowaniem upewnij się, że spełnione są następujące wymagania wstępne:

-  Biblioteka GroupDocs.Annotation dla .NET: Pobierz i zainstaluj bibliotekę GroupDocs.Annotation dla .NET ze strony[ten link](https://releases.groupdocs.com/annotation/net/).
- Dokument do adnotacji: Przygotuj dokument (np. PDF), do którego chcesz dodać adnotację dotyczącą odległości.
- Środowisko programistyczne: Skonfiguruj środowisko programistyczne za pomocą programu Visual Studio lub dowolnego innego wybranego środowiska IDE.

## Importuj przestrzenie nazw

Zanim zaczniesz, pamiętaj o uwzględnieniu w kodzie niezbędnych przestrzeni nazw. Te przestrzenie nazw są niezbędne do uzyskania dostępu do wymaganych klas i metod.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Krok 1: Zainicjuj adnotator

 Rozpocznij od inicjalizacji pliku`Annotator` obiekt ze ścieżką do dokumentu, do którego chcesz dodać adnotację.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```

## Krok 2: Utwórz adnotację odległości

 Teraz utwórz`DistanceAnnotation` obiektu i skonfiguruj jego właściwości, takie jak wymiary pudełka, treść, przezroczystość, kolor pisaka itp.

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

 Dodaj utworzoną adnotację odległości do dokumentu za pomocą`Add` metoda obiektu adnotatora.

```csharp
annotator.Add(distance);
```

## Krok 4: Zapisz dokument

Zapisz dokument z adnotacjami w wybranej lokalizacji w systemie.

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

Dodawanie adnotacji dotyczących odległości do dokumentów za pomocą GroupDocs.Annotation dla .NET jest prostym procesem. Wykonując czynności opisane w tym samouczku, możesz wzbogacić swoje dokumenty o cenne adnotacje, ułatwiając lepszą współpracę i komunikację.

## Często zadawane pytania

### P: Czy mogę dostosować wygląd adnotacji o odległości?

Odp.: Tak, możesz dostosować różne właściwości, takie jak kolor, krycie, styl linii itp., aby dostosować je do swoich wymagań.

### P: Czy GroupDocs.Annotation obsługuje adnotacje w różnych typach dokumentów?

O: Tak, GroupDocs.Annotation obsługuje adnotacje w szerokiej gamie formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i innych.

### P: Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Annotation?

 O: Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Adnotacja z[ten link](https://releases.groupdocs.com/).

### P: Gdzie mogę znaleźć dokumentację GroupDocs.Annotation dla .NET?

 Odp.: Możesz zapoznać się z dostępną szczegółową dokumentacją[Tutaj](https://tutorials.groupdocs.com/annotation/net/).

### P: Jak mogę uzyskać wsparcie lub pomoc dotyczącą GroupDocs.Annotation?

 Odpowiedź: Możesz szukać wsparcia i pomocy na forum społeczności GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).