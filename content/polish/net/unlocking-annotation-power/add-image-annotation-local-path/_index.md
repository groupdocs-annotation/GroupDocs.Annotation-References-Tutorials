---
title: Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)
linktitle: Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje graficzne do dokumentów za pomocą GroupDocs.Annotation dla .NET. Z łatwością zwiększ możliwości przetwarzania dokumentów.
weight: 14
url: /pl/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)

## Wstęp
GroupDocs.Annotation dla .NET to potężna biblioteka, która umożliwia programistom programowe dodawanie różnych typów adnotacji do dokumentów. W tym samouczku dowiemy się, jak dodawać adnotacje graficzne do dokumentu przy użyciu ścieżki lokalnej.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1. Podstawowa znajomość języka programowania C#.
2. Program Visual Studio zainstalowany w systemie.
3. GroupDocs.Annotation dla biblioteki .NET zainstalowanej lub wymienionej w projekcie.
4. Dokument wejściowy (np. PDF) i plik obrazu do adnotacji.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do pliku C#. Te przestrzenie nazw zapewniają dostęp do klas i metod wymaganych do pracy z GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Zdefiniuj ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj adnotator
Zainicjuj adnotator, podając ścieżkę do dokumentu wejściowego.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj znajduje się kod adnotacji
}
```
## Krok 3: Utwórz adnotację obrazu
 Utwórz instancję`ImageAnnotation`class i określ jej właściwości, takie jak położenie, przezroczystość, numer strony i ścieżka obrazu.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Krok 4: Dodaj adnotację
 Dodaj utworzoną adnotację obrazu do dokumentu za pomocą`Add` metoda adnotatora.
```csharp
annotator.Add(image);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl ścieżkę wyjściową
Wyświetl komunikat informujący o pomyślnym zapisaniu dokumentu i lokalizacji pliku wyjściowego.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku nauczyliśmy się, jak dodawać adnotacje graficzne do dokumentu za pomocą GroupDocs.Annotation dla .NET. Wykonując te proste kroki, możesz zwiększyć możliwości przetwarzania dokumentów dzięki zaawansowanym funkcjom dodawania adnotacji.
## Często zadawane pytania
### Czy mogę dodawać adnotacje do dokumentów innych niż PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy GroupDocs.Annotation jest kompatybilny z .NET Core?
Tak, GroupDocs.Annotation jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście możesz dostosować wygląd, rozmiar, kolor i inne właściwości adnotacji zgodnie ze swoimi wymaganiami.
### Czy GroupDocs.Annotation zapewnia obsługę wspólnych adnotacji?
Tak, GroupDocs.Annotation oferuje funkcje wspólnych notatek, które umożliwiają wielu użytkownikom jednoczesne dodawanie adnotacji do dokumentów.
### Gdzie mogę znaleźć dodatkową pomoc lub wsparcie?
Możesz odwiedzić forum GroupDocs.Annotation, aby uzyskać pomoc i wsparcie społeczności.