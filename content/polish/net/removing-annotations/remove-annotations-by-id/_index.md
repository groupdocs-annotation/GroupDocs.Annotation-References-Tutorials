---
title: Usuń adnotacje według identyfikatora
linktitle: Usuń adnotacje według identyfikatora
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak usuwać adnotacje według identyfikatora za pomocą GroupDocs.Annotation dla .NET. Usprawnij efektywnie obieg dokumentów.
type: docs
weight: 11
url: /pl/net/removing-annotations/remove-annotations-by-id/
---
## Wstęp
W tym samouczku przeprowadzimy Cię przez proces usuwania adnotacji według ich identyfikatorów za pomocą GroupDocs.Annotation dla .NET. Adnotacje mogą zaśmiecać dokumenty, a ich selektywne usuwanie może usprawnić przepływ pracy. Poprowadzimy Cię krok po kroku, upewniając się, że dobrze rozumiesz każdy etap.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że spełniasz następujące wymagania wstępne:
1.  GroupDocs.Annotation dla .NET: Upewnij się, że zainstalowałeś bibliotekę GroupDocs.Annotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Dostęp do dokumentu z adnotacjami: Dodaj adnotacje do dokumentu za pomocą GroupDocs.Annotation. Jeśli go nie masz, możesz skorzystać z naszych poprzednich samouczków, aby dodać adnotacje do dokumentu.
3. Podstawowa znajomość języka C#: Do zrozumienia przykładów kodu wymagana jest znajomość języka programowania C#.

## Importuj przestrzenie nazw
Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z usuniętymi adnotacjami.
## Krok 2: Zainicjuj adnotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 Tutaj inicjujemy`Annotator` obiekt ze ścieżką do dokumentu PDF z adnotacjami.
## Krok 3: Usuń adnotacje
```csharp
annotator.Remove(0);
```
 Usuwamy adnotacje podając ich identyfikatory. W tym przykładzie usuwamy adnotację z identyfikatorem`0` . Możesz wymienić`0` z identyfikatorem adnotacji, którą chcesz usunąć.
## Krok 4: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Po usunięciu adnotacji zapisujemy zmodyfikowany dokument do określonej wcześniej ścieżki wyjściowej.
## Krok 5: Wyświetl komunikat o powodzeniu
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Na koniec wyświetlamy komunikat o powodzeniu wraz ze ścieżką, w której zapisany jest zmodyfikowany dokument.

## Wniosek
W tym samouczku dowiedzieliśmy się, jak usuwać adnotacje według ich identyfikatorów za pomocą GroupDocs.Annotation dla .NET. Ta funkcja pomaga w efektywniejszym zarządzaniu dokumentami z adnotacjami poprzez selektywne usuwanie adnotacji.
## Często zadawane pytania
### Czy mogę usunąć wiele adnotacji na raz?
 Tak, możesz usunąć wiele adnotacji, podając ich identyfikatory w pliku`Remove` metoda.
### Czy istnieje sposób na cofnięcie usunięcia adnotacji?
Nie, usuniętych adnotacji nie można cofnąć. Przed usunięciem adnotacji pamiętaj o utworzeniu kopii zapasowej dokumentu.
### Czy mogę usunąć adnotacje z dokumentów innych niż pliki PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym DOCX, XLSX, PPTX i inne.
### Czy są jakieś ograniczenia dotyczące liczby adnotacji, które można usunąć?
Nie, możesz usunąć dowolną liczbę adnotacji z dokumentu, o ile poprawnie określisz ich identyfikatory.
### Czy pomoc techniczna jest dostępna w przypadku napotkania jakichkolwiek problemów?
 Tak, możesz uzyskać pomoc techniczną na forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).