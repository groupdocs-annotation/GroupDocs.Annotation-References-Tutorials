---
title: Aggiungi annotazione immagine al documento (percorso remoto)
linktitle: Aggiungi annotazione immagine al documento (percorso remoto)
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di immagini ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la gestione dei documenti con potenti funzionalità di annotazione.
type: docs
weight: 15
url: /it/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## introduzione
In questo tutorial, esamineremo il processo di aggiunta di annotazioni immagine a un documento utilizzando GroupDocs.Annotation per .NET. Questa libreria fornisce potenti strumenti per annotare vari tipi di documenti a livello di codice.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Annotation per .NET: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: assicurati di disporre di un ambiente di sviluppo funzionante configurato per lo sviluppo .NET.
3.  Documento: prepara il documento che desideri annotare. Per questo tutorial, supponiamo che tu abbia un documento PDF denominato`input.pdf`.
4. Immagine per l'annotazione: scegli l'immagine che desideri utilizzare per l'annotazione. Assicurati di avere a portata di mano l'URL dell'immagine o il percorso locale.

## Importa spazi dei nomi
Prima di iniziare a scrivere il codice, importiamo gli spazi dei nomi necessari:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Passaggio 1: impostare il percorso di output
Innanzitutto, definisci il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializza Annotatore
 Crea un'istanza di`Annotator` classe e specificare il documento di input.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: aggiungi annotazione immagine
Ora aggiungiamo l'annotazione dell'immagine al documento. Specificheremo le proprietà dell'annotazione dell'immagine come posizione, opacità, numero di pagina e percorso dell'immagine.
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
## Passaggio 4: salva il documento
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
```
## Passaggio 5: Visualizza il percorso di output
Informare l'utente dell'avvenuta operazione di salvataggio del documento e visualizzare il percorso di output.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial abbiamo imparato come aggiungere annotazioni immagine a un documento utilizzando GroupDocs.Annotation per .NET. Seguendo questi passaggi, puoi migliorare le tue applicazioni di gestione dei documenti con potenti funzionalità di annotazione.
## Domande frequenti
### È possibile utilizzare GroupDocs.Annotation con altri formati di documenti oltre al PDF?
Sì, GroupDocs.Annotation supporta vari formati di documenti tra cui Word, Excel, PowerPoint e altri.
### GroupDocs.Annotation è compatibile con .NET Core?
Sì, GroupDocs.Annotation è compatibile sia con .NET Framework che con .NET Core.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, puoi personalizzare l'aspetto delle annotazioni come colore, opacità e dimensione.
### GroupDocs.Annotation supporta le funzionalità di annotazione collaborativa?
Sì, GroupDocs.Annotation offre funzionalità di annotazione collaborativa per la collaborazione in tempo reale sui documenti.
### È disponibile una versione di prova per i test?
 Sì, puoi ottenere una prova gratuita di GroupDocs.Annotation da[Qui](https://releases.groupdocs.com/).