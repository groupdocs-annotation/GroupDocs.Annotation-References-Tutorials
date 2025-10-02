---
"description": "Dowiedz się, jak skonfigurować licencję licznikową dla GroupDocs.Annotation .NET w celu wykorzystania zasobów i możliwości adnotacji dokumentów w aplikacjach .NET."
"linktitle": "Ustaw licencję licznikową"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ustaw licencję licznikową"
"url": "/pl/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# Ustaw licencję licznikową

## Wstęp
GroupDocs.Annotation for .NET to potężna biblioteka, która umożliwia deweloperom łatwe dodawanie funkcji adnotacji dokumentów do aplikacji .NET. Niezależnie od tego, czy tworzysz system zarządzania dokumentami, platformę współpracy, czy jakąkolwiek aplikację, która obejmuje przegląd dokumentów i znaczniki, GroupDocs.Annotation for .NET zapewnia kompleksowy zestaw narzędzi usprawniających ten proces.
W tym samouczku zagłębimy się w proces konfigurowania licencji mierzonej dla GroupDocs.Annotation .NET. Licencja mierzona pozwala płacić tylko za zasoby, które zużywasz, co czyni ją opłacalnym rozwiązaniem dla projektów o dowolnej skali. Postępując zgodnie z poniższymi krokami, będziesz w stanie bezproblemowo zintegrować GroupDocs.Annotation z aplikacją .NET, optymalizując jednocześnie wykorzystanie zasobów i utrzymując kontrolę budżetową.
## Wymagania wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1. GroupDocs.Annotation dla biblioteki .NET: Pobierz bibliotekę z [strona internetowa](https://releases.groupdocs.com/annotation/net/).
2. Dostęp do konta GroupDocs: Będziesz potrzebować konta GroupDocs, aby uzyskać klucze publiczne i prywatne wymagane do skonfigurowania licencji mierzonej. Jeśli jeszcze nie masz konta, możesz zapisać się na bezpłatny okres próbny [Tutaj](https://releases.groupdocs.com/).
3. Podstawowa znajomość języka C# i platformy .NET Framework: Znajomość języka programowania C# i platformy .NET Framework będzie korzystna przy wdrażaniu kroków opisanych w tym samouczku.

## Importuj przestrzenie nazw
Na początek upewnij się, że zaimportowałeś niezbędne przestrzenie nazw do swojego projektu C#. Te przestrzenie nazw są niezbędne do interakcji z funkcjonalnością GroupDocs.Annotation.
```csharp
using System;
```
## Krok 1: Uzyskaj klucze publiczne i prywatne
Przed skonfigurowaniem licencji licznikowej musisz uzyskać klucze publiczne i prywatne z panelu konta GroupDocs.
1. Zaloguj się na swoje konto GroupDocs.
2. Przejdź do sekcji zarządzania licencjami.
3. Skopiuj klucze publiczny i prywatny dostarczone przez GroupDocs.
## Krok 2: Ustaw licencję licznikową
Po uzyskaniu kluczy publicznych i prywatnych możesz skonfigurować licencję licznikową w swojej aplikacji .NET.
```csharp
string publicKey = "*****"; // Zastąp ***** swoim kluczem publicznym
string privateKey = "*****"; // Zastąp ***** swoim kluczem prywatnym
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Wniosek
Podsumowując, skonfigurowanie licencji mierzonej dla GroupDocs.Annotation .NET to prosty proces, który zapewnia efektywne wykorzystanie zasobów i opłacalność projektów adnotacji dokumentów. Postępując zgodnie z krokami opisanymi w tym samouczku, możesz bezproblemowo zintegrować GroupDocs.Annotation z aplikacją .NET i ulepszyć możliwości współpracy i przeglądu dokumentów.
## Najczęściej zadawane pytania
### Czy mogę używać GroupDocs.Annotation dla .NET w projektach komercyjnych?
Tak, GroupDocs.Annotation dla .NET może być używany zarówno w projektach komercyjnych, jak i niekomercyjnych. Jednak musisz nabyć odpowiednią licencję w oparciu o wymagania swojego projektu.
### Czy jest dostępna wersja próbna GroupDocs.Annotation dla .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET, odwiedzając stronę [ten link](https://releases.groupdocs.com/).
### W jaki sposób mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation dla platformy .NET?
Możesz szukać pomocy technicznej, odwiedzając forum GroupDocs [Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy są dostępne jakieś opcje licencji tymczasowej?
Tak, możesz uzyskać tymczasową licencję od GroupDocs do krótkoterminowego użytku lub celów ewaluacyjnych. Odwiedź [ten link](https://purchase.groupdocs.com/temporary-license/) Aby uzyskać więcej informacji.
### Czy mogę dostosować funkcje adnotacji do wymagań mojego projektu?
Tak, GroupDocs.Annotation dla platformy .NET oferuje rozbudowane opcje dostosowywania, pozwalające dostosować funkcje adnotacji do konkretnych potrzeb projektu.