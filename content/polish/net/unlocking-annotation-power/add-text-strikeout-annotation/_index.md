---
title: Dodaj przekreśloną adnotację tekstową do dokumentu
linktitle: Dodaj przekreśloną adnotację tekstową do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać przekreślone adnotacje tekstowe do dokumentów za pomocą GroupDocs.Annotation dla .NET. Usprawnij efektywnie procesy współpracy i przeglądu dokumentów.
weight: 26
url: /pl/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Wstęp
tym samouczku omówimy, jak dodać przekreśloną adnotację tekstową do dokumentu za pomocą programu GroupDocs.Annotation dla platformy .NET. Ta biblioteka zapewnia zaawansowane narzędzia do dodawania adnotacji do różnych typów dokumentów, usprawniające współpracę i procesy przeglądania dokumentów.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  GroupDocs.Adnotacja dla .NET: Zainstaluj bibliotekę. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Skonfiguruj odpowiednie środowisko programistyczne dla programowania .NET.
3. Dokument: Przygotuj dokument do dodania adnotacji, na przykład plik PDF.

## Importowanie przestrzeni nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Adnotacja:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Podzielmy teraz proces dodawania przekreślonego tekstu na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tutaj definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj adnotator
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
Utwórz obiekt StrikeoutAnnotation z żądanymi właściwościami, takimi jak wiadomość, krycie, numer strony, kolor tła, punkty (współrzędne) i odpowiedzi.
## Krok 4: Dodaj adnotację
```csharp
annotator.Add(strikeout);
```
Dodaj utworzoną adnotację przekreślenia do dokumentu.
## Krok 5: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodać przekreśloną adnotację tekstową do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ta potężna biblioteka umożliwia wydajne dodawanie adnotacji do dokumentów, usprawniając współpracę i procesy przeglądania dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Annotation jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, Word, Excel, PowerPoint i inne.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście możesz dostosować właściwości adnotacji, takie jak kolor, przezroczystość, rozmiar czcionki i inne, zgodnie z własnymi wymaganiami.
### Czy GroupDocs.Annotation udostępnia funkcje współpracy?
Tak, GroupDocs.Annotation ułatwia współpracę, umożliwiając użytkownikom dodawanie komentarzy, odpowiedzi i adnotacji do dokumentów.
### Czy dostępny jest bezpłatny okres próbny?
 Tak, możesz skorzystać z bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?
 Możesz uzyskać wsparcie od[Forum GroupDocs.Adnotacje](https://forum.groupdocs.com/c/annotation/10).