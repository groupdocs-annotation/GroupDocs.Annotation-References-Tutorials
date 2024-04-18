---
title: Dodaj adnotację punktową do dokumentu
linktitle: Dodaj adnotację punktową do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodać adnotację punktu do plików PDF za pomocą GroupDocs.Annotation dla .NET. Przewodnik krok po kroku dotyczący bezproblemowej integracji.
type: docs
weight: 17
url: /pl/net/unlocking-annotation-power/add-point-annotation/
---
## Wstęp
GroupDocs.Annotation dla .NET to potężne narzędzie, które pozwala programistom programowo dodawać różne typy adnotacji do dokumentów. W tym samouczku skupimy się na dodaniu adnotacji punktu do dokumentu przy użyciu języka C#.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1. Podstawowa znajomość języka programowania C#.
2. Program Visual Studio zainstalowany w systemie.
3.  Zainstalowana biblioteka GroupDocs.Adnotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).

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
## Krok 2: Zainicjuj adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Tutaj inicjujemy`Annotator` obiekt z dokumentem wejściowym („input.pdf”).
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
 Na tym etapie tworzymy plik`PointAnnotation` obiekt i określ jego właściwości, takie jak pozycja, wiadomość, numer strony i odpowiedzi.
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
W tym samouczku dowiedzieliśmy się, jak dodać adnotację punktu do dokumentu za pomocą GroupDocs.Annotation dla .NET. Dzięki tej potężnej bibliotece możesz ulepszyć swoje aplikacje do zarządzania dokumentami, włączając funkcje adnotacji.
## Często zadawane pytania
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, Microsoft Word, Excel, PowerPoint i inne.
### Czy mogę dostosować wygląd adnotacji?
Absolutnie! GroupDocs.Annotation dla .NET udostępnia rozbudowane opcje dostosowywania wyglądu adnotacji do potrzeb aplikacji.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Annotation dla platformy .NET?
 Tak, możesz skorzystać z bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc w przypadku jakichkolwiek problemów lub zapytań związanych z GroupDocs.Annotation for .NET?
 Pomoc można uzyskać na forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy mogę uzyskać tymczasową licencję do celów testowych?
 Tak, możesz uzyskać licencję tymczasową od[Tutaj](https://purchase.groupdocs.com/temporary-license/).