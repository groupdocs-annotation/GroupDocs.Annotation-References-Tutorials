---
title: Dodaj komponent pola wyboru do dokumentu PDF
linktitle: Dodaj komponent pola wyboru do dokumentu PDF
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodać komponent Checkbox do dokumentów PDF za pomocą Groupdocs.Annotation dla .NET. Ulepsz swoje pliki PDF za pomocą elementów interaktywnych.
weight: 11
url: /pl/net/document-components/add-checkbox-component-to-pdf/
---

# Dodaj komponent pola wyboru do dokumentu PDF

## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania komponentu Checkbox do dokumentu PDF za pomocą Groupdocs.Annotation dla .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  Groupdocs.Adnotacja dla .NET SDK: Możesz ją pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Upewnij się, że masz skonfigurowane środowisko programistyczne .NET.

## Importuj przestrzenie nazw
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Podzielmy teraz przykład na kilka kroków:
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tutaj definiujemy ścieżkę wyjściową, w której zostanie zapisany zmodyfikowany dokument PDF.
## Krok 2: Zainicjuj adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Zainicjuj`Annotator` obiektu, przekazując ścieżkę wejściowego dokumentu PDF.
## Krok 3: Utwórz komponent pola wyboru
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 Stwórz`CheckBoxComponent` obiekt i dostosuj jego właściwości, np`Checked`, `Box` wymiary,`PenColor`, `Style`dodaj kilka odpowiedzi.
## Krok 4: Dodaj komponent pola wyboru
```csharp
annotator.Add(checkBox);
```
Dodaj utworzony komponent pola wyboru do dokumentu PDF.
## Krok 5: Zapisz dokument
```csharp
annotator.Save("result.pdf");
```
Zapisz zmodyfikowany dokument PDF ze składnikiem pola wyboru.
## Krok 6: Wyświetl ścieżkę wyjściową
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Wyświetl ścieżkę, w której zapisano zmodyfikowany dokument PDF.

## Wniosek
W tym samouczku dowiedzieliśmy się, jak dodać komponent Checkbox do dokumentu PDF za pomocą Groupdocs.Annotation dla .NET. Dzięki tej wiedzy możesz wzbogacić swoje dokumenty PDF o elementy interaktywne.
## Często zadawane pytania
### Czy mogę dostosować wygląd pola wyboru?
Tak, możesz dostosować różne właściwości, takie jak kolor, styl i rozmiar, zgodnie z własnymi wymaganiami.
### Czy Groupdocs.Annotation dla .NET nadaje się do użytku komercyjnego?
Tak, Groupdocs.Annotation dla .NET oferuje licencje komercyjne dla firm.
### Czy przed zakupem mogę wypróbować Groupdocs.Annotation dla .NET?
 Tak, możesz skorzystać z bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć pomoc dotyczącą Groupdocs.Annotation dla .NET?
 Wsparcie i zasoby znajdziesz na stronie[Forum Groupdocs](https://forum.groupdocs.com/c/annotation/10).
### Czy potrzebuję tymczasowej licencji do celów testowych?
 Tymczasową licencję na testowanie można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).