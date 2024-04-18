---
title: Usuń odpowiedzi na adnotacje w .NET
linktitle: Usuń odpowiedzi na adnotacje w .NET
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak usunąć odpowiedzi na adnotacje w .NET przy użyciu GroupDocs.Annotation. Przewodnik krok po kroku z przykładami kodu.
type: docs
weight: 15
url: /pl/net/removing-annotations/remove-replies-to-annotations/
---
## Wstęp
tym samouczku omówimy, jak usunąć odpowiedzi na adnotacje w platformie .NET za pomocą GroupDocs.Annotation. GroupDocs.Annotation to potężna biblioteka .NET, która umożliwia programistom łatwe dodawanie adnotacji do dokumentów. Niezależnie od tego, czy chodzi o dodawanie komentarzy, wyróżnianie tekstu czy dodawanie stempli, GroupDocs.Annotation zapewnia kompleksowy zestaw narzędzi do dodawania adnotacji w dokumentach.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
- Podstawowa znajomość programowania w C# i .NET.
- Program Visual Studio zainstalowany w systemie.
-  Zainstalowano GroupDocs.Adnotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
- Zrozumienie działania adnotacji w GroupDocs.Annotation.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do klas i metod GroupDocs.Annotation w kodzie C#.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## Krok 1: Załaduj dokument
 Załaduj dokument zawierający adnotacje z odpowiedziami, korzystając z opcji`Annotator` klasa.
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    // Twój kod trafia tutaj
}
```
## Krok 2: Uzyskaj kolekcję adnotacji
Pobierz kolekcję adnotacji z dokumentu.
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## Krok 3: Usuń odpowiedzi
Usuń odpowiedzi na adnotacje. Na przykład usuńmy pierwszą odpowiedź według indeksu.
```csharp
annotations[0].Replies.RemoveAt(0);
```
## Krok 4: Zapisz zmiany
Zapisz zmiany wprowadzone w adnotacjach.
```csharp
annotator.Update(annotations);
```
## Krok 5: Zapisz dokument
Zapisz dokument ze zmodyfikowanymi adnotacjami w wybranej lokalizacji.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```
## Krok 6: Wyświetl potwierdzenie
Wyświetl komunikat potwierdzający, że dokument został pomyślnie zapisany.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak usuwać odpowiedzi na adnotacje w .NET za pomocą GroupDocs.Annotation. Wystarczy kilka prostych kroków, aby efektywnie manipulować adnotacjami w dokumentach.
## Często zadawane pytania
### Czy mogę usunąć wiele odpowiedzi na raz?
Tak, możesz usunąć wiele odpowiedzi, przeglądając kolekcję odpowiedzi i usuwając je jedna po drugiej.
### Czy GroupDocs.Annotation obsługuje inne formaty dokumentów oprócz PDF?
Tak, GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy dostępna jest wersja próbna programu GroupDocs.Annotation?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Annotation?
 Licencję tymczasową można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Gdzie mogę znaleźć pomoc i wsparcie dotyczące GroupDocs.Annotation?
 Możesz odwiedzić forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10) za pomoc i wsparcie.