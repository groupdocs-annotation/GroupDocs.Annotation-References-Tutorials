---
title: Dodaj adnotację obrazu do dokumentu (ścieżka zdalna)
linktitle: Dodaj adnotację obrazu do dokumentu (ścieżka zdalna)
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje graficzne do dokumentów za pomocą GroupDocs.Annotation dla .NET. Usprawnij zarządzanie dokumentami dzięki zaawansowanym funkcjom dodawania adnotacji.
weight: 15
url: /pl/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Wstęp
W tym samouczku omówimy proces dodawania adnotacji graficznych do dokumentu za pomocą GroupDocs.Annotation dla .NET. Ta biblioteka zapewnia zaawansowane narzędzia do programowego dodawania adnotacji do różnych typów dokumentów.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące elementy:
1.  GroupDocs.Adnotacja dla .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Upewnij się, że masz działające środowisko programistyczne skonfigurowane do programowania .NET.
3.  Dokument: Przygotuj dokument, do którego chcesz dodać adnotacje. W tym samouczku założymy, że masz dokument PDF o nazwie`input.pdf`.
4. Obraz do adnotacji: Wybierz obraz, którego chcesz użyć do adnotacji. Upewnij się, że masz gotowy adres URL obrazu lub ścieżkę lokalną.

## Importuj przestrzenie nazw
Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Ustaw ścieżkę wyjściową
Najpierw określ ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
 Utwórz instancję`Annotator` class i określ dokument wejściowy.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
## Krok 3: Dodaj adnotację do obrazu
Teraz dodajmy adnotację obrazu do dokumentu. Określimy właściwości adnotacji obrazu, takie jak położenie, krycie, numer strony i ścieżka obrazu.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Określ położenie adnotacji
    CreatedOn = DateTime.Now, // Ustaw datę utworzenia
    Opacity = 0.7, // Ustaw krycie (0 do 1)
    PageNumber = 0, // Określ numer strony
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Podaj adres URL obrazu
};
annotator.Add(image); // Dodaj adnotację do obrazu
```
## Krok 4: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 5: Wyświetl ścieżkę wyjściową
Poinformuj użytkownika o pomyślnym zapisaniu dokumentu i wyświetl ścieżkę wyjściową.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
tym samouczku dowiedzieliśmy się, jak dodawać adnotacje graficzne do dokumentu za pomocą programu GroupDocs.Annotation dla platformy .NET. Wykonując poniższe kroki, możesz wzbogacić swoje aplikacje do zarządzania dokumentami o zaawansowane możliwości dodawania adnotacji.
## Często zadawane pytania
### Czy GroupDocs.Annotation można używać z dokumentami w innych formatach niż PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy GroupDocs.Annotation jest kompatybilny z .NET Core?
Tak, GroupDocs.Annotation jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować wygląd adnotacji, na przykład kolor, przezroczystość i rozmiar.
### Czy GroupDocs.Annotation obsługuje funkcje wspólnych adnotacji?
Tak, GroupDocs.Annotation oferuje funkcje wspólnych adnotacji, umożliwiające współpracę nad dokumentami w czasie rzeczywistym.
### Czy dostępna jest wersja próbna do przetestowania?
 Tak, możesz uzyskać bezpłatną wersję próbną GroupDocs.Annotation z[Tutaj](https://releases.groupdocs.com/).