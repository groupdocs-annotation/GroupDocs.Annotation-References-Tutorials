---
"description": "Scopri come aggiungere annotazioni a distanza ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la collaborazione e la comunicazione senza sforzo."
"linktitle": "Aggiungi annotazione di distanza al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione di distanza al documento"
"url": "/it/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Aggiungi annotazione di distanza al documento

## Introduzione
In questo tutorial imparerai come aggiungere un'annotazione di distanza a un documento utilizzando GroupDocs.Annotation per .NET. Segui questi passaggi per completare l'operazione:
## Prerequisiti

Prima di procedere, accertarsi che siano soddisfatti i seguenti prerequisiti:

- Libreria GroupDocs.Annotation per .NET: Scarica e installa la libreria GroupDocs.Annotation per .NET da [questo collegamento](https://releases.groupdocs.com/annotation/net/).
- Documento da annotare: preparare il documento (ad esempio, PDF) a cui si desidera aggiungere l'annotazione della distanza.
- Ambiente di sviluppo: configura il tuo ambiente di sviluppo con Visual Studio o qualsiasi altro IDE di tua scelta.

## Importa spazi dei nomi

Prima di iniziare, assicurati di includere gli spazi dei nomi necessari nel tuo codice. Questi spazi dei nomi sono essenziali per accedere alle classi e ai metodi richiesti.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Passaggio 1: inizializzare l'annotatore

Iniziare inizializzando il `Annotator` oggetto con il percorso del documento che si desidera annotare.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```

## Passaggio 2: creare l'annotazione della distanza

Ora, crea un `DistanceAnnotation` oggetto e configurarne le proprietà, quali dimensioni della casella, messaggio, opacità, colore della penna, ecc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Passaggio 3: aggiungere annotazioni

Aggiungere l'annotazione della distanza creata al documento utilizzando `Add` metodo dell'oggetto annotatore.

```csharp
annotator.Add(distance);
```

## Passaggio 4: Salva il documento

Salvare il documento annotato nella posizione desiderata sul sistema.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Passaggio 5: conferma della visualizzazione

Infine, visualizza un messaggio che conferma l'avvenuto salvataggio del documento annotato.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione

Aggiungere annotazioni di distanza ai documenti utilizzando GroupDocs.Annotation per .NET è un processo semplice. Seguendo i passaggi descritti in questo tutorial, puoi arricchire i tuoi documenti con annotazioni preziose, facilitando una migliore collaborazione e comunicazione.

## Domande frequenti

### D: Posso personalizzare l'aspetto dell'annotazione della distanza?

R: Sì, puoi personalizzare varie proprietà, come colore, opacità, stile della linea, ecc., in base alle tue esigenze.

### D: GroupDocs.Annotation supporta annotazioni su diversi tipi di documenti?

R: Sì, GroupDocs.Annotation supporta annotazioni su un'ampia gamma di formati di documenti, tra cui PDF, Word, Excel, PowerPoint e altri.

### D: È disponibile una prova gratuita per GroupDocs.Annotation?

A: Sì, puoi accedere a una prova gratuita di GroupDocs.Annotation da [questo collegamento](https://releases.groupdocs.com/).

### D: Dove posso trovare la documentazione per GroupDocs.Annotation per .NET?

A: Puoi fare riferimento alla documentazione dettagliata disponibile [Qui](https://tutorials.groupdocs.com/annotation/net/).

### D: Come posso ottenere supporto o assistenza con GroupDocs.Annotation?

A: Puoi cercare supporto e assistenza nel forum della community GroupDocs.Annotation [Qui](https://forum.groupdocs.com/c/annotation/10).