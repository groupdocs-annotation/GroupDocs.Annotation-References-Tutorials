---
categories:
- Java Development
date: '2026-03-30'
description: Dowiedz się, jak dodać adnotację przekreślenia w Javie przy użyciu GroupDocs.Annotation.
  Przewodnik krok po kroku z przykładami kodu, wskazówkami rozwiązywania problemów
  i najlepszymi praktykami dotyczącymi oznaczania dokumentów.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Dodaj adnotację przekreślenia – samouczek Java z GroupDocs
type: docs
url: /pl/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Dodaj adnotację przekreślenia Java - Kompletny przewodnik GroupDocs

Czy kiedykolwiek patrzyłeś na dokument i myślałeś: „Muszę przekreślić ten tekst, ale nie mogę po prostu wziąć czerwonego długopisu”? Nie jesteś sam. Niezależnie od tego, czy budujesz system przeglądu dokumentów, tworzysz przepływ pracy edycji, czy po prostu musisz oznaczyć tekst do usunięcia w swojej aplikacji Java, **add strikeout annotation java** jest niezbędną umiejętnością. W tym samouczku przeprowadzimy Cię przez wszystko, co musisz wiedzieć, aby zaimplementować funkcję przekreślania tekstu, która naprawdę działa w produkcji.

## Szybkie odpowiedzi
- **Jaką bibliotekę obsługuje adnotacje przekreślenia w Javie?** GroupDocs.Annotation for Java  
- **Jakie główne słowo kluczowe powinienem targetować pod SEO?** add strikeout annotation java  
- **Czy potrzebuję licencji, aby uruchomić przykładowy kod?** Darmowa wersja próbna lub tymczasowa licencja działa w środowisku deweloperskim; pełna licencja jest wymagana w produkcji.  
- **Czy mogę używać tego z plikami PDF, DOCX i PPTX?** Tak – GroupDocs.Annotation obsługuje wszystkie główne formaty dokumentów.  
- **Jakiej wersji Javy wymaga?** JDK 8 lub wyższy (zalecany JDK 11+).

## Co to jest add strikeout annotation java?
Adnotacja przekreślenia rysuje linię przez wybrany tekst, wizualnie wskazując, że zawartość powinna zostać usunięta lub zignorowana. Jest to nieniszczący sposób sugerowania usunięć przy zachowaniu oryginalnego tekstu w całości, co jest przydatne w ścieżkach audytu lub współpracujących przeglądach.

## Dlaczego używać adnotacji przekreślenia w aplikacjach Java?
- **Przepływy przeglądu dokumentów** – recenzenci mogą oznaczać niepożądany tekst bez zmiany źródła.  
- **Wspólna edycja** – członkowie zespołu widzą sugerowane usunięcia natychmiast.  
- **Prawo i zgodność** – utrzymuj przejrzystą ścieżkę audytu zmian.  
- **Migracja treści** – oznacz przestarzałe sekcje przed przeniesieniem treści między systemami.  

## Wymagania wstępne i konfiguracja środowiska
Będziesz potrzebował następujących rzeczy przed zanurzeniem się w kodzie:

- **Java Development Kit (JDK)** 8+ (zalecany JDK 11+).  
- **Maven lub Gradle** do zarządzania zależnościami.  
- **IDE** – IntelliJ IDEA, Eclipse lub VS Code z rozszerzeniami Java.  
- **Biblioteka GroupDocs.Annotation** – w przykładach użyjemy wersji 25.2.  

*Przydatne:* podstawowa znajomość adnotacji Java i obsługi PDF.

## Konfiguracja GroupDocs.Annotation dla Java

### Konfiguracja Maven, która naprawdę działa
Dodaj repozytorium i zależność do swojego `pom.xml` dokładnie tak, jak pokazano:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### Uzyskanie licencji
GroupDocs oferuje kilka opcji licencjonowania:

- **Free trial** – idealny do testów (bez wymogu karty kredytowej).  
- **Temporary license** – idealna do rozwoju i środowiska testowego.  
- **Full license** – wymagana do użytku produkcyjnego; zobacz [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** Zacznij od darmowej wersji próbnej, aby zapoznać się z API, a następnie przejdź na tymczasową licencję, gdy będziesz gotowy zbudować funkcję w rzeczywistym świecie.

### Szybka kontrola poprawności
Uruchom ten minimalny program, aby zweryfikować, że biblioteka ładuje się poprawnie:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Jeśli konsola wyświetli komunikat o sukcesie bez błędów, jesteś gotowy dodać adnotacje przekreślenia.

## Jak dodać adnotację przekreślenia java

Poniżej znajduje się kompletny, gotowy do produkcji implementacja podzielona na jasne kroki.

### Krok 1 – Inicjalizacja Annotatora
Utwórz instancję `Annotator`, która wskazuje na dokument źródłowy:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Dlaczego to ważne:** Użycie ścieżki bezwzględnej lub prawidłowo rozwiązanej względnej zapobiega wyjątkom „plik nie znaleziony”.

### Krok 2 – (Opcjonalnie) Przygotowanie odpowiedzi komentarzy
Dodawanie odpowiedzi sprawia, że adnotacja jest współpracująca:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Te komentarze pojawiają się, gdy użytkownik najedzie kursorem na przekreślenie.

### Krok 3 – Zdefiniowanie obszaru przekreślenia
Określ prostokąt obejmujący tekst, który chcesz przekreślić:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Wskazówka dotycząca współrzędnych:** Punkt początkowy (0,0) znajduje się w lewym górnym rogu strony; X rośnie w prawo, Y w dół. Użyj przeglądarki PDF wyświetlającej współrzędne, aby precyzyjnie dostroić te wartości.

### Krok 4 – Konfiguracja adnotacji przekreślenia
Ustaw wygląd, numer strony i dołącz komentarze:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Uwaga o kolorze:* `65535` odpowiada żółtemu w formacie całkowitoliczbowym RGB. Zmień wartość, aby użyć innych kolorów.

### Krok 5 – Zastosowanie adnotacji i zapis
Dodaj adnotację do dokumentu i zapisz plik wyjściowy:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Krok 6 – Czyszczenie zasobów (Krytyczne!)
Zawsze zwalniaj annotator, aby zwolnić zasoby natywne:

```java
if (annotator != null) {
    annotator.dispose();
}
```

W produkcji, otocz użycie blokiem try‑with‑resources lub konstrukcją `try/finally`.

## Typowe problemy i jak je naprawić

| Problem | Objaw | Rozwiązanie |
|---------|-------|-------------|
| **Plik nie znaleziony** | `Annotator` zgłasza wyjątek | Użyj ścieżek bezwzględnych, sprawdź uprawnienia odczytu, upewnij się, że żaden inny proces nie blokuje pliku |
| **Nieprawidłowe współrzędne** | Przekreślenie pojawia się poza zamierzonym tekstem | Sprawdź dwukrotnie system współrzędnych przeglądarki PDF; dostosuj punkty odpowiednio |
| **Adnotacja niewidoczna** | Brak widocznego przekreślenia po zapisaniu | Zwiększ `opacity` (np. `0.9`), sprawdź `pageNumber` (liczba od 0), upewnij się, że punkty tworzą prawidłowy prostokąt |
| **OutOfMemoryError** | Aplikacja się zawiesza przy dużych plikach PDF | Zwiększ przydział pamięci JVM (`-Xmx2048m`), przetwarzaj dokumenty w partiach, zawsze wywołuj `dispose()` |

## Najlepsze praktyki wydajnościowe dla produkcji

### Zarządzanie pamięcią
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Strategia przetwarzania wsadowego
Gdy musisz adnotować dziesiątki lub setki plików:

- Przetwarzaj 10‑20 dokumentów na partię.  
- Loguj sukces/porażkę dla każdego pliku.  
- Ponownie inicjalizuj `Annotator` dla każdego dokumentu, aby uniknąć wycieków pamięci.  

### Wskazówki dotyczące buforowania
- Buforuj często używane szablony dokumentów.  
- Przechowuj wstępnie obliczone mapy współrzędnych dla standardowych układów.  

## Przykłady zastosowań w rzeczywistym świecie

1. **Systemy przeglądu dokumentów** – Redaktorzy sugerują usunięcia bez zmiany oryginalnej umowy.  
2. **Poprawki prawne** – Prawnicy śledzą usunięcia klauzul, zachowując oryginalną treść dla audytu.  
3. **Recenzja akademicka** – Recenzenci oznaczają sekcje do usunięcia i dodają komentarze w tekście.  
4. **Migracja treści** – Podczas migracji CMS, przekreślenia podkreślają przestarzałe treści wymagające zastąpienia.  

## Zaawansowana personalizacja

### Niestandardowy styl
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Dodawanie metadanych
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Lista kontrolna rozwiązywania problemów
- ✅ Czy możesz otworzyć plik źródłowy ręcznie?  
- ✅ Czy wszystkie zależności GroupDocs są obecne w classpath?  
- ✅ Czy punkty tworzą prawidłowy prostokąt?  
- ✅ Czy numer strony jest prawidłowy (liczba od 0)?  
- ✅ Czy jest wystarczająca pamięć sterty?  
- ✅ Czy masz uprawnienia do zapisu w folderze wyjściowym?  
- ✅ Czy format dokumentu jest obsługiwany (PDF, DOCX, PPTX, itp.)?  

## Najczęściej zadawane pytania

**Q: Czy mogę używać GroupDocs.Annotation wewnątrz usługi Spring Boot?**  
A: Tak. Dodaj zależność Maven, wstrzyknij klasę serwisową, która tworzy `Annotator`, i zarządzaj jej cyklem życia przy użyciu zakresów beanów Springa.

**Q: Jakie formaty dokumentów obsługują adnotacje przekreślenia?**  
A: PDF, DOCX, PPTX i wiele innych formatów obsługiwanych przez GroupDocs.Annotation. PDF oferuje najdokładniejsze obsługiwanie współrzędnych.

**Q: Jak obsługiwać dokumenty o różnych rozmiarach stron?**  
A: Pobierz wymiary strony za pomocą `annotator.getPageInfo(pageNumber)` i skaluj współrzędne odpowiednio.

**Q: Czy można edytować lub usunąć istniejącą adnotację przekreślenia?**  
A: Absolutnie. Użyj `annotator.getAnnotations(pageNumber)`, aby pobrać, a następnie `annotator.update(updatedAnnotation)` lub `annotator.delete(annotationId)`.

**Q: Jaki jest wpływ na wydajność dodawania wielu adnotacji?**  
A: Dodawanie setek adnotacji jest zazwyczaj w porządku, ale monitoruj zużycie pamięci. W przypadku bardzo dużych zestawów adnotacji rozważ paginację widoku lub ładowanie adnotacji na żądanie.

## Zakończenie
Masz teraz kompletny, gotowy do produkcji przewodnik do **add strikeout annotation java** przy użyciu GroupDocs.Annotation. Zacznij od prostego przykładu kontrolnego, a następnie przejdź do przetwarzania wsadowego, niestandardowego stylu i wzbogacania metadanymi. Pamiętaj, aby dokładnie testować współrzędne, odpowiedzialnie zarządzać zasobami i wybrać odpowiedni model licencjonowania dla swojego środowiska.

Gotowy, aby odkrywać więcej? Sprawdź inne typy adnotacji — podświetlenie, notatka, obraz, strzałka i znak wodny — aby zbudować w pełni funkcjonalny zestaw współpracy nad dokumentami.

---

**Ostatnia aktualizacja:** 2026-03-30  
**Testowano z:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Dodatkowe zasoby**

- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/java/)
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)
- [Purchase Full License](https://purchase.groupdocs.com/buy)
- [Start Free Trial](https://releases.groupdocs.com/annotation/java/)
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/)