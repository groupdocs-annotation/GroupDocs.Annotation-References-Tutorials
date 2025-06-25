---
"description": "Scopri come aggiungere annotazioni di testo sottolineate ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la collaborazione e la comunicazione senza sforzo."
"linktitle": "Aggiungi annotazione di sottolineatura del testo al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione di sottolineatura del testo al documento"
"url": "/it/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Aggiungi annotazione di sottolineatura del testo al documento

## Introduzione
In questo tutorial, illustreremo come aggiungere un'annotazione di testo sottolineato a un documento utilizzando GroupDocs.Annotation per .NET. Le annotazioni di testo sottolineato possono essere utili per enfatizzare parti specifiche di un documento, come passaggi importanti o punti chiave.
## Prerequisiti
Prima di iniziare, assicurati di aver installato i seguenti prerequisiti:
1. GroupDocs.Annotation per .NET: Scarica e installa GroupDocs.Annotation per .NET da [Qui](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: assicurati che .NET Framework sia installato sul tuo sistema.

## Importazione di spazi dei nomi
Per prima cosa, importiamo gli spazi dei nomi necessari nel nostro progetto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ora scomponiamo l'esempio in più passaggi:
## Passaggio 1: definire il percorso di output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In questo passaggio definiamo il percorso di output in cui verrà salvato il documento annotato.
## Passaggio 2: inizializzare l'annotatore
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Qui, inizializziamo un'istanza di `Annotator` classe fornendo il percorso del documento di input.
## Passaggio 3: creare un'annotazione sottolineata
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // funziona supportando solo documenti Word e PDF
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Questo passaggio prevede la creazione di un `UnderlineAnnotation` oggetto con varie proprietà quali colore del carattere, messaggio, opacità, numero di pagina, colore di sfondo, colore di sottolineatura, punti e risposte.
## Passaggio 4: aggiungere annotazioni al documento
```csharp
annotator.Add(underline);
```
Qui aggiungiamo l'annotazione sottolineata al documento.
## Passaggio 5: Salva il documento annotato
```csharp
annotator.Save(outputPath);
```
Infine, salviamo il documento annotato nel percorso di output specificato.

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere un'annotazione di testo sottolineato a un documento utilizzando GroupDocs.Annotation per .NET. Questa potente libreria offre diverse opzioni di annotazione per migliorare la collaborazione e la comunicazione sui documenti.
## Domande frequenti
### Posso personalizzare l'aspetto dell'annotazione sottolineata?
Sì, puoi personalizzare proprietà quali colore, opacità e posizione in base alle tue esigenze.
### GroupDocs.Annotation è compatibile con diversi formati di documenti?
Sì, GroupDocs.Annotation supporta un'ampia gamma di formati di documenti, tra cui Word e PDF.
### Posso aggiungere più annotazioni a un singolo documento?
Certamente, GroupDocs.Annotation consente di aggiungere più annotazioni di diverso tipo a un documento.
### È disponibile una prova gratuita per GroupDocs.Annotation?
Sì, puoi accedere alla versione di prova gratuita da [Qui](https://releases.groupdocs.com/).
### Dove posso ottenere supporto per GroupDocs.Annotation?
Puoi ottenere supporto dal forum della community GroupDocs.Annotation [Qui](https://forum.groupdocs.com/c/annotation/10).