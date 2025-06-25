---
"date": "2025-05-06"
"description": "Dowiedz się, jak dodawać i usuwać podkreślenia w dokumentach Java za pomocą GroupDocs.Annotation. Ulepsz zarządzanie dokumentami dzięki temu szczegółowemu przewodnikowi."
"title": "Dodawanie i usuwanie podkreślonych adnotacji w Javie przy użyciu GroupDocs&#58; Kompleksowy przewodnik"
"url": "/pl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
"weight": 1
---

# Jak wdrożyć Javę: dodawanie i usuwanie podkreślonych adnotacji za pomocą GroupDocs

## Wstęp

Ulepszasz swój system zarządzania dokumentami, dodając lub usuwając adnotacje programowo? Ten samouczek przeprowadzi Cię przez korzystanie z potężnej biblioteki GroupDocs.Annotation w Javie, aby dodawać podkreślone adnotacje i usuwać je z dokumentów, takich jak pliki PDF.

**Czego się nauczysz:**
- Zainicjuj klasę Annotator.
- Dodaj adnotację podkreślającą z komentarzami, korzystając z GroupDocs.Annotation dla języka Java.
- Usuń wszystkie adnotacje z dokumentu.
- Skonfiguruj swoje środowisko, aby efektywnie korzystać z GroupDocs.Annotation.

Przyjrzyjmy się, jak te funkcjonalności mogą być wykorzystane w Twoich projektach. Upewnij się, że masz spełnione niezbędne wymagania wstępne przed rozpoczęciem.

## Wymagania wstępne

### Wymagane biblioteki i zależności
Aby skutecznie skorzystać z tego samouczka, upewnij się, że posiadasz:
- **GroupDocs.Annotation dla Java**:Zalecana jest wersja 25.2 lub nowsza.
- **Zestaw narzędzi programistycznych Java (JDK)**: Wymagana jest wersja 8 lub nowsza.

### Wymagania dotyczące konfiguracji środowiska
Upewnij się, że Twoje środowisko programistyczne obejmuje środowisko IDE, takie jak IntelliJ IDEA lub Eclipse, oraz narzędzie do kompilacji, takie jak Maven.

### Wymagania wstępne dotyczące wiedzy
Przydatna będzie podstawowa znajomość programowania w Javie, zwłaszcza umiejętność pracy z bibliotekami za pośrednictwem Maven.

## Konfigurowanie GroupDocs.Annotation dla Java

Aby rozpocząć korzystanie z GroupDocs.Annotation w projektach Java, wykonaj następujące kroki konfiguracji:

**Konfiguracja Maven:**
Dodaj następującą konfigurację do swojego `pom.xml` plik umożliwiający pobranie i zintegrowanie GroupDocs.Annotation.

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

**Nabycie licencji:**
Zacznij od pobrania bezpłatnej wersji próbnej lub uzyskania tymczasowej licencji od GroupDocs, aby poznać pełne możliwości ich biblioteki. Do użytku produkcyjnego konieczne jest zakupienie licencji.

## Przewodnik wdrażania

### Funkcja 1: Zainicjuj adnotację i dodaj adnotację podkreślenia

Ta sekcja przeprowadzi Cię przez proces inicjalizacji `Annotator` klasę i dodanie podkreślenia do dokumentu.

#### Przegląd
Dodawanie adnotacji pomaga wyróżnić określone części dokumentu. Tutaj skupiamy się na podkreślaniu tekstu komentarzami w celu wyjaśnienia lub uzyskania informacji zwrotnej.

#### Wdrażanie krok po kroku

**1. Zainicjuj adnotator**
Utwórz `Annotator` obiekt i załaduj plik PDF.

```java
import com.groupdocs.annotation.Annotator;

// Załaduj dokument, który chcesz adnotować
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Twórz komentarze z odpowiedziami**
Zdefiniuj komentarze powiązane z podkreśleniem.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Zdefiniuj punkty dla podkreślenia adnotacji**
Ustaw współrzędne, aby określić miejsce, w którym ma pojawić się podkreślenie.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Utwórz i skonfiguruj adnotację podkreślenia**
Utwórz adnotację podkreślającą i ustaw jej właściwości, takie jak kolor, krycie i komentarze.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Żółty w formacie ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Zapisz dokument z adnotacjami**
Zapisz zmiany w nowym pliku.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Porady dotyczące rozwiązywania problemów
- Upewnij się, że wszystkie współrzędne punktów znajdują się w granicach dokumentu.
- Sprawdź, czy `outputPath` katalog istnieje i jest zapisywalny.

### Funkcja 2: Zapisz dokument bez adnotacji

tej sekcji opisano, jak usunąć wszystkie adnotacje z dokumentu, do którego dodano już wcześniej adnotacje.

#### Przegląd
Może zaistnieć potrzeba zapisania czystej wersji dokumentu, bez żadnych adnotacji, w celu udostępnienia jej lub archiwizacji.

#### Wdrażanie krok po kroku

**1. Zainicjuj Adnotator z adnotowanym dokumentem**
Załaduj dokument zawierający istniejące adnotacje.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Skonfiguruj opcje zapisywania, aby usunąć adnotacje**
Określ, że w pliku wyjściowym nie mają być zapisywane żadne adnotacje.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Zapisz dokument bez adnotacji**
Zdefiniuj ścieżkę dla wyczyszczonego dokumentu i zapisz go.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Zastosowania praktyczne

Oto kilka scenariuszy z życia wziętych, w których te funkcje mogą okazać się przydatne:
1. **Przegląd dokumentów**:Podświetlanie i komentowanie fragmentów umowy lub raportu w celu ich przeglądu.
2. **Narzędzia edukacyjne**:Dodawanie adnotacji do podręczników, w tym uwag i poprawek dla uczniów.
3. **Współpraca przy edycji**:Udostępnianie wersji roboczych z komentarzami członkom zespołu w celu uzyskania opinii.
4. **Dokumentacja prawna**:Podkreślanie kluczowych klauzul w dokumentach prawnych podczas dyskusji.
5. **Materiały marketingowe**:Podkreślanie ważnych informacji w broszurach przed ich rozpowszechnieniem.

## Rozważania dotyczące wydajności
Podczas pracy z GroupDocs.Annotation należy wziąć pod uwagę poniższe wskazówki, aby zoptymalizować wydajność:
- **Zarządzanie pamięcią**:Prawidłowo utylizować `Annotator` obiektów w celu zwolnienia zasobów.
- **Przetwarzanie wsadowe**:Jeśli dodajesz adnotacje do wielu dokumentów, przetwarzaj je partiami, aby efektywnie zarządzać obciążeniem systemu.
- **Alokacja zasobów**: Upewnij się, że Twoje środowisko dysponuje wystarczającą ilością pamięci i mocy przetwarzania do obsługi dużych plików.

## Wniosek
Nauczyłeś się, jak dodawać i usuwać podkreślone adnotacje za pomocą GroupDocs.Annotation dla Java. Ten samouczek obejmował inicjowanie klasy Annotator, konfigurowanie adnotacji z komentarzami i zapisywanie dokumentów bez adnotacji. 

celu dalszego zgłębiania tej funkcjonalności, rozważ zintegrowanie tych funkcji z istniejącymi systemami zarządzania dokumentami lub poeksperymentuj z innymi typami adnotacji udostępnianymi przez GroupDocs.

## Sekcja FAQ
1. **Jak skonfigurować wiele podkreśleń w jednym przebiegu?**
   - Utwórz wiele `UnderlineAnnotation` obiekty i dodawać je sekwencyjnie za pomocą `annotator.add()` metoda.
2. **Czy za pomocą tej biblioteki mogę dodawać adnotacje do obrazów w plikach PDF?**
   - Tak, GroupDocs.Annotation obsługuje adnotacje obrazów w dokumentach, takich jak pliki PDF.
3. **Jakie formaty plików obsługuje GroupDocs.Annotation?**
   - Obsługuje różne formaty dokumentów, w tym PDF, Word, Excel i inne.