---
"description": "Dowiedz się, jak bez wysiłku dodawać adnotacje znaku wodnego do dokumentów, korzystając z GroupDocs.Annotation dla platformy .NET. Zwiększ przejrzystość i bezpieczeństwo dokumentów."
"linktitle": "Dodaj adnotację znaku wodnego do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację znaku wodnego do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Dodaj adnotację znaku wodnego do dokumentu

## Wstęp
tym samouczku przejdziemy przez proces dodawania adnotacji znaku wodnego do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Adnotacje znaku wodnego są przydatne do wskazywania statusu dokumentu, oznaczania go jako poufnego lub dodawania innych istotnych informacji.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. GroupDocs.Annotation dla .NET: Można go pobrać ze strony [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Upewnij się, że w systemie jest zainstalowany program Visual Studio.
3. Podstawowa znajomość języka C#: Znajomość języka programowania C# jest konieczna do zrozumienia i implementacji przykładów kodu.

## Importuj przestrzenie nazw

Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Teraz podzielimy proces dodawania adnotacji znaku wodnego na kilka kroków:

## Krok 1: Zdefiniuj ścieżkę wyjściową

Najpierw musimy zdefiniować ścieżkę wyjściową, gdzie zostanie zapisany adnotowany dokument. Użyjemy `Path` klasa od `System.IO` przestrzeń nazw łącząca ścieżkę do katalogu wyjściowego z nazwą pliku.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Zainicjuj Adnotator

Następnie zainicjujemy adnotator, podając ścieżkę dokumentu wejściowego. Pozwoli nam to dodać adnotacje do dokumentu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```

## Krok 3: Utwórz adnotację znaku wodnego

Teraz utwórzmy obiekt adnotacji znaku wodnego z pożądanymi właściwościami, takimi jak kąt, pozycja, tekst, kolor czcionki, krycie itp.

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

Teraz dodamy adnotację znaku wodnego do dokumentu za pomocą `Add` metoda obiektu adnotatora.

```csharp
annotator.Add(watermark);
```

## Krok 5: Zapisz dokument

Na koniec zapiszemy dokument z adnotacjami w określonej ścieżce wyjściowej.

```csharp
annotator.Save(outputPath);
```

## Wniosek

W tym samouczku dowiedzieliśmy się, jak dodać adnotację znaku wodnego do dokumentu za pomocą GroupDocs.Annotation dla .NET. Adnotacje znaku wodnego są cennym narzędziem do oznaczania dokumentów odpowiednimi informacjami lub wskazywania ich statusu.

## Najczęściej zadawane pytania

### P: Czy mogę dostosować wygląd adnotacji znaku wodnego?

O: Tak, możesz dostosować różne właściwości, takie jak tekst, rozmiar czcionki, kolor, krycie, położenie itp., aby dostosować znak wodny do swoich wymagań.

### P: Czy GroupDocs.Annotation dla platformy .NET jest kompatybilny z różnymi formatami dokumentów?

O: Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word, Excel, PowerPoint i formaty obrazów.

### P: Czy mogę dodać wiele adnotacji do jednego dokumentu?

O: Oczywiście, GroupDocs.Annotation pozwala dodawać wiele adnotacji różnych typów do jednego dokumentu, co umożliwia kompleksowe oznaczanie dokumentu.

### P: Czy GroupDocs.Annotation obsługuje wspólne adnotacje?

O: Tak, GroupDocs.Annotation ułatwia wspólne tworzenie adnotacji, pozwalając użytkownikom na dodawanie komentarzy, odpowiedzi i adnotacji, co sprzyja efektywnej współpracy między członkami zespołu.

### P: Czy jest dostępna wersja próbna GroupDocs.Annotation dla platformy .NET?

A: Tak, możesz pobrać bezpłatną wersję próbną ze strony [Tutaj](https://releases.groupdocs.com/).