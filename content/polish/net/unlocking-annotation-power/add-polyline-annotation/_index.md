---
"description": "Dowiedz się, jak dodawać adnotacje wieloliniowe do dokumentów za pomocą GroupDocs.Annotation dla .NET. Ulepsz współpracę i procesy przeglądania dokumentów bez wysiłku."
"linktitle": "Dodaj adnotację polilinii do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację polilinii do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# Dodaj adnotację polilinii do dokumentu

## Wstęp
GroupDocs.Annotation for .NET to potężne narzędzie, które umożliwia programistom programowe adnotowanie dokumentów PDF i Microsoft Office. Wśród jego funkcji znajduje się możliwość dodawania adnotacji poliliniowych do dokumentów, co usprawnia współpracę i procesy przeglądu dokumentów.
## Wymagania wstępne
Zanim przejdziesz do tego samouczka, upewnij się, że posiadasz następujące elementy:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość języka programowania C#.
- Zainstalowano bibliotekę GroupDocs.Annotation dla .NET. Można ją pobrać z [Tutaj](https://releases.groupdocs.com/annotation/net/).

## Importuj przestrzenie nazw
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Najpierw zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj Adnotator
Zainicjuj adnotator, podając nazwę dokumentu wejściowego.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz obiekt adnotacji polilinii
Utwórz obiekt adnotacji polilinii i ustaw jego właściwości, takie jak pozycja, komunikat, krycie, kolor pióra, styl pióra i szerokość pióra.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Krok 4: Dodaj adnotację polilinii
Dodaj adnotację wielolinii do dokumentu za pomocą obiektu adnotatora.
```csharp
annotator.Add(polyline);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Wyświetl komunikat potwierdzający pomyślne zapisanie dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku nauczyliśmy się, jak dodać adnotację polilinii do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ta funkcja usprawnia współpracę i procesy przeglądu dokumentów, ułatwiając użytkownikom skuteczną komunikację opinii i sugestii.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation dla platformy .NET obsługuje popularne formaty dokumentów, takie jak PDF oraz formaty pakietu Microsoft Office, w tym Word, Excel i PowerPoint.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować różne właściwości adnotacji, takie jak kolor, krycie, styl i szerokość, by odpowiadały Twoim potrzebom.
### Czy GroupDocs.Annotation dla .NET oferuje bezpłatną wersję próbną?
Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET, odwiedzając stronę [ten link](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację dotyczącą GroupDocs.Annotation dla platformy .NET?
Dokumentację dla GroupDocs.Annotation dla .NET można znaleźć [Tutaj](https://tutorials.groupdocs.com/annotation/net/).
### Gdzie mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z GroupDocs.Annotation dla platformy .NET?
Możesz uzyskać pomoc odwiedzając forum GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).