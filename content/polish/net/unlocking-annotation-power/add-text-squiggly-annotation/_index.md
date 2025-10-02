---
"description": "Dowiedz się, jak bez wysiłku dodawać do dokumentów tekstowe adnotacje w formie falbanek, korzystając z Groupdocs.Annotation dla platformy .NET. Ulepsz współpracę i procesy przeglądania dokumentów."
"linktitle": "Dodaj tekstową falistą adnotację do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj tekstową falistą adnotację do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# Dodaj tekstową falistą adnotację do dokumentu

## Wstęp

Groupdocs.Annotation dla .NET to wszechstronna biblioteka, która umożliwia deweloperom bezproblemową integrację solidnych możliwości adnotacji z aplikacjami .NET. Niezależnie od tego, czy pracujesz z plikami PDF, dokumentami Word czy innymi popularnymi formatami plików, Groupdocs.Annotation zapewnia bezproblemowe rozwiązanie do adnotacji i usprawniania współpracy nad dokumentami.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że spełnione są następujące wymagania wstępne:

## Importuj przestrzenie nazw

Pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw, aby uzyskać dostęp do funkcjonalności udostępnianych przez Groupdocs.Annotation dla platformy .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Teraz, gdy omówiliśmy już wymagania wstępne, podzielmy proces dodawania tekstu w formie falowanych adnotacji na kilka kroków.

## Krok 1: Zdefiniuj ścieżkę wyjściową

Zdefiniuj ścieżkę, w której zostanie zapisany dokument z adnotacjami.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Zainicjuj Adnotator

Zainicjuj obiekt Annotator, podając ścieżkę do dokumentu wejściowego.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji wpisz tutaj
}
```

## Krok 3: Utwórz falistą adnotację

Utwórz obiekt SquigglyAnnotation i określ jego właściwości.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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
    }
};
```

## Krok 4: Dodaj adnotację

Dodaj utworzoną falistą adnotację do dokumentu.

```csharp
annotator.Add(squiggly);
```

## Krok 5: Zapisz dokument

Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.

```csharp
annotator.Save(outputPath);
```

## Krok 6: Wyświetl potwierdzenie

Wyświetl komunikat potwierdzający pomyślne zapisanie dokumentu z adnotacjami.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek

Podsumowując, Groupdocs.Annotation for .NET zapewnia deweloperom solidny zestaw narzędzi do bezproblemowej integracji funkcji adnotacji dokumentów z aplikacjami .NET. Postępując zgodnie z tym przewodnikiem krok po kroku, możesz bez wysiłku dodawać do dokumentów kręte adnotacje tekstowe, usprawniając współpracę i procesy przeglądu dokumentów.

## Najczęściej zadawane pytania

### P: Czy Groupdocs.Annotation obsługuje adnotacje w różnych formatach plików?

O: Tak, Groupdocs.Annotation obsługuje adnotacje w szerokiej gamie formatów plików, w tym w plikach PDF, dokumentach Word, arkuszach Excel i innych.

### P: Czy Groupdocs.Annotation jest kompatybilny zarówno z aplikacjami komputerowymi, jak i internetowymi?

A: Oczywiście! Groupdocs.Annotation można bezproblemowo zintegrować z aplikacjami desktopowymi i internetowymi, oferując elastyczność i wszechstronność.

### P: Czy są dostępne jakieś opcje licencjonowania dla Groupdocs.Annotation?

O: Tak, Groupdocs.Annotation oferuje elastyczne opcje licencjonowania dostosowane do potrzeb indywidualnych użytkowników i przedsiębiorstw, w tym licencje tymczasowe w celach próbnych.

### P: Czy adnotacje utworzone za pomocą Groupdocs.Annotation można dostosowywać?

A: Oczywiście! Groupdocs.Annotation zapewnia rozbudowane opcje dostosowywania adnotacji, umożliwiając deweloperom dostosowywanie adnotacji do ich konkretnych wymagań.

### P: Czy Groupdocs.Annotation oferuje pomoc techniczną i dokumentację dla deweloperów?

A: Rzeczywiście! Groupdocs.Annotation zapewnia kompleksową dokumentację i dedykowane fora wsparcia, aby pomóc deweloperom w efektywnym wykorzystaniu jego funkcji.