---
title: Umieść adnotację obrazu nad tekstem
linktitle: Umieść adnotację obrazu nad tekstem
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje graficzne do tekstu w platformie .NET przy użyciu narzędzia GroupDocs.Annotation w celu wydajnego zarządzania dokumentami i współpracy.
type: docs
weight: 21
url: /pl/net/advanced-usage/put-image-annotation-over-text/
---
## Wstęp
świecie programowania .NET GroupDocs.Annotation oferuje potężne rozwiązanie do dodawania adnotacji do dokumentów, zwiększając efektywność współpracy i zarządzania dokumentami. Jednym z typowych wymagań jest umieszczanie adnotacji graficznych nad tekstem, co można bezproblemowo wykonać za pomocą GroupDocs.Annotation dla .NET.
## Warunki wstępne
Zanim zaczniesz umieszczać adnotacje graficzne w tekście za pomocą GroupDocs.Annotation dla .NET, upewnij się, że posiadasz następujące elementy:
1.  GroupDocs.Adnotacja dla biblioteki .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: skonfiguruj odpowiednie środowisko programistyczne, takie jak Visual Studio lub dowolne inne środowisko .NET IDE.
3. Pliki dokumentów i obrazów: Przygotuj plik dokumentu (PDF, DOCX itp.) oraz plik obrazu, którego chcesz użyć do adnotacji.
4. Podstawowa znajomość języka C#: Znajomość języka programowania C# jest konieczna do implementacji fragmentów kodu przedstawionych w tym samouczku.

## Importuj przestrzenie nazw
Przed kontynuowaniem procesu adnotacji upewnij się, że zaimportowałeś niezbędne przestrzenie nazw do projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Najpierw zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Krok 2: Zainicjuj adnotator
 Zainicjuj`Annotator` obiekt podając ścieżkę dokumentu wejściowego:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
## Krok 3: Utwórz adnotację obrazu
 Stworzyć`ImageAnnotation` obiekt o pożądanych właściwościach, takich jak wymiary pudełka, nieprzezroczystość, numer strony, ścieżka obrazu i indeks Z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Krok 4: Dodaj adnotację
 Dodaj adnotację obrazu do dokumentu za pomocą`Add` metoda`Annotator` obiekt:
```csharp
annotator.Add(image);
```
## Krok 5: Zapisz dokument z adnotacjami
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Wyświetl komunikat o powodzeniu ze ścieżką do dokumentu z adnotacjami:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
Podsumowując, dodawanie adnotacji graficznych do tekstu w aplikacjach .NET za pomocą GroupDocs.Annotation jest prostym procesem. Postępując zgodnie ze szczegółowym przewodnikiem zawartym w tym samouczku, możesz efektywnie dodawać adnotacje do dokumentów oraz zwiększać możliwości współpracy i zarządzania dokumentami w projektach .NET.
## Często zadawane pytania
### Czy mogę dodawać adnotacje do dokumentów innych niż pliki PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, takie jak DOCX, XLSX, PPTX i inne.
### Czy dostępna jest bezpłatna wersja próbna GroupDocs.Annotation?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?
 Pomoc można uzyskać na forum społeczności GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy potrzebuję tymczasowej licencji do celów testowych?
 Tak, możesz uzyskać licencję tymczasową od[Tutaj](https://purchase.groupdocs.com/temporary-license/) do celów testowych.
### Czy mogę dostosować wygląd adnotacji?
Tak, GroupDocs.Annotation udostępnia różne opcje dostosowywania wyglądu adnotacji, takie jak kolor, krycie, rozmiar czcionki itp.