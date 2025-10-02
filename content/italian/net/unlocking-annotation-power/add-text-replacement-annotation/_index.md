---
"description": "Scopri come aggiungere annotazioni di sostituzione del testo ai tuoi documenti .NET senza sforzo utilizzando GroupDocs.Annotation per .NET. Migliora le tue capacità di manipolazione dei documenti."
"linktitle": "Aggiungi annotazione di sostituzione del testo al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione di sostituzione del testo al documento"
"url": "/it/net/unlocking-annotation-power/add-text-replacement-annotation/"
type: docs
"weight": 24
---

# Aggiungi annotazione di sostituzione del testo al documento

## Introduzione
In questo tutorial, ti guideremo attraverso il processo di aggiunta di un'annotazione di sostituzione del testo ai tuoi documenti utilizzando GroupDocs.Annotation per .NET. Questa potente libreria consente agli sviluppatori di manipolare e annotare vari tipi di documenti a livello di codice. Al termine di questo tutorial, avrai le conoscenze necessarie per integrare perfettamente le annotazioni di sostituzione del testo nelle tue applicazioni .NET.
## Prerequisiti
Prima di iniziare, assicurati di aver installato i seguenti prerequisiti:
### 1. .NET Framework installato
Assicurati di avere .NET Framework installato sul tuo computer di sviluppo. Puoi scaricarlo dal sito web di Microsoft.
### 2. GroupDocs.Annotation per la libreria .NET
Scarica e installa la libreria GroupDocs.Annotation per .NET da [sito web](https://releases.groupdocs.com/annotation/net/)Questa libreria fornisce gli strumenti e le funzionalità necessari per lavorare con annotazioni in vari formati di documenti.
### 3. Configurazione dell'ambiente di sviluppo
Imposta il tuo ambiente di sviluppo preferito, ad esempio Visual Studio, per creare ed eseguire applicazioni .NET.

## Importa spazi dei nomi
Prima di addentrarci nella parte di codifica, importiamo gli spazi dei nomi necessari per lavorare con GroupDocs.Annotation per .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Passaggio 1: definire il percorso di output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Qui definiamo il percorso di output in cui verrà salvato il documento annotato.
## Passaggio 2: inizializzare l'annotatore
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione verrà inserito qui
}
```
Inizializziamo l'oggetto Annotator specificando il documento di input ("input.pdf") all'interno di un blocco using per garantire il corretto smaltimento delle risorse.
## Passaggio 3: creare un'annotazione sostitutiva
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
Qui creiamo un oggetto ReplacementAnnotation con varie proprietà, quali data di creazione, colore del carattere, messaggio, opacità, numero di pagina, colore di sfondo, punti (coordinate), risposte (commenti) e testo da sostituire.
## Passaggio 4: aggiungere annotazioni
```csharp
annotator.Add(replacement);
```
Aggiungiamo l'annotazione sostitutiva creata all'annotatore.
## Passaggio 5: Salva il documento
```csharp
annotator.Save(outputPath);
```
Infine, salviamo il documento annotato nel percorso di output specificato.
## Passaggio 6: visualizzare il messaggio di successo
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Viene visualizzato un messaggio di successo che indica che il documento è stato salvato correttamente.

## Conclusione
In questo tutorial abbiamo illustrato come aggiungere annotazioni di sostituzione del testo ai documenti utilizzando GroupDocs.Annotation per .NET. Seguendo la guida passo passo e comprendendo i prerequisiti, potrete integrare facilmente questa funzionalità nelle vostre applicazioni .NET.
## Domande frequenti
### Posso annotare documenti di formati diversi utilizzando GroupDocs.Annotation per .NET?
Sì, GroupDocs.Annotation per .NET supporta l'annotazione di vari formati di documenti, tra cui PDF, DOCX, PPTX, XLSX e altri.
### GroupDocs.Annotation per .NET è adatto sia per le applicazioni desktop che per quelle web?
Sì, GroupDocs.Annotation per .NET può essere utilizzato sia nelle applicazioni desktop che web, offrendo flessibilità agli sviluppatori.
### Posso personalizzare l'aspetto delle annotazioni aggiunte tramite GroupDocs.Annotation per .NET?
Certamente, puoi personalizzare l'aspetto delle annotazioni modificando proprietà quali colore, opacità, carattere, ecc.
### GroupDocs.Annotation per .NET supporta le funzionalità di annotazione collaborativa?
Sì, GroupDocs.Annotation per .NET offre funzionalità per l'annotazione collaborativa, consentendo a più utenti di annotare documenti contemporaneamente.
### È disponibile una versione di prova gratuita di GroupDocs.Annotation per .NET?
Sì, puoi usufruire di una prova gratuita di GroupDocs.Annotation per .NET da [sito web](https://releases.groupdocs.com/).