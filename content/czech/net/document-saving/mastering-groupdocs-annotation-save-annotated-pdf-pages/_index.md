---
"date": "2025-05-06"
"description": "Naučte se, jak efektivně ukládat pouze anotované stránky PDF pomocí nástroje GroupDocs.Annotation pro .NET. Vylepšete správu dokumentů a spolupráci s tímto podrobným průvodcem."
"title": "Jak uložit anotované stránky do PDF pomocí GroupDocs.Annotation pro .NET"
"url": "/cs/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# Jak uložit anotované stránky do PDF pomocí GroupDocs.Annotation pro .NET

## Zavedení

Máte potíže s ukládáním konkrétních anotovaných stránek z vašich PDF dokumentů? Tato komplexní příručka ukazuje, jak toho efektivně dosáhnout pomocí GroupDocs.Annotation pro .NET. Využitím funkcí anotací zefektivníte správu dokumentů a vylepšíte spolupráci zaměřením na relevantní obsah.

tomto tutoriálu se naučíte:
- Nastavení vývojového prostředí s GroupDocs.Annotation
- Přidávání různých typů anotací
- Efektivní ukládání pouze anotovaných stránek

Připraveni začít? Ujistěme se, že máte vše připravené.

### Předpoklady

Než začnete, ujistěte se, že máte následující:
- **.NET Framework** (verze 4.6 nebo novější) nebo **.NET Core/5+**
- Editor kódu, jako je Visual Studio
- Základní znalost nastavení projektů v C# a .NET

## Nastavení GroupDocs.Annotation pro .NET

Chcete-li začít používat GroupDocs.Annotation, nainstalujte si ho pomocí NuGetu.

**Konzola Správce balíčků NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\Rozhraní příkazového řádku .NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Získání licence

GroupDocs nabízí bezplatnou zkušební verzi pro plné prozkoumání softwaru. Pro delší používání si zakupte licenci nebo požádejte o dočasnou:
- **Bezplatná zkušební verze**Prozkoumejte funkce bez omezení po počáteční dobu.
- **Dočasná licence**Dočasně používejte GroupDocs.Annotation v produkčním prostředí.
- **Nákup**Zajistěte si své dlouhodobé potřeby komerční licencí.

Po instalaci inicializujte knihovnu takto:

```csharp
using GroupDocs.Annotation;

// Základní nastavení pro načítání a anotaci dokumentů
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Průvodce implementací

### Přidávání anotací

#### Přehled

Anotace pomáhají zvýraznit důležité oblasti v dokumentu. Pojďme se podívat na přidání `AreaAnnotation` a `EllipseAnnotation`.

**Krok 1: Vytvoření anotace oblasti**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definujte anotaci oblasti
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozice a velikost
    BackgroundColor = 65535,                // Hodnota barvy ARGB pro zvýraznění
    PageNumber = 1                          // Konkrétní číslo stránky
};
```

Ten/Ta/To `AreaAnnotation` zvýrazní obdélníkovou oblast v dokumentu. Přizpůsobte její polohu (`Box`) a barvu pozadí.

**Krok 2: Vytvořte anotaci elipsy**

```csharp
// Definujte anotaci elipsy
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozice a velikost
    BackgroundColor = 123456,                // Hodnota barvy ARGB pro zvýraznění
    PageNumber = 1                           // Konkrétní číslo stránky
};
```

Ten/Ta/To `EllipseAnnotation` umožňuje nakreslit oválný tvar v dokumentu. Upravte polohu a rozměry pomocí `Box` vlastnictví.

**Krok 3: Přidání anotací**

```csharp
// Přidávání anotací k instanci Annotatoru
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Použití `Add` metodu, zahrnout více typů anotací. Tento krok přidá jak `AreaAnnotation` a `EllipseAnnotation`.

### Ukládání pouze anotovaných stránek

#### Přehled

Chcete-li ukládat pouze stránky obsahující anotace, nakonfigurujte odpovídajícím způsobem možnosti ukládání.

**Krok 4: Uložení anotovaných stránek**

```csharp
using GroupDocs.Annotation.Options;

// Nastavení možností ukládání tak, aby zahrnovaly pouze stránky s poznámkami
annotator.Save("path/to/output/document.pdf\