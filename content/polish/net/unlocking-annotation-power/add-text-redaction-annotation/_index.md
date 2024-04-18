---
title: Dodaj adnotację dotyczącą redakcji tekstu do dokumentu
linktitle: Dodaj adnotację dotyczącą redakcji tekstu do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje redakcyjne tekstu do dokumentów PDF za pomocą GroupDocs.Annotation dla .NET. Chroń poufne informacje bez wysiłku.
type: docs
weight: 23
url: /pl/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Wstęp
Dodanie adnotacji o redakcji tekstu do dokumentu może być kluczowym krokiem w bezpiecznym zarządzaniu poufnymi informacjami. GroupDocs.Annotation dla .NET zapewnia solidne rozwiązanie umożliwiające bezproblemowe osiągnięcie tego celu. W tym samouczku przeprowadzimy Cię krok po kroku przez proces dodawania adnotacji redakcyjnej do dokumentu.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1.  GroupDocs.Annotation dla .NET: Upewnij się, że zainstalowano bibliotekę GroupDocs.Annotation dla .NET. Można go pobrać z[strona internetowa](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Skonfiguruj środowisko programistyczne z IDE zgodnym z platformą .NET, takim jak Visual Studio.

## Importowanie przestrzeni nazw
Na początek zaimportujmy do naszego projektu niezbędne przestrzenie nazw:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której chcesz zapisać dokument z adnotacjami. Upewnij się, że jest dostępny i możliwy do zapisu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Zainicjuj adnotator, podając ścieżkę dokumentu wejściowego. Zastępować`"input.pdf"` ze ścieżką do dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
## Krok 3: Utwórz adnotację redakcyjną tekstu
 Stwórz`TextRedactionAnnotation`obiekt o wymaganych właściwościach, takich jak`PageNumber`, `FontColor` , I`Points`. Dostosuj adnotację zgodnie ze swoimi wymaganiami.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Krok 4: Dodaj adnotację i zapisz
Dodaj utworzoną adnotację do dokumentu za pomocą adnotatora i zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Krok 5: Sprawdź dane wyjściowe
Na koniec potwierdź, że dokument został pomyślnie zapisany w określonej ścieżce wyjściowej.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku omówiliśmy proces dodawania adnotacji redakcyjnej tekstu do dokumentu przy użyciu programu GroupDocs.Annotation dla platformy .NET. Dzięki tym krokom możesz teraz bezpiecznie zarządzać poufnymi informacjami w swoich dokumentach.
## Często zadawane pytania
### Czy mogę dostosować wygląd adnotacji redakcyjnej tekstu?
Tak, możesz dostosować różne właściwości, takie jak kolor czcionki, kolor wypełnienia i krycie, do swoich wymagań.
### Czy przed zakupem dostępna jest wersja próbna?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej z[strona internetowa](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc, jeśli napotkam jakiekolwiek problemy?
 Pomoc można uzyskać na forum społeczności GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy potrzebuję tymczasowej licencji do celów testowych?
 Tak, możesz uzyskać tymczasową licencję od[strona zakupu](https://purchase.groupdocs.com/temporary-license/)dla testów.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Oczywiście GroupDocs.Annotation umożliwia dodawanie różnych typów adnotacji i wielu instancji do jednego dokumentu.