---
title: Aggiungi l'annotazione del frammento di testo di ricerca al documento
linktitle: Aggiungi l'annotazione del frammento di testo di ricerca al documento
second_title: API GroupDocs.Annotation .NET
description: Esplora la potenza di GroupDocs.Annotation per .NET e aggiungi facilmente funzionalità di annotazione dei documenti alle tue applicazioni.
weight: 20
url: /it/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Aggiungi l'annotazione del frammento di testo di ricerca al documento

## introduzione
Nell'ambito dello sviluppo .NET, GroupDocs.Annotation si distingue come un potente strumento per annotare i documenti senza problemi. Che tu sia uno sviluppatore esperto o che tu stia semplicemente entrando nel mondo di .NET, questo tutorial completo ti guiderà attraverso gli elementi essenziali dell'utilizzo di GroupDocs.Annotation per .NET, dall'importazione degli spazi dei nomi alla padronanza delle complessità dell'aggiunta di annotazioni di frammenti di testo di ricerca al tuo documenti.
## introduzione
GroupDocs.Annotation per .NET consente agli sviluppatori di incorporare facilmente funzionalità di annotazione dei documenti nelle loro applicazioni. Grazie alla sua API intuitiva e alle sue robuste funzionalità, gli sviluppatori possono annotare vari formati di documenti, inclusi PDF, documenti di Microsoft Office, immagini e altro ancora.
## Prerequisiti
Prima di immergerti in GroupDocs.Annotation per .NET, assicurati di disporre dei seguenti prerequisiti:

## Importa spazi dei nomi
Innanzitutto, importa gli spazi dei nomi necessari per accedere alle classi e ai metodi GroupDocs.Annotation nel tuo progetto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: definire il percorso di output
Inizia definendo il percorso di output in cui verrà salvato il documento annotato:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializza Annotatore
 Successivamente, inizializza un'istanza di`Annotator` class fornendo il percorso del documento che desideri annotare:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Passaggio 3: creare un'annotazione del frammento di testo di ricerca
 Creare un`SearchTextFragment` oggetto con le proprietà desiderate, ad esempio testo da cercare, dimensione del carattere, famiglia di caratteri, colore del carattere e colore di sfondo:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Passaggio 4: aggiungi annotazione
 Aggiungi l'annotazione del frammento di testo di ricerca creato al documento utilizzando il comando`Add` metodo dell'annotatore:
```csharp
annotator.Add(searchText);
```
## Passaggio 5: salva il documento con annotazioni
Salva il documento annotato nel percorso di output specificato:
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: Visualizza il messaggio di successo
Informa l'utente che il documento è stato salvato con successo:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, GroupDocs.Annotation per .NET semplifica il processo di aggiunta di annotazioni ai documenti, migliorando la collaborazione e i processi di revisione dei documenti. Seguendo i passaggi descritti in questa guida, puoi integrare perfettamente le funzionalità di annotazione dei documenti nelle tue applicazioni .NET.
## Domande frequenti
### GroupDocs.Annotation è compatibile con tutti i formati di documenti?
Sì, GroupDocs.Annotation supporta un'ampia gamma di formati di documenti, inclusi PDF, documenti di Microsoft Office, immagini e altro ancora.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente! GroupDocs.Annotation fornisce ampie opzioni di personalizzazione per le annotazioni, consentendo di regolare proprietà come dimensione, colore e stile del carattere.
### È disponibile una prova gratuita per GroupDocs.Annotation?
 Sì, puoi accedere a una prova gratuita di GroupDocs.Annotation per esplorarne le caratteristiche e le capacità prima di effettuare un acquisto[Qui](https://releases.groupdocs.com/)..
### Dove posso trovare supporto per GroupDocs.Annotation?
 Per supporto e assistenza con GroupDocs.Annotation, puoi visitare GroupDocs[Forum](https://forum.groupdocs.com/c/annotation/10) dedicato a domande e discussioni relative alle annotazioni.
### Come posso ottenere una licenza temporanea per GroupDocs.Annotation?
 È possibile acquisire una licenza temporanea per GroupDocs.Annotation tramite GroupDocs[sito web](https://purchase.groupdocs.com/temporary-license/), consentendoti di valutare il prodotto in modo completo.