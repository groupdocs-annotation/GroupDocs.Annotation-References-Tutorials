---
title: Aggiungi annotazione di testo barrato al documento
linktitle: Aggiungi annotazione di testo barrato al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di testo barrate ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la collaborazione e i processi di revisione dei documenti in modo efficiente.
weight: 26
url: /it/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## introduzione
In questo tutorial esploreremo come aggiungere un'annotazione di testo barrato a un documento utilizzando GroupDocs.Annotation per .NET. Questa libreria fornisce potenti strumenti per annotare vari tipi di documenti, migliorando la collaborazione e i processi di revisione dei documenti.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1.  GroupDocs.Annotation per .NET: installare la libreria. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: impostare un ambiente di sviluppo adatto per lo sviluppo .NET.
3. Documento: avere un documento pronto per l'annotazione, ad esempio un file PDF.

## Importazione di spazi dei nomi
Innanzitutto, importa gli spazi dei nomi necessari per accedere alle funzionalità di GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ora suddividiamo il processo di aggiunta di un'annotazione di testo barrato in più passaggi:
## Passaggio 1: definire il percorso di output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Qui definiamo il percorso di output in cui verrà salvato il documento annotato.
## Passaggio 2: inizializza Annotatore
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inizializza l'oggetto Annotator fornendo il percorso del documento di input (file PDF in questo caso).
## Passaggio 3: crea un'annotazione barrata
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Crea un oggetto StrikeoutAnnotation con le proprietà desiderate come messaggio, opacità, numero di pagina, colore di sfondo, punti (coordinate) e risposte.
## Passaggio 4: aggiungi annotazione
```csharp
annotator.Add(strikeout);
```
Aggiungi l'annotazione barrata creata al documento.
## Passaggio 5: salva il documento
```csharp
annotator.Save(outputPath);
```
Salva il documento annotato nel percorso di output specificato.

## Conclusione
In questo tutorial abbiamo imparato come aggiungere un'annotazione di testo barrato a un documento utilizzando GroupDocs.Annotation per .NET. Questa potente libreria consente un'annotazione efficiente dei documenti, migliorando la collaborazione e i processi di revisione dei documenti.
## Domande frequenti
### GroupDocs.Annotation è compatibile con vari formati di documenti?
Sì, GroupDocs.Annotation supporta un'ampia gamma di formati di documenti tra cui PDF, Word, Excel, PowerPoint e altri.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente, puoi personalizzare le proprietà delle annotazioni come colore, opacità, dimensione del carattere e altro in base alle tue esigenze.
### GroupDocs.Annotation fornisce funzionalità di collaborazione?
Sì, GroupDocs.Annotation facilita la collaborazione consentendo agli utenti di aggiungere commenti, risposte e annotazioni ai documenti.
### È disponibile una prova gratuita?
 Sì, puoi usufruire di una prova gratuita da[Qui](https://releases.groupdocs.com/).
### Dove posso ottenere supporto per GroupDocs.Annotation?
 Puoi ottenere supporto da[Forum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).