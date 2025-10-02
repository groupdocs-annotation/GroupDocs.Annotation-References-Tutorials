---
"description": "Dowiedz się, jak dodawać adnotacje redakcyjne tekstu do dokumentów PDF za pomocą GroupDocs.Annotation dla platformy .NET. Bezproblemowo chroń poufne informacje."
"linktitle": "Dodaj adnotację redakcyjną tekstu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację redakcyjną tekstu do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Dodaj adnotację redakcyjną tekstu do dokumentu

## Wstęp
Dodanie adnotacji redakcji tekstu do dokumentu może być kluczowym krokiem w bezpiecznym zarządzaniu poufnymi informacjami. GroupDocs.Annotation dla .NET zapewnia solidne rozwiązanie, aby osiągnąć to bezproblemowo. W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji redakcji tekstu do dokumentu krok po kroku.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:
1. GroupDocs.Annotation dla .NET: Upewnij się, że zainstalowałeś bibliotekę GroupDocs.Annotation dla .NET. Możesz ją pobrać ze strony [strona internetowa](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: skonfiguruj środowisko programistyczne przy użyciu środowiska IDE zgodnego z platformą .NET, np. Visual Studio.

## Importowanie przestrzeni nazw
Najpierw zaimportujmy niezbędne przestrzenie nazw do naszego projektu:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której chcesz zapisać adnotowany dokument. Upewnij się, że jest on dostępny i zapisywalny.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj Adnotator
Zainicjuj adnotator ścieżką dokumentu wejściowego. Zastąp `"input.pdf"` ze ścieżką do Twojego dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```
## Krok 3: Utwórz adnotację redakcyjną tekstu
Utwórz `TextRedactionAnnotation` obiekt z wymaganymi właściwościami, takimi jak `PageNumber`, `FontColor`, I `Points`. Dostosuj adnotację zgodnie ze swoimi wymaganiami.
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
Dodaj utworzoną adnotację do dokumentu za pomocą adnotatora i zapisz adnotowany dokument w określonej ścieżce wyjściowej.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Krok 5: Sprawdź wynik
Na koniec sprawdź, czy dokument został pomyślnie zapisany w określonej ścieżce wyjściowej.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku przeprowadziliśmy proces dodawania adnotacji redakcji tekstu do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Dzięki tym krokom możesz teraz bezpiecznie zarządzać poufnymi informacjami w swoich dokumentach.
## Najczęściej zadawane pytania
### Czy mogę dostosować wygląd adnotacji redagującej tekst?
Tak, możesz dostosować różne właściwości, takie jak kolor czcionki, kolor wypełnienia i krycie, do swoich potrzeb.
### Czy jest dostępna wersja próbna przed zakupem?
Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej pod adresem [strona internetowa](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc, jeśli napotkam jakieś problemy?
Możesz uzyskać pomoc na forum społeczności GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy potrzebuję tymczasowej licencji do celów testowych?
Tak, możesz uzyskać tymczasową licencję od [strona zakupu](https://purchase.groupdocs.com/temporary-license/) do testowania.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Oczywiście, GroupDocs.Annotation pozwala dodawać różne typy adnotacji i wiele wystąpień do jednego dokumentu.