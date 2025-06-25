---
"description": "Scopri come aggiungere annotazioni alle immagini dei documenti utilizzando GroupDocs.Annotation per .NET. Migliora la gestione dei documenti con potenti funzionalità di annotazione."
"linktitle": "Aggiungi annotazione immagine al documento (percorso remoto)"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione immagine al documento (percorso remoto)"
"url": "/it/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Aggiungi annotazione immagine al documento (percorso remoto)

## Introduzione
In questo tutorial, illustreremo il processo di aggiunta di annotazioni alle immagini a un documento utilizzando GroupDocs.Annotation per .NET. Questa libreria fornisce potenti strumenti per annotare vari tipi di documenti a livello di codice.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. GroupDocs.Annotation per .NET: Scarica e installa la libreria da [Qui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: assicurati di disporre di un ambiente di sviluppo funzionante configurato per lo sviluppo .NET.
3. Documento: prepara il documento che desideri annotare. Per questo tutorial, daremo per scontato che tu abbia un documento PDF denominato `input.pdf`.
4. Immagine per l'annotazione: scegli l'immagine che desideri utilizzare per l'annotazione. Assicurati di avere a portata di mano l'URL o il percorso locale dell'immagine.

## Importa spazi dei nomi
Prima di iniziare a scrivere il codice, importiamo gli spazi dei nomi necessari:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Passaggio 1: impostare il percorso di output
Per prima cosa, definisci il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializzare l'annotatore
Crea un'istanza di `Annotator` classe e specificare il documento di input.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: aggiungere annotazioni all'immagine
Ora aggiungiamo l'annotazione dell'immagine al documento. Specifichiamo le proprietà dell'annotazione dell'immagine, come posizione, opacità, numero di pagina e percorso dell'immagine.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Specificare la posizione dell'annotazione
    CreatedOn = DateTime.Now, // Imposta la data di creazione
    Opacity = 0.7, // Imposta l'opacità (da 0 a 1)
    PageNumber = 0, // Specificare il numero di pagina
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Fornisci l'URL dell'immagine
};
annotator.Add(image); // Aggiungi l'annotazione dell'immagine
```
## Passaggio 4: Salva il documento
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
```
## Passaggio 5: visualizzare il percorso di output
Informa l'utente dell'avvenuto salvataggio del documento e visualizza il percorso di output.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial abbiamo imparato come aggiungere annotazioni alle immagini di un documento utilizzando GroupDocs.Annotation per .NET. Seguendo questi passaggi, puoi migliorare le tue applicazioni di gestione dei documenti con potenti funzionalità di annotazione.
## Domande frequenti
### GroupDocs.Annotation può essere utilizzato con altri formati di documento oltre al PDF?
Sì, GroupDocs.Annotation supporta vari formati di documenti, tra cui Word, Excel, PowerPoint e altri.
### GroupDocs.Annotation è compatibile con .NET Core?
Sì, GroupDocs.Annotation è compatibile sia con .NET Framework che con .NET Core.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, puoi personalizzare l'aspetto delle annotazioni, ad esempio colore, opacità e dimensione.
### GroupDocs.Annotation supporta le funzionalità di annotazione collaborativa?
Sì, GroupDocs.Annotation offre funzionalità di annotazione collaborativa per la collaborazione in tempo reale sui documenti.
### Esiste una versione di prova disponibile per effettuare dei test?
Sì, puoi ottenere una prova gratuita di GroupDocs.Annotation da [Qui](https://releases.groupdocs.com/).