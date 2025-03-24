---
title: Dodaj adnotację w postaci elipsy do dokumentu
linktitle: Dodaj adnotację w postaci elipsy do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje w kształcie elipsy do dokumentów w platformie .NET przy użyciu GroupDocs.Annotation. Usprawnij współpracę i komunikację bez wysiłku.
weight: 13
url: /pl/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Wstęp
W tym samouczku dowiesz się, jak dodać adnotację w kształcie elipsy do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ten przewodnik krok po kroku przeprowadzi Cię przez proces, upewniając się, że dobrze rozumiesz każdy krok.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące elementy:
1.  GroupDocs.Annotation dla .NET: Upewnij się, że pobrałeś i zainstalowałeś GroupDocs.Annotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. IDE (Zintegrowane środowisko programistyczne): Aby napisać i wykonać kod, będziesz potrzebować zainstalowanego w systemie środowiska IDE, takiego jak Visual Studio.

## Importuj przestrzenie nazw
Najpierw zaimportuj niezbędne przestrzenie nazw do swojego projektu:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Ustaw ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
Zainicjuj adnotator, podając ścieżkę dokumentu wejściowego:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz adnotację w postaci elipsy
 Utwórz instancję`EllipseAnnotation` class i ustaw jej właściwości:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
Dodaj adnotację w postaci elipsy do dokumentu:
```csharp
annotator.Add(ellipse);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```

## Wniosek
Gratulacje! Pomyślnie dodałeś adnotację w postaci elipsy do dokumentu za pomocą GroupDocs.Annotation for .NET. Możesz teraz zintegrować tę funkcjonalność z aplikacjami .NET, aby usprawnić współpracę i komunikację nad dokumentami.
## Często zadawane pytania
### Czy mogę dostosować wygląd adnotacji w postaci elipsy?
Tak, możesz dostosować różne właściwości, takie jak kolor tła, kolor obramowania, krycie itp., zgodnie ze swoimi wymaganiami.
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, PPTX, XLSX i inne.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Tak, możesz dodać wiele adnotacji, w tym elipsy, prostokąty, tekst itp., do jednego dokumentu.
### Czy dostępna jest wersja próbna do celów testowych?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/) aby ocenić jego cechy.
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation dla .NET?
 Pomoc techniczną można uzyskać na forum społeczności GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).