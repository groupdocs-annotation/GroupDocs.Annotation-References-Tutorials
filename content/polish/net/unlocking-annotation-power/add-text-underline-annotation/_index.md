---
"description": "Dowiedz się, jak dodawać podkreślenia tekstu do dokumentów za pomocą GroupDocs.Annotation dla platformy .NET. Bezproblemowo usprawnij współpracę i komunikację."
"linktitle": "Dodaj adnotację podkreślenia tekstu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację podkreślenia tekstu do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Dodaj adnotację podkreślenia tekstu do dokumentu

## Wstęp
tym samouczku przejdziemy przez proces dodawania adnotacji podkreślenia tekstu do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Adnotacje podkreślenia tekstu mogą być przydatne do podkreślania określonych części dokumentu, takich jak ważne fragmenty lub kluczowe punkty.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że masz zainstalowane następujące wymagania wstępne:
1. GroupDocs.Annotation dla .NET: Pobierz i zainstaluj GroupDocs.Annotation dla .NET z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Upewnij się, że w systemie jest zainstalowany .NET Framework.

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

Teraz podzielmy przykład na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
W tym kroku definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj Adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Tutaj inicjujemy instancję `Annotator` klasę, podając ścieżkę do dokumentu wejściowego.
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
    UnderlineColor = 1422623, // prace obsługują tylko dokumenty Word i PDF
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
Ten krok obejmuje utworzenie `UnderlineAnnotation` obiekt o różnych właściwościach, takich jak kolor czcionki, komunikat, krycie, numer strony, kolor tła, kolor podkreślenia, punkty i odpowiedzi.
## Krok 4: Dodaj adnotację do dokumentu
```csharp
annotator.Add(underline);
```
Tutaj dodajemy do dokumentu adnotację podkreślającą.
## Krok 5: Zapisz dokument z adnotacjami
```csharp
annotator.Save(outputPath);
```
Na koniec zapisujemy dokument z adnotacjami w określonej ścieżce wyjściowej.

## Wniosek
W tym samouczku nauczyliśmy się, jak dodać adnotację podkreślenia tekstu do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Ta potężna biblioteka zapewnia różne opcje adnotacji, aby usprawnić współpracę nad dokumentem i komunikację.
## Najczęściej zadawane pytania
### Czy mogę dostosować wygląd podkreślenia?
Tak, możesz dostosować właściwości, takie jak kolor, krycie i położenie, zgodnie ze swoimi wymaganiami.
### Czy GroupDocs.Annotation jest kompatybilny z różnymi formatami dokumentów?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym Word i PDF.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Oczywiście, GroupDocs.Annotation pozwala na dodawanie do dokumentu wielu adnotacji różnego typu.
### Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation?
Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej pod adresem [Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?
Możesz uzyskać pomoc na forum społeczności GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).