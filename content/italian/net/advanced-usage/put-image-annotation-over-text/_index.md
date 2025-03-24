---
title: Metti l'annotazione dell'immagine sul testo
linktitle: Metti l'annotazione dell'immagine sul testo
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di immagini sul testo in .NET utilizzando GroupDocs.Annotation per una gestione e una collaborazione efficienti dei documenti.
weight: 21
url: /it/net/advanced-usage/put-image-annotation-over-text/
---

# Metti l'annotazione dell'immagine sul testo

## introduzione
Nel mondo dello sviluppo .NET, GroupDocs.Annotation offre una potente soluzione per aggiungere annotazioni ai documenti, rendendo più efficiente la collaborazione e la gestione dei documenti. Un requisito comune è l'inserimento di annotazioni di immagini sul testo, operazione che può essere eseguita senza problemi utilizzando GroupDocs.Annotation per .NET.
## Prerequisiti
Prima di immergerti nel processo di inserimento delle annotazioni delle immagini sul testo utilizzando GroupDocs.Annotation per .NET, assicurati di avere quanto segue:
1.  GroupDocs.Annotation per .NET Library: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: configura un ambiente di sviluppo adatto, come Visual Studio o qualsiasi altro IDE .NET.
3. File di documenti e immagini: prepara il file di documento (PDF, DOCX, ecc.) e il file di immagine che desideri utilizzare per le annotazioni.
4. Comprensione di base di C#: la familiarità con il linguaggio di programmazione C# è necessaria per implementare i frammenti di codice forniti in questo tutorial.

## Importa spazi dei nomi
Prima di procedere con il processo di annotazione, assicurati di importare gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Passaggio 1: definire il percorso di output
Innanzitutto, definisci il percorso di output in cui verrà salvato il documento annotato:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Passaggio 2: inizializza Annotatore
 Inizializza il`Annotator` oggetto fornendo il percorso del documento di input:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: crea un'annotazione sull'immagine
 Creare un`ImageAnnotation` oggetto con le proprietà desiderate come dimensioni della casella, opacità, numero di pagina, percorso dell'immagine e z-index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Passaggio 4: aggiungi annotazione
 Aggiungi l'annotazione dell'immagine al documento utilizzando il file`Add` metodo del`Annotator` oggetto:
```csharp
annotator.Add(image);
```
## Passaggio 5: salva il documento con annotazioni
Salva il documento annotato nel percorso di output specificato:
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: Visualizza il messaggio di successo
Visualizza un messaggio di successo con il percorso del documento annotato:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, l'aggiunta di annotazioni di immagini sul testo nelle applicazioni .NET utilizzando GroupDocs.Annotation è un processo semplice. Seguendo la guida passo passo fornita in questo tutorial, puoi annotare documenti in modo efficiente e migliorare le funzionalità di collaborazione e gestione dei documenti nei tuoi progetti .NET.
## Domande frequenti
### Posso annotare documenti diversi dai PDF?
Sì, GroupDocs.Annotation supporta vari formati di documenti come DOCX, XLSX, PPTX e altri.
### È disponibile una prova gratuita per GroupDocs.Annotation?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per GroupDocs.Annotation?
 Puoi ottenere supporto dal forum della community GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).
### Ho bisogno di una licenza temporanea a scopo di test?
 Sì, puoi ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/) a scopo di test.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, GroupDocs.Annotation fornisce varie opzioni per personalizzare l'aspetto delle annotazioni come colore, opacità, dimensione del carattere, ecc.