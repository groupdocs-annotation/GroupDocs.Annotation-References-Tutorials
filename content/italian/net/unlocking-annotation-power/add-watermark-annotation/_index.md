---
"description": "Scopri come aggiungere annotazioni con filigrana ai tuoi documenti senza sforzo utilizzando GroupDocs.Annotation per .NET. Migliora la chiarezza e la sicurezza dei documenti."
"linktitle": "Aggiungi annotazione filigrana al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione filigrana al documento"
"url": "/it/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# Aggiungi annotazione filigrana al documento

## Introduzione
In questo tutorial, illustreremo come aggiungere un'annotazione con filigrana a un documento utilizzando GroupDocs.Annotation per .NET. Le annotazioni con filigrana sono utili per indicare lo stato di un documento, contrassegnarlo come riservato o aggiungere qualsiasi altra informazione pertinente.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. GroupDocs.Annotation per .NET: puoi scaricarlo da [Qui](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: assicurati che Visual Studio sia installato sul tuo sistema.
3. Conoscenza di base di C#: è necessaria familiarità con il linguaggio di programmazione C# per comprendere e implementare gli esempi di codice.

## Importa spazi dei nomi

Prima di iniziare a scrivere il codice, importiamo gli spazi dei nomi necessari:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Ora, scomponiamo il processo di aggiunta di un'annotazione con filigrana in più passaggi:

## Passaggio 1: definire il percorso di output

Per prima cosa, dobbiamo definire il percorso di output in cui verrà salvato il documento annotato. Useremo il `Path` classe da `System.IO` namespace per combinare il percorso della directory di output con il nome del file.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Passaggio 2: inizializzare l'annotatore

Successivamente, inizializzeremo l'annotatore specificando il percorso del documento di input. Questo ci permetterà di aggiungere annotazioni al documento.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```

## Passaggio 3: creare un'annotazione con filigrana

Ora creiamo un oggetto di annotazione filigrana con le proprietà desiderate, quali angolo, posizione, testo, colore del carattere, opacità, ecc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```

## Passaggio 4: aggiungere l'annotazione della filigrana

Ora aggiungeremo l'annotazione della filigrana al documento utilizzando `Add` metodo dell'oggetto annotatore.

```csharp
annotator.Add(watermark);
```

## Passaggio 5: Salva il documento

Infine, salveremo il documento annotato nel percorso di output specificato.

```csharp
annotator.Save(outputPath);
```

## Conclusione

In questo tutorial abbiamo imparato come aggiungere un'annotazione con filigrana a un documento utilizzando GroupDocs.Annotation per .NET. Le annotazioni con filigrana sono uno strumento prezioso per contrassegnare i documenti con informazioni rilevanti o indicarne lo stato.

## Domande frequenti

### D: Posso personalizzare l'aspetto dell'annotazione della filigrana?

R: Sì, puoi personalizzare varie proprietà, come testo, dimensione del carattere, colore, opacità, posizione, ecc., per adattare la filigrana alle tue esigenze.

### D: GroupDocs.Annotation per .NET è compatibile con diversi formati di documenti?

R: Sì, GroupDocs.Annotation supporta un'ampia gamma di formati di documenti, tra cui PDF, Microsoft Word, Excel, PowerPoint e formati immagine.

### D: Posso aggiungere più annotazioni a un singolo documento?

R: Assolutamente sì, GroupDocs.Annotation consente di aggiungere più annotazioni di diverso tipo a un singolo documento, consentendo una marcatura completa del documento.

### D: GroupDocs.Annotation supporta l'annotazione collaborativa?

R: Sì, GroupDocs.Annotation facilita l'annotazione collaborativa consentendo agli utenti di aggiungere commenti, risposte e annotazioni, favorendo una collaborazione efficace tra i membri del team.

### D: È disponibile una versione di prova di GroupDocs.Annotation per .NET?

A: Sì, puoi scaricare una versione di prova gratuita da [Qui](https://releases.groupdocs.com/).