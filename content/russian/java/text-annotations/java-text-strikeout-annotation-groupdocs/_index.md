---
categories:
- Java Development
date: '2026-03-30'
description: Узнайте, как добавить аннотацию «зачёркнутый текст» в Java с помощью
  GroupDocs.Annotation. Пошаговое руководство с примерами кода, советами по устранению
  неполадок и лучшими практиками разметки документов.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Добавление аннотации зачёркивания в Java. Руководство с GroupDocs
type: docs
url: /ru/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Добавление зачеркивающей аннотации Java — Полное руководство GroupDocs

Когда‑то вы, глядя на документ, думали: «Нужно зачеркнуть этот текст, но у меня нет красной ручки»? Вы не одиноки. Будь то система рецензирования документов, рабочий процесс редактирования или просто необходимость пометить текст для удаления в вашем Java‑приложении, **add strikeout annotation java** — важный навык. В этом руководстве мы пройдем всё, что нужно знать, чтобы реализовать функцию зачеркивания текста, действительно работающую в продакшене.

## Быстрые ответы
- **Какая библиотека поддерживает зачеркивающие аннотации в Java?** GroupDocs.Annotation for Java  
- **Какое ключевое слово следует использовать для SEO?** add strikeout annotation java  
- **Нужна ли лицензия для запуска примера кода?** Для разработки подходит бесплатная пробная или временная лицензия; для продакшена требуется полная лицензия.  
- **Можно ли использовать её с PDF, DOCX и PPTX?** Да — GroupDocs.Annotation поддерживает все основные форматы документов.  
- **Какая версия Java требуется?** JDK 8 или выше (рекомендовано JDK 11+).

## Что такое add strikeout annotation java?
Зачеркивающая аннотация рисует линию через выбранный текст, визуально указывая, что содержимое следует удалить или игнорировать. Это недеструктивный способ предложить удаление, сохраняя оригинальный текст для аудита или совместных рецензий.

## Почему использовать зачеркивающие аннотации в Java‑приложениях?
- **Рабочие процессы рецензирования** — рецензенты могут помечать нежелательный текст, не изменяя исходный файл.  
- **Совместное редактирование** — участники команды сразу видят предложенные удаления.  
- **Юридические и комплаенс‑требования** — сохраняется чёткая трассировка изменений.  
- **Миграция контента** — отмечайте устаревшие разделы перед переносом между системами.  

## Предварительные требования и настройка окружения
Вам понадобится следующее перед тем, как приступить к коду:

- **Java Development Kit (JDK)** 8+ (рекомендовано JDK 11+)  
- **Maven или Gradle** для управления зависимостями  
- **IDE** — IntelliJ IDEA, Eclipse или VS Code с Java‑расширениями  
- **Библиотека GroupDocs.Annotation** — в примерах используется версия 25.2  

*Желательно:* базовые знания Java‑аннотаций и работы с PDF.

## Настройка GroupDocs.Annotation для Java

### Maven‑конфигурация, которая действительно работает
Добавьте репозиторий и зависимость в ваш `pom.xml` точно как показано:

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

### Получение лицензии
GroupDocs предлагает несколько вариантов лицензирования:

- **Бесплатная пробная** — идеально для тестов (без необходимости указывать кредитную карту)  
- **Временная лицензия** — подходит для разработки и тестовых сред  
- **Полная лицензия** — обязательна для продакшена; см. [страницу покупки](https://purchase.groupdocs.com/buy)

> **Pro tip:** Начните с бесплатной пробной версии, чтобы изучить API, затем переключитесь на временную лицензию, когда будете готовы реализовать реальную функцию.

### Быстрая проверка работоспособности
Запустите эту минимальную программу, чтобы убедиться, что библиотека загружается корректно:

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

Если в консоли появилось сообщение об успехе без ошибок, вы готовы добавлять зачеркивающие аннотации.

## Как добавить зачеркивающую аннотацию java

Ниже представлена полная, готовая к продакшену реализация, разбитая на понятные шаги.

### Шаг 1 — Инициализация Annotator
Создайте экземпляр `Annotator`, указывающий на исходный документ:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Почему это важно:** Использование абсолютного или правильно разрешённого относительного пути предотвращает исключения «file not found».

### Шаг 2 — (Опционально) Подготовка ответов к комментариям
Добавление ответов делает аннотацию совместной:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Эти комментарии появляются, когда пользователь наводит курсор на зачеркивание.

### Шаг 3 — Определение области зачеркивания
Укажите прямоугольник, охватывающий текст, который нужно зачеркнуть:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Подсказка по координатам:** Начало (0,0) находится в левом верхнем углу страницы; X растёт вправо, Y — вниз. Используйте PDF‑просмотрщик, показывающий координаты, чтобы точно подобрать значения.

### Шаг 4 — Настройка зачеркивающей аннотации
Установите внешний вид, номер страницы и привяжите комментарии:

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

*Примечание о цвете:* `65535` соответствует желтому в целочисленном формате RGB. Измените значение, чтобы использовать другие цвета.

### Шаг 5 — Применение аннотации и сохранение
Добавьте аннотацию в документ и запишите файл‑результат:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Шаг 6 — Очистка ресурсов (Критически важно!)
Всегда освобождайте `Annotator`, чтобы освободить нативные ресурсы:

```java
if (annotator != null) {
    annotator.dispose();
}
```

В продакшене оберните использование в блок `try‑with‑resources` или конструкцию `try/finally`.

## Распространённые проблемы и их решения

| Проблема | Симптом | Решение |
|----------|---------|---------|
| **File Not Found** | `Annotator` бросает исключение | Используйте абсолютные пути, проверьте права чтения, убедитесь, что файл не заблокирован другим процессом |
| **Wrong Coordinates** | Зачеркивание появляется не там, где нужно | Перепроверьте систему координат в PDF‑просмотрщике; скорректируйте точки |
| **Annotation Invisible** | После сохранения нет видимого зачеркивания | Увеличьте `opacity` (например, `0.9`), проверьте `pageNumber` (нумерация с 0), убедитесь, что точки образуют корректный прямоугольник |
| **OutOfMemoryError** | Приложение падает при работе с большими PDF | Увеличьте размер кучи JVM (`-Xmx2048m`), обрабатывайте документы пакетами, всегда вызывайте `dispose()` |

## Лучшие практики производительности для продакшена

### Управление памятью
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

### Стратегия пакетной обработки
Когда нужно аннотировать десятки или сотни файлов:

- Обрабатывайте 10‑20 документов за один пакет.  
- Ведите журнал успехов/ошибок для каждого файла.  
- Переинициализируйте `Annotator` для каждого документа, чтобы избежать утечек памяти.  

### Советы по кэшированию
- Кешируйте часто используемые шаблоны документов.  
- Храните предварительно рассчитанные карты координат для стандартных макетов.  

## Реальные сценарии использования

1. **Системы рецензирования документов** — редакторы предлагают удаление без изменения оригинального контракта.  
2. **Юридические поправки** — юристы отслеживают удаление пунктов, сохраняя оригинальный текст для аудита.  
3. **Академический peer review** — рецензенты отмечают части для удаления и добавляют встроенные комментарии.  
4. **Миграция контента** — при переносе CMS зачеркивания выделяют устаревший копирайт, требующий замены.  

## Расширенная настройка

### Пользовательские стили
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Добавление метаданных
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Чек‑лист по отладке
- ✅ Можно ли открыть исходный файл вручную?  
- ✅ Все ли зависимости GroupDocs находятся в classpath?  
- ✅ Формируют ли точки корректный прямоугольник?  
- ✅ Правильный ли номер страницы (нумерация с 0)?  
- ✅ Достаточно ли выделено памяти в куче?  
- ✅ Есть ли права записи в папку вывода?  
- ✅ Поддерживается ли формат документа (PDF, DOCX, PPTX и т.д.)?  

## Часто задаваемые вопросы

**В: Можно ли использовать GroupDocs.Annotation внутри сервиса Spring Boot?**  
О: Да. Добавьте Maven‑зависимость, внедрите сервисный класс, создающий `Annotator`, и управляйте его жизненным циклом через области видимости Spring‑бинов.

**В: Какие форматы документов поддерживают зачеркивающие аннотации?**  
О: PDF, DOCX, PPTX и многие другие форматы, поддерживаемые GroupDocs.Annotation. PDF обеспечивает наиболее точную работу с координатами.

**В: Как обрабатывать документы с разными размерами страниц?**  
О: Получайте размеры страницы через `annotator.getPageInfo(pageNumber)` и масштабируйте координаты соответственно.

**В: Можно ли редактировать или удалять существующую зачеркивающую аннотацию?**  
О: Конечно. Используйте `annotator.getAnnotations(pageNumber)`, затем `annotator.update(updatedAnnotation)` или `annotator.delete(annotationId)`.

**В: Каково влияние на производительность при добавлении большого количества аннотаций?**  
О: Добавление сотен аннотаций обычно не проблематично, но следует мониторить использование памяти. Для очень больших наборов аннотаций рассматривайте пагинацию представления или ленивую загрузку по запросу.

## Заключение
Теперь у вас есть полное, готовое к продакшену руководство по **add strikeout annotation java** с использованием GroupDocs.Annotation. Начните с простого примера проверки, затем масштабируйте до пакетной обработки, пользовательских стилей и обогащения метаданными. Не забывайте тщательно проверять координаты, правильно управлять ресурсами и выбирать подходящую модель лицензирования для вашего окружения.

Готовы исследовать дальше? Ознакомьтесь с другими типами аннотаций — highlight, note, image, arrow и watermark — чтобы построить полноценный набор инструментов для совместной работы с документами.

---

**Последнее обновление:** 2026-03-30  
**Тестировано с:** GroupDocs.Annotation 25.2 for Java  
**Автор:** GroupDocs  

**Дополнительные ресурсы**

- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/java/)
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)
- [Purchase Full License](https://purchase.groupdocs.com/buy)
- [Start Free Trial](https://releases.groupdocs.com/annotation/java/)
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/)