---
title: Dodaj adnotację obszaru do dokumentu
linktitle: Dodaj adnotację obszaru do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Usprawnij współpracę nad dokumentami dzięki Groupdocs.Annotation dla platformy .NET. Dowiedz się, jak krok po kroku dodawać adnotacje obszarów.
weight: 10
url: /pl/net/unlocking-annotation-power/add-area-annotation/
---
## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji obszarów do dokumentów przy użyciu Groupdocs.Annotation for .NET. Adnotacje obszarowe to cenna funkcja, która pozwala użytkownikom wyróżniać określone obszary dokumentu, zapewniając przejrzystość i kontekst treści.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  Groupdocs.Adnotacja dla .NET: Upewnij się, że masz zainstalowane niezbędne biblioteki i zależności. Można je pobrać z[strona internetowa](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Przygotuj odpowiednie środowisko programistyczne do programowania w platformie .NET.

## Importuj przestrzenie nazw
Na początek zaimportuj wymagane przestrzenie nazw do swojego projektu. Te przestrzenie nazw zawierają klasy i metody niezbędne do pracy z adnotacjami.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## Krok 1: Zainicjuj ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Utwórz instancję`Annotator` class, przekazując ścieżkę dokumentu jako parametr.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
## Krok 3: Utwórz adnotację obszaru
Zdefiniuj właściwości adnotacji obszaru, takie jak kolor tła, położenie, komunikat, nieprzezroczystość itp.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
## Krok 4: Dodaj adnotację
 Dodaj adnotację obszaru do dokumentu za pomocą`Add` metoda`Annotator` instancja.
```csharp
annotator.Add(area);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Poinformuj użytkownika, że dokument został pomyślnie dodany i zapisany.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodawać adnotacje obszarów do dokumentów przy użyciu narzędzia Groupdocs.Annotation for .NET. Postępując zgodnie ze szczegółowym przewodnikiem, możesz łatwo wzbogacić swoje dokumenty o cenne adnotacje, poprawiając współpracę i zrozumienie.
## Często zadawane pytania
### Czy mogę dostosować wygląd adnotacji obszaru?
Tak, możesz dostosować różne aspekty, takie jak kolor tła, krycie, styl pióra itp., aby dopasować je do swoich preferencji.
### Czy Groupdocs.Annotation jest kompatybilny z innymi formatami dokumentów?
Tak, Groupdocs.Annotation obsługuje różne formaty dokumentów, w tym PDF, DOCX, PPTX i inne.
### Czy mogę dodać wiele adnotacji do tego samego dokumentu?
Oczywiście możesz dodać wiele adnotacji różnych typów do tego samego dokumentu, jeśli zajdzie taka potrzeba.
### Czy Groupdocs.Annotation zapewnia zgodność między platformami?
Tak, Groupdocs.Annotation jest kompatybilny z platformą .NET Framework, dzięki czemu nadaje się do środowisk programistycznych Windows, Linux i macOS.
### Czy dostępna jest wersja próbna do celów testowych?
 Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej z[strona internetowa](https://releases.groupdocs.com/).