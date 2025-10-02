---
"date": "2025-05-06"
"description": "Scopri come salvare in modo efficiente solo le pagine annotate di un PDF utilizzando GroupDocs.Annotation per .NET. Migliora la gestione dei documenti e la collaborazione con questa guida dettagliata."
"title": "Come salvare le pagine annotate in PDF utilizzando GroupDocs.Annotation per .NET"
"url": "/it/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# Come salvare le pagine annotate in PDF utilizzando GroupDocs.Annotation per .NET

## Introduzione

Hai difficoltà a salvare pagine annotate specifiche dai tuoi documenti PDF? Questa guida completa illustra come farlo in modo efficiente utilizzando GroupDocs.Annotation per .NET. Sfruttando le funzionalità di annotazione, semplifica la gestione dei documenti e migliora la collaborazione concentrandoti sui contenuti pertinenti.

In questo tutorial imparerai:
- Impostazione dell'ambiente di sviluppo con GroupDocs.Annotation
- Aggiunta di vari tipi di annotazioni
- Salvataggio efficace solo delle pagine annotate

Pronti a iniziare? Assicuriamoci che tutto sia pronto.

### Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:
- **Framework .NET** (versione 4.6 o successiva) o **.NET Core/5+**
- Un editor di codice come Visual Studio
- Conoscenza di base di C# e configurazione di progetti .NET

## Impostazione di GroupDocs.Annotation per .NET

Per iniziare a utilizzare GroupDocs.Annotation, installalo tramite NuGet.

**Console del gestore pacchetti NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\Interfaccia a riga di comando .NET**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Acquisizione della licenza

GroupDocs offre una prova gratuita per esplorare appieno il software. Per un utilizzo prolungato, acquista una licenza o richiedine una temporanea:
- **Prova gratuita**: Esplora le funzionalità senza limitazioni per un periodo iniziale.
- **Licenza temporanea**: Utilizzare temporaneamente GroupDocs.Annotation in produzione.
- **Acquistare**Proteggi le tue esigenze a lungo termine con una licenza commerciale.

Una volta installata, inizializzare la libreria come segue:

```csharp
using GroupDocs.Annotation;

// Configurazione di base per caricare e annotare documenti
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Guida all'implementazione

### Aggiungere annotazioni

#### Panoramica

Le annotazioni aiutano a evidenziare le aree importanti all'interno del documento. Esploriamo l'aggiunta di un `AreaAnnotation` e un `EllipseAnnotation`.

**Passaggio 1: creare annotazioni di area**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definisci l'annotazione dell'area
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posizione e dimensione
    BackgroundColor = 65535,                // Valore colore ARGB per l'evidenziazione
    PageNumber = 1                          // Numero di pagina specifico
};
```

IL `AreaAnnotation` evidenzia un'area rettangolare sul documento. Personalizzane la posizione (`Box`) e colore di sfondo.

**Passaggio 2: creare un'annotazione ellittica**

```csharp
// Definisci l'annotazione dell'ellisse
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posizione e dimensione
    BackgroundColor = 123456,                // Valore colore ARGB per l'evidenziazione
    PageNumber = 1                           // Numero di pagina specifico
};
```

IL `EllipseAnnotation` consente di disegnare una forma ovale sul documento. Regola posizione e dimensioni utilizzando `Box` proprietà.

**Passaggio 3: aggiungere annotazioni**

```csharp
// Aggiunta di annotazioni all'istanza Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Utilizzando il `Add` metodo, include più tipi di annotazioni. Questo passaggio aggiunge sia `AreaAnnotation` E `EllipseAnnotation`.

### Salvataggio solo delle pagine annotate

#### Panoramica

Per salvare solo le pagine contenenti annotazioni, configura di conseguenza le opzioni di salvataggio.

**Passaggio 4: Salva le pagine annotate**

```csharp
using GroupDocs.Annotation.Options;

// Imposta le opzioni di salvataggio per includere solo le pagine annotate
annotator.Save("path/to/output/document.pdf\