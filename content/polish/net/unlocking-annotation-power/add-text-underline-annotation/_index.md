---
title: Dodaj adnotację podkreślenia tekstu do dokumentu
linktitle: Dodaj adnotację podkreślenia tekstu do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać podkreślenia tekstu do dokumentów za pomocą GroupDocs.Annotation dla .NET. Usprawnij współpracę i komunikację bez wysiłku.
type: docs
weight: 27
url: /pl/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Wstęp
W tym samouczku omówimy proces dodawania adnotacji podkreślenia tekstu do dokumentu za pomocą programu GroupDocs.Annotation for .NET. Adnotacje podkreślenia tekstu mogą być przydatne do podkreślania określonych części dokumentu, takich jak ważne fragmenty lub kluczowe punkty.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz zainstalowane następujące wymagania wstępne:
1.  GroupDocs.Annotation dla .NET: Pobierz i zainstaluj GroupDocs.Annotation dla .NET z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Upewnij się, że masz zainstalowaną platformę .NET Framework w swoim systemie.

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

Podzielmy teraz przykład na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
W tym kroku definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Tutaj inicjujemy instancję`Annotator` class, podając ścieżkę dokumentu wejściowego.
## Krok 3: Utwórz adnotację podkreślenia
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // działa obsługiwane tylko dokumenty Word i PDF
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
 Ten krok polega na utworzeniu pliku`UnderlineAnnotation`obiekt o różnych właściwościach, takich jak kolor czcionki, wiadomość, nieprzezroczystość, numer strony, kolor tła, kolor podkreślenia, punkty i odpowiedzi.
## Krok 4: Dodaj adnotację do dokumentu
```csharp
annotator.Add(underline);
```
Tutaj dodajemy podkreślenie do dokumentu.
## Krok 5: Zapisz dokument z adnotacjami
```csharp
annotator.Save(outputPath);
```
Na koniec zapisujemy dokument z adnotacjami w określonej ścieżce wyjściowej.

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodać adnotację dotyczącą podkreślenia tekstu do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ta potężna biblioteka zapewnia różne opcje adnotacji, które usprawniają współpracę i komunikację nad dokumentami.
## Często zadawane pytania
### Czy mogę dostosować wygląd podkreślenia?
Tak, możesz dostosować właściwości, takie jak kolor, krycie i położenie, zgodnie z własnymi wymaganiami.
### Czy GroupDocs.Annotation jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym Word i PDF.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Oczywiście GroupDocs.Annotation umożliwia dodawanie do dokumentu wielu adnotacji różnych typów.
### Czy dostępna jest bezpłatna wersja próbna GroupDocs.Annotation?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej z[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?
 Pomoc można uzyskać na forum społeczności GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).