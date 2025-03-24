---
title: Dodaj falistą adnotację tekstową do dokumentu
linktitle: Dodaj falistą adnotację tekstową do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak bez wysiłku dodawać faliste adnotacje tekstowe do dokumentów za pomocą Groupdocs.Annotation for .NET. Usprawnij procesy współpracy i przeglądu dokumentów.
weight: 25
url: /pl/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Wstęp

Groupdocs.Annotation dla .NET to wszechstronna biblioteka, która umożliwia programistom bezproblemową integrację zaawansowanych funkcji adnotacji z aplikacjami .NET. Niezależnie od tego, czy pracujesz z plikami PDF, dokumentami programu Word czy innymi popularnymi formatami plików, Groupdocs.Annotation zapewnia płynne rozwiązanie do dodawania adnotacji i usprawniania współpracy nad dokumentami.

## Warunki wstępne

Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:

## Importuj przestrzenie nazw

Pamiętaj, aby zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności udostępnianych przez Groupdocs.Annotation dla .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Skoro już omówiliśmy wymagania wstępne, podzielmy proces dodawania falistych adnotacji tekstowych na kilka etapów.

## Krok 1: Zdefiniuj ścieżkę wyjściową

Określ ścieżkę, w której zostanie zapisany dokument z adnotacjami.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Zainicjuj adnotator

Zainicjuj obiekt Annotator, podając ścieżkę dokumentu wejściowego.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj znajduje się kod adnotacji
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

Podsumowując, Groupdocs.Annotation dla .NET zapewnia programistom solidny zestaw narzędzi do płynnej integracji funkcji adnotacji w dokumentach z aplikacjami .NET. Postępując zgodnie z tym szczegółowym przewodnikiem, możesz z łatwością dodawać faliste adnotacje tekstowe do swoich dokumentów, usprawniając współpracę i procesy recenzowania dokumentów.

## Często zadawane pytania

### P: Czy Groupdocs.Annotation obsługuje adnotacje w różnych formatach plików?

O: Tak, Groupdocs.Annotation obsługuje adnotacje w szerokiej gamie formatów plików, w tym w plikach PDF, dokumentach programu Word, arkuszach programu Excel i innych.

### P: Czy Groupdocs.Annotation jest kompatybilny zarówno z aplikacjami komputerowymi, jak i internetowymi?

Odp.: Absolutnie! Groupdocs.Annotation można bezproblemowo zintegrować z aplikacjami stacjonarnymi i internetowymi, oferując elastyczność i wszechstronność.

### P: Czy są dostępne opcje licencjonowania dla Groupdocs.Annotation?

O: Tak, Groupdocs.Annotation oferuje elastyczne opcje licencjonowania dostosowane do potrzeb indywidualnych lub przedsiębiorstw, w tym licencje tymczasowe do celów próbnych.

### P: Czy adnotacje utworzone za pomocą Groupdocs.Annotation można dostosowywać?

Odp.: Oczywiście! Groupdocs.Annotation zapewnia szerokie możliwości dostosowywania adnotacji, umożliwiając programistom dostosowywanie adnotacji do ich konkretnych wymagań.

### P: Czy Groupdocs.Annotation oferuje wsparcie i dokumentację dla programistów?

Odp.: Rzeczywiście! Groupdocs.Annotation zapewnia obszerną dokumentację i dedykowane fora pomocy technicznej, aby pomóc programistom w efektywnym wykorzystaniu jego funkcji.