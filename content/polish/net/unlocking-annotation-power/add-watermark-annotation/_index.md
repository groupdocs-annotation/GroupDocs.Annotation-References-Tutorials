---
title: Dodaj adnotację znaku wodnego do dokumentu
linktitle: Dodaj adnotację znaku wodnego do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak bez wysiłku dodawać adnotacje ze znakami wodnymi do dokumentów, korzystając z GroupDocs.Annotation dla .NET. Zwiększ przejrzystość i bezpieczeństwo dokumentów.
weight: 28
url: /pl/net/unlocking-annotation-power/add-watermark-annotation/
---
## Wstęp
W tym samouczku omówimy proces dodawania adnotacji znaku wodnego do dokumentu za pomocą GroupDocs.Annotation dla .NET. Adnotacje ze znakiem wodnym są przydatne do wskazania statusu dokumentu, oznaczenia go jako poufnego lub dodania innych istotnych informacji.

## Warunki wstępne

Zanim zaczniemy, upewnij się, że masz następujące elementy:

1.  GroupDocs.Adnotacja dla .NET: Możesz ją pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Upewnij się, że masz zainstalowany program Visual Studio w swoim systemie.
3. Podstawowa znajomość języka C#: Znajomość języka programowania C# jest konieczna do zrozumienia i wdrożenia przykładów kodu.

## Importuj przestrzenie nazw

Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Podzielmy teraz proces dodawania adnotacji znaku wodnego na kilka kroków:

## Krok 1: Zdefiniuj ścieżkę wyjściową

 Najpierw musimy zdefiniować ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami. Skorzystamy z`Path` klasa od`System.IO` namespace, aby połączyć ścieżkę katalogu wyjściowego z nazwą pliku.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Zainicjuj adnotator

Następnie zainicjujemy adnotator, podając ścieżkę dokumentu wejściowego. Dzięki temu będziemy mogli dodać adnotacje do dokumentu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```

## Krok 3: Utwórz adnotację znaku wodnego

Utwórzmy teraz obiekt adnotacji znaku wodnego z pożądanymi właściwościami, takimi jak kąt, pozycja, tekst, kolor czcionki, krycie itp.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Krok 4: Dodaj adnotację znaku wodnego

 Teraz dodamy adnotację znaku wodnego do dokumentu za pomocą`Add` metoda obiektu adnotatora.

```csharp
annotator.Add(watermark);
```

## Krok 5: Zapisz dokument

Na koniec zapiszemy dokument z adnotacjami w określonej ścieżce wyjściowej.

```csharp
annotator.Save(outputPath);
```

## Wniosek

W tym samouczku dowiedzieliśmy się, jak dodać adnotację znaku wodnego do dokumentu za pomocą GroupDocs.Annotation dla .NET. Adnotacje ze znakiem wodnym są cennym narzędziem do oznaczania dokumentów odpowiednimi informacjami lub wskazywania ich statusu.

## Często zadawane pytania

### P: Czy mogę dostosować wygląd adnotacji znaku wodnego?

Odp.: Tak, możesz dostosować różne właściwości, takie jak tekst, rozmiar czcionki, kolor, przezroczystość, położenie itp., aby dostosować znak wodny do swoich wymagań.

### P: Czy GroupDocs.Annotation for .NET jest kompatybilny z różnymi formatami dokumentów?

O: Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word, Excel, PowerPoint i formaty obrazów.

### P: Czy mogę dodać wiele adnotacji do jednego dokumentu?

O: Oczywiście GroupDocs.Annotation umożliwia dodawanie wielu adnotacji różnych typów do jednego dokumentu, umożliwiając kompleksowe oznaczanie dokumentów.

### P: Czy GroupDocs.Annotation zapewnia obsługę wspólnych adnotacji?

O: Tak, GroupDocs.Annotation ułatwia wspólne tworzenie adnotacji, umożliwiając użytkownikom dodawanie komentarzy, odpowiedzi i adnotacji, co sprzyja efektywnej współpracy między członkami zespołu.

### P: Czy dostępna jest wersja próbna programu GroupDocs.Annotation dla platformy .NET?

 Odp.: Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).