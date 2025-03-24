---
title: Usuń wiele adnotacji według identyfikatorów
linktitle: Usuń wiele adnotacji według identyfikatorów
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak usunąć wiele adnotacji według identyfikatorów w .NET za pomocą GroupDocs.Annotation, co bez wysiłku zwiększa możliwości zarządzania dokumentami.
weight: 13
url: /pl/net/removing-annotations/remove-multiple-annotations-by-ids/
---

# Usuń wiele adnotacji według identyfikatorów

## Wstęp
świecie zarządzania dokumentami i współpracy GroupDocs.Annotation dla .NET okazuje się potężnym narzędziem, umożliwiającym programistom płynne dodawanie adnotacji i manipulowanie dokumentami w aplikacjach .NET. W tym samouczku omówimy jedną z podstawowych funkcji oferowanych przez GroupDocs.Annotation dla .NET: usuwanie wielu adnotacji według identyfikatorów. Postępując zgodnie z tym przewodnikiem krok po kroku, uzyskasz kompleksową wiedzę na temat skutecznego usuwania adnotacji, co umożliwi Ci zwiększenie możliwości zarządzania dokumentami.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że spełnione są następujące wymagania wstępne:
### 1. Instalacja GroupDocs.Annotation dla .NET
 Po pierwsze, musisz mieć zainstalowany GroupDocs.Annotation for .NET w swoim środowisku programistycznym. Możesz pobrać wymagany pakiet ze strony[link do pobrania](https://releases.groupdocs.com/annotation/net/) udostępniane przez GroupDocs.
### 2. Podstawowa znajomość .NET Framework
Aby zrozumieć przykłady kodu i efektywnie wdrożyć dostarczone rozwiązanie, niezbędna jest podstawowa znajomość .NET Framework.

## Importuj przestrzenie nazw
Aby rozpocząć, zaimportuj niezbędne przestrzenie nazw do aplikacji .NET. Te przestrzenie nazw zapewniają dostęp do funkcji wymaganych do manipulowania adnotacjami.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
W tym kroku definiujemy ścieżkę, w której zostanie zapisany zmodyfikowany dokument z usuniętymi adnotacjami.
## Krok 2: Utwórz instancję obiektu adnotatora
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 Tutaj tworzymy instancję`Annotator` class, przekazując jako parametr ścieżkę dokumentu PDF z adnotacjami.
## Krok 3: Usuń adnotacje według identyfikatorów
```csharp
annotator.Remove(new List<int>{0,1});
```
W tym kluczowym kroku określamy identyfikatory adnotacji, które mają zostać usunięte. Na liście można przekazać wiele identyfikatorów w celu jednoczesnego usunięcia.
## Krok 4: Zapisz zmodyfikowany dokument
```csharp
annotator.Save(outputPath);
```
Po usunięciu określonych adnotacji zmodyfikowany dokument zapisujemy pod wcześniej zdefiniowaną ścieżką wyjściową.
## Krok 5: Wyświetl komunikat o powodzeniu
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Na koniec powiadamiamy użytkownika o pomyślnym zakończeniu procesu i udostępniamy ścieżkę, w której zapisany jest zmodyfikowany dokument.

## Wniosek
Podsumowując, w tym samouczku wyjaśniono proces usuwania wielu adnotacji według identyfikatorów przy użyciu GroupDocs.Annotation dla .NET. Wykonując opisane kroki, programiści mogą bezproblemowo zintegrować tę funkcjonalność ze swoimi aplikacjami .NET, zwiększając w ten sposób efektywność zarządzania dokumentami i współpracę.
## Często zadawane pytania
### Czy adnotacje różnych typów można usuwać jednocześnie?
Tak, adnotacje różnych typów można usunąć jednocześnie, podając ich odpowiednie identyfikatory na liście usuwania.
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi wersjami .NET Framework?
Tak, GroupDocs.Annotation for .NET jest kompatybilny z różnymi wersjami .NET Framework, zapewniając wszechstronność i łatwość integracji.
### Czy przed zakupem mogę wypróbować GroupDocs.Annotation dla .NET?
 Absolutnie! Możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET w witrynie[strona wydania](https://releases.groupdocs.com/)aby poznać jego cechy i możliwości.
### Czy potrzebuję tymczasowej licencji do celów testowych?
Chociaż licencja tymczasowa może poprawić jakość testowania, nie jest ona obowiązkowa w przypadku wersji próbnej. Jednak do użytku produkcyjnego wymagana jest ważna licencja.
### Gdzie mogę zwrócić się o pomoc, jeśli napotkam jakiekolwiek problemy podczas wdrażania?
 Możesz poprosić o pomoc i nawiązać kontakt z tętniącą życiem społecznością GroupDocs za pośrednictwem[forum wsparcia](https://forum.groupdocs.com/c/annotation/10), gdzie eksperci i entuzjaści są łatwo dostępni, aby odpowiedzieć na Twoje pytania i wątpliwości.