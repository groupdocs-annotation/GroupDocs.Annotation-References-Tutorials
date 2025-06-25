---
"description": "Dowiedz się, jak dodawać adnotacje punktowe do plików PDF za pomocą GroupDocs.Annotation dla .NET. Przewodnik krok po kroku dla bezproblemowej integracji."
"linktitle": "Dodaj adnotację punktu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację punktu do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Dodaj adnotację punktu do dokumentu

## Wstęp
GroupDocs.Annotation for .NET to potężne narzędzie, które pozwala programistom programowo dodawać różne typy adnotacji do dokumentów. W tym samouczku skupimy się na dodawaniu adnotacji punktowej do dokumentu za pomocą języka C#.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że masz następujące rzeczy:
1. Podstawowa znajomość języka programowania C#.
2. Program Visual Studio zainstalowany w systemie.
3. Zainstalowano bibliotekę GroupDocs.Annotation dla .NET. Można ją pobrać z [Tutaj](https://releases.groupdocs.com/annotation/net/).

## Importowanie niezbędnych przestrzeni nazw
Aby rozpocząć, musisz zaimportować wymagane przestrzenie nazw do swojego projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
W tym kroku definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj Adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Tutaj inicjujemy `Annotator` obiekt z dokumentem wejściowym ("input.pdf").
## Krok 3: Utwórz adnotację punktu
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
W tym kroku tworzymy `PointAnnotation` obiekt i określ jego właściwości, takie jak pozycja, wiadomość, numer strony i odpowiedzi.
## Krok 4: Dodaj adnotację
```csharp
annotator.Add(point);
```
Tutaj dodajemy utworzoną adnotację punktową do dokumentu.
## Krok 5: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Na koniec zapisujemy dokument z adnotacjami w określonej ścieżce wyjściowej.

## Wniosek
W tym samouczku nauczyliśmy się, jak dodać adnotację punktu do dokumentu za pomocą GroupDocs.Annotation dla .NET. Dzięki tej potężnej bibliotece możesz ulepszyć swoje aplikacje do zarządzania dokumentami, włączając funkcjonalności adnotacji.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation dla platformy .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word, Excel, PowerPoint i inne.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście! GroupDocs.Annotation dla .NET zapewnia rozbudowane opcje dostosowywania wyglądu adnotacji do potrzeb Twojej aplikacji.
### Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation dla platformy .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej [Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z GroupDocs.Annotation dla platformy .NET?
Możesz uzyskać pomoc na forum GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy mogę uzyskać tymczasową licencję do celów testowych?
Tak, możesz uzyskać tymczasową licencję od [Tutaj](https://purchase.groupdocs.com/temporary-license/).