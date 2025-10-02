---
"description": "Dowiedz się, jak dodawać adnotacje tekstowe przekreślone do dokumentów za pomocą GroupDocs.Annotation dla platformy .NET. Usprawnij współpracę i procesy przeglądania dokumentów."
"linktitle": "Dodaj adnotację przekreślenia tekstu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację przekreślenia tekstu do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Dodaj adnotację przekreślenia tekstu do dokumentu

## Wstęp
tym samouczku pokażemy, jak dodać adnotację przekreślenia tekstu do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Ta biblioteka udostępnia potężne narzędzia do adnotacji różnych typów dokumentów, usprawniając współpracę i procesy przeglądu dokumentów.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:
1. GroupDocs.Annotation dla .NET: Zainstaluj bibliotekę. Możesz ją pobrać z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: skonfiguruj odpowiednie środowisko programistyczne do tworzenia aplikacji .NET.
3. Dokument: Przygotuj dokument, który będziesz mógł komentować, np. plik PDF.

## Importowanie przestrzeni nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Teraz podzielimy proces dodawania adnotacji przekreślenia tekstu na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tutaj definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj Adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Zainicjuj obiekt Annotator, podając ścieżkę do dokumentu wejściowego (w tym przypadku pliku PDF).
## Krok 3: Utwórz adnotację przekreślenia
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
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
    }
};
```
Utwórz obiekt StrikeoutAnnotation z pożądanymi właściwościami, takimi jak wiadomość, krycie, numer strony, kolor tła, punkty (współrzędne) i odpowiedzi.
## Krok 4: Dodaj adnotację
```csharp
annotator.Add(strikeout);
```
Dodaj do dokumentu utworzoną adnotację o przekreśleniu.
## Krok 5: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodać adnotację przekreślenia tekstu do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Ta potężna biblioteka umożliwia wydajną adnotację dokumentu, usprawniając współpracę i procesy przeglądu dokumentów.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i inne.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście, możesz dostosować właściwości adnotacji, takie jak kolor, krycie, rozmiar czcionki i inne, zależnie od swoich wymagań.
### Czy GroupDocs.Annotation udostępnia funkcje współpracy?
Tak, GroupDocs.Annotation ułatwia współpracę, pozwalając użytkownikom dodawać komentarze, odpowiedzi i adnotacje do dokumentów.
### Czy jest dostępna bezpłatna wersja próbna?
Tak, możesz skorzystać z bezpłatnej wersji próbnej [Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?
Możesz uzyskać wsparcie od [Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).