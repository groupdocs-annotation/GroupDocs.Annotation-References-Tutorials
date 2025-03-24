---
title: Dodaj adnotację o polilinii do dokumentu
linktitle: Dodaj adnotację o polilinii do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje polilinii do dokumentów za pomocą GroupDocs.Annotation dla .NET. Bez wysiłku usprawnij procesy współpracy i przeglądu dokumentów.
weight: 18
url: /pl/net/unlocking-annotation-power/add-polyline-annotation/
---
## Wstęp
GroupDocs.Annotation dla .NET to potężne narzędzie, które umożliwia programistom programowe dodawanie adnotacji do dokumentów PDF i Microsoft Office. Wśród jego funkcji znajduje się możliwość dodawania adnotacji poliliniowych do dokumentów, usprawniających współpracę i procesy przeglądania dokumentów.
## Warunki wstępne
Przed kontynuowaniem tego samouczka upewnij się, że posiadasz następujące elementy:
- Program Visual Studio zainstalowany w systemie.
- Podstawowa znajomość języka programowania C#.
-  Zainstalowana biblioteka GroupDocs.Adnotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).

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
Najpierw określ ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
Zainicjuj adnotator, podając nazwę dokumentu wejściowego.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Utwórz obiekt opisu polilinii
Utwórz obiekt adnotacji polilinii i ustaw jego właściwości, takie jak położenie, komunikat, krycie, kolor pisaka, styl pisaka i szerokość pisaka.
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
Dodaj adnotację polilinii do dokumentu za pomocą obiektu adnotatora.
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
tym samouczku nauczyliśmy się, jak dodać adnotację polilinii do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ta funkcja usprawnia procesy współpracy i przeglądu dokumentów, ułatwiając użytkownikom skuteczne przekazywanie opinii i sugestii.
## Często zadawane pytania
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation dla .NET obsługuje popularne formaty dokumentów, takie jak PDF i formaty Microsoft Office, w tym Word, Excel i PowerPoint.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować różne właściwości adnotacji, takie jak kolor, krycie, styl i szerokość, do własnych wymagań.
### Czy GroupDocs.Annotation dla .NET oferuje bezpłatną wersję próbną?
 Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET, odwiedzając stronę[ten link](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację GroupDocs.Annotation dla .NET?
 Dokumentację GroupDocs.Annotation for .NET można znaleźć[Tutaj](https://tutorials.groupdocs.com/annotation/net/).
### Jak mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z GroupDocs.Annotation for .NET?
 Możesz uzyskać pomoc, odwiedzając forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).