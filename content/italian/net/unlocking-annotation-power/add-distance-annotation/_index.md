---
title: Aggiungi l'annotazione della distanza al documento
linktitle: Aggiungi l'annotazione della distanza al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni sulla distanza ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la collaborazione e la comunicazione senza sforzo.
type: docs
weight: 12
url: /it/net/unlocking-annotation-power/add-distance-annotation/
---
## introduzione
In questo tutorial imparerai come aggiungere un'annotazione di distanza a un documento utilizzando GroupDocs.Annotation per .NET. Seguire questi passaggi per eseguire l'attività:
## Prerequisiti

Prima di procedere, assicurati di disporre dei seguenti prerequisiti:

-  Libreria GroupDocs.Annotation per .NET: scaricare e installare la libreria GroupDocs.Annotation per .NET da[questo link](https://releases.groupdocs.com/annotation/net/).
- Documento da annotare: preparare il documento (ad esempio PDF) a cui si desidera aggiungere l'annotazione della distanza.
- Ambiente di sviluppo: configura il tuo ambiente di sviluppo con Visual Studio o qualsiasi altro IDE di tua scelta.

## Importa spazi dei nomi

Prima di iniziare, assicurati di includere gli spazi dei nomi necessari nel codice. Questi spazi dei nomi sono essenziali per accedere alle classi e ai metodi richiesti.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Passaggio 1: inizializza Annotatore

 Inizia inizializzando il file`Annotator` oggetto con il percorso del documento che desideri annotare.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```

## Passaggio 2: crea l'annotazione della distanza

 Ora crea un file`DistanceAnnotation` oggetto e configurarne le proprietà come dimensioni della casella, messaggio, opacità, colore della penna, ecc.

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

## Passaggio 3: aggiungi annotazione

 Aggiungi l'annotazione della distanza creata al documento utilizzando il comando`Add` metodo dell'oggetto annotatore.

```csharp
annotator.Add(distance);
```

## Passaggio 4: salva il documento

Salva il documento annotato nella posizione desiderata sul tuo sistema.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Passaggio 5: Visualizza conferma

Infine, visualizza un messaggio che conferma l'avvenuto salvataggio del documento annotato.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione

L'aggiunta di annotazioni sulla distanza ai documenti utilizzando GroupDocs.Annotation per .NET è un processo semplice. Seguendo i passaggi delineati in questo tutorial, puoi arricchire i tuoi documenti con annotazioni preziose, facilitando una migliore collaborazione e comunicazione.

## Domande frequenti

### D: Posso personalizzare l'aspetto dell'annotazione della distanza?

R: Sì, puoi personalizzare varie proprietà come colore, opacità, stile della linea, ecc., in base alle tue esigenze.

### D: GroupDocs.Annotation supporta annotazioni su diversi tipi di documenti?

R: Sì, GroupDocs.Annotation supporta annotazioni su un'ampia gamma di formati di documenti tra cui PDF, Word, Excel, PowerPoint e altri.

### D: È disponibile una prova gratuita per GroupDocs.Annotation?

 R: Sì, puoi accedere a una prova gratuita di GroupDocs.Annotation da[questo link](https://releases.groupdocs.com/).

### D: Dove posso trovare la documentazione per GroupDocs.Annotation per .NET?

 R: Puoi fare riferimento alla documentazione dettagliata disponibile[Qui](https://reference.groupdocs.com/annotation/net/).

### D: Come posso ottenere supporto o assistenza con GroupDocs.Annotation?

 R: Puoi chiedere supporto e assistenza al forum della community GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).