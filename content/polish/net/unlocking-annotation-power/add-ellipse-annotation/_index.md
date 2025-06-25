---
"description": "Dowiedz się, jak dodawać adnotacje elipsy do dokumentów w .NET przy użyciu GroupDocs.Annotation. Ulepsz współpracę i komunikację bez wysiłku."
"linktitle": "Dodaj adnotację elipsy do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację elipsy do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Dodaj adnotację elipsy do dokumentu

## Wstęp
W tym samouczku dowiesz się, jak dodać adnotację elipsy do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ten przewodnik krok po kroku przeprowadzi Cię przez proces, zapewniając, że jasno zrozumiesz każdy krok.
## Wymagania wstępne
Zanim zaczniesz, upewnij się, że masz następujące rzeczy:
1. GroupDocs.Annotation dla .NET: Upewnij się, że pobrałeś i zainstalowałeś GroupDocs.Annotation dla .NET. Możesz pobrać go z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. IDE (zintegrowane środowisko programistyczne): Aby pisać i wykonywać kod, w systemie musi być zainstalowane środowisko IDE, np. Visual Studio.

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
## Krok 2: Zainicjuj Adnotator
Zainicjuj adnotator, podając ścieżkę do dokumentu wejściowego:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz adnotację elipsy
Utwórz instancję `EllipseAnnotation` klasę i ustaw jej właściwości:
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
Dodaj adnotację elipsy do dokumentu:
```csharp
annotator.Add(ellipse);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```

## Wniosek
Gratulacje! Pomyślnie dodano adnotację elipsy do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Teraz możesz zintegrować tę funkcjonalność ze swoimi aplikacjami .NET, aby usprawnić współpracę nad dokumentami i komunikację.
## Najczęściej zadawane pytania
### Czy mogę dostosować wygląd adnotacji elipsy?
Tak, możesz dostosować różne właściwości, takie jak kolor tła, kolor obramowania, krycie itp., zależnie od swoich wymagań.
### Czy GroupDocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation dla platformy .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, PPTX, XLSX i inne.
### Czy mogę dodać wiele adnotacji do jednego dokumentu?
Tak, do jednego dokumentu można dodawać wiele adnotacji, w tym elipsy, prostokąty, tekst itp.
### Czy jest dostępna wersja próbna do celów testowych?
Tak, możesz pobrać bezpłatną wersję próbną ze strony [Tutaj](https://releases.groupdocs.com/) aby ocenić jego cechy.
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation dla platformy .NET?
Możesz uzyskać pomoc techniczną na forum społeczności GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).