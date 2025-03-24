---
title: Dodaj adnotację wyróżnienia tekstu do dokumentu
linktitle: Dodaj adnotację wyróżnienia tekstu do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje z wyróżnianiem tekstu do dokumentów za pomocą GroupDocs.Annotation dla .NET. Popraw współpracę i produktywność dzięki temu kompleksowemu rozwiązaniu.
weight: 22
url: /pl/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Wstęp
dziedzinie zarządzania dokumentami i współpracy GroupDocs.Annotation dla .NET okazuje się solidnym rozwiązaniem, umożliwiającym programistom bezproblemową integrację adnotacji z wyróżnianiem tekstu w swoich aplikacjach. Ten samouczek stanowi kompleksowy przewodnik dotyczący dodawania adnotacji z wyróżnianiem tekstu do dokumentów przy użyciu programu GroupDocs.Annotation for .NET. Dzięki instrukcjom krok po kroku i szczegółowym objaśnieniom zyskasz biegłość w wykorzystywaniu możliwości tej potężnej biblioteki.
## Warunki wstępne
Przed przystąpieniem do implementacji adnotacji z wyróżnianiem tekstu upewnij się, że spełnione są następujące wymagania wstępne:
1. Konfiguracja środowiska: Skonfiguruj odpowiednie środowisko programistyczne do programowania .NET.
2.  Instalacja GroupDocs.Annotation dla .NET: Pobierz i zainstaluj GroupDocs.Annotation dla .NET z dostarczonego[link do pobrania](https://releases.groupdocs.com/annotation/net/).
3. Znajomość języka C#: Podstawowa znajomość języka programowania C#.
4. Dokument do opatrzenia adnotacjami: Przygotuj dokument (np. PDF), do którego chcesz dodać adnotacje.

## Importuj przestrzenie nazw
Na początek zaimportuj niezbędne przestrzenie nazw do swojego kodu C#, aby móc korzystać z funkcjonalności GroupDocs.Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Teraz podzielmy proces dodawania adnotacji o zaznaczeniu tekstu na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
Określ ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Utwórz instancję`Annotator` class, przekazując nazwę pliku dokumentu jako parametr:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 3: Utwórz adnotację wyróżnienia
 Utwórz instancję a`HighlightAnnotation` obiekt i skonfiguruj jego właściwości:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
Dodaj utworzoną adnotację dotyczącą wyróżnienia do dokumentu:
```csharp
annotator.Add(highlight);
```
## Krok 5: Zapisz dokument z adnotacjami
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```

## Wniosek
Podsumowując, GroupDocs.Annotation dla .NET oferuje uproszczone podejście do włączania adnotacji z wyróżnianiem tekstu do dokumentów. Wykonując kroki opisane w tym samouczku, programiści mogą bezproblemowo usprawnić współpracę nad dokumentami i zwiększyć produktywność w swoich aplikacjach.
## Często zadawane pytania
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation dla .NET obsługuje różne formaty dokumentów, w tym PDF, Word, Excel i inne. Pełną listę można znaleźć w dokumentacji.
### Czy adnotacje można dostosować do konkretnych wymagań?
Tak, programiści mają pełną kontrolę nad właściwościami i wyglądem adnotacji, co pozwala na dostosowanie ich do różnorodnych potrzeb.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Annotation dla platformy .NET?
 Tak, możesz poznać funkcje GroupDocs.Annotation dla .NET, korzystając z bezpłatnej wersji próbnej z dostarczonej[połączyć](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z GroupDocs.Annotation for .NET?
 Aby uzyskać pomoc i wsparcie, odwiedź forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Jakie opcje licencjonowania są dostępne dla GroupDocs.Annotation dla .NET?
 GroupDocs.Annotation dla .NET oferuje różne opcje licencjonowania, w tym licencje tymczasowe do celów testowych i licencje komercyjne dla środowisk produkcyjnych. Odwiedź stronę zakupu[Tutaj](https://purchase.groupdocs.com/buy) po więcej szczegółów.