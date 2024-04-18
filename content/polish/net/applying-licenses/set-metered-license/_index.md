---
title: Ustaw licencję taryfową
linktitle: Ustaw licencję taryfową
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak skonfigurować licencję taryfową dla GroupDocs.Annotation .NET w celu wykorzystania zasobów i możliwości dodawania adnotacji do dokumentów w aplikacjach .NET.
type: docs
weight: 12
url: /pl/net/applying-licenses/set-metered-license/
---
## Wstęp
GroupDocs.Annotation dla .NET to potężna biblioteka, która umożliwia programistom łatwe dodawanie funkcji adnotacji do dokumentów do aplikacji .NET. Niezależnie od tego, czy tworzysz system zarządzania dokumentami, platformę współpracy, czy jakąkolwiek aplikację obejmującą przeglądanie i oznaczanie dokumentów, GroupDocs.Annotation dla .NET zapewnia kompleksowy zestaw narzędzi usprawniających ten proces.
W tym samouczku omówimy proces konfigurowania licencji taryfowej dla GroupDocs.Annotation .NET. Licencja licznikowa pozwala płacić tylko za zużyte zasoby, co czyni ją opłacalnym rozwiązaniem dla projektów o dowolnej skali. Wykonując kroki opisane poniżej, będziesz w stanie bezproblemowo zintegrować GroupDocs.Annotation z aplikacją .NET, optymalizując jednocześnie wykorzystanie zasobów i zachowując kontrolę budżetową.
## Warunki wstępne
Przed przystąpieniem do samouczka upewnij się, że spełniasz następujące wymagania wstępne:
1.  GroupDocs.Adnotation for .NET Library: Pobierz bibliotekę z[strona internetowa](https://releases.groupdocs.com/annotation/net/).
2. Dostęp do konta GroupDocs: Będziesz potrzebować konta GroupDocs, aby uzyskać klucze publiczne i prywatne wymagane do skonfigurowania licencji taryfowej. Jeśli nie masz jeszcze konta, możesz zapisać się na bezpłatny okres próbny[Tutaj](https://releases.groupdocs.com/).
3. Podstawowa znajomość języków C# i .NET Framework: Znajomość języka programowania C# i platformy .NET będzie korzystna przy wdrażaniu kroków opisanych w tym samouczku.

## Importuj przestrzenie nazw
Na początek pamiętaj o zaimportowaniu niezbędnych przestrzeni nazw do projektu C#. Te przestrzenie nazw są niezbędne do interakcji z funkcjonalnością GroupDocs.Annotation.
```csharp
using System;
```
## Krok 1: Uzyskaj klucze publiczne i prywatne
Przed skonfigurowaniem licencji taryfowej musisz uzyskać klucze publiczne i prywatne z panelu konta GroupDocs.
1. Zaloguj się na swoje konto GroupDocs.
2. Przejdź do sekcji zarządzania licencjami.
3. Skopiuj klucze publiczne i prywatne dostarczone przez GroupDocs.
## Krok 2: Ustaw licencję taryfową
Po uzyskaniu kluczy publicznych i prywatnych możesz skonfigurować licencję taryfową w swojej aplikacji .NET.
```csharp
string publicKey = "*****"; // Zamień ***** na swój klucz publiczny
string privateKey = "*****"; // Zamień ***** na swój klucz prywatny
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Wniosek
Podsumowując, skonfigurowanie licencji taryfowej dla GroupDocs.Annotation .NET to prosty proces, który zapewnia efektywne wykorzystanie zasobów i opłacalność projektów adnotacji do dokumentów. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować GroupDocs.Annotation z aplikacją .NET i zwiększyć możliwości współpracy i przeglądania dokumentów.
## Często zadawane pytania
### Czy mogę używać GroupDocs.Annotation for .NET w projektach komercyjnych?
Tak, GroupDocs.Annotation dla .NET można używać zarówno w projektach komercyjnych, jak i niekomercyjnych. Musisz jednak nabyć odpowiednią licencję w oparciu o wymagania swojego projektu.
### Czy dostępna jest wersja próbna programu GroupDocs.Annotation dla platformy .NET?
 Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET, odwiedzając stronę[ten link](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation dla .NET?
 Możesz uzyskać pomoc techniczną, odwiedzając forum GroupDocs[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy są dostępne opcje licencji tymczasowych?
 Tak, możesz uzyskać tymczasową licencję od GroupDocs do celów krótkoterminowego użytkowania lub oceny. Odwiedzać[ten link](https://purchase.groupdocs.com/temporary-license/) po więcej informacji.
### Czy mogę dostosować funkcje adnotacji do wymagań mojego projektu?
Tak, GroupDocs.Annotation dla .NET oferuje szerokie możliwości dostosowywania, umożliwiając dostosowanie funkcji adnotacji do konkretnych potrzeb projektu.